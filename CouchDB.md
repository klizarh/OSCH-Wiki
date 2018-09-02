[CouchDB](http://couchdb.apache.org/), an no-SQL database, is the data storage tool used by the MVP.  If you are use to a SQL relational database, Couch can take a bit of work to get your head around it; but once you get it working, it is easy to use and quite robust, and comes with a built in Soap Rest API.

CouchDB stores data as document files.  We are using [JSON structured files](https://github.com/futureag/blog/wiki/Storage-and-Message-Structures).

Read the documentation and Google for examples.  The following is a quick summary of what I found to be helpful starting knowledge.  Couch is easy, once you understand how it 'thinks', but it can take days to stumble down dead-ends and syntax mistakes.  Couch needs to be understood as four separate parts, and in two 'flavors'; Mango indexes and queries, and Map/Reduce functions and queries.  Don't confuse Mango and map/reduce; a Mango query will not work against /_find, and you cannot exchange the query language between the two.  Start with with existing map/reduce functions and what is in the MVP code (ie graph reports), get something working and modify from there.  The Futon interface to CouchDB is good for building functions and queries, but it doesn't have much in the way of debugging and help.

## Mango
Mango is is the data 'slice and dice' tool.  For it to run you need to index the documents on the fields you will search against.  The index needs to be sequenced in the order you will query.  The real power of Mango is the query capabilities; the query is a JSON sturcture where you specify the conditions of what you are searching for, what fields you want returned, sort order and how many records to return.  A query can look something like this:
> {"selector":{"start_date.timestamp":{"$lt":ts}, "status.status_qualifier":{"$eq": "Success"}, "activity_type":{"$eq":"Environment_Observation"}, "subject.name":{"$eq": "Air"},"subject.location.name": {"$eq": "Top"},"subject.attribute.name": {"$eq": "Temperature"}}, "fields":["start_date.timestamp", "subject.attribute.value"], "sort":[{"start_date.timestamp":"desc"}], "limit":250}

## Map/Reduce
Map/Reduce are (usually) Javascript functions that state an if condition of what data to select and return (the map function).  This function always returns the document id, an index key and a value.  The optional reduce function can do aggregate functions over these records.  There are built in reduce functions for _sum, _count and _stats.  The query side of map/reduce seems limited, but has some nifty surprises; in addition to specifying a specific key or key range, it allows for the results to be grouped.  The trick of grouping is to have a key array.  For example, a data based key of:
> [2018, 08, 25]
will allow you to search by  a data or date range (first of August through September of 2018):
> startkey=[2018, 08, 1], endkey=[2018, 09, 30] 
By adding a group=True and group_level=2 you could get monthly summaries, and group_level=3 would give you daily summaries.

## Accessing the database
Couch is accessed via HTTP requests.  Some of this can be done via a browser query line (for database status), but queries usually take a more robust tool.  The Linux command line tool Curl can do a lot, but I found it to get picky about quotes and escaping '[' to the point I gave up on it.  I initially was using the Python library requests, which is a simple HTTP request tool, but found it was messing up my array searches; it worked fine for Mango queries, but was giving problems for map/reduce queries.  At this time I am standardizing on the couchdb library.

To access the database you specify it as a URL:
If the instance of Couch is on the same machine where you are running the code the couchdb library will default to:
> localhost:5984
For a remote machine you specify:
> http://{url name}:{port}/{database}
For remote machines with security, you specify:
> http://{user}:{pwd}@{url name}:{port}/{database}
To the end of this is a specification of what you want to access.  For Mango queries it always goes against
> /_find
Map/Reduce queries go against the design document and specific view within it:
> /_design/{document name}/_view{view name}
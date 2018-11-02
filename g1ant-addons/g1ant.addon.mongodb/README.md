# G1ANT.Addon.Mongodb

**MongoDB Addon for G1ANT.Robot**

Simple addon for fetching data from MonogDB \(NoSQL database\)

**Simple usage**

```text
mongodb.init connectionstring ‴mongodb://user:pass@127.0.0.1:27017‴ databasename ‴db_name‴
mongodb.find collection ‴collection_name‴  filter ‴{name : John}‴ sort ‴{_id:-1}‴ skip 5 limit 10 result ♥json
dialog message ♥json
```

Results are returned as JSON formatted into string

See more:  


* [about Mongo connection string](https://mongodb.github.io/mongo-java-driver/3.5/javadoc/com/mongodb/ConnectionString.html)
* [format query into collection](https://www.tutorialspoint.com/mongodb/mongodb_query_document.htm)
* [sorting in MongoDB](https://www.tutorialspoint.com/mongodb/mongodb_sort_record.htm)
* [limiting and skiping records](https://www.tutorialspoint.com/mongodb/mongodb_limit_record.htm)


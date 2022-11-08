MongoDB is a document database. It stores data in a type of JSON format called BSON.

MongoDB is a document database which is often referred to as a non-relational database.

The [MongoDB Query API](https://www.mongodb.com/docs/manual/query-api/?utm_campaign=w3schools_mdb&utm_source=w3schools&utm_medium=referral) is the way you will interact with your data. The MongoDB Query API can be used two ways:

- CRUD Operations
- Aggregation Pipelines

# CRUD

create collection

```
db.createCollection("posts")
```

insert document

```
db.posts.insertOne({
  title: "Post Title 1",
  body: "Body of post.",
  category: "News",
  likes: 1,
  tags: ["news", "events"],
  date: Date()
})


db.posts.insertMany([  
  {
    title: "Post Title 2",
    body: "Body of post.",
    category: "Event",
    likes: 2,
    tags: ["news", "events"],
    date: Date()
  },
  {
    title: "Post Title 3",
    body: "Body of post.",
    category: "Technology",
    likes: 3,
    tags: ["news", "events"],
    date: Date()
}
])
```

find,first argument query, second project field

```sql
db.posts.find() -- This method accepts a query object. If left empty, all documents will be returned.

db.posts.findOne() -- This method accepts a query object. If left empty, it will return the first document it finds.

db.posts.find( {category: "News"} )

db.posts.find({}, {_id:0, title: 1, date: 1})
 -- Both find and findone methods accept a second parameter called projection. This parameter is an object that describes which fields to include in the results.
 -- use a 1 to include a field and 0 to exclude a field.
```

update

```
//first argument query, second new value
db.posts.updateOne( { title: "Post Title 1" }, { $set: { likes: 2 } } ) 

db.posts.updateOne( 
  { title: "Post Title 5" }, 
  {
    $set: 
      {
        title: "Post Title 5",
        body: "Body of post.",
        category: "Event",
        likes: 5,
        tags: ["news", "events"],
        date: Date()
      }
  }, 
  { upsert: true }
)

db.posts.updateMany({}, { $set: { likes: 1 } }) -- if it is not found, you can use the upsert option.
```

delete

```
db.posts.deleteOne({ title: "Post Title 5" }) -- delete the first document that matches the query provided.

b.posts.deleteMany({ category: "Technology" })
```



# Operator

### Comparison

The following operators can be used in queries to compare values:

- `$eq`: Values are equal
- `$ne`: Values are not equal
- `$gt`: Value is greater than another value
- `$gte`: Value is greater than or equal to another value
- `$lt`: Value is less than another value
- `$lte`: Value is less than or equal to another value
- `$in`: Value is matched within an array

### Logical

The following operators can logically compare multiple queries.

- `$and`: Returns documents where both queries match
- `$or`: Returns documents where either query matches
- `$nor`: Returns documents where both queries fail to match
- `$not`: Returns documents where the query does not match

### Evaluation

The following operators assist in evaluating documents.

- `$regex`: Allows the use of regular expressions when evaluating field values
- `$text`: Performs a text search
- `$where`: Uses a JavaScript expression to match documents



There are many update operators that can be used during document updates.

### Fields

The following operators can be used to update fields:

- `$currentDate`: Sets the field value to the current date
- `$inc`: Increments the field value
- `$rename`: Renames the field
- `$set`: Sets the value of a field
- `$unset`: Removes the field from the document

### Array

The following operators assist with updating arrays.

- `$addToSet`: Adds distinct elements to an array
- `$pop`: Removes the first or last element of an array
- `$pull`: Removes all elements from an array that match the query
- `$push`: Adds an element to an array



# Aggregation

Aggregation operations allow you to group, sort, perform calculations, analyze data, and much more.

Aggregation pipelines can have one or more "stages". The order of these stages are important. Each stage acts upon the results of the previous stage.



```sql
-- group document by property_type
{ $group : { _id : "$property_type" } }

--  limits the number of documents passed to the next stage.
{ $limit: 1 }

-- passes only the specified fields along to the next aggregation stage.
{
    $project: {
      "name": 1,
      "cuisine": 1,
      "address": 1
    }
 } 
 
 -- sorts all documents in the specified sort order.
{ 
    $sort: { "accommodates": -1 } 
  }
  
-- filter documents that match the query provided.
{ $match : { property_type : "House" } }

-- add new field
{
    $addFields: {
      avgGrade: { $avg: "$grades.score" }
    }
  }
  
-- count return the number of documents at the $count stage
{
    $count: "totalChinese"
  }

-- lookup, performs a left outer join to a collection in the same database.
{
    $lookup: {
      from: "movies",
      localField: "movie_id",
      foreignField: "_id",
      as: "movie_details",
    },
  }
  
  
-- out, writes the returned documents from the aggregation pipeline to a collection.
-- The $out stage must be the last stage of the aggregation pipeline.
{ $out: "properties_by_type" }
-- create a new collection called properties_by_type in the current database and write the resulting documents into that collection.
```


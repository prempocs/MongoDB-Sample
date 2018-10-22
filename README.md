# MongoDB-Sample
##Commands

### 1 Show Databases
  		 show dbs	
### 2 Create Database
  		 use  database-name 
### 3 Drop Database
      db.dropDatabase()
### 1 Show Collection
  		 show collections
### 2 Create Collection
  		db.createCollection(collection-name, { capped : true, autoIndexId : true, size : 6142800, max : 10000 } )
### 3 Drop Collection
      db.COLLECTION_NAME.drop()
      
      
### Insert Document    
        >db.post.insert([
           {
              title: 'MongoDB Overview', 
              description: 'MongoDB is no sql database',
              by: 'tutorials point',
              url: 'http://www.tutorialspoint.com',
              tags: ['mongodb', 'database', 'NoSQL'],
              likes: 100
           },

           {
              title: 'NoSQL Database', 
              description: "NoSQL database doesn't have tables",
              by: 'tutorials point',
              url: 'http://www.tutorialspoint.com',
              tags: ['mongodb', 'database', 'NoSQL'],
              likes: 20, 
              comments: [	
                 {
                    user:'user1',
                    message: 'My first comment',
                    dateCreated: new Date(2013,11,10,2,35),
                    like: 0 
                 }
              ]
           }
        ])
  
### Query Document
      db.mycol.find().pretty()
### Update Document
      >db.COLLECTION_NAME.update(SELECTION_CRITERIA, UPDATED_DATA)
      >db.COLLECTION_NAME.save({_id:ObjectId(),NEW_DATA})
### Delete Document
#### Remove All
      >db.COLLECTION_NAME.remove()
#### Remove based on criteria
      >db.COLLECTION_NAME.remove(DELLETION_CRITTERIA)
#### Remove Just one
      >db.COLLECTION_NAME.remove(DELETION_CRITERIA,1)

### Projection
    >db.COLLECTION_NAME.find({},{KEY:flag})
    flag means true or false
### Pagination
    >db.COLLECTION_NAME.find().limit(TO).skip(FROM)
### Sorting
    >db.COLLECTION_NAME.find().sort({KEY:1})
### Indexing
    db.COLLECTION_NAME.ensureIndex({KEY:1})
    ensureIndex() method also accepts list of options (which are optional). Following is the list −
    
    Parameter           |	Type 	     |    Description
    ------------------- | ---------- | ----------------
    background         |	Boolean |	Builds the index in the background so that building an index does not block other database activities.Specify true to build in the background. The default value is false.
    unique             |	Boolean |    Creates a unique index so that the collection will not accept insertion of documents where the index  key or keys match an existing value in the index. Specify true to create a unique index. The default value is false.name 	string 	The name of the index. If unspecified, MongoDB generates an index name by concatenating the names of the indexed fields and the sort order.
    dropDups 	         |  Boolean  |Creates a unique index on a field that may have duplicates. MongoDB indexes only the first occurrence of a key and removes all documents from the collection that contain subsequent occurrences of that key. Specify true to create unique index. The default value is false.
    sparse 	           |  Boolean 	|If true, the index only references documents with the specified field. These indexes use less space but behave differently in some situations (particularly sorts). The default value is false.
    expireAfterSeconds |  integer 	|Specifies a value, in seconds, as a TTL to control how long MongoDB retains documents in this collection.
    v 	               |  index version |	The index version number. The default index version depends on the version of MongoDB running when creating the index.
    weights            |	document     |	The weight is a number ranging from 1 to 99,999 and denotes the significance of the field relative to the other indexed fields in terms of the score.
    default_language   | 	string     |	For a text index, the language that determines the list of stop words and the rules for the stemmer and tokenizer. The default value is english.
    language_override  |	string       |	For a text index, specify the name of the field in the document that contains, the language to override the default language. The default value is language.
### Aggregation
      db.COLLECTION_NAME.aggregate(AGGREGATE_OPERATION)
      Expression |	Description |	Example
      $sum       |	Sums up the defined value from all documents in the collection. 	|db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$sum : "$likes"}}}])
      $avg       |	Calculates the average of all given values from all documents in the collection. 		|db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$avg : "$likes"}}}])
      $min       |	Gets the minimum of the corresponding values from all documents in the collection. 		|db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$min : "$likes"}}}])
      $max       |	Gets the maximum of the corresponding values from all documents in the collection. 	|	db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$max : "$likes"}}}])
      $push      |	Inserts the value to an array in the resulting document. 	|	db.mycol.aggregate([{$group : {_id : "$by_user", url : {$push: "$url"}}}])
      $addToSet  |	Inserts the value to an array in the resulting document but does not create duplicates. 	|	db.mycol.aggregate([{$group : {_id : "$by_user", url : {$addToSet : "$url"}}}])
      $first     |	Gets the first document from the source documents according to the grouping. Typically this makes only sense together with some previously applied “$sort”-stage. 	|	db.mycol.aggregate([{$group : {_id : "$by_user", first_url : {$first : "$url"}}}])
      $last 	   |  Gets the last document from the source documents according to the grouping. Typically this makes only sense together with some previously applied “$sort”-stage. 	|	db.mycol.aggregate([{$group : {_id : "$by_user", last_url : {$last : "$url"}}}]

### Pipeline Concept

In UNIX command, shell pipeline means the possibility to execute an operation on some input and use the output as the input for the next command and so on. MongoDB also supports same concept in aggregation framework. There is a set of possible stages and each of those is taken as a set of documents as an input and produces a resulting set of documents (or the final resulting JSON document at the end of the pipeline). This can then in turn be used for the next stage and so on.

Following are the possible stages in aggregation framework −

    $project − Used to select some specific fields from a collection.

    $match − This is a filtering operation and thus this can reduce the amount of documents that are given as input to the next stage.

    $group − This does the actual aggregation as discussed above.

    $sort − Sorts the documents.

    $skip − With this, it is possible to skip forward in the list of documents for a given amount of documents.

    $limit − This limits the amount of documents to look at, by the given number starting from the current positions.

    $unwind − This is used to unwind document that are using arrays. When using an array, the data is kind of pre-joined and this operation will be undone with this to have individual documents again. Thus with this stage we will increase the amount of documents for the next stage.

### Indexing
### Indexing
### Indexing
### Indexing
    
    
    
    
      

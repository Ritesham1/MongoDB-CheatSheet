# MongoDB-CheatSheet
Quick references to get you onboard in MongoDB

## Show All Databases

```
show dbs
```

## Show Current Database

```
db
```

## Create Or Switch Database

```
use mydb_test
```

## Drop

```
db.dropDatabase()
```

## Create Collection

```
db.createCollection('rapid')
```

## Show Collections

```
show collections
```

## Insert Row

```
db.rapid.insert({
  title: 'Post One',
  body: 'Body of post one',
  category: 'News',
  tags: ['news', 'events'],
  user: {
    name: 'Ritesham Shastri',
    status: 'author'
  },
  date: Date()
})
```

## Insert Multiple Rows

```
db.rapid.insertMany([
  {
    title: 'Post Two',
    body: 'Body of post two',
    category: 'Technology',
    date: Date()
  },
  {
    title: 'Post Three',
    body: 'Body of post three',
    category: 'News',
    date: Date()
  },
  {
    title: 'Post Four',
    body: 'Body of post three',
    category: 'Entertainment',
    date: Date()
  }
])
```

## Get All Rows

```
db.rapid.find()
```

## Get All Rows Formatted

```
db.rapid.find().pretty()
```

## Find Rows

```
db.rapid.find({ category: 'News' })
```

## Sort Rows

```
# asc
db.rapid.find().sort({ title: 1 }).pretty()
# desc
db.rapid.find().sort({ title: -1 }).pretty()
```

## Count Rows

```
db.rapid.find().count()
db.rapid.find({ category: 'news' }).count()
```

## Limit Rows

```
db.rapid.find().limit(2).pretty()
```

## Chaining

```
db.rapid.find().limit(2).sort({ title: 1 }).pretty()
```

## Foreach

```
db.rapid.find().forEach(function(doc) {
  print("Blog Post: " + doc.title)
})
```

## Find One Row

```
db.rapid.findOne({ category: 'News' })
```

## Find Specific Fields

```
db.rapid.find({ title: 'Post One' }, {
  title: 1,
  author: 1
})
```

## Update Row

```
db.rapid.update({ title: 'Post Two' },
{
  title: 'Post Two',
  body: 'New body for post 2',
  date: Date()
},
{
  upsert: true
})
```

## Update Specific Field

```
db.rapid.update({ title: 'Post Two' },
{
  $set: {
    body: 'Body for post 2',
    category: 'Technology'
  }
})
```

## Increment Field (\$inc)

```
db.rapid.update({ title: 'Post Two' },
{
  $inc: {
    likes: 5
  }
})
```

## Rename Field

```
db.rapid.update({ title: 'Post Two' },
{
  $rename: {
    likes: 'views'
  }
})
```

## Delete Row

```
db.rapid.remove({ title: 'Post Four' })
```

## Sub-Documents

```
db.rapid.update({ title: 'Post One' },
{
  $set: {
    comments: [
      {
        body: 'Comment One',
        user: 'Veeresh Kumar',
        date: Date()
      },
      {
        body: 'Comment Two',
        user: 'Vaishnavi Solanki',
        date: Date()
      }
    ]
  }
})
```

## Find By Element in Array (\$elemMatch)

```
db.rapid.find({
  comments: {
     $elemMatch: {
       user: 'Veeresh Kumar'
       }
    }
  }
)
```

## Add Index

```
db.rapid.createIndex({ title: 'text' })
```

## Text Search

```
db.rapid.find({
  $text: {
    $search: "\"Post O\""
    }
})
```

## Greater & Less Than

```
db.rapid.find({ views: { $gt: 2 } })
db.rapid.find({ views: { $gte: 7 } })
db.rapid.find({ views: { $lt: 7 } })
db.rapid.find({ views: { $lte: 7 } })
```

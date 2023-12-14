## Generic Commands

#### Show Databases
shows dbs

#### Use Database
use admin

#### create and use Database
use school

#### Add data to school db by creating collections
db.createCollection("students")

#### Drop Database
db.dropDatabase()

#### Instert data into students
db.students.insertOne({name:"Gowtham", age:24, gpa: 4})

#### View documents created in a collection
db.students.find()

#### Instert many data into students
db.students.insertMany([{name:"Patric", age:44, gpa: 3},{name:"Jackman", age:34, gpa: 3.4}])

## DataTypes
db.students.insertOne(
    {name:"Hanuma",
     age:24,
     gpa: 3.9,
     fullTime: true,
     registerDate: new Date(),
     graduationDate: null,
     course: ["IR", "Cloud", "OS"],
     address: {
        street: "123 St",
        city: "Cincinnati",
        zip: 12345
     }
    }
    )

## Sort and Limit Documents

### Sort
db.students.find().sort({name:1})
db.students.find().sort({gpa:-1})
Alphabetical/ascending order 1
Reverse Alphabetical/descending order -1

### Limit
db.students.find().limit(1)

### Together
db.students.find().sort({gpa:-1}).limit(1)

## Find
.find({query},{projection})

db.students.find({name:"Gowtham"})
db.students.find({name:"Gowtham", gpa:4})

db.students.find({},{name:true})
db.students.find({},{_id: false, name:true, gpa: true})

## Update
.updateOne(filter, update)

### Set
db.students.updateOne({name:"Gowtham"}, {$set:{fullTime: true}})

### Unset
db.students.updateOne({name:"Gowtham"}, {$unset:{fullTime: ""}})

### Update Many
db.students.updateMany({}, {$set:{fullTime: true}})

### Update Many if fullTime fields doesn't exists
db.students.updateMany({fullTime: {$exists: false}}, {$set:{fullTime: true}})

## Delete
db.students.deleteOne({name:"Jackman"})
db.students.deleteMany({registerDate:{$exists: false}})

## Comparision Operators
### Not Equal
db.students.find({name:{$ne: "Gowtham"}})

### less/greater than and less/greater than Equal
db.students.find({age:{$gt: 20}})

db.students.find({age:{$lte: 24}})

db.students.find({gpa:{$gte:3.5, $lte: 4}})

### in - matching values
db.students.find({name:{$in:["Gowtham", "Hanuma"]}})

### not in - not matching values
db.students.find({name:{$nin:["Gowtham", "Hanuma"]}})


## Logical Operators
### $and
db.students.find({$and: [{fullTime: true}, {age: {$gt: 24}}]})

### $or
db.students.find({$or: [{fullTime: true}, {age: {$gt: 24}}]})

### $nor - both false
db.students.find({$nor: [{fullTime: true}, {age: {$gt: 24}}]})

### $not
db.students.find({age: {$not: {$lt: 24}}})

## Indexes
Quick lookup of a field.

### Linear search
db.students.find({name:"Hanuma"}).explain("executionStats")


### Apply index
db.students.createIndex({name: 1})

### Get Indexes
db.students.getIndexes()



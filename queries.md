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

#### DataTypes
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

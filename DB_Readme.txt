# College DB Assignment

## Database Name
college_db

## Tool Used
MongoDB Compass Shell (mongosh)

## Description
This database contains collections for:
1. Student Admission
2. Career Guidance
3. Academic Events and Notices

## Commands Used
- use college_db → Creates and switches database
- db.createCollection("students") → Stores student data
- db.createCollection("courses") → Stores course data
- db.createCollection("admissions") → Stores admission records
- db.createCollection("admission_enquiries")
- db.createCollection("career_domains")
- db.createCollection("counselors")
- db.createCollection("career_requests")
- db.createCollection("events")
- db.createCollection("event_registrations")
- db.createCollection("notices")

## Validation
Schema validation used with:
- bsonType
- required
- enum
- minimum
- regex pattern

## Assignment 2 – Data Insertion and Updates

### Insert Operations Used:
- insertMany() used for all collections
- ISODate() used for date fields
- Arrays used in career_requests.skills

### Update Operators Used:
- $set → update student mobile and admission status
- $push → add new skill
- $pull → remove skill
- $addToSet → avoid duplicate skill
- replaceOne() → replace full notice document

## Assignment 3 – Queries & Administration

### Operators Used:
- Comparison: $eq, $gt, $in
- Logical: $and, $or
- Element: $exists, $type
- Evaluation: $regex, $expr
- Array: $size, $all, $elemMatch

### Aggregation:
- $match, $group, $project, $sort, $skip, $limit, $unwind

### Indexing:
- createIndex(), getIndexes(), dropIndex()


Operators Used:
Comparison Operators:
Used to compare values in queries.
$eq → Matches equal values
$gt → Greater than
$lt → Less than
$in → Matches values from a list

Used for:
Finding students by age (using dateOfBirth)
Finding courses by fee range
Filtering admissions by status

Logical Operators:
Used to combine multiple conditions.
$and → All conditions must be true
$or → Any one condition true
$not → Negates a condition
$nor → None of the conditions true

Used for:
Fetching students based on multiple rules
Filtering admissions using combined logic

Element Operators:
$exists → Checks whether a field is present
Used to find documents where optional fields like description exist.

$type → Checks BSON data type
Used to confirm fields like dateOfBirth are stored as Date type.

Evaluation Operators:
$regex → Pattern matching in text
Used for searching names starting with specific letters.

$expr → Compare fields inside the same document
Used for advanced conditions like comparing fee values.

Array Operators:
$size → Finds arrays with specific length
$all → Matches arrays containing all given values
$elemMatch → Matches specific element inside array

Used for:
Querying students who have multiple skills in career requests.

Aggregation Framework
Aggregation was used to generate reports and analytics.
$match → Filters documents
$group → Groups data (like GROUP BY in SQL)
$project → Selects specific fields
$sort → Sorts output
$skip → Skips records for pagination
$limit → Limits number of records
$unwind → Breaks array into individual documents

Used for:
Total admissions per course
Career domain popularity
Event registration counts
Paginated student reports

## Indexing
createIndex()
Used to improve query performance on frequently used fields like studentId.

getIndexes()
Used to view all existing indexes in a collection.

dropIndex()
Used to remove unnecessary indexes.

### Backup
Backup created using mongodump command

### Atlas
Connected MongoDB Compass to MongoDB Atlas cluster successfully

## Backup and Restore – college_db

### Backup Method Used
MongoDB Database Tools (mongodump)

### Description
The above command creates a backup of the college_db database.
A new folder named backup/college_db was created containing .bson files for each collection such as:
- students.bson
- courses.bson
- admissions.bson
- career_requests.bson
- events.bson
etc.

### Evidence
Screenshots attached in the screenshots folder:
- mongodump success output
- backup folder structure


# Mini Project – Enhancement of college_db

## Part A: Data Modeling and Validation

### Referenced Fields
The database uses referencing instead of embedding to avoid data duplication and improve flexibility.
Examples:
- students.studentId referenced in admissions, career_requests, event_registrations
- courses.courseId referenced in admissions
- events.eventId referenced in event_registrations

Referencing allows independent updates and better scalability.

### Schema Validation Review
Schema validation includes:
- Required fields using required[]
- Enum validation using enum
- Data type enforcement using bsonType
- Minimum value checks using minimum

Validation was demonstrated using a failed insert which returned:
"Document failed validation"

---

## Part B: Advanced Aggregation

### $lookup
Used to join students with admissions to retrieve combined details.

### $facet
Used to generate multiple reports (by status and by course) in a single query.

### $bucket
Used to categorize courses based on fee ranges.

### $group and $project
Used to summarize data and format output reports.

---

## Part C: Query Optimization

### explain()
Used to analyze query performance.

Before index:
- Query used COLLSCAN (collection scan)

After creating index on studentId:
- Query used IXSCAN (index scan)
- Performance improved

Index was created because studentId is frequently used in filters.

Part D: MongoDB Atlas and Administration

MongoDB Atlas Setup and Verification
1. Create a Free-Tier MongoDB Atlas Cluster
Go to https://www.mongodb.com/atlas and sign up/login.
Click Create → Deployment and select M0 Free Tier.
Choose a cloud provider and region, then create the cluster.
Create a database user (username & password).
Go to Network Access → Add IP Address → Allow access from anywhere (0.0.0.0/0).
This completes the cloud database setup.

2. Connect college_db to Atlas using MongoDB Compass
In Atlas, go to Cluster → Connect → Compass.
Copy the connection string:
mongodb+srv://username:<password>@cluster0.xxxxx.mongodb.net/
Replace <password> with your actual password.
Paste the string into MongoDB Compass and click Connect.
Create a database named college_db
Create collections such as:
students
courses
admissions
events
career_requests
event_registrations

3. Verify Data Availability and Query Execution
Check collections and data:
Open college_db in MongoDB Compass
Click any collection (e.g., students)
View data under the Documents tab

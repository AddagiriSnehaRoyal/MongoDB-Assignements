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

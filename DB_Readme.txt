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


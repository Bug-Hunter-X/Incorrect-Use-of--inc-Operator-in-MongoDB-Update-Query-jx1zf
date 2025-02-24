# Incorrect Use of $inc Operator in MongoDB Update Query
This repository demonstrates an example of an uncommon error in MongoDB update queries: Incorrectly using the $inc operator with a string value.

## Bug Description
The bug arises from using the `$inc` operator with a string value instead of a numeric value in the update query. This results in unexpected behavior and potential data corruption.

## Bug Reproduction
1. Create a MongoDB collection named `myCollection`. 
2. Insert a document with an `_id` of 1 and a `field` of 0: `db.myCollection.insertOne({ _id: 1, field: 0 })`.
3. Run the faulty update query: `db.collection('myCollection').updateOne({ _id: 1 }, { $inc: { field: 'value' } });`
4. Observe the result of the update.  The expected result would be an increment of the field 'field'. However, the actual result will be an unexpected change or error.

## Solution
The solution is to ensure that the value passed to the `$inc` operator is a number.  Correct query should be:

`db.collection('myCollection').updateOne({ _id: 1 }, { $inc: { field: 5 } });`

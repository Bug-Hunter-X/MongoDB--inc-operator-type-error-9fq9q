# MongoDB $inc Operator Type Error

This repository demonstrates a common error when using the `$inc` operator in MongoDB update operations. The `$inc` operator is used to increment a numerical field in a document.  However, if you provide a non-numeric value to `$inc` as a parameter, it will throw an error.

## Bug
The bug is in the following line of code:
```javascript
db.collection.updateOne({"_id":ObjectId("someId")},{$inc:{counter: '1'}});
```
The `counter` is incremented with a string value of '1', causing the update to fail. The correct usage should be with a number value.

## Solution
The solution is to correct the datatype passed to the `$inc` operator to be numeric.
```javascript
db.collection.updateOne({"_id":ObjectId("someId")},{$inc:{counter: 1}});
```
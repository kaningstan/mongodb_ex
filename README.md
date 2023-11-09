# mongodb_ex

 ** 01.1. Create a Database called customers. **

   ```
use customers
```

**2. Create a collection called customerdetails.**
```
db.createCollection("customerdetails")
{ ok: 1 }
customers> 

```
**3. Insert all documents into the collection named   customerdetails.**
```
db.customerdetails.insertMany([{name:"john",age:25,gender:"male",city:"new york"},{name:"emily",age:22,gender:"female",city:"london"},{name:"daniel",age:28,gender:"male",city:"sydney"},{name:"sophia",age:24,gender:"female",city:"paris"},{name:"william",age:26,gender:"male",city:"chicago"},{name:"olivia",age:23,gender:"female",city:"los angeles"},{name:"benjamin",age:27,gender:"male",city:"toronto"},{name:"mila",age:29,gender:"female",city:"berlin"},{name:"james",age:30,gender:"male",city:"tokyo"}])



{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId("654caa00114b079e9176d260"),
    '1': ObjectId("654caa00114b079e9176d261"),
    '2': ObjectId("654caa00114b079e9176d262"),
    '3': ObjectId("654caa00114b079e9176d263"),
    '4': ObjectId("654caa00114b079e9176d264"),
    '5': ObjectId("654caa00114b079e9176d265"),
    '6': ObjectId("654caa00114b079e9176d266"),
    '7': ObjectId("654caa00114b079e9176d267"),
    '8': ObjectId("654caa00114b079e9176d268")
  }
}
```
** 4. Retrieve all documents from the collection and sort the results by the “age” field    in ascending order.**
```
 db.customerdetails.find().sort({age:1}).pretty()


[
  {
    _id: ObjectId("654caa00114b079e9176d261"),
    name: 'emily',
    age: 22,
    gender: 'female',
    city: 'london'
  },
  {
    _id: ObjectId("654caa00114b079e9176d265"),
    name: 'olivia',
    age: 23,
    gender: 'female',
    city: 'los angeles'
  },
  {
    _id: ObjectId("654caa00114b079e9176d263"),
    name: 'sophia',
    age: 24,
    gender: 'female',
    city: 'paris'
  },
  {
    _id: ObjectId("654caa00114b079e9176d260"),
    name: 'john',
    age: 25,
    gender: 'male',
    city: 'new york'
  },
  {
    _id: ObjectId("654caa00114b079e9176d264"),
    name: 'william',
    age: 26,
    gender: 'male',
    city: 'chicago'
  },
  {
    _id: ObjectId("654caa00114b079e9176d266"),
    name: 'benjamin',
    age: 27,
    gender: 'male',
    city: 'toronto'
  },
  {
    _id: ObjectId("654caa00114b079e9176d262"),
    name: 'daniel',
    age: 28,
    gender: 'male',
    city: 'sydney'
  },
  {
    _id: ObjectId("654caa00114b079e9176d267"),
    name: 'mila',
    age: 29,
    gender: 'female',
    city: 'berlin'
  },
  {
    _id: ObjectId("654caa00114b079e9176d268"),
    name: 'james',
    age: 30,
    gender: 'male',
    city: 'tokyo'
  }
]
```
**5. Count the number of females.**

``` db.customerdetails.countDocuments({gender:"female"})


4
customers>
```
**6.Insert one document into the customerdetails collection.**
```
db.customerdetails.insertOne({name:"kani",age:21,gender:"male",city:"jaffna"})

_id: ObjectId("654cae2d114b079e9176d269"),
    name: 'kani',
    age: 21,
    gender: 'male',
    city: 'jaffna'
```


**7. Update city=SriLanka to John.**
```
customers> db.customerdetails.update({name:"john",age:25},{$set:{city:"jaffna"}},{upsert:true})



DeprecationWarning: Collection.update() is deprecated. Use updateOne, updateMany, or bulkWrite.
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
customers> db.customerdetails.find()
[
  {
    _id: ObjectId("654caa00114b079e9176d260"),
    name: 'john',
    age: 25,
    gender: 'male',
    city: 'jaffna'
```

**8. Remove the customer from Tokyo.**
```
db.customerdetails.remove({city:"tokyo"})


DeprecationWarning: Collection.remove() is deprecated. Use deleteOne, deleteMany, findOneAndDelete, or bulkWrite.
{ acknowledged: true, deletedCount: 1 }
```

**9.  Find customers not from Los Angeles.**
```
db.customerdetails.find({city:{$ne:"los angeles"}})

{
    _id: ObjectId("654caa00114b079e9176d260"),
    name: 'john',
    age: 25,
    gender: 'male',
    city: 'jaffna'
  },
  {
    _id: ObjectId("654caa00114b079e9176d261"),
    name: 'emily',
    age: 22,
    gender: 'female',
    city: 'london'
  },
  {
    _id: ObjectId("654caa00114b079e9176d262"),
    name: 'daniel',
    age: 28,
    gender: 'male',
    city: 'sydney'
  },
  {
    _id: ObjectId("654caa00114b079e9176d263"),
    name: 'sophia',
    age: 24,
    gender: 'female',
    city: 'paris'
  },
  {
    _id: ObjectId("654caa00114b079e9176d264"),
    name: 'william',
    age: 26,
    gender: 'male',
    city: 'chicago'
  },
  {
    _id: ObjectId("654caa00114b079e9176d266"),
    name: 'benjamin',
    age: 27,
    gender: 'male',
    city: 'toronto'
  },
  {
    _id: ObjectId("654caa00114b079e9176d267"),
    name: 'mila',
    age: 29,
    gender: 'female',
    city: 'berlin'
  },
  {
    _id: ObjectId("654cae2d114b079e9176d269"),
    name: 'kani',
    age: 21,
    gender: 'male',
    city: 'jaffna'
  }
]
```












  

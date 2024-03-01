Practical-3: CRUD USING Mangodb 
Roll No. - 17



test> use userdb;
switched to db userdb
userdb> db.createCollection("users")
{ ok: 1 }
userdb> db.users.insertOne({
...
...   name: "Angela",
...
...   age: 27,
...
... });
{
  acknowledged: true,
  insertedId: ObjectId('65e210cd140c00c04de9806e')
}
userdb> db.users.insertMany([
...
...     {
...
...         name: "Angela",
...
...         age: 27,
...
...     },
...
...     {
...
...         name: "Dwight",
...
...         age: 30,
...
...
...
...     },
...
...     {
...
...         name: "Jim",
...
...         age: 29,
...
...     }
...
... ]);
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('65e21100140c00c04de9806f'),
    '1': ObjectId('65e21100140c00c04de98070'),
    '2': ObjectId('65e21100140c00c04de98071')
  }
}
userdb> db.users.find()
[
  {
    _id: ObjectId('65e210cd140c00c04de9806e'),
    name: 'Angela',
    age: 27
  },
  {
    _id: ObjectId('65e21100140c00c04de9806f'),
    name: 'Angela',
    age: 27
  },
  {
    _id: ObjectId('65e21100140c00c04de98070'),
    name: 'Dwight',
    age: 30
  },
  { _id: ObjectId('65e21100140c00c04de98071'), name: 'Jim', age: 29 }
]
userdb> db.users.find({ age: { $gt: 29 } }, { name: 1, age: 1 })
[
  {
    _id: ObjectId('65e21100140c00c04de98070'),
    name: 'Dwight',
    age: 30
  }
]
userdb> db.users.findOne({ name: "Jim" })
{ _id: ObjectId('65e21100140c00c04de98071'), name: 'Jim', age: 29 }
userdb> db.users.updateOne({ name: "Angela" }, { $set: { email: "angela@gmail.com" } })
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
userdb> db.users.updateOne({ name: "Angela" }, { $set: { email: "angela@gmail.com" }})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 0,
  upsertedCount: 0
}
userdb> db.users.updateMany({ age: { $lt: 30 } }, { $set: { status: "active" } })
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 3,
  modifiedCount: 3,
  upsertedCount: 0
}
userdb> db.users.find()
[
  {
    _id: ObjectId('65e210cd140c00c04de9806e'),
    name: 'Angela',
    age: 27,
    email: 'angela@gmail.com',
    status: 'active'
  },
  {
    _id: ObjectId('65e21100140c00c04de9806f'),
    name: 'Angela',
    age: 27,
    status: 'active'
  },
  {
    _id: ObjectId('65e21100140c00c04de98070'),
    name: 'Dwight',
    age: 30
  },
  {
    _id: ObjectId('65e21100140c00c04de98071'),
    name: 'Jim',
    age: 29,
    status: 'active'
  }
]
userdb> db.users.deleteOne({ name: "Angela" })
{ acknowledged: true, deletedCount: 1 }

userdb> db.users.find()
[
  {
    _id: ObjectId('65e21100140c00c04de9806f'),
    name: 'Angela',
    age: 27,
    status: 'active'
  },
  {
    _id: ObjectId('65e21100140c00c04de98070'),
    name: 'Dwight',
    age: 30
  },
  {
    _id: ObjectId('65e21100140c00c04de98071'),
    name: 'Jim',
    age: 29,
    status: 'active'
  }
]
userdb> db.users.deleteMany({ age: { $lt: 30 } })
{ acknowledged: true, deletedCount: 2 }
userdb> db.users.find()
[
  {
    _id: ObjectId('65e21100140c00c04de98070'),
    name: 'Dwight',
    age: 30
  }
]
userdb> db.users.drop()
true
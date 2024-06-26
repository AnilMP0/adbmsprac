# MongoDb Replication

## Configure Primary Node (Port 22334)
```javascript
mongod --port 22334 --dbpath C:\Replication\primary --replSet rs
```
## Configure Secondary Node 1 (Port 22335)
```javascript
mongod --port 22335 --dbpath C:\Replication\replicaset1 --replSet rs
```
## Configure Secondary Node 2 (Port 22336)
```javascript
mongod --port 22336 --dbpath C:\Replication\replicaset2 --replSet rs
```
## Connect to MongoDB Shell (Port 22334)
```javascript
mongosh --port 22334
```
## Initialize the Replication Set
```javascript
rs.initiate({_id: "rs", members: [{_id: 0, host: "localhost:27017"}, {_id: 1, host: "localhost:27018"}, {_id: 2, host: "localhost:27019"}]})
```
## Check Replication Set Status
```javascript
rs.status()
```
Output:
```javascript
  members: [
    {
      _id: 0,
      name: 'localhost:22334',
      health: 1,
      state: 1,
      stateStr: 'PRIMARY',
      uptime: 36,
      syncSourceHost: '',
      syncSourceId: -1,
    },
    {
      _id: 1,
      name: 'localhost:22335',
      health: 1,
      state: 2,
      stateStr: 'SECONDARY',
      uptime: 19,
      syncSourceHost: 'localhost:27017',
      syncSourceId: 0,
    },
    {
      _id: 2,
      name: 'localhost:22336',
      health: 1,
      state: 2,
      stateStr: 'SECONDARY',
      uptime: 12,
      syncSourceHost: 'localhost:27018',
      syncSourceId: 1,
    }
  ]
```

## Create a Database and Collection in the Primary Node
```javascript
use testdb
```
```javascript
db.testcollection.insertOne({name: "example"})
```

## Check if Database and Collection Exist in Secondary Nodes
### > Connect to Secondary Node 1 (Port 22335)
```javascript
mongosh --port 22335
```
## Check if the database exists
```javascript
use testdb
```
```javascript
db.testcollection.find()
```

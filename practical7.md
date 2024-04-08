# Practical 7 - Crud Operation in Neo4j

### *Creating nodes with label Person*



```javascript
CREATE (:Person {name: 'Joe'})
CREATE (:Person {name: 'Jhon'})
CREATE (:College {name: 'Mithibai'})
CREATE (:College {name: 'Wilson'})
```
![image](https://github.com/AsadCodeCraft/Neo4j/assets/157724449/d7c96d84-a64b-4997-a8eb-8b072aa4d792)

### Creating Relationship between Nodes
```javascript
match (a:Person),(b:College) where a.name="Joe" and b.name="Mithibai" create(a)-[:studyin]->(b)
match (a:Person),(b:College) where a.name="Jhon" and b.name="Wilson" create(a)-[:studyin]->(b)
match (a:Person),(b:Person) where a.name="Jhon" and b.name="Joe" create(a)-[:friend]->(b)
```
![image](https://github.com/AsadCodeCraft/Neo4j/assets/157724449/243c11f6-6e57-4b95-b4d5-6f189b3a2f7e)


### Findig/Retreving Nodes
```javascript
match (a:Person) return a
```
![image](https://github.com/AsadCodeCraft/Neo4j/assets/157724449/6c654086-3076-41a3-aada-d14a7c035405)

```javascript
match (a:Person) return a.name
```


### Updating Node Properties
```javascript
match (a:Person{name:"Joe"}) set a.age=20 
match (a:Person{name:"Jhon"}) set a.age=21 
```

### Finding Age of Particular Node with Property Name 
```javascript
match (a:Person) where a.name="Jhon" return a.age #table view
```
![image](https://github.com/AsadCodeCraft/Neo4j/assets/157724449/d3d2be8c-4507-4c15-8a23-06cbb0e4aba6)


### Deleting Node & Relationship
#### > Detaching Relationship & Delteting Node
```javascript
match (a:Person) where a.name="Jhon" detach delete a
```

#### > Detaching Relationship using `label`
```javascript
MATCH (n:Person {name: 'Joe'})-[r:studyin]->() DELETE r #detaching relation ship
```

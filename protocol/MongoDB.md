# `MongoDB`

MongoDB is a widely used, open-source NoSQL database system known for its flexibility and scalability. It stores data in a flexible, JSON-like format called BSON, allowing developers to model complex relationships in their data. MongoDB is designed to handle large volumes of unstructured or semi-structured data, making it suitable for a variety of applications.


### Connect to MongoDB Shell:
mongo

### Show Databases:
show dbs

### Switch Database:
use mydatabase

### Show Collections:
show collections

### Insert Document:
db.myCollection.insert({ field1: "value1", field2: "value2" })

### Query Documents:
db.myCollection.find({ field1: "value1" })

### Tools

MongoDB Compass: MongoDB Compass is a graphical user interface (GUI) tool that provides a visual representation of the database schema, along with features for querying and analyzing data.

mongodump and mongorestore: These command-line tools are used for creating and restoring binary exports of MongoDB data, providing a way to back up and restore databases.

MongoDB Atlas: MongoDB Atlas is a cloud-based database service that provides a fully managed MongoDB database. It offers automated backups, scaling, and monitoring features.

# How to install MongoDB database server on LinuxONE Community Cloud
Open source software (IBMZ/LinuxONE). MongoDB stores data in flexible, JSON-like documents, meaning fields can vary from document to document and data structure can be changed over time

At a high level, MongoDB enables developers that use data to build easily, adapt quickly, and scale reliably. 
In this tutorial, We will be using Rhel 7.


## Prerequisites
 1. Request access to LinuxONE Community Cloud. Follow instructions [here] (https://github.com/PhilaD1/technical-resources)


### Step 1: Configure repository
 
   1.1 Create repo file
   Create a repo file so that you can install MongoDB enterprise directly using yum
   
   For RHEL7.8: 
   ```sh
   # sudo vi /etc/yum.repos.d/mongodb-enterprise-4.4.repo
   ```
   #[mongodb-enterprise-4.4]
name=MongoDB Enterprise Repository
baseurl=https://repo.mongodb.com/yum/redhat/$releasever/mongodb-enterprise/4.4/$basearch/
gpgcheck=1
enabled=1
gpgkey=https://www.mongodb.org/static/pgp/server-4.4.asc
 
   1.2 Save and quite vi
   #wq:


   ### Step 2: Install MongoDB database server on LinuxONE Community Cloud
   
   2.1 Install MongoDB
   Install the MongoDB Enterprise packages
    For RHEL 7.8:
   ```sh
   # sudo yum install -y mongodb-enterprise
   ```
   
    
   ### Step 3: Configure MongoDB server
   
   3.1 Start MongoDB
   ```sh
   # sudo systemctl start mongod
   ```
   If you receive an error similar to the following when starting mongod:
      Failed to start mongod.service: Unit mongod.service not found.
      
   Run the following command first:
             
    ```sh 
    # sudo systemctl daemon-reload
    ```
   
   3.2 Enable MongoDB
   ```sh
   # sudo systemctl enable mongod
   ```
   
   
   3.3 Check status of the MongoDB server
   ```sh
   # sudo systemctl status mongod
   ```
  
    
   3.4 MongoDB Shell
   ```sh
   # mongo
   ```
   
   
   ### Step 4: Create MongoDB Collections
   4.1 Show existing database
   ```sh
   # show dbs; 
   ```
  admin   0.000GB
  config  0.000GB
  local   0.000GB
   
   
   4.2 Create database
   ```sh
   # use demo_db
   ```
  switched to db demo_db
   
   
   4.3 Create Collection
   ```sh
   # db.createCollection('user'); 
   ```
   { "ok" : 1 }
   
   
   4.4 Show collections
   ```sh
   # show collections;
   ```
   user
   
   
   4.5 Insert
   ```sh
   # db.user.insert({"name":"Phila"});
   ```
   WriteResult({ "nInserted" : 1 })
   
   
   4.6 Find collection
   ```sh
   # db.user.find();
   ```
   { "_id" : ObjectId("5f3b6b0a3b6976978ce646c1"), "name" : "Phila" } 
   
   
   4.7 Delete collection
   ```sh
   # db.user.drop()
   ```
   true
   
   
   4.8 Show collections
   ```sh
   # show collections;
   ```
  
  
  WELL DONE!
   
   
 

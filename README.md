# How to install MongoDB database server on LinuxONE Community Cloud
Open source software (IBMZ/LinuxONE). MongoDB stores data in flexible, JSON-like documents, meaning fields can vary from document to document and data structure can be changed over time

At a high level, MongoDB enables developers that use data to build easily, adapt quickly, and scale reliably. 
In this tutorial, We will be using RHEL 7.8


## Prerequisites
 1. Request access to LinuxONE Community Cloud. Follow instructions [here](https://github.com/PhilaD1/technical-resources/blob/master/faststart/deploy-virtual-server.md)


### Step 1: Configure repository
 
   1.1 Create repo file
   Create a repo file so that you can install MongoDB enterprise directly using yum
   
   For RHEL 7.8: 
   ```sh
   # sudo vi /etc/yum.repos.d/mongodb-enterprise-4.4.repo
   ```
   ```sh
   #[mongodb-enterprise-4.4]
    name=MongoDB Enterprise Repository
    baseurl=https://repo.mongodb.com/yum/redhat/$releasever/mongodb-enterprise/4.4/$basearch/
    gpgcheck=1
    enabled=1
    gpgkey=https://www.mongodb.org/static/pgp/server-4.4.asc
   ```
   
   1.2 Save and quite vi
   #wq:


   ### Step 2: Install MongoDB database server on LinuxONE Community Cloud
   
   2.1 Install MongoDB
   Install the MongoDB Enterprise packages
    For RHEL 7.8:
   ```sh
   # sudo yum install -y mongodb-enterprise
   ```
   <img width="678" alt="Screenshot 2020-08-18 at 06 56 44" src="https://user-images.githubusercontent.com/50323060/90484801-fac63a00-e136-11ea-9286-747ad854c789.png">
   <img width="451" alt="Screenshot 2020-08-18 at 06 57 15" src="https://user-images.githubusercontent.com/50323060/90485274-99529b00-e137-11ea-998e-270a44744f72.png">
    
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
  
<img width="676" alt="Screenshot 2020-08-18 at 07 00 54" src="https://user-images.githubusercontent.com/50323060/90486387-2518f700-e139-11ea-9341-165b094bdc86.png">
    
   3.4 MongoDB Shell
   ```sh
   # mongo
   ```
   <img width="676" alt="Screenshot 2020-08-18 at 07" src="https://user-images.githubusercontent.com/50323060/90486447-3cf07b00-e139-11ea-8d17-66de1e93280a.png">
   
   ### Step 4: Create MongoDB Collections
   4.1 Show existing database
   ```sh
   # show dbs; 
   ```
  <img width="114" alt="Screenshot 2020-08-18 at 07 48 44" src="https://user-images.githubusercontent.com/50323060/90487041-2eef2a00-e13a-11ea-8e20-e5d2cb735cac.png">
   
   
   4.2 Create database
   ```sh
   # use demo_db
   ```
   <img width="159" alt="Screenshot 2020-08-18 at 10 02 57" src="https://user-images.githubusercontent.com/50323060/90487084-3e6e7300-e13a-11ea-9db3-a052edabc1d3.png">
   
   
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
   <img width="233" alt="Screenshot 2020-08-18 at 10 06 36" src="https://user-images.githubusercontent.com/50323060/90487342-a2913700-e13a-11ea-8984-6ad8ba8adb04.png">
   
   
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
 
  
  ### WELL DONE!
   
   
 

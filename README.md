## Database Week at the AWS Loft

Database Week at the AWS Loft is an opportunity to learn about Amazon’s broad and deep family of managed database services. These services provide easy, scalable, reliable, and cost-effective ways to manage your data in the cloud.

## Labs

[Getting Started with Linux on Amazon EC2](https://github.com/wrbaldwin/db-week/blob/master/Labs/getting-started-with-ec2-linux.pdf) - This lab will walk you through launching, configuring, and customizing an EC2 virtual machine
to run a web server. It will walk you though successfully provisioning and starting an EC2
instance using the AWS Management Console.

[Managed Database Basics](https://github.com/wrbaldwin/db-week/blob/master/Labs/managed-database-basics.md) - In this lab you will learn, how to create an EC2 instance for use as a SQL client that connects to an RDS/MySQL instance. Next, you will create a database, load a public Landsat dataset into it, and query your database using SQL. Finally, you will learn how to use the RDS console including stopping, starting, monitoring, snapshots and other RDS features.

[Aurora MySQL](https://github.com/wrbaldwin/db-week/blob/master/Labs/aurora-mysql.pdf) - In this lab you will, create Aurora MySQL DB Instance, grant Aurora MySQL access i.e. modify security group to allow access from your computer, and load data from S3 into Aurora MySQL database. Create read replica instance & access table, create a database copy using Aurora “Clone” feature, and perform DML query on primary DB and validate data on primary and cloned DB copy.

[Upgrading and Consolidating MySQL](https://github.com/wrbaldwin/db-week/blob/master/Labs/upgrading-and-consolidating-mySQL.md) - In this lab you will load data into a MySQL instance running on EC2. Next you will create an Aurora MySQL instance. Finally, you will use DMS to migrate data from one MySQL database to another.

[A Simple Database Migration](https://github.com/wrbaldwin/db-week/blob/master/Labs/a-simple-database-migration.md) - This workshop is a hands-on journey for existing Oracle DBAs moving to Aurora PostgreSQL. Attendees will deploy an instance of Aurora PostgreSQL, migrate and generate a test workload on PostgreSQL, and manually monitor the database to understand the workload. They will review a few ways to track queries and their execution plans, and what can be done to optimize the queries. Attendees will also learn how to do the same on Aurora PostgreSQL using Performance Insights for query analysis and tuning.

[Comparing Redis with Relational](https://github.com/wrbaldwin/db-week/blob/master/Labs/comparing-redis-with-relational.md) - In this lab you create an EC2 instance for use as a SQL and Redis client. Next, you will create an RDS instance using MySQL, connect your SQL client instance to your RDS instance. Then you will create a database and load a public landsat dataset into it and query your database using SQL. Finally, you will create an ElastiCache for Redis cluster, connect your Redis client instance to your ElastiCache cluster, and query your ElastiCache cluster using Redis commands.

[Using a Property Graph](https://github.com/paulfryer/neptune-developer-workshop/blob/master/Labs/Airports/README.md) - In the lab you will create a Neptune instance and configure security groups. You will then use Gremlin to run transversals after you load data into Neptune

[DynamoDB Basics](https://github.com/wrbaldwin/db-week/blob/master/Labs/dynamoDB-basics.md) - In this lab you will set up and use DynamoDB and DAX. You’ll need a laptop with a Firefox or Chrome browser.

[DynamoDB and Search](https://github.com/wrbaldwin/db-week/blob/master/Labs/dynamoDB-and-search.md) - In this lab, you’ll explore using Amazon Elasticsearch Service (Amazon ES) to augment the more fundamental query capabilities of Amazon Dynamo DB (Dynamo DB). You’ll deploy a CloudFormation template that generates a Dynamo DB table and loads movie data into that table. You’ll employ Dynamo Streams to replicate the initial data load to an Amazon Elasticsearch Service domain. You’ll enable Cognito authentication to provide simple access to Kibana so that you can use Kibana’s UI to send searches to Amazon ES. Finally, you’ll run a Lambda function to generate updates to the Dynamo DB table, see those updates replicated to Amazon ES, and build Kibana visualizations for the changes.

[Break a Monolith Application into Microservices](https://aws.amazon.com/getting-started/projects/break-monolith-app-microservices-ecs-docker-ec2/) - In this tutorial, you will deploy a monolithic node.js application to a Docker container, then decouple the application into microservices without any downtime. The node.js application hosts a simple message board with threads and messages between users.

[Data Design for Microservices](https://github.com/wrbaldwin/db-week/blob/master/Labs/data-design-for-microservices.md) - We didn't give you enough information to answer the question. Welcome to consulting! Since you don't have enough information, the real question is, "What will you ask the client at your next meeting?" What can you begin to recommend based on the limited information you have?

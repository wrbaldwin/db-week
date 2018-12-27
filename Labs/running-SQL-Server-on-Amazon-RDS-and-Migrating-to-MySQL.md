# Workshop: Running SQL Server on Amazon RDS and Migrating to MySQL



## Log into your AWS account (we will provide credits.)

You will need an EC2 key pair in order to log into your SCT instance.
If you have access to an existing one, you can skip this step, (but you should check to make sure.)
To create a new key pair:

Open the EC2 service console
In the left hand gutter under "Network & Security" click "Key Pairs"
Click "Create Key Pair" (top left)
Supply a name and click "Create"
Download or otherwise save the .pem file  


[Download/Copy the Cloud Formation Template](https://github.com/db-week/Labs/reinvent-2018-dms-workshop-template.txt)

## Launching your assets
Open the Cloud Formation Service
Choose: Create Stack
Under choose a template select "upload a template"
click "choose file"
choose the file you just created

--> Supply a stack name
--> Source Database
Under SourceDBInstanceType - pick one (it's helpful if not everyone selects the default)
Under SourceDBEngineType pick sqlserver-se

--> Target Database
Under AuroraInstanceType - pick one ( bigger = more $$ but faster. It's helpful if not everyone selects the default)
Under AuroraEngineType - pick aurora-mysql

--> Schema Conversion Tool Host Configuration
Under SCTHostKeyName - pick a key pair you have access to. This is required to unlock the password of the ec2 instance launched.
Under SCTHostInstanceType - pick one (again it's helpful if not everyone accepts the default)

--> Other Parameters
LaptopIPAddress - you can leave this wide open or you can supply your address to limit access. 

Click "Next"

You can tag your resources or just...
Click "Next"

Click "Create"

--> Once your stack is created you can begin the migration lab
NOTE: Important information about your assets will be listed in your Cloud Formation "Outputs" listing for your stack


## Logging into your SCT windows server
Log into the ec2 console and find your instance. The name should include your cloudwatch stack name.
---> Get the password
Select your instance
Click "Connect" (button on top)
Click "Get Password"
	Supply the full contents of the .pem file you created earlier or the one you will use for this class.
Click "Decrypt Password"
Copy and save the password.
Close the dialog.

Launch Remote Desktop (or a similar tool to connect to your windows server)
Find the "public DNS" for your server (log into this)
You will log into the "Administrator" account.
To supply this in "Remote Desktop" click the "More Options" (lower left on the dialog)
Supply the username and click "Connect"
You will be prompted for a password - supply the one you just obtained.
Click "YES" to log in despite certificate errors.

## Installing Drivers
Unfortunately for legal reasons we are not allowed to pre-install the drivers for you.
You will need to install bot SQL Server and MySQL drivers in order to connect to your source and target databases.
Instructions are on the desktop in the file "JDBC Driver Install Instructions"

Follow the instructions and install the appropriate drivers.


## Launch the SCT and connect to your source and target
The icon for the Schema Conversion Tool is on your desktop - double click and launch it! 
Note: We purposely installed a prior instance so you could see the prompt when a new version is available.
Choose "Not Now" and launch the current instance.

Note: elements you need to supply are listed in your Cloud Formation Stack Outputs (CF Outputs) page. 
You can find them there or...
...you can cruise around the AWS console and find them. Up to you!

Following the wizard:
Set your "source database engine" to Microsoft SQL Server
Click  "Next" and enter the following...

--> Choose your source database
Server Name: <SourceDBHostname> (from CF Outputs)
Server Port: 1433
User Name: dbmaster
Password: srcadmin123
Microsoft SQL Server driver path: C:\JDBC Drivers\SQLServer\mssql-jdbc-7.0.0.jre8.jar

Click: "Test connection"  (lower left corner of dialog)

Click "Next"

Choose the dms_sample.dbo schema (Databases -> dms_sample -> Schemas -> dbo)

Click "Next"

.................you can scroll through the assessment report if you like

Click "Next"

--> Choose your target database
Server Name: <TargetDBHostname> (from CF Outputs)
Server port: 3306
User Name: auradmin
Password: auroradmin123
MySQL driver path: C:\JDBC Drivers\MySQL\mysql-connector-java-8.0.13.jar

Click: "Test connection"  (lower left corner of dialog)

Click "Finish"

...At this point you can poke around a bit. You'll notice there are some errors mostly with code objects.
This is intentional to show how the tool will highlight issues that need attention.

## Generate your target MySQL database
In the left hand panel right click on the dms_sample.dbo schema.
From the menu select "Convert schema"

In the right hand panel find and right click on the dms_sample_dbo schema.
From the menu select "Apply to database"

You have now used the SCT to convert your SQL Server schema to an Aurora MySQL schema!  Woohoo!!!

## Next - we'll use the Database Migration Service to migrate the data from your SQL Server instance to your Aurora MySQL instance
Log into the AWS Console and go to the Database Migration Service

--> Create your source endpoint
Click "Endpoints" on the left hand side
Click "Create endpoint" (button up top-left)
Endpoint type: Select "source"
check "select RDS DB Instance"
choose your source SQL Server instance from the RDS Instance drop down
Source engine: sqlserver
server name: <should be supplied - verify it if you want>
port: 1433
SSL mode: none
user name: dbmaster
password: srcadmin123  <SourceDBUserPassword> (from CF Ourputs)
database name: dms_sample
vpc: select the vpc that contains your CF stack name
replication instance: choose the instance that contains your CF stack name
click "Run Test"
If the test is successful click "Save", otherwise fix any issues and/or ask for help

--> Create your target endpoint
Click "Endpoints" on the left hand side
Click "Create endpoint" (button up top-left)
Endpoint type: Select "target"
check "select RDS DB Instance"
choose your target Aurora MySQL instance from the RDS Instance drop down
Target engine: aurora
Server name: < should be supplied - verify if you want>
port: 3306
SSL mode: none
User name: auradmin
Password: auroradmin123  <TargetDBUserPassword> (from CF Ourputs)

!!! Open the advanced section and turn off foreign key checks for the Aurora target !!!
Extra connection attributes: initstmt=SET FOREIGN_KEY_CHECKS=0
 
vpc: select the vpc that contains your CF stack name
replication instance: choose the instance that contains your CF stack name
click "Run Test"
If the test is successful click "Save", otherwise fix any issues and/or ask for help

--> Create your task and migrate your data!
Select "Tasks" on the left hand side of the console
Click "Create task" (button up top-left)

Task name: reinvent-2018-dms-workshop (or whatever you want)
Replication instance: select the on that includes your CF stack name
Source endpoint: select the one you just created
Target endpoint: select the one you just created
Migration type: select migrate existing data and replicate ongoing changes
...keep defaults for the rest and scroll down the Table mappings...
 
From the "Guided" tab add some selection rules:
Schema name is: dbo
Table name is like: %
Action: include
Click "Add selection rule"

Click "Create task" (button bottom-right)


## Tear Down
When you are done, you'll want to tear down your environment. To do so:

STOP your task! (this is important to ensure the replication instance is destroyed and you aren't charged $$$$$$)
Once it's stopped...
Go to your Cloud Formation console
Select your CF Stack
From the actions drop down select "delete stack"

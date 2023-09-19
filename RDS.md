   
## connecting to rds mariadb or any database through ec2 

> mysql -h <rds endpoint here > -P 3306 -u <username_defined_in_rds> -p <databasename> 



-- after hitting this command we need to enter the password we specified in the rds creation !! 

-- we can connect without specifying databse name here by that we will only be connecting with the rds database server


### Example command

> mysql -h insert-your-database-name.abcdefgh.us-east-1.rds.amazonaws.com  -P 3306 -u admin -p




# Migration of Database in EC2 Instance to RDS Database:

## cmnd1

> mysqldump -u <username> -p <databasename> > <database_name>.sql

> mysqldump -u root -p ec2db > ec2db.sql

 here we are dumping (storing ) our database into .sql which we will be sending to rds 



## cmnd2 

> mysql -h <replace-rds-end-point-here> -P 3306 -u <rdsuser-in-rds> -p <database-name> < ec2db.sql

using this our data has been dumped to rds 


## cmnd3

> mysql -h <replace-rds-end-point-here> -P 3306 -u rdsuser -p

connecting to the rds database


## cmnd3

> USE rdsdb
> SELECT * FROM table1;










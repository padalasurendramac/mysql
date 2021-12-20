# MySQL
![image](https://user-images.githubusercontent.com/53860717/139904453-397130af-0769-4a70-b932-840be00e30a1.png)



# how to connect mysql remote
  mysql -u  root  -p password -h 192.168.0.1
  
  
   
   1.each and every end of the command require semicollian (;)
   2. after excute command flush privilage
   FLUSH PRIVILEGES;

   

---------------------------------------

##how to check list of databases.
------------------------------------------
     # use this below command
     show databases;

## get into any database
---------------------------------
        # use this below command for get into that database.
        use <databasename>;

##  how to created databases
       # use this below command to connect
       CREATE DATABASE foo;
  
  
## For checking the mysql users in database
  -------------------------------------------
         # use below command to check users
         select host, user from mysql.user;

## how to create  a mysql user on mysql
-----------------------------------------------------  
  
        #  below command for create mysql user  three parameter  username, password, host means ip or we can give % for anywhere access to that useer
        CREATE USER '<username>'@'<host>' IDENTIFIED WITH mysql_native_password BY '<password>';

        # providing privilleage to that user. ( ALL means read and write ,  database.tables  ( reporting.* ) or * means all databases. username, host
        GRANT ALL ON reporting.* TO '<username>'@'<host>';

        or GRANT ALL ON *  TO '<username>'@'<host>';  #  FOR TO  ALL ACCESS.
  
--------------------
##  To Show user permissin use this below commands:-

        show grants for '<user>'@'%';  
  
## HOW TO update host for already created user
-----------------------------------------------  
  
       #use this below command  new means  new ip , old means old host address.  username
       UPDATE mysql.user SET Host='<new>' WHERE Host='<old>' AND User='<username>';
  
  
##  How to update passsword or changing the encryption type
--------------------------------------------------  
       # use this below coommand  mysql_native_password is encryption type , alter user like if statement to update password
       ALTER USER '<username>'@'<host>' IDENTIFIED WITH mysql_native_password BY '<password>';
  
  
  
## how to take all databases backup 
-----------------
        # use below comamnd to take backup
        mysqldump -u root -p --all-databases > /root/all_db_bkup_OPS-3507.sql
  

## to restore database two  method either we use < lessthen symbol to restore or we can use source path comamnd
------------------------------
              ## less then command to restore.
                                                           
              mysqldump -u root -p --all-databases < /root/all_db_bkup_OPS-3507.sql                                           
      
              ## source path command 
              source /root/all_db_bkup_OPS-3507.sql
  
##  For particular database backup
----------------------------  
              ## use this below command for particular databases.
              mysqldump -u root -p directory  > /root/directory_bkup_04-04-2021_RFC-293.sql

## For particular table backup and restore
----------------  
      ## backup 
         mysqldump db_name table_name > table_name.sql

      ## restore
         mysql -u <user_name> -p db_name
         mysql> source <full_path>/table_name.sql
         or
         mysql -u username -p db_name < /path/to/table_name.sql
  
## how to delete database
-------------------  
              # command
              DROP DATABASE <databasename>;
  
## how to delete mysql user
------------------------  
              # command
              DROP USER '<username>'@'<host>';
  

  
  
  
  


    
    
     

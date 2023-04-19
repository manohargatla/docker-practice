Create an alpine container in interactive mode and instal python 
------------------------------------------------------------------
  * Ans: `docker container run -it --name alpine1 -P alpine:3.16` 
  *  `apk add --update`
  *  `apk add python3` 
  *  `python3 --version`
  * ![preview](images/docker1.png)
  
Create an ubuntu container with sleep 1d then login user exec.Install python
----------------------------------------------------------------------------
  * Ans:`docker container run -d --name py -P ubuntu:20.04 sleep 1d`,
  * `docker container exec -it py /bin/bash`,
  * `apt update`,`apt install python3` 
  * `python3 --version`
  * ![preview](images/docker2.png)
  * ![preview](images/docker3.png)

Create a postgress container with user panoramic and password as trekking. try logging in and show the databases (querry for thr psql)
--------------------------------------------------------------------------------------------------------------------------------------
  * Ans:`docker container run -d --name database -e POSTGRES_USER=panoramic -e POSTGRES_PASSWORD=trekking -e POSTGRES_DB=psqldata -P postgres:15`,`docker exec -it database /bin/bash`,`psql --help`,this command is used to list the database `\l`
  * ![preview](images/docker4.png)
  * ![preview](images/docker5.png)
  * To create table `CREATE TABLE Persons (
    PersonID int,
    LastName varchar(255),
    FirstName varchar(255),
    Address varchar(255),
    City varchar(255)
);`
`Insert into Persons Values (1, 'manohar', 'gatla', 'srnagar', 'hyd'); Insert into Persons Values (2, 'raju', 'gatla', 'srnagar', 'hyd'); Insert into Persons Values (3, 'pavan', 'gatla', 'srnagar','hyd'); Insert into Persons Values (4, 'Rajreddy', 'gatla', 'srnagar', 'hyd');
SELECT * from Person;`"`
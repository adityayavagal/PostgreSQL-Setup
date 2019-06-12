# Setting up SonarQube for continuous inspection of code quality

## PostgreSQL Setup on Ubuntu 18.04

Postgres, is a relational database management system that provides an implementation of the SQL querying language. It is a popular choice for many small and large projects and has the advantage of being standards-compliant and having many advanced features like reliable transactions and concurrency without read locks.

### Step 1 - Installation

```bash
sudo apt update
sudo apt install postgresql postgresql-contrib
```

### Step 2 - Using PostgreSQL  Roles and Databases

Switch to Over to PostgreSQL account using
```bash
sudo -i -u postgres
```
To Enter the shell type
```bash
psql
```

Alternatively, to enter psql Shell directly
```bash
sudo -u postgres psql
```
#### Note: 
1. For Postgres Tutorials Follow This [Link](https://www.tutorialspoint.com/postgresql)
2. For Accessing Postgres remotely Follow This [Link](https://blog.bigbinary.com/2016/01/23/configure-postgresql-to-allow-remote-connection.html)

### Step 3 - Creating our Sonarqube db user

First Enter postgres user, Create user using following command
```bash
createuser sonarqube
```
Next, Enter psql Shell with psql command and Create password and database for the user
```bash
ALTER USER sonar WITH ENCRYPTED password 'password';
CREATE DATABASE sonar OWNER sonar;
```
and quit shell by typing
```bash
\q
```

## Installing and Configuring SonarQube
First, Create a ubuntu user with name sonar
```bash
sudo adduser sonar
```

Next, Download the Latest SonarQube(LTS versions are recommended)

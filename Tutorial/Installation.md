# Generally information about Nebula CNC

 Firstly thank you for choosing & using Nebula CNC

## Suggested specifications

OS: `Ubuntu 20.04 -> latest`
minimum *RAM*: `2 GB`
Recommended *RAM*: `4 GB`
Minimum *CPU*: `1 Core`
Recommended *CPU*: `4 Cores`

## Installation

Nebula CNC utilizes a MySQL database for storing data for its clients, this means you will have to
install MySQL-server and setup and create your database and a database user for the cnc to access
via.


### MySQL install for **Ubuntu 20.04 -> latest**

 - As of Nebula CNC v1.0.5 the cnc will automatically create your database tables so
 - you only need to install, Config & Create the database as Nebula CNC will do the rest.

    1. Install         `sudo apt install mysql-server`
    2. Start           `sudo systemctl start mysql.service`
    3. Configure       `sudo mysql_secure_installation`
    4. Open MySQL      `sudo mysql`
    5. Create DB       `CREATE DATABASE NebulaCNC;`
    6. Open DB         `USE NebulaCNC;`
 
 - We will now attempt to create the database user for the cnc to access and grant privileges
 - to manage, create & delete users.
    
    7. Create          `CREATE USER 'admin'@'localhost' IDENTIFIED BY 'aB3fG7kLmN9qRsTuVwXyZ1aB5cD8eFhJ';`
    8. Grant perms     `GRANT ALL PRIVILEGES ON * . * TO 'admin'@'localhost';`
    9. Update          `FLUSH PRIVILEGES;`
    10. Add SQL        `source /root/NebulaCNC/assets/c2.sql`
    11. Give access    `chmod 777 *`
    12. Install screen `apt install screen`
    13. Screen main    `screen ./main`

 - Now we much set the configuration options for the database which Nebula CNC loads
 - from and parses the information for opening the connection with the database
    indication **1** [location](../assets/config.json) 
    ```json
    "mysql": {
    "host": "localhost",
    "user": "root",
    "password": "aB3fG7kLmN9qRsTuVwXyZ1aB5cD8eFhJ",
    "db": "NebulaCNC"
    },
    ```

 - Congratulations! you have successfully setup Nebula CNC
 - [LATER] If you get a `sharing detected` error please run 3 to 4 times to allow rebinding
 - and if that doesn't fix it, please report it to FemboyRouter

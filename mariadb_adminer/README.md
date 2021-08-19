# Simple MariaDB and Adminer setup with Docker Compose

For testing a local app i need a local db with some test data.

## Default Ports

I have some other containers and use not default ports.

* 3306 (=> i use 4444)
* 8080 (=> i use 5555)

## Login

### Normal User:

    adminer:adminer

### Root User:

    root:root10Adminer!

This is **only for local test use**.
You can always change the passwords.

## Run

    docker-compose up -d



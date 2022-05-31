# snippetbox

## how to build
```
go build ./cmd/web
```

## how to run
```
go run ./cmd/web
```

## how to run on specific port
```
go run ./cmd/web -addr=":9999"
```

## how to test
```
go test -v ./cmd/web
```
or to run tests in all sub directories of current directory (including internal directory):
```
go test -v ./...
```

## how to create volume for mysql container
```
docker volume create --name=mysqldata
```


## how to star mysqldocker container

See details here:

* https://hub.docker.com/_/mysql
* https://phoenixnap.com/kb/mysql-docker-container

run like this:

```
docker run --name my-mysql -v mysqldata:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=rootpwd -p 3306:3306 -d mysql
```

connect to container and run

```
mysql -u root -p
```

## how to connect to mysql from go
https://tutorialedge.net/golang/golang-mysql-tutorial/

## create user that can be accessed from host

see https://medium.com/tech-learn-share/docker-mysql-access-denied-for-user-172-17-0-1-using-password-yes-c5eadad582d3 

```
CREATE USER 'web'@'172.17.0.1';
GRANT SELECT, INSERT, UPDATE, DELETE ON snippetbox.* TO 'web'@'172.17.0.1';
ALTER USER 'web'@'172.17.0.1' IDENTIFIED BY 'pass';
```
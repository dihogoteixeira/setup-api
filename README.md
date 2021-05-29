# Spring Boot, MySQL, JPA, Hibernate Rest API Tutorial

Build Restful CRUD API for a simple 'Setups' application using Spring Boot, Mysql, JPA and Hibernate.

## Requirements

1. Java - 1.8.x

2. Maven - 3.x.x

3. Mysql - 5.x.x

## Steps to Setup

**1. Clone the application**

```bash
git clone https://github.com/dihogoteixeira/setup-api.git
```

**2.0 Running Docker Mysql Container**

```bash
$ docker run --name fiap-mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=root -d mysql
```

**2.1 Create Mysql DATABASE**

```mysql
CREATE DATABASE checkpoint_setup
```

**2.2 Create Mysql TABLE and set column id AUTO_INCREMENT**

```mysql
CREATE TABLE `checkpoint_setup`.`setup` (
                                        `id` INT NOT NULL,
                                        `name` VARCHAR(255) NULL,
                                        `email` VARCHAR(255) NULL,
                                        `phone` VARCHAR(45) NULL,
                                        PRIMARY KEY (`id`));

ALTER TABLE `checkpoint_setup`.`setup`
    CHANGE COLUMN `id` `id` INT(11) NOT NULL AUTO_INCREMENT ,
    ADD UNIQUE INDEX `id_UNIQUE` (`id` ASC);
```

**3. Change mysql username and password as per your installation**

+ open `src/main/resources/application.properties`

+ change `spring.datasource.username` and `spring.datasource.password` as per your mysql installation

**4. Build and run the app using maven**

```bash
mvn package
java -jar target/setup-api.jar
```

Alternatively, you can run the app without packaging it using -

```bash
mvn spring-boot:run
```

The app will start running at <http://localhost:8080>.

## Explore Rest APIs

The app defines following CRUD APIs.

```
    GET /setups
    
    POST /setups
    
    GET /setups/{id}
    
    PUT /setups/{id}
    
    DELETE /setups/{id}
```

You can test them using postman or any other rest client.


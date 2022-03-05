
# Code Challenge exercise done for Adasa - by Santi Lozano

This project is made to present my position as a Full Stack Developer for 
Adasa.  
https://www.adasasystems.com/en/

The goal is to develop a web application to view meteorological data from 
various stations. MySQL script is provided with database data and also a
REST service. A backend has been developed with Spring Boot (and Java 8) 
and also a frontend with Angular 13.

In this readme you have many chapters for further information, such as
concrete technology versions, steps to execute the project, and many more.


## Tools & Technologies (versions)

### Tools

These are the highlighed tools I used for this project:  
1. Eclipse IDE for Enterprise Java and Web Developers  
https://www.eclipse.org/downloads/packages/  
2. Visual Studio Code  
https://code.visualstudio.com/  
3. Atom  
https://atom.io/  
4. Git and Git Bash  
https://git-scm.com/  
5. Operating System: Microsoft Windows 10 Home  

### Backend and database

These are the highlighted technologies used for this project (and its version):  
1. Java 8 (1.8.0_261)  
https://www.oracle.com/es/java/technologies/javase/javase8-archive-downloads.html  
2. Maven 3.6.3 (was embedded in Eclipse)  
3. Spring Boot 2.6.4  
https://spring.io/projects/spring-boot  
4. MySQL Community Server 8.0.19  
https://www.mysql.com/  
5. Lombok  
https://projectlombok.org/  

### Frontend

These are the highlighted technologies used for this project (and its version):  
1. Node 16.13.2  
https://nodejs.org/en/  
2. npm 8.1.2  
https://www.npmjs.com/  
3. Angular CLI 13.2.5  
https://angular.io/  
4. Material Angular  
https://material.angular.io/components/categories  
5. amCharts 4  
https://www.amcharts.com/docs/v4/  

## Project structure

The project is divided in two folders, one for the backend and the other for 
the frontend.

## Backend Information

### Installation

#### Git

1. Download git if you don't have it  
2. Clone the project  

#### DB

1. Run the database script (ie: from MySQL Workbench as root user)  
  The script is in the path back/codechallenge/scripts

#### Import project and backend setup

1. Install Java (version provided at versions section)  
  If other version is installed before, we can change versions with
  environment variables
2. Install Eclipse, create/open a workspace  
3. Import project in Eclipse, Maven existing project, select backend folder  
  I have deactivated the build automatically option, and git connection (team)

### Project Starter

The project starter has been generated from this source:  
https://start.spring.io/

Selecting: Maven Project, Language Java, Spring Boot 2.6.4, Packaging Jar,
Java 8.  
As dependencies:  
1. Lombok  
2. Spring Data JPA  
3. MySQL Driver  
4. Rest Repositories  

Then set the database connection in:
src/main/resources/application.properties

```bash
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.datasource.url=jdbc:mysql://localhost:3306/meteo?useSSL=false&useUnicode=yes&characterEncoding=UTF-8&allowPublicKeyRetrieval=true&serverTimezone=UTC
spring.datasource.username=meteouser
spring.datasource.password=dembele
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect
spring.data.rest.base-path=/api
```

### Execute

Right click on  
back\codechallenge\src\main\java\com\meteo\codechallenge\CodechallengebetaApplication.java  
And run as Java Application

### Functional Information

The backend provides endpoints automatically generated by Spring Data Rest
that we can call to get the data from database in JSON format.  
Once the backend is up we can go to these url to see the data we stored in
database.  
http://localhost:8080/api/meteoStations  
http://localhost:8080/api/meteoVariables

### Technical Information

The application contains two main layers:  
1. Entity: maps the database table into a Java class  
2. DAO (Data Access Object): provides access to that entity  

With Spring Boot through Spring Data JPA the entity is recognized and then with
Spring Data Rest the DAO detects it and can expose the entity via an endpoint
automatically using less code.  
https://docs.spring.io/spring-data/jpa/docs/current/reference/html/#reference  
https://docs.spring.io/spring-data/rest/docs/current/reference/html/#reference

It also uses Lombok to reduce code such as getters and setters 

#### Packages view

dao  
1. MeteoStationRepository.java  
2. MeteoVariableRepository.java  

entity  
1. MeteoStation.java  
2. MeteoVariable.java  

## Frontend Information

### Installation

I have used nvm to manage node versions.  
https://github.com/nvm-sh/nvm  
To install node and npm (with nvm installed):
```bash
nvm install 16.13.2
nvm use 16.13.2
```
Install angular CLI
```bash
npm install -g @angular/cli@13.2.5
```

### Project Starter

The project starter has been generated this way (through Angular CLI):  
1. Generate project with `ng new front-cc`  
  Options: with angular routing and CSS  
  We can check angular project version in generated package.json  
  ("@angular/core": "~13.2.0")  
2. Change to project folder `cd front-cc`  
3. Add Material Angular  
  ```bash
  ng add @angular/material
  ```
  (added version 12.2.13)  
4. Install amCharts 4  
  `npm install @amcharts/amcharts4`  
  * Adapt package.json `"build": "ng build --prod --build-optimizer=false",`  
  * `npm start` (http://localhost:4200/) (check everything is ok and close)  
  * Avoid Typescript compiler errors, add in file tsconfig.json compilerOptions  
  ```bash
  "strictNullChecks": false,
  "noImplicitAny": false,
  ```

### Execute

Run `npm start` from the source frontend folder (front-cc)  
Connect through a browser once is up  
http://localhost:4200/

### Functional Information

#### General features

#### Header

It is a simple header containing buttons to change between the pages / sections 
of the application that are shown below it.

#### Main

#### Table

#### Table Graphic Detail

#### Graphic

#### Map

### Technical Information

#### General features

#### Header

The header is made with css and material angular button toggle.

It uses the routes of the application defined in app-routing.module.ts to 
switch the route component that is being shown defined in app.component.html 
through the router-outlet.

#### Main

#### Table

#### Table Graphic Detail

#### Graphic

#### Map

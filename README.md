# Microservices with Spring Boot and Spring Cloud

This is a book notes for [Hands-On Microservices with Spring Boot and Spring Cloud]

## 1. Design

![Architecture001](img/Architecture001.png)

### Product composite service

The product composite service aggregates information from the three core services and presents information about a product as follows:

* Product information
* A list of product reviews
* A list of product recommendations

### Product service

* Product ID
* Name
* Weight

### Review service

* Product ID
* Review ID
* Author
* Subject
* Content

### Recommendation service

* Product ID
* Recommendation ID
* Author
* Rate
* Content

## 2. Implementation

### Init

[create-projects.bat](create-projects.bat) generate skeleton code using Spring Initializr.

### Build

```text
cd microservices/product-composite-service; ./gradlew build; cd ../..;
cd microservices/product-service;           ./gradlew build; cd ../..;
cd microservices/recommendation-service;    ./gradlew build; cd ../..;
cd microservices/review-service;            ./gradlew build; cd ../..;
```

#### Multi-project Builds

##### 1. Create settings.gradle

```text
include ':microservices:product-service'
include ':microservices:review-service'
include ':microservices:recommendation-service'
include ':microservices:product-composite-service'
```

##### 2. Copy the generated Gradle executable files from one of the projects

```bash
cp -r microservices/product-service/gradle .
cp microservices/product-service/gradlew .
cp microservices/product-service/gradlew.bat .
cp microservices/product-service/.gitignore .
```

##### 3. Remove the generated Gradle executable files in each project

```bash
find microservices -depth -name "gradle" -exec rm -rfv "{}" \;
find microservices -depth -name "gradlew*" -exec rm -fv "{}" \;
```

##### 4. Build

```bash
./gradlew build
```

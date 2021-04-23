# Spring Boot Starte Project - Checklist

### Step 1 - Creating a new project

Inside of ` Package Explorer ` right click -> new -> Spring Starter Project

![Create Spring Starter Project](https://github.com/kcwebers/SpringStarterProjectSetUp/blob/main/screencaps/createproj.png "Create Spring Starter Project")

Inside of the Pop-up we need to:

* Create a unique project name, example ` LoginReg `
* Make sure the type is ` Maven `
* Set Java Version to ` 11 `
* Set Packaging to ` War `
* Group name convention... ` com.username ` <-- your username/initials here
* Package name convention... ` com.username.loginreg ` <-- your project name here!

![Spring Tool Starter Project set-up](https://github.com/kcwebers/SpringStarterProjectSetUp/blob/main/screencaps/sp_start.PNG "Spring Tool Starter Project set-up")

Once these are set choose ` Next `

Select/Search for the following packages:

* Spring Boot DevTools
* Spring Web

Last, click ` Finish `

![Spring Tool Starter Project set-up dependencies](https://github.com/kcwebers/SpringStarterProjectSetUp/blob/main/screencaps/dependencies.PNG "Spring Tool Starter Project set-up dependencies")

### If you select these options often, they may appear above in the `Frequently Used` section!

### Step 2 - pom.xml

Your ` pom.xml ` is located at the very bottom of your project's file tree. 

![Pom.xml location](https://github.com/kcwebers/SpringStarterProjectSetUp/blob/main/screencaps/pomxml.png "Pom.xml location")

Add these to the ` <dependencies></dependencies> ` tag in the file and save it

```xml
<dependencies>
    <!--Basics (for general web dev) -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-devtools</artifactId>
        <scope>runtime</scope>
        <optional>true</optional>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-tomcat</artifactId>
        <scope>provided</scope>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-test</artifactId>
        <scope>test</scope>
    </dependency>

    <!--For handling views (to see your .jsp pages) -->
    <dependency>
        <groupId>org.apache.tomcat.embed</groupId>
        <artifactId>tomcat-embed-jasper</artifactId>
    </dependency>
    <dependency>
        <groupId>javax.servlet</groupId>
        <artifactId>jstl</artifactId>
    </dependency>

    <!-- MySQL -->
    <!-- Comment this section in if you are using MySQL! -->
    <!-- <dependency>
        <groupId>mysql</groupId>
        <artifactId>mysql-connector-java</artifactId>
        <scope>runtime</scope>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-jpa</artifactId>
    </dependency> --> 

    <!--Validations -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-validation</artifactId>
    </dependency>
    
    <!-- Bcrypt -->
    <dependency>
        <groupId>org.mindrot</groupId>
        <artifactId>jbcrypt</artifactId>
        <version>0.4</version>
    </dependency>
</dependencies>
```

If you are having trouble with these dependencies, remove the comments!

### Step 3 - Adding Settings to `application.properties`

Next add this line to the `src/main/resources/application.properties` file

```
spring.mvc.view.prefix=/WEB-INF/

spring.datasource.url=jdbc:mysql://localhost:3306/<<YOUR_SCHEMA>>?&serverTimezone=UTC
spring.datasource.username=<<YOUR_USERNAME>>
spring.datasource.password=<<YOUR_PASSWORD>>
spring.jpa.hibernate.ddl-auto=update

spring.mvc.hiddenmethod.filter.enabled=true

spring.mvc.view.prefix=/WEB-INF/
```

Swap out the `<<YOUR_USERNAME>>`, `<<YOUR_PASSWORD>>`, and `<<YOUR_SCHEMA>>` for the details related to your project. 

#### Important!

Don't forget to create a schema for your project in MySQL! you can do so by accessing your workbench and entering your local instance (likely Local Instance at port 3306). After that, select the option to create your schema, name it as you like, and hit `Apply`.

![Adding schema to MySQL to connect to project](https://github.com/kcwebers/SpringStarterProjectSetUp/blob/main/screencaps/createschema.PNG "Adding schema to MySQL to connect to project")

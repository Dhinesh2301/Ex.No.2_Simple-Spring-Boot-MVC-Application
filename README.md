# Exp_2_Simple-Spring-Boot-MVC-Application

## AIM:
To develop a Simple Spring Boot MVC (Model-View-Controller) Application that uses a Controller to handle HTTP requests, a Model to pass data, and a View (Thymeleaf) to render dynamic HTML pages.

## ALGORITHM:
1. Create a project using Spring Initializr  
2. Add dependencies: Spring Web, Thymeleaf  
3. Set up the main application class  
4. Create a controller to handle requests  
5. Define a method for the home page  
6. Pass data from controller to view  
7. Create HTML file in `templates` folder  
8. Add basic CSS styles (inside HTML or separate file)  
9. Use Thymeleaf to display data  
10. Run the application  
11. Open http://localhost:8080/ in browser  
## PROGRAM
```
spring-mvc-demo/
├── src/
│   └── main/
│       ├── java/
│       │   └── com.example.mvc/
│       │       ├── MvcApplication.java
│       │       └── HomeController.java
│       └── resources/
│           ├── templates/
│           │   └── index.html
│           └── application.properties
├── pom.xml
```
### pom.xml :
```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>4.0.6</version>
		<relativePath/> <!-- lookup parent from repository -->
	</parent>
	<groupId>com.example</groupId>
	<artifactId>MVC-Application</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<name/>
	<description/>
	<url/>
	<licenses>
		<license/>
	</licenses>
	<developers>
		<developer/>
	</developers>
	<scm>
		<connection/>
		<developerConnection/>
		<tag/>
		<url/>
	</scm>
	<properties>
		<java.version>25</java.version>
	</properties>
	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-webmvc</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-thymeleaf</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-webmvc-test</artifactId>
			<scope>test</scope>
		</dependency>
	</dependencies>

	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
		</plugins>
	</build>

</project>

```
### MvcApplication.java (Main Class):
```java
package com.example.MVC_Application;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class MvcApplication {
    public static void main(String[] args) {
        SpringApplication.run(MvcApplication.class, args);
    }
}

```
### HomeController.java (Controller):
```java
package com.example.MVC_Application;


import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;

@Controller
public class HomeController {

    @GetMapping("/")
    public String homePage(Model model) {
        System.out.println("Controller is called"); // DEBUG
        model.addAttribute("message", "Welcome To ThymeLeaf");
        return "index";
    }
}
```
### script.js (inside src/main/resources/static/);
```
function showMessage() {
    alert("Button clicked! Spring Boot MVC is working!");
}
```

```
function changeText(){
    document.querySelector("h1").innerText = "Text Changed Successfully!"
}
```
### style.css(inside src/main/resources/static/);
```
body {
    font-family: Arial, sans-serif;
    background: linear-gradient(to right, #4facfe, #00f2fe);
    margin: 0;
    padding: 0;
    text-align: center;
}

.container {
    margin-top: 100px;
}

h1 {
    color: white;
    font-size: 40px;
    animation: fadeIn 2s ease-in-out;
}

button {
    padding: 10px 20px;
    font-size: 16px;
    border: none;
    border-radius: 5px;
    background-color: #ffffff;
    color: #333;
    cursor: pointer;
    margin-top: 20px;
    transition: 0.3s;
}

button:hover {
    background-color: #333;
    color: white;
}

@keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
}
```
### index.html (View – inside src/main/resources/templates/):
```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
    <title>Spring MVC</title>

    <!-- Link CSS -->
    <link rel="stylesheet" href="/style.css">
</head>
<body>

<div class="container">
    <h1 th:text="${message}">Default Message</h1>

    <button onclick="showMessage()">Click Me</button>

    <button onClick="changeText()">Change Text</button>
</div>

<!-- Link JS -->
<script src="/script.js"></script>

</body>
</html>
```
### application.properties:
```
server.port=4000
```
### Output : 
<img width="1915" height="567" alt="image" src="https://github.com/user-attachments/assets/48564ef0-e627-434f-8dbb-3857e111aa60" />
<img width="1899" height="539" alt="image" src="https://github.com/user-attachments/assets/f1cb2d96-4cb3-4561-be4c-09ea350db959" />
<img width="1915" height="498" alt="image" src="https://github.com/user-attachments/assets/2b76aa8f-fb27-4d7c-bffa-dc02df873627" />

### Result:
A simple Spring Boot MVC application was successfully developed and executed, displaying dynamic content using Thymeleaf with interactive UI functionality.



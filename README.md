# notes
Notes for studying.

## Mock Stub
In Stub we only care about the fixed response, and with Mock we care more about the behavior, about how a method or a service is called.

## TDD Advantages:
-better code quality
-fewer bugs
-safer refactoring, catching regressions early
-better architecture --> TDD encourages decoupling

## TDD Disadvantages:
-slower initial development
-higher entrance threshold
-hard to apply in legacy applications

## Spring Advantages:
-Dependency Injection and Inversion of Control --> makes code loosely coupled, testable, modular
-Auto-configuration saves time, embedded Tomcat
-Huge ecosystem (Spring Security, Spring Batch, Spring Cloud, Spring JPA)
-Strong community and documentation
-Great integration, works well with Hibernate, RabbitMQ, databases, Kubernetes

## Spring Disadvantages:
-Hard to learn, many modules and abstractions
-Auto-configurations can be hard to debug ("Why was this Bean created?")
-Heavy memory usage during startup
-Misuse of annotations can lead to complex architectures

# Spring
JPA is a set of rules/interfaces (specification) that defines how to map Java entities to database tables,
instead of writing SQL manually. Hibernate is the most popular JPA provider.

## What is Inversion of Control? What is Loose coupling?
IoC is a design principle where the framework controls object creation and dependency management, enhancing modularity and loose coupling in applications.
In IoC, changing one service or class, has very little impact on the others.
Loose coupling means classes or components are independent of each other and replacing one class will have minimum impact on others.

## Dependency Injection
Dependency Injection is a design pattern which is used to implement Inversion of Control principle (loose coupling) in Java. 
Field Injection, Constructor Injection, Setter Injection, Method Injection. With @Autowired annotation we don't have to write
code for Constructor Injection.

## Spring Boot
Is an open-source framework on top of Spring, provides auto-configuration, based on dependencies, allowing developers to focus on business logic.

## Beans
Beans are a building blocks of a Spring Application, every Component in Spring is also a Bean. It's an object managed by the IoC container.

## What is AppConfig, @Configuration and @ComponentScan?
AppConfig is a configuration class that defines Beans.
@Configuration indicates that a class declares one or more Beans.
@ComponentScan is used to indicate that Spring will automatically scan and register beans from given package.

## What is the difference between @Controller and  @RestController annotations?
@Controller is general-purpose, handles web requests, typically where the response is HTML, JSP, or other type of view.
@RestController is more specialized where response is in JSON or XML format.

## RequestParam vs PathVariable
RP extracts query parameters from the URL.
PV extracts values from the URI itself.

## SpringBootApplication
Is like a meta-annotation, a main one, that triggers other important ones like Configuration and ComponentScan.

## DAO
A DAO (Data Access Object) is a design pattern that provides an interface to a database.
It separates the persistence logic (SQL, JPA, database queries) from business logic.
In Spring Boot we usually call it a Repository layer.

## DTO
A DTO is a plain object used to transfer data between layers of an application, typically between the backend and frontend, or between services.
It usually contains only data — no business logic.
Helps decouple internal entities (like JPA entities) from what you expose externally.
Improves security, performance, and clarity of API responses.

## Servlet
A Servlet is a Java class that runs on a web server (like Tomcat) and handles HTTP requests and responses.
It is part of Java EE / Jakarta EE.
Usually used to process client requests, generate dynamic content (HTML, JSON), and manage sessions.
The web server calls the servlet when a matching URL is requested.

## JSP
JSP (JavaServer Pages) is a Java technology used to create dynamic web pages on the server.
It allows you to write HTML mixed with Java code.
The server compiles JSP into a Servlet behind the scenes.

## DOM
DOM (Document Object Model) is a programming interface for web documents.
It represents HTML or XML pages as a tree of objects.
Each element, attribute, and text node becomes a node in this tree.
JavaScript can read, modify, add, or delete nodes dynamically.

## BPM
BPM files define business processes and workflows.

## Spring MVC
Spring MVC is a web framework within the Spring ecosystem that follows the Model-View-Controller (MVC) design pattern.
Controller → handles HTTP requests and coordinates responses.
Model → contains business data and logic (entities, DTOs, services).
View → renders the output (HTML, JSON, JSP, Thymeleaf).

Spring MVC makes it easy to build web applications and REST APIs using Spring Boot or traditional Spring.

# Data Structures Differences

## List, Set, Map
List - ordered, allows duplicates
Set - no duplicates
Map - key-value pairs, keys are unique

## Array and ArrayList
Array - fixed size, can store primitives
ArrayList - dynamic size, stores objects only

## ArrayList and LinkedList
Both part of Java Collections framework, similar methods, both implement the List interface.

LinkedList contains nodes which consist of value and a pointer to the next node, there can also be a doubly linked list where it contains pointers to both
next and previous value, we even have a circular list where besides that, the first elements points to the last and the last to the first. (head and tail)

In Java its a doubly LinkedList.

.get() is faster for ArrayList, it jumps straight to that element, but LinkedList starts with the reference to the beginning element and the end element,
if it wants to get in between it has to follow the pointers.

.add(), so insertion is faster for LinkedList, if I want to insert an element somewhere inside, it just has to change the pointers, all the other nodes stay the same.
With ArrayList it has to create a new larger Array under the hood, then copy all the existing elements to their right spots, along with the new value. 
.remove() is also faster for LinkedList

LinkedList better for inserting and removing elements.

# Java

JDK → development kit
JRE → runtime environment
JVM → virtual machine executing bytecode

## Abstract class and Interfaces
Abstract class is sort of a template for subclasses, cannot be instantiated directly, can contain abstract methods
(no implementation), as well as concrete methods (with implementation).

An interface is kind of more restrictive, it's fully abstract, so it contains only abstract methods, no concrete implementation,
and its like a contract with a class, that it must implement certain methods, a class can have many interfaces.





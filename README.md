# notes
Notes for studying and interview questions.

## Mock vs Stub
In Stub we only care about the fixed response, and with Mock we care more about the behavior, about how a method or a service is called.

## TDD Advantages
-better code quality
-fewer bugs
-safer refactoring, catching regressions early
-better architecture --> TDD encourages decoupling

## TDD Disadvantages
-slower initial development
-higher entrance threshold
-hard to apply in legacy applications

## Spring Advantages
-Dependency Injection and Inversion of Control --> makes code loosely coupled, testable, modular
-Auto-configuration saves time, embedded Tomcat
-Huge ecosystem (Spring Security, Spring Batch, Spring Cloud, Spring JPA)
-Strong community and documentation
-Great integration, works well with Hibernate, RabbitMQ, databases, Kubernetes

## Spring Disadvantages
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
A Java Bean is a reusable, serializable Java class that follows certain conventions and is used to encapsulate data.
Java Beans are commonly used in Java EE for managing application components and in frameworks like Spring.
Beans are a building blocks of a Spring Application, every Component in Spring is also a Bean. It's an object managed by the IoC container.
Must have a no-argument constructor.
Properties are private with public getters and setters.

In the context of frameworks like Spring, bean scope defines how long the bean instance lives and how it is shared:

Scope - Description
Singleton	One shared instance per Spring container (default).
Prototype	A new instance every time it’s requested.
Request	One instance per HTTP request (web applications).
Session	One instance per HTTP session.
Application	One instance per ServletContext.
WebSocket	One instance per WebSocket session.

Lifecycle of a Bean (Spring Example)

Instantiation – Spring creates the bean instance.
Populate Properties – Dependency Injection sets properties.
BeanNameAware / BeanFactoryAware – Spring calls these methods if implemented.
Pre-initialization (BeanPostProcessor) – Custom processing before initialization.
Initialization – @PostConstruct or afterPropertiesSet() methods are called.
Post-initialization (BeanPostProcessor) – Additional processing after initialization.
Usage – Bean is ready to be used by the application.
Destruction – @PreDestroy or destroy() is called when the container shuts down.

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
Is a meta-annotation, a main one, that triggers other important ones like Configuration and ComponentScan.

## DAO
A DAO (Data Access Object) is a design pattern that provides an interface to a database.
It separates the persistence logic (SQL, JPA, database queries) from business logic.
In Spring Boot we usually call it Repository layer.

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

## ArrayList vs LinkedList
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


# FRONTEND

# Angular

## What is Angular?
Frontend framework for SPAs. It uses TypeScript.

## Angular components
Basic building block, contains TS file (logic), HTML template, CSS stylesheet, test file for TS. Also, @Component decorator.

## Angular module
A module is a container for related components, directives, pipes and services. At least one module (AppModule).

## Data Binding
It connects data between the component and the template.
Interpolation {{value}}
Property binding [disabled]="isDisabled"
Event binding (click)="handleClick()"
Two-way binding [(ngModel)]="name"

## DI in Angular
We can automatically provide instance of a service in components. Through a constructor:
constructor(private userService: UserService) {}

## Angular Service
A service is a class used to handle business logic, HTTP requests, or shared data. @Injectable

## Angular Routing
Angular Router allows navigation between pages in SPA.
const routes: Routes = [
{ path: 'home', component: HomeComponent }
];

## Directives
Directives let you modify the DOM.
Structural: *ngIf, *ngFor
Attribute: [ngClass], [ngStyle]
Custom directives

## AngularJS vs Angular
AngularJS → JavaScript, MVC, old (1.x)
Angular → TypeScript, component-based, modern (2+)

## HttpClient
Is a service used for HTTP requests.

## @Input @Output difference
@Input() → passes data from parent to child
@Output() → emits events from child to parent

## Pipe
Pipes transform values in the template.
{{ name | uppercase }}

## Change Detection
It's Angular’s mechanism to update the DOM whenever component data changes.



## Short
-PATCH - partial modification of the resource, PUT replaces

## TypeScript
Advantages:

Static Typing
TypeScript enforces types at compile time, catching errors before the code runs.
Example: Assigning a string to a number variable throws an error immediately.
✅ Reduces runtime bugs, especially in large projects.

Improved Developer Experience
Autocomplete, IntelliSense, and type hints in editors like VS Code.
Makes code easier to understand, refactor, and maintain.
✅ Speeds up development and reduces cognitive load.

Better Scalability and Maintainability
Explicit types and interfaces make code more predictable.
Easier collaboration on large codebases, since function contracts are clear.
✅ Ideal for large projects or teams working on complex applications.

Disadvantages:

Learning Curve
Developers must learn types, interfaces, generics, and sometimes advanced type features.
❌ Can slow down adoption for teams used to plain JavaScript.

Compilation Step
TypeScript needs to be compiled to JavaScript before execution.
❌ Adds build complexity and slightly longer development cycles.

Overhead for Small Projects
For small scripts or simple websites, TypeScript may feel like overkill.
❌ Extra setup and type declarations may not justify the benefits.

## Interface in TypeScript
An interface in TypeScript is a way to define the shape of an object. It specifies the properties and their types, and optionally methods, without implementing them.
interface User {
name: string;
age: number;
email?: string; // optional property
}

## Interceptors in Frontend-Backend Communication
Adding authentication tokens
Logging or auditing requests/responses
Global error handling
Modifying request/response data (like converting date formats)

Adding Tokens Example
Automatically attach a JWT token to every outgoing request:
Axios example (frontend):

import axios from 'axios';

axios.interceptors.request.use(config => {
const token = localStorage.getItem('token');
if (token) {
config.headers['Authorization'] = `Bearer ${token}`;
}
return config;
});

## == and === difference
== (Equality)
Checks value equality only.
Performs type coercion if the operands are of different types.

5 == "5"    // true, because "5" is converted to number 5
0 == false  // true, because false is converted to 0

=== (Strict Equality)
Checks both value and type equality.
No type coercion is done.

5 === "5"   // false, number !== string
0 === false // false, number !== boolean
5 === 5     // true, same type and value

## Destructuring
Destructuring is a syntax that allows you to unpack values from arrays or properties from objects into separate variables. It makes code cleaner and more readable.

const numbers = [1, 2, 3];
const [a, b, c] = numbers;
console.log(a)

const user = { name: "Alice", age: 25 };
const { name, age } = user;
console.log(name)

## Generics
Generics allow you to create reusable components, functions, or classes that can work with any data type while still maintaining type safety.

## JavaScript Event Loop
The event loop is a mechanism that allows JavaScript, which is single-threaded, to handle asynchronous operations.
It continuously checks the call stack and the task queue: if the stack is empty, it takes the next callback from the queue and executes it.
This enables non-blocking I/O and smooth execution of async code like setTimeout, promises, and DOM events.

## const, let, var
var:
Function-scoped
Allows re-declaration
Hoisted with default value undefined
Not recommended in modern JS due to unpredictable behavior

let:
Block-scoped
Cannot be re-declared in the same scope
Hoisted but not initialized (temporal dead zone)

const:
Same rules as let (block-scoped, TDZ)
Must be assigned at declaration
The variable binding cannot change, but the contents of objects/arrays can

Summary:
Use let for variables that change, const for everything else. Avoid var.

## closure
In practice, it means an inner function can access variables defined outside of it because those variables are kept alive in memory

## WebSockets
WebSockets are a protocol that enables full-duplex, bidirectional communication between a client (browser) and a server over a single, long-lived connection.
Unlike HTTP, which is request-response, WebSockets allow real-time data exchange without repeatedly opening new connections.



# Frontend x Backend Communication

## What is REST API?
A REST API (Representational State Transfer API) is a way for systems to communicate over HTTP using simple, 
uniform operations. It uses standard HTTP methods—GET, POST, PUT, DELETE—to access and manipulate resources, 
which are identified by URLs. REST APIs are stateless, scalable, and easy to use because they rely on widely adopted web standards.

When a REST API is stateless, it means:
The server does not store any information about the client’s previous requests.
Each request must contain all the data needed for the server to understand and process it (e.g., authentication tokens, parameters).
The server treats every request as independent.

## How does it communicate?
Via HTTP requests, GET, POST, PUT, PATCH, DELETE.

## How to handle authentication and authorization?
Most modern apps use token-based authentication, commonly JWT.
After logging in:
the backend issues a token
the frontend stores it (preferably in memory or httpOnly cookies)
the frontend sends it in the Authorization: Bearer <token> header for each protected request

The backend verifies the token on every request.

## Catching errors on the frontend
Via global interceptors for common errors like 401, 403, 500.
Via .pipe(catchError()) in services in Angular

## How do you pass data between frontend and backend securely?
Always use HTTPS
Use proper authentication tokens
Avoid sending sensitive data in URL params
Validate and sanitize all data server-side
Use strong typing in DTOs to avoid unexpected structures
Security is mostly backend responsibility, but the frontend should not expose vulnerabilities.

## CORS
CORS is a browser security mechanism restricting cross-origin requests.
If the frontend and backend run on different domains or ports, the backend must allow the frontend’s origin using CORS headers like:

Access-Control-Allow-Origin
Access-Control-Allow-Methods
Access-Control-Allow-Headers

Without proper CORS config, the browser blocks the request.

## How do you handle request/response data structures?
I usually create TypeScript interfaces or models that correspond to backend DTOs.
This ensures type safety and makes refactoring easier.
If the backend changes a field name, TypeScript will catch it at compile time.

## How do you handle pagination or filtering from the frontend?
The frontend sends query parameters like page, size, sort, etc.
Example: GET /customers?page=0&size=20&sort=name,asc
The backend returns a paginated response with metadata (total pages, total items).
The frontend uses that metadata to render pagination controls.

## How do interceptors help in frontend–backend communication?
Interceptors let us modify requests or responses globally.
Typically used to:
attach auth tokens
handle common error codes
add headers
log requests in development
This reduces repeated code across services.

## How do you ensure the frontend doesn’t break when the backend changes?
Use TypeScript types/interfaces
Use shared API documentation (OpenAPI/Swagger)
Communicate changes early
Feature flagging for phased rollouts
Fallbacks in UI for missing/optional fields
Integration tests on the pipeline

## What’s the difference between any and unknown?
any disables all type checking, so you can do anything with it.
unknown is safer — you must perform type narrowing before using it.
I avoid any unless absolutely necessary.

## How do you prevent XSS attacks on the frontend?
Angular automatically sanitizes most bindings, but best practices include:
Never using innerHTML with untrusted input
Escaping user-generated content
Avoiding bypassing sanitization (DomSanitizer.bypassSecurityTrust... only when safe)
Validating and sanitizing data on the backend
Security should always be handled on both sides.

## What steps are included in a typical CI pipeline for a frontend app?
Installing dependencies
Running unit tests
Building the application
Producing a build artifact
Optionally running E2E tests
Deploying to test or production environments

## What is semantic versioning and why is it useful?
Semantic versioning uses the format MAJOR.MINOR.PATCH:
MAJOR: breaking changes
MINOR: new features, no breaking change
PATCH: bug fixes

## What’s the difference between unit tests and integration tests?
Unit tests test individual pieces of logic in isolation.
Integration tests verify how multiple components or modules work together.
Both are important — unit tests catch logic bugs early, while integration tests validate real app behavior.

## equals and hashCode contract
The equals–hashCode contract in Java ensures that objects behave correctly in hash-based collections (HashMap, HashSet, etc.).

The contract says:
If two objects are equal according to equals(), they must have the same hashCode().
Otherwise, a HashMap/HashSet won’t be able to find the object in the correct bucket.

If two objects have the same hashCode(), they do not have to be equal.
Collisions are allowed — hashCode only narrows down the bucket.

hashCode() must always return the same value for the same object during its lifetime (as long as fields used in equals don’t change).

Why it matters:
If you override equals() but forget to override hashCode(), collections like HashSet will fail to locate objects properly — you can insert an object but not find or remove it later.
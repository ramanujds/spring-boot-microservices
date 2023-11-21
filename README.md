# Introduction to Microservices

## Examples and Case Studies

https://github.com/ramanujds/online-shopping-app



## Step 1: Definition
Microservices is an architectural style that structures an application as a collection of small, independent services, each focusing on a specific business capability.

## Step 2: Characteristics
- Microservices are independently deployable, scalable, and can be developed using different technologies.
- They communicate over well-defined APIs.
- Each service is responsible for a specific business domain.

### Example
Consider an e-commerce application where services like user management, order processing, and inventory management are implemented as separate microservices.

# Problems with Monolithic Applications

## Step 1: Definition
Monolithic applications are traditionally built as a single, tightly integrated unit.

## Step 2: Challenges
- Scalability: Difficult to scale individual components.
- Maintenance: Changes in one part may affect the entire application.
- Technology Stack: Limited to a single technology stack.

### Example
A change in the payment processing module of a monolithic e-commerce application may require redeployment of the entire application.

# What and Why Microservices?

## Step 1: What are Microservices?
Microservices are small, independent services that work together to form a complete application.

## Step 2: Why Microservices?
- Scalability: Easier to scale individual services.
- Flexibility: Can use different technologies for different services.
- Resilience: If one service fails, others can continue working.

### Example
A company adopts microservices to quickly scale its user management service during peak times without affecting other services.

# Advantages and Disadvantages of Microservices

## Step 1: Advantages
- Scalability: Easy to scale individual services.
- Technology Diversity: Can use the best technology for each service.
- Resilience: Failure in one service doesn't affect the entire application.

## Step 2: Disadvantages
- Complexity: Increased complexity in managing multiple services.
- Communication Overhead: Services need to communicate over a network, introducing latency.

### Example
- Advantage: An e-commerce company scales its order processing service independently during a flash sale.
- Disadvantage: Debugging a network-related issue between two microservices.

# Use Case for Microservices

## Step 1: Identify the Problem
Identify scenarios where scalability, independent development, and resilience are critical.

## Step 2: Implement Microservices
Break down the application into independent services that align with business capabilities.

### Example
An online streaming service adopts microservices to independently scale its video streaming, recommendation engine, and user authentication services.

# Domain Driven Design

## Step 1: Define Domain
Identify and define the business domain of the application.

## Step 2: Design Microservices Around Domains
Each microservice should align with a specific business domain.

### Example
In an e-commerce application, domains could include order management, inventory, and user authentication, each implemented as a separate microservice.


### Spring Boot Introduction:

**What is Spring Boot?**
- Spring Boot is an extension of the Spring framework designed to simplify the process of building production-ready applications with minimal configuration.

**Example:**
- An e-commerce application using Spring Boot simplifies the setup of a web server, database connection, and other components.

### Spring Boot Maven Dependencies:

- Spring Boot uses Maven or Gradle for dependency management.
- Starter dependencies are used to simplify the inclusion of common sets of dependencies.

**Example:**
```xml
<!-- Spring Boot Starter Web for web applications -->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

### @EnableAutoConfiguration:

- Automatically configures the Spring application based on dependencies in the classpath.

**Example:**
```java
@SpringBootApplication
public class ECommerceApplication {
    public static void main(String[] args) {
        SpringApplication.run(ECommerceApplication.class, args);
    }
}
```

### What is @EnableAutoConfiguration doing behind the scenes:

- Scans the classpath for specific libraries and configures the application accordingly.
- Uses various AutoConfiguration classes to set up beans and configurations.

### Diving Deep into various AutoConfiguration classes:

- AutoConfiguration classes in Spring Boot configure beans and components based on the project's dependencies.

**Example:**
- `DataSourceAutoConfiguration` configures a `DataSource` bean if there is no existing `DataSource` bean defined.

### @SpringBootApplication:

- Meta-annotation that combines `@EnableAutoConfiguration`, `@ComponentScan`, and `@Configuration`.
- Used to mark the main class of a Spring Boot application.

**Example:**
```java
@SpringBootApplication
public class ECommerceApplication {
    public static void main(String[] args) {
        SpringApplication.run(ECommerceApplication.class, args);
    }
}
```

### Externalizing configuration in Spring Boot:

- Configuration can be externalized using properties files, YAML files, or environment variables.

**Example:**
- Externalize database configuration in `application.properties`:
  ```properties
  spring.datasource.url=jdbc:mysql://localhost:3306/ecommerce
  spring.datasource.username=root
  spring.datasource.password=secret
  ```

### Accessing Command line properties:

- Command line properties can be passed during application startup.

**Example:**
- Start the application with command line properties:
  ```bash
  java -jar myapp.jar --server.port=8081
  ```

### Application properties:

- Configuration properties defined in `application.properties` or `application.yml`.

**Example:**
```properties
# Application properties
server.port=8080
app.title=E-Commerce App
```

### @ConfigurationProperties:

- Binds externalized properties to Java objects.

**Example:**
```java
@ConfigurationProperties(prefix = "app")
public class AppConfig {
    private String title;

    // getters and setters
}
```

### Configuring DataSource using Boot:

- Spring Boot can automatically configure a `DataSource` based on the project's dependencies.

**Example:**
- Configure `DataSource` in `application.properties`:
  ```properties
  spring.datasource.url=jdbc:mysql://localhost:3306/ecommerce
  spring.datasource.username=root
  spring.datasource.password=secret
  ```

### TypeSafe Configuration Properties:

- Ensures that configuration properties are type-safe by binding them to specific Java objects.

**Example:**
```java
@ConfigurationProperties(prefix = "app.datasource")
public class DataSourceProperties {
    private String url;
    private String username;
    private String password;

    // getters and setters
}
```


### Spring MVC REST using Boot:

#### Basics of REST:

- **Definition:** REST (Representational State Transfer) is an architectural style for designing networked applications.
- **Key Principles:**
  - Stateless communication
  - Resources are identified by URLs
  - CRUD operations using HTTP methods (GET, POST, PUT, DELETE)

#### Discussion on REST Architectural Principles:

- **Statelessness:**
  - Each request from a client to a server contains all the information to understand and fulfill the request.
- **Resource Identification:**
  - Resources are uniquely identified by URLs.
- **CRUD Operations:**
  - Use HTTP methods (GET, POST, PUT, DELETE) for Create, Read, Update, and Delete operations.

#### @ResponseBody:

- **Purpose:** Indicates that the return value of a method should be directly written to the response body.
  
**Example:**
```java
@RestController
public class MyController {

    @GetMapping("/hello")
    @ResponseBody
    public String sayHello() {
        return "Hello, World!";
    }
}
```

#### @RequestBody:

- **Purpose:** Extracts the request body and binds it to a method parameter.

**Example:**
```java
@RestController
public class MyController {

    @PostMapping("/addUser")
    public String addUser(@RequestBody User user) {
        // Logic to add the user
        return "User added successfully!";
    }
}
```

#### HttpMessageConverters:

- **Purpose:** Converts the HTTP request and response to and from objects.
- **Example:** Spring Boot configures converters to serialize/deserialize objects in JSON format by default.

#### Content Negotiation:

- **Purpose:** Select the representation of the resource based on the client's requested media type.
  
**Example:**
```java
@RestController
public class MyController {

    @GetMapping(value = "/user", produces = MediaType.APPLICATION_XML_VALUE)
    public User getUser() {
        // Return user data
    }
}
```

#### Exception Handling:

- **Purpose:** Handle exceptions gracefully and provide meaningful error responses.

**Example:**
```java
@ControllerAdvice
public class GlobalExceptionHandler {

    @ExceptionHandler(Exception.class)
    public ResponseEntity<String> handleException(Exception e) {
        return new ResponseEntity<>("An error occurred: " + e.getMessage(), HttpStatus.INTERNAL_SERVER_ERROR);
    }
}
```

#### Pagination:

- **Purpose:** Break large result sets into smaller chunks for better performance.

**Example:**
```java
@GetMapping("/users")
public ResponseEntity<List<User>> getUsers(@RequestParam int page, @RequestParam int size) {
    // Logic to retrieve paginated user data
    return ResponseEntity.ok(userService.getUsers(page, size));
}
```

#### Http Entity:

- **Purpose:** Represents an HTTP request or response entity, consisting of headers, body, and status.

**Example:**
```java
@PostMapping("/addUser")
public ResponseEntity<String> addUser(@RequestBody User user) {
    // Logic to add the user
    return new ResponseEntity<>("User added successfully!", HttpStatus.CREATED);
}
```

#### ResponseEntity:

- **Purpose:** Represents the entire HTTP response, including status code, headers, and body.

**Example:**
```java
@GetMapping("/user/{id}")
public ResponseEntity<User> getUserById(@PathVariable Long id) {
    User user = userService.getUserById(id);
    return ResponseEntity.ok(user);
}
```

#### Client using Rest Template:

- **Purpose:** Client-side HTTP access. Allows communication with RESTful services.

**Example:**
```java
RestTemplate restTemplate = new RestTemplate();
String url = "https://api.example.com/user/{id}";
User user = restTemplate.getForObject(url, User.class, 1);
```




### Spring Cloud Overview and Its Modules:

- **Definition:** Spring Cloud is a set of tools and frameworks for building cloud-native applications.
- **Modules:**
  - **Eureka:** Service discovery and registration.
  - **Config:** Externalized configuration management.
  - **Ribbon:** Load balancing.
  - **Hystrix:** Circuit breaker pattern.
  - **Feign:** Declarative REST client.

### Spring Cloud Eureka:

#### Why Discovery Server?

- **Purpose:** In a microservices architecture, services need a way to discover and communicate with each other dynamically.
- **Eureka:** A self-service discovery server for service instances.

#### How to Create a Eureka Server:

- **Annotation:** Use `@EnableEurekaServer` or `@EnableDiscoveryServer` on a Spring Boot application class.

**Example:**
```java
@SpringBootApplication
@EnableEurekaServer
public class EurekaServerApplication {
    public static void main(String[] args) {
        SpringApplication.run(EurekaServerApplication.class, args);
    }
}
```

#### How to Register Eureka Client:

- **Annotation:** Use `@EnableEurekaClient` or `@EnableDiscoveryClient` on a Spring Boot application class.

**Example:**
```java
@SpringBootApplication
@EnableEurekaClient
public class EurekaClientApplication {
    public static void main(String[] args) {
        SpringApplication.run(EurekaClientApplication.class, args);
    }
}
```

#### How to Look Up a Service from Eureka Server:

- **RestTemplate:** Use a `RestTemplate` to make requests to services registered with Eureka.

**Example:**
```java
@RestController
public class MyController {

    @Autowired
    private RestTemplate restTemplate;

    @GetMapping("/hello")
    public String sayHello() {
        String serviceUrl = "http://my-eureka-client/hello-service";
        return restTemplate.getForObject(serviceUrl, String.class);
    }
}
```

In this example, the service named "my-eureka-client" is looked up in Eureka, and a request is made to its "/hello-service" endpoint.


### Spring Cloud Ribbon:

#### Why Client-Side Load Balancing?

- **Traditional Load Balancing:** Centralized load balancers distribute traffic, but they can become bottlenecks.
- **Client-Side Load Balancing:** Each client instance is aware of the available service instances and can make load-balanced requests.

#### What is Ribbon and How to Use Spring Ribbon?

- **Ribbon:** A client-side load balancing library provided by Spring Cloud.
- **Usage in Spring Boot:**
  - Add the `spring-cloud-starter-netflix-ribbon` dependency.
  - Use `@LoadBalanced` with `RestTemplate` to enable load balancing.

**Example:**

1. **Add Dependency:**
   ```xml
   <dependency>
       <groupId>org.springframework.cloud</groupId>
       <artifactId>spring-cloud-starter-netflix-ribbon</artifactId>
   </dependency>
   ```

2. **Use `@LoadBalanced` with `RestTemplate`:**
   ```java
   import org.springframework.cloud.client.loadbalancer.LoadBalanced;
   import org.springframework.context.annotation.Bean;
   import org.springframework.context.annotation.Configuration;
   import org.springframework.web.client.RestTemplate;

   @Configuration
   public class RibbonConfig {

       @Bean
       @LoadBalanced
       public RestTemplate restTemplate() {
           return new RestTemplate();
       }
   }
   ```

3. **Make Load-Balanced Requests:**
   ```java
   import org.springframework.beans.factory.annotation.Autowired;
   import org.springframework.web.bind.annotation.GetMapping;
   import org.springframework.web.bind.annotation.RestController;
   import org.springframework.web.client.RestTemplate;

   @RestController
   public class MyController {

       @Autowired
       private RestTemplate restTemplate;

       @GetMapping("/hello")
       public String sayHello() {
           // Service name ("my-eureka-client") is used instead of a fixed URL
           String serviceUrl = "http://my-eureka-client/hello-service";
           return restTemplate.getForObject(serviceUrl, String.class);
       }
   }
   ```

In this example, `@LoadBalanced` is used with `RestTemplate` to enable client-side load balancing with Ribbon. The `RestTemplate` is then used to make requests to a service named "my-eureka-client," and Ribbon handles the load balancing among available instances of that service.



### Spring Cloud Feign:

#### What is Feign?

- **Definition:** Feign is a declarative web service client developed by Netflix and integrated into Spring Cloud.
- **Purpose:** Simplifies the creation of REST clients by allowing developers to write HTTP requests in a straightforward and declarative manner.

#### Implementing REST Clients in Declarative Approach:

- **Annotation:** Use `@FeignClient` to declare a REST client interface. Feign will automatically create a proxy implementing that interface.
- **Method Signatures:** Declare methods in the interface with annotations such as `@RequestMapping`, `@GetMapping`, `@PostMapping`, etc.

**Example:**

1. **Add Dependency:**
   ```xml
   <dependency>
       <groupId>org.springframework.cloud</groupId>
       <artifactId>spring-cloud-starter-openfeign</artifactId>
   </dependency>
   ```

2. **Enable Feign in the Application:**
   ```java
   import org.springframework.cloud.openfeign.EnableFeignClients;
   import org.springframework.context.annotation.Configuration;

   @Configuration
   @EnableFeignClients
   public class FeignConfig {
   }
   ```

3. **Declare Feign Client Interface:**
   ```java
   import org.springframework.cloud.openfeign.FeignClient;
   import org.springframework.web.bind.annotation.GetMapping;

   @FeignClient(name = "my-eureka-client")
   public interface HelloFeignClient {

       @GetMapping("/hello-service")
       String sayHello();
   }
   ```

4. **Use Feign Client in Controller:**
   ```java
   import org.springframework.beans.factory.annotation.Autowired;
   import org.springframework.web.bind.annotation.GetMapping;
   import org.springframework.web.bind.annotation.RestController;

   @RestController
   public class MyController {

       @Autowired
       private HelloFeignClient helloFeignClient;

       @GetMapping("/hello")
       public String sayHello() {
           return helloFeignClient.sayHello();
       }
   }
   ```

#### LAB: Implementing REST Client using Feign

- **Objective:** Create a Feign client interface and use it in a Spring MVC controller to make a declarative REST request.

**Instructions:**

1. **Add Feign Dependency:**
   ```xml
   <dependency>
       <groupId>org.springframework.cloud</groupId>
       <artifactId>spring-cloud-starter-openfeign</artifactId>
   </dependency>
   ```

2. **Enable Feign in the Application:**
   ```java
   import org.springframework.cloud.openfeign.EnableFeignClients;
   import org.springframework.context.annotation.Configuration;

   @Configuration
   @EnableFeignClients
   public class FeignConfig {
   }
   ```

3. **Declare Feign Client Interface:**
   ```java
   import org.springframework.cloud.openfeign.FeignClient;
   import org.springframework.web.bind.annotation.GetMapping;

   @FeignClient(name = "example-service")
   public interface ExampleFeignClient {

       @GetMapping("/api/example")
       String getExampleData();
   }
   ```

4. **Use Feign Client in Controller:**
   ```java
   import org.springframework.beans.factory.annotation.Autowired;
   import org.springframework.web.bind.annotation.GetMapping;
   import org.springframework.web.bind.annotation.RestController;

   @RestController
   public class MyController {

       @Autowired
       private ExampleFeignClient exampleFeignClient;

       @GetMapping("/example")
       public String getExampleData() {
           return exampleFeignClient.getExampleData();
       }
   }
   ```

In this example, Feign is used to create a declarative REST client (`ExampleFeignClient`). The client is then injected into a Spring MVC controller (`MyController`), where it is used to make a declarative REST request to the "example-service." This approach simplifies the creation of REST clients by providing a clean and declarative way to define and use them.



### Circuit Breaker:

#### What is a Circuit Breaker?

- **Definition:** A circuit breaker is a design pattern used in distributed systems to prevent a cascade of failures by temporarily stopping the flow of requests to a failing service.
- **Purpose:** Protects a system from failures by providing a fallback mechanism when a service is unavailable or experiencing issues.

### API Gateway:

#### Why API Gateway?

- **Purpose:** An API Gateway is a server that acts as an entry point for a microservices architecture, handling tasks such as authentication, authorization, and routing.
- **Benefits:**
  - Single entry point for clients.
  - Simplifies microservices communication.
  - Centralized security and monitoring.

#### What is Cloud Gateway?

- **Definition:** Spring Cloud Gateway is an API Gateway built on Spring WebFlux that provides a simple, yet effective way to route requests and apply cross-cutting concerns.

### Spring Cloud Config:

#### Configuring Server and Client Pointing to Configuration File in GitHub:

- **Configuration Server:**
  - Use `@EnableConfigServer` on the main class.
  - Configure `spring.cloud.config.server.git.uri` to point to the GitHub repository.

**Example:**
```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.config.server.EnableConfigServer;

@SpringBootApplication
@EnableConfigServer
public class ConfigServerApplication {
    public static void main(String[] args) {
        SpringApplication.run(ConfigServerApplication.class, args);
    }
}
```

- **Configuring Client:**
  - Use `spring.cloud.config.uri` to specify the Config Server's address.
  - Use `spring.application.name` and `spring.profiles.active` to identify the application and profile.

**Example:**
```yaml
spring:
  application:
    name: my-service
  profiles:
    active: dev
  cloud:
    config:
      uri: http://config-server:8888
```

#### HTTP, Resource-Based API for External Configuration:

- **Endpoint:** `/actuator/configprops`
- **Purpose:** Allows clients to query the configuration properties that are available for binding.

### Lab: Using Configuration File Configured in GitHub:

- **Objective:** Configure a Spring Cloud Config Server and a client to retrieve configuration from a GitHub repository.

**Instructions:**

1. **Config Server:**
   - Create a Spring Boot application.
   - Add `@EnableConfigServer` to the main class.
   - Configure `spring.cloud.config.server.git.uri` to point to the GitHub repository.

2. **Config Client:**
   - Create a Spring Boot application.
   - Configure `spring.cloud.config.uri` to specify the Config Server's address.
   - Use `spring.application.name` and `spring.profiles.active` to identify the application and profile.

3. **Access Configured Properties:**
   - Create an endpoint in the client to access properties retrieved from the Config Server.
   - Use `@RefreshScope` to refresh properties without restarting the application.

In this lab example, the Config Server is set up to retrieve configuration from a GitHub repository, and the client is configured to fetch its properties from the Config Server. The `/actuator/configprops` endpoint can be used to inspect the available configuration properties.

These simplified notes and examples cover the basics of a circuit breaker, API Gateway, and Spring Cloud Config, along with a hands-on lab for configuring a Spring Cloud Config Server and client using GitHub.

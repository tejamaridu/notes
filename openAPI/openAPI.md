## Open API

### What is OpenAPI?
OpenAPI, formerly known as Swagger, is an open-source specification for describing and documenting RESTful APIs. It allows developers to define the structure, endpoints, request/response parameters, and data types of an API in a machine-readable format. OpenAPI specifications provide a standardized way for API consumers to understand and interact with the API, enabling easy integration and client code generation. Open API specifications describe what a REST API can do. It typically returns in YAML or JSON. 

### Key Concepts
1.  OpenAPI Specification (OAS): The OpenAPI Specification is a JSON or YAML file that defines the API's structure, including its endpoints, request and response models, authentication methods, and other relevant information.

2.  Paths: Paths represent the endpoints of the API. They define the URL paths, HTTP methods, and the request/response models associated with each endpoint.

3.  Operations: Operations are the HTTP methods (GET, POST, PUT, DELETE, etc.) that define the actions that can be performed on a path.

4.  Request/Response Models: Request and response models describe the data format and structure expected in API requests and the data returned in API responses.

### Benefits: 
**1. Standardisation:** Standardized format for described REST API, and it is readable by humans and machines (OpenAPI definition can be fed into any automation tool or DevApps for testing, etc). <br>
    **Open API Describes:**
      - Resources (Properties, Data Types)
      - Endpoints
      - Operations
      - Parameters
      - Authorisations

**2. Guidance:** It allows someone referencing the API definition to understand or use the REST API, and It shows what can API can exactly do.

**3. Extend with Tooling:** 1. API validator 2. API Doc generator. 3. SDK Generator.


### Step-by-Step Process to Implement OpenAPI in Spring Boot

#### Step 1: Create a Spring Boot Project

Assuming you have Java and Maven installed, create a new Spring Boot project using your preferred IDE or the Spring Initializr website.

#### Step 2: Add Required Dependencies

Add the necessary dependencies for Spring Boot, Spring Web, and Springfox Swagger. Springfox is a library that integrates Swagger with Spring Boot applications.

In your `pom.xml`, add the following dependencies:
 

```
<!-- Spring Boot Starter -->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter</artifactId>
</dependency>

<!-- Spring Web Starter -->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>

<!-- Springfox Swagger2 -->
<dependency>
    <groupId>io.springfox</groupId>
    <artifactId>springfox-swagger2</artifactId>
    <version>3.0.0</version>
</dependency>

<!-- Swagger UI for Documentation -->
<dependency>
    <groupId>io.springfox</groupId>
    <artifactId>springfox-swagger-ui</artifactId>
    <version>3.0.0</version>
</dependency>
```

#### Step 3: Configure Swagger in Spring Boot

Create a configuration class to enable and configure Swagger for your Spring Boot application. Here's an example:
 

```
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import springfox.documentation.builders.PathSelectors;
import springfox.documentation.builders.RequestHandlerSelectors;
import springfox.documentation.spi.DocumentationType;
import springfox.documentation.spring.web.plugins.Docket;
import springfox.documentation.swagger2.annotations.EnableSwagger2;

@Configuration
@EnableSwagger2
public class SwaggerConfig {

    @Bean
    public Docket api() {
        return new Docket(DocumentationType.SWAGGER_2)
                .select()
                .apis(RequestHandlerSelectors.basePackage("com.example.controller"))
                .paths(PathSelectors.any())
                .build();
    }
}
```

In this example, Swagger is configured to scan the `com.example.controller` package for REST controllers to include in the API documentation.

#### Step 4: Document Your API

Now, document your REST API using annotations from the Springfox Swagger library. Add these annotations to your controller methods:

javaCopy code

```
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;
import io.swagger.annotations.Api;
import io.swagger.annotations.ApiOperation;

@RestController
@RequestMapping("/api")
@Api(tags = "Example API")
public class ExampleController {

    @GetMapping("/greeting")
    @ApiOperation("Get a greeting message")
    public String getGreeting() {
        return "Hello, World!";
    }
}
```

In this example, the `@Api` annotation is used to provide a tag for the API, and `@ApiOperation` is used to describe the specific operation (GET) and its purpose.

#### Step 5: Run the Application and Access Swagger UI

Now, run your Spring Boot application. You should be able to access the Swagger UI at `http://localhost:8080/swagger-ui/index.html`. It will display all your documented API endpoints, their methods, and the models used for request/response.

#### Step 6: Customizing OpenAPI Specification (Optional)

You can customize the OpenAPI specification further by adding more information, such as the API title, description, contact details, license information, etc. You can do this by modifying the `Docket` bean in the `SwaggerConfig` class.

```
@Bean
public Docket api() {
    return new Docket(DocumentationType.SWAGGER_2)
            .select()
            .apis(RequestHandlerSelectors.basePackage("com.example.controller"))
            .paths(PathSelectors.any())
            .build()
            .apiInfo(apiInfo());
}

private ApiInfo apiInfo() {
    return new ApiInfoBuilder()
            .title("My Awesome API")
            .description("A sample API for demonstration purposes.")
            .version("1.0.0")
            .license("Apache 2.0")
            .licenseUrl("https://www.apache.org/licenses/LICENSE-2.0")
            .build();
}
```

### Summary

In this tutorial, we learned about OpenAPI (Swagger) and how to implement it in a Spring Boot REST API. By following these steps, you can easily generate comprehensive API documentation for your Spring Boot applications, making it easier for other developers to understand and consume your APIs.

Make sure to explore the Springfox Swagger documentation for more advanced configuration options and features to enhance your API documentation further! Happy coding!


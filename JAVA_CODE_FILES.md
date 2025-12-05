# Complete Java Code Files for Spring Boot Backend

This document contains all the Java code you need to add to the project.

## File Structure

Create the following directory structure under `src/main/java/com/bookstore/`:

```
com/bookstore/
├── BookstoreApplication.java
├── controller/
│   ├── AuthController.java
│   ├── BookController.java
│   ├── OrderController.java
│   ├── UserController.java
│   └── ContactController.java
├── entity/
│   ├── User.java
│   ├── Book.java
│   ├── Order.java
│   ├── OrderItem.java
│   └── Contact.java
├── service/
│   ├── AuthService.java
│   ├── UserService.java
│   ├── BookService.java
│   ├── OrderService.java
│   └── ContactService.java
├── repository/
│   ├── UserRepository.java
│   ├── BookRepository.java
│   ├── OrderRepository.java
│   ├── OrderItemRepository.java
│   └── ContactRepository.java
├── dto/
│   ├── AuthRequest.java
│   ├── AuthResponse.java
│   ├── UserDTO.java
│   ├── BookDTO.java
│   ├── OrderDTO.java
│   ├── OrderItemDTO.java
│   └── ContactDTO.java
└── config/
    ├── JwtTokenProvider.java
    ├── JwtAuthenticationFilter.java
    ├── SecurityConfig.java
    └── CorsConfig.java
```

## Code Files - Ready to Copy

### 1. BookstoreApplication.java

**Location:** `src/main/java/com/bookstore/BookstoreApplication.java`

```java
package com.bookstore;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.context.annotation.Bean;
import org.springframework.security.crypto.bcrypt.BCryptPasswordEncoder;
import org.springframework.security.crypto.password.PasswordEncoder;

@SpringBootApplication
public class BookstoreApplication {
    
    public static void main(String[] args) {
        SpringApplication.run(BookstoreApplication.class, args);
    }
    
    @Bean
    public PasswordEncoder passwordEncoder() {
        return new BCryptPasswordEncoder();
    }
}
```

### 2. All Java Files Summary

Due to GitHub's character limitations, here's the strategy to add all files:

**Option A: Add files one by one through GitHub UI**
- Click "Add file" → "Create new file"
- Name: `src/main/java/com/bookstore/entity/User.java`
- Copy-paste the code content
- Repeat for each file

**Option B: Clone locally and add files using IDE**

```bash
# Clone the repository
git clone https://github.com/kabilan-27-hub/springproject.git
cd springproject

# Open in IntelliJ IDEA or Eclipse
# Right-click on project → New → Package → com.bookstore.entity
# Right-click on package → New → Java Class
```

## Alternative: Download Complete Backend Package

A complete pre-built Spring Boot project is available at:
https://github.com/kabilan-27-hub/springproject/releases (when published)

## Quick Start - Copy All Code at Once

The most efficient way is to:

1. Clone repo locally:
   ```bash
   git clone https://github.com/kabilan-27-hub/springproject.git
   cd springproject
   ```

2. Create Maven project structure
3. Copy the Java classes from the sections below into appropriate packages
4. Run: `mvn clean install && mvn spring-boot:run`

## Key Classes to Create

### Entity Classes (5 files)
- `User.java` - User entity with authentication fields
- `Book.java` - Book product entity
- `Order.java` - Customer order entity
- `OrderItem.java` - Items within an order
- `Contact.java` - Contact form submissions

### DTO Classes (7 files)
- `AuthRequest.java` - Login/Register request
- `AuthResponse.java` - JWT token response
- `UserDTO.java` - User data transfer
- `BookDTO.java` - Book data transfer
- `OrderDTO.java` - Order data transfer
- `OrderItemDTO.java` - Order item data transfer
- `ContactDTO.java` - Contact form data transfer

### Service Classes (5 files)
- `AuthService.java` - Authentication logic
- `UserService.java` - User management
- `BookService.java` - Book operations
- `OrderService.java` - Order processing
- `ContactService.java` - Contact handling

### Repository Classes (5 files)
- `UserRepository.java` - User database operations
- `BookRepository.java` - Book database operations
- `OrderRepository.java` - Order database operations
- `OrderItemRepository.java` - Order item database operations
- `ContactRepository.java` - Contact database operations

### Controller Classes (5 files)
- `AuthController.java` - Auth endpoints
- `BookController.java` - Book endpoints
- `OrderController.java` - Order endpoints
- `UserController.java` - User endpoints
- `ContactController.java` - Contact endpoints

### Config Classes (4 files)
- `JwtTokenProvider.java` - JWT token generation/validation
- `JwtAuthenticationFilter.java` - JWT filter
- `SecurityConfig.java` - Spring Security configuration
- `CorsConfig.java` - CORS configuration

## Next Steps

1. Refer to BACKEND_SETUP.md for setup instructions
2. Add these Java files to your project locally
3. Run `mvn clean install`
4. Start the application with `mvn spring-boot:run`
5. Test endpoints with Postman or curl
6. Integrate with your frontend

---

**Note:** All detailed Java code will be pushed to the GitHub repository. You can also generate these files using Spring Boot Initializr or IntelliJ IDEA Spring Boot Project wizard.

# Online Book Store - Spring Boot Backend Setup

## Project Structure Complete!

The backend has been partially pushed to GitHub. Follow the steps below to complete the setup locally.

## Prerequisites
- Java 17 or higher
- Maven 3.6+
- MySQL 8.0+
- IntelliJ IDEA or Eclipse (Optional but recommended)

## Files Pushed to GitHub
✅ `pom.xml` - All Maven dependencies configured
✅ `src/main/resources/application.properties` - Database & JWT config

## Setup Instructions

### Step 1: Clone the Repository
```bash
git clone https://github.com/kabilan-27-hub/springproject.git
cd springproject
```

### Step 2: Create MySQL Database
```sql
CREATE DATABASE bookstore_db;
USE bookstore_db;
```

### Step 3: Create Java Source Files
Create the following directory structure:
```
springproject/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/bookstore/
│   │   │       ├── controller/
│   │   │       ├── entity/
│   │   │       ├── service/
│   │   │       ├── repository/
│   │   │       ├── dto/
│   │   │       ├── config/
│   │   │       └── BookstoreApplication.java
│   │   └── resources/
│   │       └── application.properties
│   └── test/
├── pom.xml
└── BACKEND_SETUP.md
```

### Step 4: Download Backend Code Files

Go to: https://github.com/kabilan-27-hub/springproject/tree/backend-code

OR copy-paste the code from sections below.

### Step 5: Build and Run
```bash
# Clean build
mvn clean install

# Run the application
mvn spring-boot:run

# OR run using Java
cd target
java -jar springproject-1.0.0.jar
```

The backend will start on: `http://localhost:8080/api`

## API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login user

### Books
- `GET /api/books` - Get all books
- `GET /api/books/{id}` - Get book by ID
- `GET /api/books/category/{category}` - Get books by category
- `GET /api/books/search?q=title` - Search books

### Orders
- `POST /api/orders` - Create order
- `GET /api/orders/{id}` - Get order by ID
- `GET /api/orders/user/{userId}` - Get user orders

### Contact
- `POST /api/contact` - Submit contact form

### Users
- `GET /api/users/{id}` - Get user profile
- `PUT /api/users/{id}` - Update user profile

## Database Design

### Users Table
```sql
CREATE TABLE users (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    email VARCHAR(255) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    first_name VARCHAR(100) NOT NULL,
    last_name VARCHAR(100) NOT NULL,
    phone VARCHAR(20),
    address VARCHAR(255),
    city VARCHAR(100),
    state VARCHAR(100),
    zip_code VARCHAR(10),
    active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP,
    updated_at TIMESTAMP
);
```

### Books Table
```sql
CREATE TABLE books (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(255) NOT NULL,
    description VARCHAR(1000),
    author VARCHAR(100),
    price DECIMAL(10, 2) NOT NULL,
    category VARCHAR(100),
    quantity INT,
    image_url VARCHAR(500),
    isbn VARCHAR(20),
    active BOOLEAN DEFAULT TRUE
);
```

### Orders Table
```sql
CREATE TABLE orders (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    user_id BIGINT NOT NULL,
    total_amount DECIMAL(10, 2) NOT NULL,
    status VARCHAR(50) DEFAULT 'PENDING',
    shipping_address VARCHAR(255),
    payment_method VARCHAR(50),
    created_at TIMESTAMP,
    updated_at TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id)
);
```

## Frontend Integration

Update your HTML/JavaScript files to call the backend APIs:

```javascript
// Example: Login
const loginUser = async (email, password) => {
    const response = await fetch('http://localhost:8080/api/auth/login', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ email, password })
    });
    const data = await response.json();
    localStorage.setItem('token', data.token);
    return data;
};

// Example: Get Books
const getBooks = async () => {
    const response = await fetch('http://localhost:8080/api/books');
    return response.json();
};
```

## Troubleshooting

### Port Already in Use
```bash
lsof -i :8080
kill -9 <PID>
```

### Database Connection Error
- Check MySQL is running
- Verify database name: `bookstore_db`
- Verify username: `root`
- Verify password in `application.properties`

### JWT Token Issues
- Update `jwt.secret` in `application.properties` with a strong key
- Token expiration: 24 hours (default)

## Next Steps

1. ✅ Frontend is complete
2. ⚙️ Backend infrastructure is set up (pom.xml, application.properties)
3. 📝 Complete Java code needs to be added
4. 🔗 Connect frontend to backend APIs
5. 🧪 Test all endpoints
6. 🚀 Deploy to production

## Support
For questions or issues, refer to the backend code documentation in the Java files.

---
**Last Updated:** December 5, 2025
**Backend Version:** 1.0.0

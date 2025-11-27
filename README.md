# Lab7_practice

# **Product Management System – Spring Boot**

A simple **Spring Boot CRUD application** for managing products using **Spring MVC**, **Spring Data JPA**, **Thymeleaf**, and **MySQL**.
This project is built as part of lab exercises covering full-stack development with Spring Boot.

---

## **📌 Features**

* Create, read, update, delete (CRUD) products
* Search products by name
* Filter by category
* MySQL database integration
* Thymeleaf views
* Layered architecture:

  * Controller
  * Service
  * Repository
  * Entity

---

## **📁 Project Structure**

```
src/main/java/com/example/productmanagement
│
├── controller
│     └── ProductController.java
│
├── entity
│     └── Product.java
│
├── repository
│     └── ProductRepository.java
│
└── service
      ├── ProductService.java
      └── ProductServiceImpl.java
```

---

## **🛠️ Technologies Used**

* Java 17 / 21
* Spring Boot 3.3.x
* Spring Web
* Spring Data JPA
* MySQL Driver
* Thymeleaf
* Maven

---

## **🚀 Getting Started**

### **1. Clone the Repository**

```sh
git clone https://github.com/yourusername/product-management.git
cd product-management
```

---

## **2. Create MySQL Database**

Run the SQL below:

```sql
CREATE DATABASE product_management;
USE product_management;

CREATE TABLE products (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    product_code VARCHAR(20) UNIQUE NOT NULL,
    name VARCHAR(100) NOT NULL,
    price DECIMAL(10,2) NOT NULL,
    quantity INT DEFAULT 0,
    category VARCHAR(50),
    description TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

INSERT INTO products (product_code, name, price, quantity, category, description) VALUES
('P001', 'Laptop Dell XPS 13', 1299.99, 10, 'Electronics', 'High-performance laptop with Intel i7'),
('P002', 'iPhone 15 Pro', 999.99, 25, 'Electronics', 'Latest iPhone with A17 Pro chip'),
('P003', 'Samsung Galaxy S24', 899.99, 20, 'Electronics', 'Flagship Android smartphone'),
('P004', 'Office Chair Ergonomic', 199.99, 50, 'Furniture', 'Comfortable office chair with lumbar support'),
('P005', 'Standing Desk', 399.99, 15, 'Furniture', 'Adjustable height standing desk');
```

---

## **3. Configure `application.properties`**

File: `src/main/resources/application.properties`

```properties
spring.application.name=product-management
server.port=8080

spring.datasource.url=jdbc:mysql://localhost:3306/product_management?useSSL=false&serverTimezone=UTC&allowPublicKeyRetrieval=true
spring.datasource.username=root
spring.datasource.password=your_password
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQLDialect

spring.thymeleaf.cache=false
spring.thymeleaf.prefix=classpath:/templates/
spring.thymeleaf.suffix=.html
```

Replace:

```
your_password
```

with your actual MySQL password.

---

## **4. Run the Application**

### **Run via VS Code / IntelliJ**

* Right-click **ProductManagementApplication.java**
* Select **Run**

### **Run via Maven**

```sh
mvn spring-boot:run
```

---

## **5. Open in Browser**

Visit:

```
http://localhost:8080/products
```

---

## **📄 Available Pages**

| URL                            | Description            |
| ------------------------------ | ---------------------- |
| `/products`                    | List all products      |
| `/products/new`                | Create new product     |
| `/products/edit/{id}`          | Edit product           |
| `/products/delete/{id}`        | Delete product         |
| `/products/search?keyword=abc` | Search product by name |

---

## **🧪 Testing Repository (Optional)**

Inside `ProductManagementApplication.java`:

```java
@Bean
CommandLineRunner test(ProductRepository repository) {
    return args -> {
        System.out.println("=== Testing Repository ===");
        System.out.println("Total products: " + repository.count());
        repository.findAll().forEach(System.out::println);
    };
}
```

---

## **📦 Build JAR**

```sh
mvn clean install
```

Run the built JAR:

```sh
java -jar target/product-management-0.0.1-SNAPSHOT.jar
```

---

## **📘 Summary**

This project demonstrates:

* Full Spring Boot MVC CRUD flow
* MySQL integration
* Clean architecture (Entity → Repository → Service → Controller → View)
* Use of Thymeleaf templates
* Basic form handling and validation

---

If you want, I can also generate:
✅ Finished Entity
✅ Repository
✅ Service + Implementation
✅ Controller
✅ All Thymeleaf views
➡️ Ready for submission.


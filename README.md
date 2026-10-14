# 🛒 Online E-Commerce Store Using PHP and MySQL

A simple web-based e-commerce application developed using **PHP, MySQL, HTML, and CSS**. The project provides customer authentication, product browsing, shopping cart functionality, and an admin panel for managing products.

## 📌 Project Overview

The Online E-Commerce Store allows customers to register, log in, browse available products, and manage their shopping cart. Administrators can access a separate dashboard to add and manage products.

This project demonstrates the implementation of a dynamic website using PHP and a MySQL database.

## ✨ Features

### 👤 Customer Features
- User registration and login.
- Password hashing and verification.
- Session-based authentication.
- Homepage displaying available products.
- Product details, prices, descriptions, and images.
- Add products to the shopping cart.
- View and manage cart items.
- Logout functionality.

### 🛠️ Admin Features
- Separate admin login.
- Role-based access for administrators.
- Admin dashboard.
- Add new products with images.
- View and manage existing products.
- Edit and delete product entries where the corresponding functionality is implemented.
- Admin logout functionality.

### 🔐 Security Features
- Password hashing using PHP's password functions.
- Prepared SQL statements using PDO.
- Session-based authentication.
- Role checking for admin access.
- Output escaping using `htmlspecialchars()` where implemented.

## 💻 Technologies Used

| Technology | Purpose |
|---|---|
| PHP | Backend development and server-side logic |
| MySQL | Database management |
| HTML5 | Webpage structure |
| CSS3 | Styling and layout |
| PDO | Database connectivity |
| XAMPP | Local development environment |
| phpMyAdmin | Database administration |
| Git and GitHub | Version control and project hosting |

## 📂 Project Structure

```text
ecommerce/
│
├── index.php
│
├── includes/
│   └── db.php
│
├── pages/
│   ├── register.php
│   ├── login.php
│   ├── logout.php
│   └── cart.php
│
├── admin/
│   ├── login.php
│   ├── logout.php
│   ├── dashboard.php
│   ├── add_product.php
│   └── manage_products.php
│
├── css/
│   └── style.css
│
├── images/
│   ├── cart-icon.png
│   └── product images
│
└── README.md
```

*Note: This is the intended project structure. Include only the files and folders that exist in your actual project. Additional files, such as edit and delete handlers, may be added if implemented.*

## ⚙️ Requirements

Before running the project, install:

- XAMPP or another PHP/MySQL local server environment.
- A web browser.
- Visual Studio Code or another code editor.

## 🚀 Installation and Setup

### Step 1: Clone or Download the Project

Download this repository from GitHub and place the project folder inside the XAMPP `htdocs` directory.

Example location:

```text
C:\xampp\htdocs\ecommerce
```

If you already have the project on your computer, you can use that folder directly.

### Step 2: Start XAMPP

1. Open the XAMPP Control Panel.
2. Start **Apache**.
3. Start **MySQL**.
4. Open phpMyAdmin in your browser:

```text
http://localhost/phpmyadmin
```

### Step 3: Create the Database

Create a MySQL database named `ecommerce1`, provided this matches the database name configured in `includes/db.php`.

If your connection file uses another database name, use that exact name instead.

### Step 4: Create the Database Tables

Create the following tables in your selected database.

**Users table**

```sql
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    role ENUM('user', 'admin') DEFAULT 'user'
);
```

**Products table**

```sql
CREATE TABLE products (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    price DECIMAL(10, 2) NOT NULL,
    description TEXT,
    image VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

**Cart table**

```sql
CREATE TABLE cart (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    product_id INT NOT NULL,
    quantity INT NOT NULL DEFAULT 1,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
        ON UPDATE CURRENT_TIMESTAMP
);
```

Ensure that the database schema matches the SQL queries and form fields used in your PHP files.

### Step 5: Configure the Database Connection

Open `includes/db.php` and configure your MySQL connection.

Example using PDO:

```php
<?php

$host = 'localhost';
$dbname = 'ecommerce1';
$user = 'root';
$password = '';

try {
    $conn = new PDO(
        "mysql:host=$host;dbname=$dbname;charset=utf8mb4",
        $user,
        $password
    );

    $conn->setAttribute(
        PDO::ATTR_ERRMODE,
        PDO::ERRMODE_EXCEPTION
    );

} catch (PDOException $e) {
    error_log($e->getMessage());
    exit('Database connection failed.');
}
?>
```

Update the database name, username, and password according to your local MySQL configuration.

### Step 6: Run the Project

Open your browser and visit:

```text
http://localhost/ecommerce/
```

You can then navigate to the registration, login, shopping cart, and admin pages.

## 🛍️ Application Workflow

1. A customer registers for an account.
2. The customer logs in using their credentials.
3. The homepage retrieves and displays products from MySQL.
4. The customer adds products to the shopping cart.
5. Cart items are associated with the logged-in user's account.
6. An administrator logs in through the admin login page.
7. The administrator adds or manages product information.
8. Customers can view available products on the homepage.
9. Users and administrators can log out of their respective sessions.

## 🗄️ Database Design

The application uses three main database tables.

| Table | Description |
|---|---|
| `users` | Stores customer and administrator accounts |
| `products` | Stores product names, prices, descriptions, and image filenames |
| `cart` | Stores products selected by customers and their quantities |

The `role` column in the `users` table distinguishes regular customers from administrators.

## 🧪 Testing

Test the application by checking the following:

- Register a new customer account.
- Log in with valid and invalid credentials.
- Verify that products appear on the homepage.
- Add products to the cart.
- Check cart item quantities and removal functionality.
- Log in as an administrator.
- Add a product and verify that it appears in the database.
- Check product management operations that are implemented.
- Verify logout and access restrictions for protected pages.

## 🔮 Future Improvements

Possible enhancements include:

- Product search and category filtering.
- Product quantity management.
- Secure image upload validation.
- Improved responsive design.
- Order placement and order history.
- Online payment gateway integration.
- Product reviews and ratings.
- Pagination and sorting.
- Stronger authorization and input validation.

## 🎯 Learning Outcomes

This project provides practical experience with:

- PHP backend development.
- MySQL database operations.
- CRUD operations.
- User authentication and session management.
- Password hashing.
- Prepared SQL statements.
- Dynamic webpage generation.
- GitHub repository management.

## 👨‍💻 Author

**Nikhilendra Nalam**

Computer Science and Engineering — Artificial Intelligence and Machine Learning

## 📄 License

This project is intended for educational and learning purposes. Add a license file if you choose to distribute the project under a specific open-source license.

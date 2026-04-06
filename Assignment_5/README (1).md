# Thrift & Handmade Fashion Store Database

## Customer Table
```sql
CREATE TABLE Customer (
    customer_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    instagram_handle VARCHAR(100),
    phone VARCHAR(15),
    email VARCHAR(100),
    shipping_address TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## Product Table
```sql
CREATE TABLE Product (
    product_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    product_type VARCHAR(50),
    category VARCHAR(50),
    base_price DECIMAL(10,2),
    stock_quantity INT,
    size VARCHAR(20),
    color VARCHAR(30),
    product_condition VARCHAR(20),
    material VARCHAR(50),
    added_date DATE,
    is_active BOOLEAN DEFAULT TRUE
);
```

## Orders Table
```sql
CREATE TABLE Orders (
    order_id INT PRIMARY KEY AUTO_INCREMENT,
    customer_id INT,
    order_date DATE,
    total_amount DECIMAL(10,2),
    status VARCHAR(20),
    FOREIGN KEY (customer_id) REFERENCES Customer(customer_id)
);
```

## OrderItem Table
```sql
CREATE TABLE OrderItem (
    order_item_id INT PRIMARY KEY AUTO_INCREMENT,
    order_id INT,
    product_id INT,
    quantity INT,
    unit_price DECIMAL(10,2),
    subtotal DECIMAL(10,2),
    FOREIGN KEY (order_id) REFERENCES Orders(order_id),
    FOREIGN KEY (product_id) REFERENCES Product(product_id)
);
```

## Payment Table
```sql
CREATE TABLE Payment (
    payment_id INT PRIMARY KEY AUTO_INCREMENT,
    order_id INT,
    amount DECIMAL(10,2),
    payment_method VARCHAR(50),
    payment_status VARCHAR(20),
    transaction_id VARCHAR(100),
    payment_date DATE,
    FOREIGN KEY (order_id) REFERENCES Orders(order_id)
);
```

## Shipping Table
```sql
CREATE TABLE Shipping (
    shipping_id INT PRIMARY KEY AUTO_INCREMENT,
    order_id INT,
    shipping_address TEXT,
    tracking_id VARCHAR(100),
    shipped_date DATE,
    delivered_date DATE,
    shipping_cost DECIMAL(10,2),
    shipping_status VARCHAR(20),
    FOREIGN KEY (order_id) REFERENCES Orders(order_id)
);
```

## Combined Full SQL Code
```sql
CREATE TABLE Customer (
    customer_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    instagram_handle VARCHAR(100),
    phone VARCHAR(15),
    email VARCHAR(100),
    shipping_address TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE Product (
    product_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    product_type VARCHAR(50),
    category VARCHAR(50),
    base_price DECIMAL(10,2),
    stock_quantity INT,
    size VARCHAR(20),
    color VARCHAR(30),
    product_condition VARCHAR(20),
    material VARCHAR(50),
    added_date DATE,
    is_active BOOLEAN DEFAULT TRUE
);

CREATE TABLE Orders (
    order_id INT PRIMARY KEY AUTO_INCREMENT,
    customer_id INT,
    order_date DATE,
    total_amount DECIMAL(10,2),
    status VARCHAR(20),
    FOREIGN KEY (customer_id) REFERENCES Customer(customer_id)
);

CREATE TABLE OrderItem (
    order_item_id INT PRIMARY KEY AUTO_INCREMENT,
    order_id INT,
    product_id INT,
    quantity INT,
    unit_price DECIMAL(10,2),
    subtotal DECIMAL(10,2),
    FOREIGN KEY (order_id) REFERENCES Orders(order_id),
    FOREIGN KEY (product_id) REFERENCES Product(product_id)
);

CREATE TABLE Payment (
    payment_id INT PRIMARY KEY AUTO_INCREMENT,
    order_id INT,
    amount DECIMAL(10,2),
    payment_method VARCHAR(50),
    payment_status VARCHAR(20),
    transaction_id VARCHAR(100),
    payment_date DATE,
    FOREIGN KEY (order_id) REFERENCES Orders(order_id)
);

CREATE TABLE Shipping (
    shipping_id INT PRIMARY KEY AUTO_INCREMENT,
    order_id INT,
    shipping_address TEXT,
    tracking_id VARCHAR(100),
    shipped_date DATE,
    delivered_date DATE,
    shipping_cost DECIMAL(10,2),
    shipping_status VARCHAR(20),
    FOREIGN KEY (order_id) REFERENCES Orders(order_id)
);
```

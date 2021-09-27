
**Disclaimer: I have done this project during my Introduction to Database course at my University. This is a simple project based on the basic knowledge of Database and Oracle SQL. I have implemented this project in Oracle Database 10g. I apologize if there is any mistake in my project. Let me know the mistakes so that I can fix the issue.
Please do not copy that for your own project. You can take a idea from it and make a better one. This is for educational purpose.**

![](https://i.imgur.com/lMWqqJG.jpg)

# Introduction

E-commerce Management System is an application, refers to the buying and selling of goods or services online, and the transfer of money and data to execute these transactions. For the peoples, it is making life easier. For the management point of view, the admin will able to control the E-commerce system by having all the reports to hand and able to see the records of each customers.

This application will help the Ecommerce to do all functionalities more accurately and faster way by online. E-commerce Management System is often used to refer to the sale of physical products online and improves efficiency of commercial activities. The application can help products ordering from different category and brands and also there are many more functionalities like-

- To store customer information
- Control order and services
- Payments
- Add or remove products based on categories and brands
- Helps admin to control each part of the E-commerce system

The main goal is to maintain the E-commerce system&#39;s functions in an effective and accurate manner. This system will help orders to maintain day to day records.

# Case Study

#
# Title: E-commerce management system

Ecommerce, also known as electronic commerce or internet commerce, refers to the buying and selling of goods or services using the internet, and the transfer of money and data to execute these transactions. Ecommerce is often used to refer to the sale of physical products online, but it can also describe any kind of commercial transaction that is facilitated through the internet.

In our e-commerce management system there has a system administrator who can control the system. The administrator&#39;s name, email, phone no, address, username and password is stored in the system. The system administrator can add and remove products. There has many types of products. The products are defined with name, id and type. Those products has many categories. The categories has different category id and category name. These category also has different brands and those are identified by brand id and brand name. Customer&#39;s name, address, phone number, email, username, password and customer id are stored in the system. Customers are identified with customer id. A customer can login to the system with username and password. Customer can add a product to the wish list in order to buy the product later. Wish list need wish list id, product id and product name. Customer can add any product to the cart. Cart has product quantity, total cost, product id, serial number, per product price and cart id. Customer has an order option from where he/she can order a product from the cart by doing the payment. Order has order id, date of order, product id and total cost of the product. The payment option has amount, payment type (card and cash on delivery) and payment id. After the payment the order will processed.

That is how our e-commerce management system will work.

# ER Diagram

![](https://i.imgur.com/iwzHjRM.jpg)

#

# Normalization

**admin**  **add**  **product**

**UNF :**

add(admin\_id, admin\_email, admin\_password, admin\_phone\_no, admin\_name, admin\_address, product\_id, product\_type, product\_name)

**1NF:**

admin\_email, admin\_phone\_no multivalued attribute.

**2NF:**

1. admin\_id, admin\_email, admin\_password, admin\_phone\_no, admin\_name, admin\_address
2. product\_id, product\_type, product\_name, **admin\_id**

**3NF:**

1. admin\_id, admin\_email, admin\_password, admin\_phone\_no, admin\_name, admin\_address
2. product\_id, **p\_id** , **admin\_id**
3. p\_id, product\_type, product\_name

**Table:**

1. admin\_id, admin\_password, admin\_phone\_no, admin\_name, **address\_id**
2. address\_id, admin\_address, admin\_email.
3. product\_id, product\_type, product\_name **, admin\_id.**

**product**  **has**  **category**

**UNF :**

has(product\_id, product\_type, product\_name, category\_id, category\_name)

**1NF:**

No multivalued attribute.

**2NF:**

1. product\_id, product\_type, product\_name
2. category\_id, category\_name
3. **product\_id , category\_id**

**3NF:**

1. product\_id, product\_type, product\_name
2. category\_id, category\_name
3. **product\_id , category\_id**

No transitive dependency.

**Table:**

1. product\_id, product\_type, product\_name
2. category\_id, category\_name
3. **product\_id , category\_id**

**category**  **has**  **brand**

**UNF :**

has(category\_id, category\_name, brand\_id, brand\_name)

**1NF:**

No multivalued attribute.

**2NF:**

1. category\_id, category\_name
2. brand\_id, brand\_name
3. **category\_id, brand\_id**

**3NF:**

1. category\_id, category\_name
2. brand\_id, brand\_name
3. **category\_id, brand\_id**

No transitive dependency.

**Table:**

1. category\_id, category\_name
2. brand\_id, brand\_name
3. **category\_id, brand\_id**

**customer**  **has**  **wishlist**

**UNF :**

has(customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password, wishlist\_id, customer\_id, product\_id, product\_name)

**1NF:**

customer\_phone\_no multivalued attribute.

**2NF:**

1. customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password.
2. wishlist\_id, product\_id, **customer\_id.**

**3NF:**

1. customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password.
2. wishlist\_id, product\_id, **customer\_id.**

No transitive dependency.

**Table:**

1. customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password.
2. wishlist\_id, product\_id, **customer\_id.**

**customer**  **buy**  **product**

**UNF :**

buy(customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password, product\_id, product\_type, product\_name)

**1NF:**

customer\_phone\_no multivalued attribute.

**2NF:**

1. customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password
2. product\_id, product\_type, product\_name, **customer\_id**

**3NF:**

1. customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password
2. product\_id, product\_type, product\_name, **customer\_id.**

No transitive dependency.

**Table:**

1. customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password
2. product\_id, product\_type, product\_name, **customer\_id.**

**customer**  **has**  **cart**

**UNF :**

has(customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password, cart\_id, total\_cost, quantity, product\_id, serial\_id, price)

**1NF:**

customer\_phone\_no multivalued attribute.

**2NF:**

1. customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password
2. cart\_id, total\_cost, quantity, product\_id, serial\_id, price, **customer\_id**

**3NF:**

1. customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password
2. cart\_id, product\_id, serial\_id, **customer\_id** , **pq\_id**
3. pq\_id, price, quantity, total\_cost

**Table:**

1. customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password
2. cart\_id, product\_id, serial\_id, **customer\_id** , **pq\_id**
3. pq\_id, price, quantity, total\_cost.

**customer**  **does**  **payment**

**UNF :**

does(customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password, payment\_id, card, cash\_on\_delivary, amount)

**1NF:**

customer\_phone\_no multivalued attribute.

**2NF:**

1. customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password
2. payment\_id, card, cash\_on\_delivary, amount, **customer\_id**

**3NF:**

1. customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password
2. payment\_id, card, cash\_on\_delivary, amount, **customer\_id**

No transitive dependency.

**Table:**

1. customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password
2. payment\_id, card, cash\_on\_delivary, amount, **customer\_id**

**customer**  **does**  **order**

**UNF :**

does(customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password, order\_id, total\_cost, product\_id, date\_of\_order)

**1NF:**

customer\_phone\_no multivalued attribute.

**2NF:**

1. customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password
2. order\_id, total\_cost, product\_id, date\_of\_order, **customer\_id**

**3NF:**

1. customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password
2. order\_id, total\_cost, product\_id, date\_of\_order, **customer\_id**

No transitive dependency.

**Table:**

1. customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password
2. order\_id, total\_cost, product\_id, date\_of\_order, **customer\_id**

**product**  **add**  **cart**

**UNF :**

add(product\_id, product\_type, product\_name, cart\_id, total\_cost, quantity, product\_id, serial\_id, price)

**1NF:**

No multivalued attribute.

**2NF:**

1. product\_id, product\_type, product\_name, **cart\_id**
2. cart\_id, total\_cost, quantity, product\_id, serial\_id, price

**3NF:**

1. product\_id, product\_type, product\_name, **cart\_id**
2. cart\_id, product\_id, serial\_id, **pq\_id**
3. pq\_id, total\_cost, quantity, price

**Table:**

1. product\_id, product\_type, product\_name, **cart\_id**
2. cart\_id, product\_id, serial\_id, **pq\_id**
3. pq\_id, total\_cost, quantity, price.

**cart**  **has**  **order**

**UNF :**

has(cart\_id, total\_cost, quantity, product\_id, serial\_id, price, order\_id, total\_cost, product\_id, date\_of\_order)

**1NF:**

No multivalued attribute.

**2NF:**

1. cart\_id, total\_cost, quantity, product\_id, serial\_id, price
2. order\_id, total\_cost, product\_id, date\_of\_order, **cart\_id**

**3NF:**

1. cart\_id, product\_id, serial\_id, **pq\_id**
2. order\_id, total\_cost, product\_id, date\_of\_order, **cart\_id**
3. pq\_id, price, quantity, total\_cost

**Table:**

1. cart\_id, product\_id, serial\_id, **pq\_id**
2. order\_id, total\_cost, product\_id, date\_of\_order, **cart\_id**
3. pq\_id, price, quantity, total\_cost.

**order**  **done for**  **payment**

**UNF :**

done for(order\_id, total\_cost, product\_id, date\_of\_order, payment\_id, card, cash\_on\_delivary, amount)

**1NF:**

No multivalued attribute.

**2NF:**

1. order\_id, total\_cost, product\_id, date\_of\_order
2. payment\_id, card, cash\_on\_delivary, amount, **order\_id**

**3NF:**

1. order\_id, total\_cost, product\_id, date\_of\_order
2. payment\_id, card, cash\_on\_delivary, amount, **order\_id**

No transitive dependency.

**Table:**

1. order\_id, total\_cost, product\_id, date\_of\_order
2. payment\_id, card, cash\_on\_delivary, amount, **order\_id**

# Total Table

1. admin\_id, admin\_password, admin\_phone\_no, admin\_name, **address\_id**
2. address\_id, admin\_address, admin\_email
3. product\_id, product\_type, product\_name **, admin\_id**
4. ~~product\_id~~~~ , product\_type, product\_name~~
5. category\_id, category\_name
6. **product\_id, category\_id**
7. ~~category\_id~~~~ , category\_name~~
8. brand\_id, brand\_name
9. **category\_id, brand\_id**
10. customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password
11. wishlist\_id, product\_id, **customer\_id**
12. ~~customer\_id~~~~ , customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password~~
13. product\_id, product\_type, product\_name, **customer\_id**
14. ~~customer\_id~~~~ , customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password~~
15. cart\_id, product\_id, serial\_id, **customer\_id** , **pq\_id**
16. ~~pq\_id~~~~ , price, quantity, total\_cost~~
17. ~~customer\_id~~~~ , customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password~~
18. payment\_id, card, cash\_on\_delivary, amount, **customer\_id**
19. ~~customer\_id~~~~ , customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password~~
20. order\_id, total\_cost, product\_id, date\_of\_order, **customer\_id**
21. product\_id, product\_type, product\_name, **cart\_id**
22. ~~cart\_id~~~~ , product\_id, serial\_id, ~~~~**pq\_id**~~
23. ~~pq\_id~~~~ , total\_cost, quantity, price~~
24. ~~cart\_id~~~~ , product\_id, serial\_id, ~~~~**pq\_id**~~
25. order\_id, total\_cost, product\_id, date\_of\_order, **cart\_id**
26. pq\_id, price, quantity, total\_cost
27. ~~order\_id~~~~ , total\_cost, product\_id, date\_of\_order~~
28. payment\_id, card, cash\_on\_delivary, amount, **order\_id**

#

# Final Table

1. admin\_id, admin\_password, admin\_phone\_no, admin\_name, **address\_id**
2. address\_id, admin\_address, admin\_email
3. product\_id, product\_type, product\_name **, admin\_id**
4. category\_id, category\_name
5. **product\_id, category\_id**
6. brand\_id, brand\_name
7. **category\_id, brand\_id**
8. customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password
9. wishlist\_id, product\_id, **customer\_id**
10. product\_id, product\_type, product\_name, **customer\_id**
11. cart\_id, product\_id, serial\_id, **customer\_id** , **pq\_id**
12. pq\_id, price, quantity, total\_cost
13. payment\_id, card, cash\_on\_delivary, amount, **customer\_id**
14. order\_id, total\_cost, product\_id, date\_of\_order, **customer\_id**
15. product\_id, product\_type, product\_name, **cart\_id**
16. order\_id, total\_cost, product\_id, date\_of\_order, **cart\_id**
17. payment\_id, card, cash\_on\_delivary, amount, **order\_id**

# Schema Diagram

![](https://i.imgur.com/s4DUuRn.jpg)

# Table Creation

**Table : admin**

CREATE TABLE admin

(

admin\_id VARCHAR2(8) NOT NULL,

admin\_name VARCHAR2(20) NOT NULL,

admin\_password VARCHAR2(50) NOT NULL,

admin\_phone\_no NUMBER(11) NOT NULL,

address\_id NUMBER(4) NOT NULL,

CONSTRAINT admin\_PK PRIMARY KEY(admin\_id),

CONSTRAINT admin\_FK FOREIGN KEY(address\_id) REFERENCES address(address\_id)

);

DESCRIBE admin;

![](https://i.imgur.com/RNkTQG6.jpg)

**Table : address**

CREATE TABLE address

(

address\_id NUMBER(4) NOT NULL,

admin\_email VARCHAR2(30) UNIQUE,

admin\_address VARCHAR2(50) NOT NULL,

CONSTRAINT address\_PK PRIMARY KEY(address\_id)

);

DESCRIBE address;

![](https://i.imgur.com/U9trXul.jpg)

**Table : product**

CREATE TABLE product

(

product\_id NUMBER(4) NOT NULL,

product\_name VARCHAR2(30) UNIQUE,

product\_type VARCHAR2(50) NOT NULL,

admin\_id VARCHAR2(8) NOT NULL,

CONSTRAINT product\_PK PRIMARY KEY(product\_id),

CONSTRAINT product\_FK FOREIGN KEY(admin\_id) REFERENCES admin(admin\_id)

);

DESCRIBE product;

![](https://i.imgur.com/bqQcsaR.jpg)

**Table : category**

CREATE TABLE category

(

category\_id NUMBER(4) NOT NULL,

category\_name VARCHAR2(30) UNIQUE,

CONSTRAINT category\_PK PRIMARY KEY(category\_id)

);

DESCRIBE category;

![](https://i.imgur.com/unnSLKd.jpg)

**Table : pcid**

CREATE TABLE pcid (

product\_id NUMBER(8),

category\_id NUMBER(4),

CONSTRAINT pcid\_PK PRIMARY KEY(product\_id, category\_id),

CONSTRAINT pcid\_p\_FK FOREIGN KEY(product\_id) REFERENCES product(product\_id),

CONSTRAINT pcid\_c\_FK FOREIGN KEY(category\_id) REFERENCES category(category\_id)

);

DESCRIBE pcid;

![](https://i.imgur.com/kIXh2fy.jpg)

**Table : brand**

CREATE TABLE brand

(

brand\_id NUMBER(4) NOT NULL,

brand\_name VARCHAR2(30) UNIQUE,

CONSTRAINT brand\_PK PRIMARY KEY(brand\_id)

);

DESCRIBE brand;

![](https://i.imgur.com/PR1vCzK.jpg)

**Table : cbid**

CREATE TABLE cbid

(

category\_id NUMBER(4),

brand\_id NUMBER(4),

CONSTRAINT cbid\_PK PRIMARY KEY(category\_id, brand\_id),

CONSTRAINT cbid\_c\_FK FOREIGN KEY(category\_id) REFERENCES category(category\_id),

CONSTRAINT cbid\_b\_FK FOREIGN KEY(brand\_id) REFERENCES brand(brand\_id)

);

DESCRIBE cbid;

![](https://i.imgur.com/8JpG0zg.jpg)

**Table : customer**

CREATE TABLE customer

(

customer\_id VARCHAR2(8) NOT NULL,

customer\_name VARCHAR2(20) NOT NULL,

customer\_address VARCHAR2(50) NOT NULL,

customer\_phone\_no NUMBER(11) NOT NULL,

customer\_username VARCHAR2(8) NOT NULL,

customer\_password VARCHAR2(50) NOT NULL,

CONSTRAINT customer\_PK PRIMARY KEY(customer\_id),

CONSTRAINT customer\_unique UNIQUE (customer\_id, customer\_name)

);

DESCRIBE customer;

![](https://i.imgur.com/JHyNETE.jpg)

**Table : wishlist**

CREATE TABLE wishlist

(

wishlist\_id NUMBER(4) NOT NULL,

product\_id NUMBER(4) NOT NULL,

customer\_id VARCHAR2(8) NOT NULL,

CONSTRAINT wishlist\_PK PRIMARY KEY(wishlist\_id),

CONSTRAINT wishlist\_unique UNIQUE (wishlist\_id, product\_id, customer\_id)

);

DESCRIBE wishlist;

![](https://i.imgur.com/gAWFp8g.jpg)

**Table : product2**

CREATE TABLE product2

(

product\_id NUMBER(4) NOT NULL,

product\_name VARCHAR2(30) UNIQUE,

product\_type VARCHAR2(50) NOT NULL,

customer\_id VARCHAR2(8) NOT NULL,

CONSTRAINT product2\_PK PRIMARY KEY(product\_id),

CONSTRAINT product2\_FK FOREIGN KEY(customer\_id) REFERENCES customer(customer\_id),

CONSTRAINT product2\_unique UNIQUE (product\_id, product\_name, product\_type)

);

DESCRIBE product2;

![](https://i.imgur.com/b9QMHLL.jpg)

**Table : cart**

CREATE TABLE cart

(

cart\_id NUMBER(4) PRIMARY KEY,

product\_id NUMBER(4) UNIQUE,

serial\_id NUMBER(4) NOT NULL,

customer\_id VARCHAR2(8) NOT NULL,

pq\_id NUMBER(38),

CONSTRAINT cart\_c\_FK FOREIGN KEY(customer\_id) REFERENCES customer(customer\_id),

CONSTRAINT cart\_pq\_FK FOREIGN KEY(pq\_id) REFERENCES pqid(pq\_id),

CONSTRAINT cart\_unique UNIQUE (serial\_id, customer\_id, cart\_id)

);

DESCRIBE cart;

![](https://i.imgur.com/ObLNpcN.jpg)

**Table : pqid**

CREATE TABLE pqid

(

pq\_id NUMBER(4) PRIMARY KEY,

price NUMBER(38) NOT NULL,

quantity NUMBER(38) NOT NULL,

total\_cost NUMBER(38) NOT NULL

);

DESCRIBE pqid;

![](https://i.imgur.com/bpog69w.jpg)

**Table : payment**

CREATE TABLE payment

(

payment\_id NUMBER(4) NOT NULL,

card NUMBER(15),

amount NUMBER(10) NOT NULL,

customer\_id VARCHAR2(8) NOT NULL,

cash\_on\_delivary VARCHAR2(8) NOT NULL,

CONSTRAINT payment\_PK PRIMARY KEY(payment\_id),

CONSTRAINT payment\_FK FOREIGN KEY(customer\_id) REFERENCES customer(customer\_id),

CONSTRAINT payment\_unique UNIQUE (payment\_id, customer\_id)

);

DESCRIBE payment;

![](https://i.imgur.com/mrCkzqq.jpg)

**Table : order1**

CREATE TABLE order1

(

order\_id NUMBER(4) NOT NULL,

total\_cost NUMBER(15) NOT NULL,

product\_id NUMBER(4) NOT NULL,

date\_of\_order DATE,

customer\_id VARCHAR2(8) NOT NULL,

CONSTRAINT order1\_PK PRIMARY KEY(order\_id),

CONSTRAINT order1\_FK FOREIGN KEY(customer\_id) REFERENCES customer(customer\_id),

CONSTRAINT order1\_unique UNIQUE (order\_id, customer\_id, product\_id)

);

DESCRIBE order1;

![](https://i.imgur.com/cyHd5vb.jpg)

**Table : product3**

CREATE TABLE product3

(

product\_id NUMBER(4) NOT NULL,

product\_name VARCHAR2(30) UNIQUE,

product\_type VARCHAR2(50) NOT NULL,

cart\_id NUMBER(4) NOT NULL,

CONSTRAINT product3\_PK PRIMARY KEY(product\_id),

CONSTRAINT product3\_FK FOREIGN KEY(cart\_id) REFERENCES cart(cart\_id),

CONSTRAINT product3\_unique UNIQUE (product\_id, product\_type, cart\_id)

);

DESCRIBE product3;

![](https://i.imgur.com/RtOcBDW.jpg)

**Table : order2**

CREATE TABLE order2

(

payment\_id NUMBER(4) NOT NULL,

card NUMBER(15),

amount NUMBER(10) NOT NULL,

order\_id NUMBER(4) NOT NULL,

cash\_on\_delivary VARCHAR2(8),

CONSTRAINT payment2\_PK PRIMARY KEY(payment\_id),

CONSTRAINT payment2\_FK FOREIGN KEY(order\_id) REFERENCES order1(order\_id),

CONSTRAINT payment2\_unique UNIQUE (payment\_id, order\_id)

);

DESCRIBE order2;

![](https://i.imgur.com/lMZtM0A.jpg)

**Table : payment2**

CREATE TABLE payment2

(

payment\_id NUMBER(4) NOT NULL,

card NUMBER(15),

amount NUMBER(10) NOT NULL,

order\_id VARCHAR2(8) NOT NULL,

cash\_on\_delivary VARCHAR2(8) NOT NULL,

CONSTRAINT payment2\_PK PRIMARY KEY(payment\_id),

CONSTRAINT payment2\_FK FOREIGN KEY(order\_id) REFERENCES order1(order\_id),

CONSTRAINT payment2\_unique UNIQUE (payment\_id, order\_id)

);

DESCRIBE payment2;

![](https://i.imgur.com/frSw6su.jpg)

# Data Insertion:

1. **admin**

INSERT INTO admin(admin\_id, admin\_name, admin\_password, admin\_phone\_no, address\_id) VALUES(&#39;admin&#39;, &#39;alex&#39;, &#39;admin1234&#39;, &#39;0170000000&#39;, 01);

select \* from admin

![](https://i.imgur.com/EURdSIP.jpg)

2. **address**

INSERT INTO address (address\_id, admin\_email, admin\_address) VALUES (01, &#39;admin@gmail.com&#39;, &#39;Dhaka,Bangladesh&#39;);

select \* from address;

![](https://i.imgur.com/m6K6rWi.jpg)

3. **product**

INSERT INTO product (product\_id, product\_name, product\_type, admin\_id) VALUES (001, &#39;Android Mobile&#39;, &#39;Gadget&#39;, &#39;admin&#39;);

INSERT INTO product (product\_id, product\_name, product\_type, admin\_id) VALUES (002, &#39;Core i7 Laptop&#39;, &#39;Gadget&#39;, &#39;admin&#39;);

INSERT INTO product (product\_id, product\_name, product\_type, admin\_id) VALUES (003, &#39;Mens Casual Shirt&#39;, &#39;Fashion&#39;, &#39;admin&#39;);

INSERT INTO product (product\_id, product\_name, product\_type, admin\_id) VALUES (004, &#39;Mens Formal Pant&#39;, &#39;Fashion&#39;, &#39;admin&#39;);

INSERT INTO product (product\_id, product\_name, product\_type, admin\_id) VALUES (005, &#39; Oracle Database 12c Book&#39;, &#39;Stationary&#39;, &#39;admin&#39;);

INSERT INTO product (product\_id, product\_name, product\_type, admin\_id) VALUES (006, &#39;Lip Stick&#39;, &#39;Cosmetics&#39;, &#39;admin&#39;);

INSERT INTO product (product\_id, product\_name, product\_type, admin\_id) VALUES (007, &#39;Body Lotion&#39;, &#39;Cosmetics&#39;, &#39;admin&#39;);

INSERT INTO product (product\_id, product\_name, product\_type, admin\_id) VALUES (008, &#39;Rice&#39;, &#39;Glossary&#39;, &#39;admin&#39;);

INSERT INTO product (product\_id, product\_name, product\_type, admin\_id) VALUES (009, &#39;Flour&#39;, &#39;Glossary&#39;, &#39;admin&#39;);

INSERT INTO product (product\_id, product\_name, product\_type, admin\_id) VALUES (010, &#39;Soyabean Oil&#39;, &#39;Glossary&#39;, &#39;admin&#39;);

select \* from product;

![](https://i.imgur.com/rcwJfSZ.jpg)

4. **category**

INSERT INTO category (category\_id, category\_name) VALUES (011, &#39;Mobile Phone&#39;);

INSERT INTO category (category\_id, category\_name) VALUES (012, &#39;Laptop&#39;);

INSERT INTO category (category\_id, category\_name) VALUES (013, &#39;Dress&#39;);

INSERT INTO category (category\_id, category\_name) VALUES (014, &#39;Pants&#39;);

INSERT INTO category (category\_id, category\_name) VALUES (015, &#39;Books&#39;);

INSERT INTO category (category\_id, category\_name) VALUES (016, &#39;Cosmetics&#39;);

INSERT INTO category (category\_id, category\_name) VALUES (017, &#39;Cosmetics-liquid&#39;);

INSERT INTO category (category\_id, category\_name) VALUES (018, &#39;Glossary-paddy&#39;);

INSERT INTO category (category\_id, category\_name) VALUES (019, &#39;Glossary-meal&#39;);

INSERT INTO category (category\_id, category\_name) VALUES (020, &#39;Glossary-oil&#39;);

select \* from category;

![](https://i.imgur.com/6Q61s2l.jpg)

5. **pcid**

INSERT INTO pcid (product\_id, category\_id) VALUES (001, 011);

INSERT INTO pcid (product\_id, category\_id) VALUES (002, 012);

INSERT INTO pcid (product\_id, category\_id) VALUES (003, 013);

INSERT INTO pcid (product\_id, category\_id) VALUES (004, 014);

INSERT INTO pcid (product\_id, category\_id) VALUES (005, 015);

INSERT INTO pcid (product\_id, category\_id) VALUES (006, 016);

INSERT INTO pcid (product\_id, category\_id) VALUES (007, 017);

INSERT INTO pcid (product\_id, category\_id) VALUES (008, 018);

INSERT INTO pcid (product\_id, category\_id) VALUES (009, 019);

INSERT INTO pcid (product\_id, category\_id) VALUES (010, 020);

select \* from pcid;

![](https://i.imgur.com/nRDinD1.jpg)

6. **brand**

INSERT INTO brand (brand\_id, brand\_name) VALUES (111, &#39;Samsung&#39;);

INSERT INTO brand (brand\_id, brand\_name) VALUES (112, &#39;ASUS&#39;);

INSERT INTO brand (brand\_id, brand\_name) VALUES (113, &#39;Yellow&#39;);

INSERT INTO brand (brand\_id, brand\_name) VALUES (114, &#39;Cat&#39;s Eye&#39;);

INSERT INTO brand (brand\_id, brand\_name) VALUES (115, &#39;Springer Nature&#39;);

INSERT INTO brand (brand\_id, brand\_name) VALUES (116, &#39;Lakme&#39;);

INSERT INTO brand (brand\_id, brand\_name) VALUES (117, &#39;Nevia&#39;);

INSERT INTO brand (brand\_id, brand\_name) VALUES (118, &#39;Pran&#39;);

INSERT INTO brand (brand\_id, brand\_name) VALUES (119, &#39;Teer&#39;);

INSERT INTO brand (brand\_id, brand\_name) VALUES (120, &#39;Fresh&#39;);

select \* from brand;

![](https://i.imgur.com/3uLypHu.jpg)

7. **cbid**

INSERT INTO cbid (category\_id,brand\_id) VALUES (011, 111);

INSERT INTO cbid (category\_id,brand\_id) VALUES (012, 112);

INSERT INTO cbid (category\_id,brand\_id) VALUES (013, 113);

INSERT INTO cbid (category\_id,brand\_id) VALUES (014, 114);

INSERT INTO cbid (category\_id,brand\_id) VALUES (015, 115);

INSERT INTO cbid (category\_id,brand\_id) VALUES (016, 116);

INSERT INTO cbid (category\_id,brand\_id) VALUES (017, 117);

INSERT INTO cbid (category\_id,brand\_id) VALUES (018, 118);

INSERT INTO cbid (category\_id,brand\_id) VALUES (019, 119);

INSERT INTO cbid (category\_id,brand\_id) VALUES (020, 120);

select \* from cbid;

![](https://i.imgur.com/6TsENYc.jpg)

8. **customer**

INSERT INTO customer (customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password) VALUES (&#39;masufian&#39;, &#39;Md Abu Sufian&#39;, &#39;Uttara, Dhaka&#39;, &#39;01700000011&#39;, &#39;masufian&#39;, &#39;abc&#39;);

INSERT INTO customer (customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password) VALUES (&#39;smkhan&#39;, &#39;Saidul Mursalin Khan&#39;, &#39;Dhanmondi, Dhaka&#39;, &#39;01700000012&#39;, &#39;smkhan&#39;, &#39;abcd&#39;);

INSERT INTO customer (customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password) VALUES (&#39;masayeed&#39;, &#39;Md Abu Sayeed&#39;, &#39;Nikunja, Dhaka&#39;, &#39;01700000013&#39;, &#39;masayeed&#39;, &#39;abcde&#39;);

INSERT INTO customer (customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password) VALUES (&#39;sksarkar&#39;, &#39;Sumit Kanti Sarkar&#39;, &#39;Kuril, Dhaka&#39;, &#39;01700000014&#39;, &#39;sksarkar&#39;, &#39;abcdef&#39;);

INSERT INTO customer (customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password) VALUES (&#39;aira&#39;, &#39;Abzana Ira&#39;, &#39;Bashundhara, Dhaka&#39;, &#39;01700000015&#39;, &#39;aera&#39;, &#39;abcdefg&#39;);

INSERT INTO customer (customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password) VALUES (&#39;dwarner&#39;, &#39;David Warner&#39;, &#39;Mirpur,Dhaka&#39;, 01700000016, &#39;dwarner&#39;, &#39;abcdefgh&#39;);

INSERT INTO customer (customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password) VALUES (&#39;hamla&#39;, &#39;Hasim Amla&#39;, &#39;Bashundhara,Dhaka&#39;, 01700000017, &#39;hamla&#39;, &#39;abcdefghi&#39;);

INSERT INTO customer (customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password) VALUES (&#39;mali&#39;, &#39;Moien Ali&#39;, &#39;Banani,Dhaka&#39;, 01700000018, &#39;mali&#39;, &#39;abcdefghij&#39;);

INSERT INTO customer (customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password) VALUES (&#39;sali&#39;, &#39;Saif Ali&#39;, &#39;Baridhara,Dhaka&#39;, 01700000019, &#39;sali&#39;, &#39;abcdefghijk&#39;);

INSERT INTO customer (customer\_id, customer\_name, customer\_address, customer\_phone\_no, customer\_username, customer\_password) VALUES (&#39;niqbal&#39;, &#39;Nafis Iqbal&#39;, &#39;Gulshan,Dhaka&#39;, 01700000020, &#39;niqbal&#39;, &#39;abcdefghijkl&#39;);

select \* from customer;

![](https://i.imgur.com/GGGvpi5.jpg)

9. **wishlist**

INSERT INTO wishlist (wishlist\_id, product\_id, customer\_id) VALUES (121, 001, &#39;masufian&#39;);

INSERT INTO wishlist (wishlist\_id, product\_id, customer\_id) VALUES (122, 002, &#39;smkhan&#39;);

INSERT INTO wishlist (wishlist\_id, product\_id, customer\_id) VALUES (123, 003, &#39;masayeed&#39;);

INSERT INTO wishlist (wishlist\_id, product\_id, customer\_id) VALUES (124, 004, &#39;sksarkar&#39;);

INSERT INTO wishlist (wishlist\_id, product\_id, customer\_id) VALUES (125, 005, &#39;aira&#39;);

INSERT INTO wishlist (wishlist\_id, product\_id, customer\_id) VALUES (126, 006, &#39;dwarner&#39;);

INSERT INTO wishlist (wishlist\_id, product\_id, customer\_id) VALUES (127, 007, &#39;hamla&#39;);

INSERT INTO wishlist (wishlist\_id, product\_id, customer\_id) VALUES (128, 008, &#39;mali&#39;);

INSERT INTO wishlist (wishlist\_id, product\_id, customer\_id) VALUES (129, 009, &#39;sali&#39;);

INSERT INTO wishlist (wishlist\_id, product\_id, customer\_id) VALUES (130, 010, &#39;niqbal&#39;);

select \* from wishlist;

![](https://i.imgur.com/uLNNLk8.jpg)

10. **product2**

INSERT INTO product2 (product\_id, product\_name, product\_type, customer\_id) VALUES (001, &#39;Android Mobile&#39;, &#39;Gadget&#39;, &#39;masufian&#39;);

INSERT INTO product2 (product\_id, product\_name, product\_type, customer\_id) VALUES (002, &#39;Core i7 Laptop&#39;, &#39;Gadget&#39;, &#39;smkhan&#39;);

INSERT INTO product2 (product\_id, product\_name, product\_type, customer\_id) VALUES (003, &#39;Mens Casual Shirt&#39;, &#39;Fashion&#39;, &#39;masayeed&#39;);

INSERT INTO product2 (product\_id, product\_name, product\_type, customer\_id) VALUES (004, &#39;Mens Formal Pant&#39;, &#39;Fashion&#39;, &#39;sksarkar&#39;);

INSERT INTO product2 (product\_id, product\_name, product\_type, customer\_id) VALUES (005, &#39;Oracle Database 12c Book&#39;, &#39;Stationary&#39;, &#39;aira&#39;);

INSERT INTO product2 (product\_id, product\_name, product\_type, customer\_id) VALUES (006, &#39;Lip Stick&#39;, &#39;Cosmetics&#39;, &#39;dwarner&#39;);

INSERT INTO product2 (product\_id, product\_name, product\_type, customer\_id) VALUES (007, &#39;Body Lotion&#39;, &#39;Cosmetics&#39;, &#39;hamla&#39;);

INSERT INTO product2 (product\_id, product\_name, product\_type, customer\_id) VALUES (008, &#39;Rice&#39;, &#39;Glossary&#39;, &#39;mali&#39;);

INSERT INTO product2 (product\_id, product\_name, product\_type, customer\_id) VALUES (009, &#39;Flour&#39;, &#39;Glossary&#39;, &#39;sali&#39;);

INSERT INTO product2 (product\_id, product\_name, product\_type, customer\_id) VALUES (010, &#39;Soyabean Oil&#39;, &#39;Glossary&#39;, &#39;niqbal&#39;);

select \* from product2

![](https://i.imgur.com/zKdqVSk.jpg)

11. **Cart**

INSERT INTO cart (cart\_id, product\_id, serial\_id, customer\_id, pq\_id) VALUES (131, 001, 141, &#39;masufian&#39;, 151);

INSERT INTO cart (cart\_id, product\_id, serial\_id, customer\_id, pq\_id) VALUES (132, 002, 142, &#39;smkhan&#39;, 152);

INSERT INTO cart (cart\_id, product\_id, serial\_id, customer\_id, pq\_id) VALUES (133, 003, 143, &#39;masayeed&#39;, 153);

INSERT INTO cart (cart\_id, product\_id, serial\_id, customer\_id, pq\_id) VALUES (134, 004, 144, &#39;sksarkar&#39;, 154);

INSERT INTO cart (cart\_id, product\_id, serial\_id, customer\_id, pq\_id) VALUES (135, 005, 145, &#39;aira&#39;, 155);

INSERT INTO cart (cart\_id, product\_id, serial\_id, customer\_id, pq\_id) VALUES (136, 006, 146, &#39;dawarner&#39;, 156);

INSERT INTO cart (cart\_id, product\_id, serial\_id, customer\_id, pq\_id) VALUES (137, 007, 147, &#39;hamla&#39;, 157);

INSERT INTO cart (cart\_id, product\_id, serial\_id, customer\_id, pq\_id) VALUES (138, 008, 148, &#39;mali&#39;, 158);

INSERT INTO cart (cart\_id, product\_id, serial\_id, customer\_id, pq\_id) VALUES (139, 009, 149, &#39;sali&#39;, 159);

INSERT INTO cart (cart\_id, product\_id, serial\_id, customer\_id, pq\_id) VALUES (140, 010, 150, &#39;niqbal&#39;, 160);

select \* from cart;

![](https://i.imgur.com/GDIRJCq.jpg)

12. **pqid**

INSERT INTO pqid (pq\_id, price, quantity, total\_cost) VALUES (151, 20000, 01, 20000);

INSERT INTO pqid (pq\_id, price, quantity, total\_cost) VALUES (152, 65000, 01, 65000);

INSERT INTO pqid (pq\_id, price, quantity, total\_cost) VALUES (153, 1750, 03, 5250);

INSERT INTO pqid (pq\_id, price, quantity, total\_cost) VALUES (154, 1190, 03, 3570);

INSERT INTO pqid (pq\_id, price, quantity, total\_cost) VALUES (155, 450, 05, 2250);

INSERT INTO pqid (pq\_id, price, quantity, total\_cost) VALUES (156, 900, 01, 900);

INSERT INTO pqid (pq\_id, price, quantity, total\_cost) VALUES (157, 550, 02, 1100);

INSERT INTO pqid (pq\_id, price, quantity, total\_cost) VALUES (158, 55, 05, 275);

INSERT INTO pqid (pq\_id, price, quantity, total\_cost) VALUES (159, 46, 02, 92);

INSERT INTO pqid (pq\_id, price, quantity, total\_cost) VALUES (160, 105, 05, 525);

select \* from pqid

![](https://i.imgur.com/mYTawWf.jpg)

13. **payment**

INSERT INTO payment (payment\_id, card, amount, customer\_id, cash\_on\_delivary) VALUES (5551, 21541202, 20000, &#39;masufian&#39;, &#39;No&#39;);

INSERT INTO payment (payment\_id, card, amount, customer\_id, cash\_on\_delivary) VALUES (5552, 00, 65000, &#39;smkhan&#39;, &#39;Yes&#39;);

INSERT INTO payment (payment\_id, card, amount, customer\_id, cash\_on\_delivary) VALUES (5553, 4154874, 5250, &#39;masayeed&#39;, &#39;No&#39;);

INSERT INTO payment (payment\_id, card, amount, customer\_id, cash\_on\_delivary) VALUES (5554, 00, 3570, &#39;sksarkar&#39;, &#39;Yes&#39;);

INSERT INTO payment (payment\_id, card, amount, customer\_id, cash\_on\_delivary) VALUES (5555, 0790652, 2250, &#39;aira&#39;, &#39;No&#39;);

INSERT INTO payment (payment\_id, card, amount, customer\_id, cash\_on\_delivary) VALUES (5556, 24674520, 900, &#39;dwarner&#39;, &#39;No&#39;);

INSERT INTO payment (payment\_id, card, amount, customer\_id, cash\_on\_delivary) VALUES (5557, 21541204, 1100, &#39;hamla&#39;, &#39;No&#39;);

INSERT INTO payment (payment\_id, card, amount, customer\_id, cash\_on\_delivary) VALUES (5558, 00, 275, &#39;mali&#39;, &#39;Yes&#39;);

INSERT INTO payment (payment\_id, card, amount, customer\_id, cash\_on\_delivary) VALUES (5559, 54251525, 92, &#39;sali&#39;, &#39;No&#39;);

INSERT INTO payment (payment\_id, card, amount, customer\_id, cash\_on\_delivary) VALUES (5560, 00, 525, &#39;niqbal&#39;, &#39;Yes&#39;);

select \* from payment;

![](https://i.imgur.com/3AC0CRl.jpg)

14. **order1**

INSERT INTO order1 (order\_id, total\_cost, product\_id, date\_of\_order, customer\_id) VALUES (0101, 20000, 001, DATE &#39;2020-11-22&#39;, &#39;masufian&#39;);

INSERT INTO order1 (order\_id, total\_cost, product\_id, date\_of\_order, customer\_id) VALUES (0102, 65000, 002, DATE &#39;2020-11-20&#39;, &#39;smkhan&#39;);

INSERT INTO order1 (order\_id, total\_cost, product\_id, date\_of\_order, customer\_id) VALUES (0103, 5250, 003, DATE &#39;2020-11-10&#39;, &#39;masayeed&#39;);

INSERT INTO order1 (order\_id, total\_cost, product\_id, date\_of\_order, customer\_id) VALUES (0104, 3570, 004, DATE &#39;2020-11-26&#39;, &#39;sksarkar&#39;);

INSERT INTO order1 (order\_id, total\_cost, product\_id, date\_of\_order, customer\_id) VALUES (0105, 2250, 005, DATE &#39;2020-12-12&#39;, &#39;aira&#39;);

INSERT INTO order1 (order\_id, total\_cost, product\_id, date\_of\_order, customer\_id) VALUES (0106, 900, 006, DATE &#39;2020-12-11&#39;, &#39;dwarner&#39;);

INSERT INTO order1 (order\_id, total\_cost, product\_id, date\_of\_order, customer\_id) VALUES (0107, 1100, 007, DATE &#39;2020-12-11&#39;, &#39;hamla&#39;);

INSERT INTO order1 (order\_id, total\_cost, product\_id, date\_of\_order, customer\_id) VALUES (0108, 275, 008, DATE &#39;2020-12-17&#39;, &#39;mali&#39;);

INSERT INTO order1 (order\_id, total\_cost, product\_id, date\_of\_order, customer\_id) VALUES (0109, 92, 009, DATE &#39;2020-12-5&#39;, &#39;sali&#39;);

INSERT INTO order1 (order\_id, total\_cost, product\_id, date\_of\_order, customer\_id) VALUES (0110, 525, 010, DATE &#39;2020-12-4&#39;, &#39;niqbal&#39;);

select \* from order1;

![](https://i.imgur.com/w1moTd5.jpg)

15. **product3**

INSERT INTO product3 (product\_id, product\_name, product\_type, cart\_id) VALUES (001, &#39;Android Mobile&#39;, &#39;Gadget&#39;, 131);

INSERT INTO product3 (product\_id, product\_name, product\_type, cart\_id) VALUES (002, &#39;Core i7 Laptop&#39;, &#39;Gadget&#39;, 132);

INSERT INTO product3 (product\_id, product\_name, product\_type, cart\_id) VALUES (003, &#39;Mens Casual Shirt&#39;, &#39;Fashion&#39;, 133);

INSERT INTO product3 (product\_id, product\_name, product\_type, cart\_id) VALUES (004, &#39;Mens Formal Pant&#39;, &#39;Fashion&#39;, 134);

INSERT INTO product3 (product\_id, product\_name, product\_type, cart\_id) VALUES (005, &#39;Oracle Database 12c Book&#39;, &#39;Stationary&#39;, 135);

INSERT INTO product3 (product\_id, product\_name, product\_type, cart\_id) VALUES (006, &#39;Lip Stick&#39;, &#39;Cosmetics&#39;, 136);

INSERT INTO product3 (product\_id, product\_name, product\_type, cart\_id) VALUES (007, &#39;Body Lotion&#39;, &#39;Cosmetics&#39;, 137);

INSERT INTO product3 (product\_id, product\_name, product\_type, cart\_id) VALUES (008, &#39;Rice&#39;, &#39;Glossary&#39;, 138);

INSERT INTO product3 (product\_id, product\_name, product\_type, cart\_id) VALUES (009, &#39;Flour&#39;, &#39;Glossary&#39;, 139);

INSERT INTO product3 (product\_id, product\_name, product\_type, cart\_id) VALUES (010, &#39;Soyabean Oil&#39;, &#39;Glossary&#39;, 140);

select \* from product3;

![](https://i.imgur.com/6OMHm0w.jpg)

16. **order2**

INSERT INTO order2 (order\_id, total\_cost, product\_id, date\_of\_order, cart\_id) VALUES (0101, 20000, 001, DATE &#39;2020-11-22&#39;, 131);

INSERT INTO order2 (order\_id, total\_cost, product\_id, date\_of\_order, cart\_id) VALUES (0102, 65000, 002, DATE &#39;2020-11-20&#39;, 132);

INSERT INTO order2 (order\_id, total\_cost, product\_id, date\_of\_order, cart\_id) VALUES (0103, 5250, 003, DATE &#39;2020-11-10&#39;, 133);

INSERT INTO order2 (order\_id, total\_cost, product\_id, date\_of\_order, cart\_id) VALUES (0104, 3570, 004, DATE &#39;2020-11-26&#39;, 134);

INSERT INTO order2 (order\_id, total\_cost, product\_id, date\_of\_order, cart\_id) VALUES (0105, 2250, 005, DATE &#39;2020-12-12&#39;, 135);

INSERT INTO order2 (order\_id, total\_cost, product\_id, date\_of\_order, cart\_id) VALUES (0106, 900, 006, DATE &#39;2020-12-11&#39;, 136);

INSERT INTO order2 (order\_id, total\_cost, product\_id, date\_of\_order, cart\_id) VALUES (0107, 1100, 007, DATE &#39;2020-12-11&#39;, 137);

INSERT INTO order2 (order\_id, total\_cost, product\_id, date\_of\_order, cart\_id) VALUES (0108, 275, 008, DATE &#39;2020-12-17&#39;, 138);

INSERT INTO order2 (order\_id, total\_cost, product\_id, date\_of\_order, cart\_id) VALUES (0109, 92, 009, DATE &#39;2020-12-5&#39;, 139);

INSERT INTO order2 (order\_id, total\_cost, product\_id, date\_of\_order, cart\_id) VALUES (0110, 525, 010, DATE &#39;2020-12-4&#39;, 140);

select \* from order2;

![](https://i.imgur.com/EgijnLu.jpg)

17. **payment2**

INSERT INTO payment2 (payment\_id, card, amount, order\_id, cash\_on\_delivary) VALUES (5551, 21541202, 20000, 0101, &#39;No&#39;);

INSERT INTO payment2 (payment\_id, card, amount, order\_id, cash\_on\_delivary) VALUES (5552, 00, 65000, 0102, &#39;Yes&#39;);

INSERT INTO payment2 (payment\_id, card, amount, order\_id, cash\_on\_delivary) VALUES (5553, 4154874, 5250, 0103, &#39;No&#39;);

INSERT INTO payment2 (payment\_id, card, amount, order\_id, cash\_on\_delivary) VALUES (5554, 00, 3570, 0104, &#39;Yes&#39;);

INSERT INTO payment2 (payment\_id, card, amount, order\_id, cash\_on\_delivary) VALUES (5555, 0790652, 2250, 0105, &#39;No&#39;);

INSERT INTO payment2 (payment\_id, card, amount, order\_id, cash\_on\_delivary) VALUES (5556, 24674520, 900, 0106, &#39;No&#39;);

INSERT INTO payment2 (payment\_id, card, amount, order\_id, cash\_on\_delivary) VALUES (5557, 21541204, 1100, 0107, &#39;No&#39;);

INSERT INTO payment2 (payment\_id, card, amount, order\_id, cash\_on\_delivary) VALUES (5558, 00, 275, 0108, &#39;Yes&#39;);

INSERT INTO payment2 (payment\_id, card, amount, order\_id, cash\_on\_delivary) VALUES (5559, 54251525, 92, 0109, &#39;No&#39;);

INSERT INTO payment2 (payment\_id, card, amount, order\_id, cash\_on\_delivary) VALUES (5560, 00, 525, 0110, &#39;Yes&#39;);

select \* from payment2

![](https://i.imgur.com/f68QACc.jpg)

# Query Writing

1. **Sub Query**

**1-Q:**

Print the product id, product names, product type from product table where product\_id is 1.

**1-A:**

select product\_id, product\_name, product\_type from product where product\_name = (select product\_name from product2 where product\_id=1);

![](https://i.imgur.com/7SmegmK.jpg)

**2-Q:**

Print product id, product name, product type and cart id for cart id 131.

**2-A:**

SELECT product\_id, product\_name, product\_type FROM product3 WHERE cart\_id = (SELECT cart\_id FROM cart WHERE cart\_id =&#39;131&#39;);

![](https://i.imgur.com/BzDlWvy.jpg)

**3-Q:**

Print order id, total cost, product id, date of order, cart\_id from order2 table where the total cost is greater than the cost of order which were palced on 2020-11-26.

**3-A:**

SELECT order\_id, total\_cost, product\_id, date\_of\_order, cart\_id FROM order2 WHERE total\_cost \&gt; (SELECT AVG(total\_cost) FROM order2 WHERE date\_of\_order=to\_date(&#39;2020-11-26&#39;, &#39;YYYY-MM-DD&#39;));

![](https://i.imgur.com/c4FGd7F.jpg)

2. **Joining**

**1-Q:**

Print the admin name and admin address id by joining admin table and address table

**1-A:**

SELECT a.admin\_name &quot;Admin Name&quot;, ad.address\_id &quot;Admin Address ID&quot; FROM admin a, address ad WHERE a.address\_id = ad.address\_id;

![](https://i.imgur.com/pFWO1Hz.jpg)

**2-Q:**

Print the customers name for customer id masufian, smkhan and aira

**2-A:**

SELECT cname.customer\_name FROM customer cname, customer cid WHERE cname.customer\_id = cid.customer\_id AND cname.customer\_id in(&#39;masufian&#39;, &#39;smkhan&#39;, &#39;aira&#39;);

![](https://i.imgur.com/DpaQfp8.jpg)

**3-Q:**

Print the customer id and count the order id from order1 table and join the customer table with order1 table.

**3-A:**

SELECT customer\_id, COUNT( order\_id ) FROM order1 INNER JOIN customer USING(customer\_id) GROUP BY customer\_id ORDER BY customer\_id;

![](https://i.imgur.com/yAjJyea.jpg)

3. **Group Function**

**1-Q:**

Find average, maximum, minimum salary of the pqid.

**1-A:**

select avg(price) as average,max(price) as maximum,min(price) as minimum from pqid;

![](https://i.imgur.com/8LmivpA.jpg)

**2-Q:**

Display the maximum amount of payment2

**2-A:**

select max(amount) from payment2;

![](https://i.imgur.com/YPamrpZ.jpg)

**3-Q:**

Find the number of customer who have payment \&lt;3570

**3-A:**

select count(customer\_id) from payment where amount\&lt;3570;

![](https://i.imgur.com/VqC6TZI.jpg)

4. **Single row function**

**1-Q:**

print product, total price from order2 table and print the total cost in asending order

**1-A:**

select product\_id &quot;Product ID&quot;, TRUNC(total\_cost) &quot;Total Price&quot; from order2 order by total\_cost asc

![](https://i.imgur.com/IXv5qiN.jpg)

5. **View**

**1-Q:**

Create a view for customer table where we are going to print Customer ID, Customer Name, Phone Number and Address from customer table.

**1-A:**

CREATE VIEW customer\_view AS

SELECT c.customer\_id &quot;Customer ID&quot;, c.customer\_name &quot;Customer Name&quot;, c.customer\_phone\_no &quot;Phone Number&quot;, c.customer\_address &quot;Address&quot; FROM customer c;

![](https://i.imgur.com/W8seb4g.jpg)

6. **Sequence**

- **Table(shipping) Create for sequence:**

CREATE TABLE shipping

(

shipping\_id NUMBER(8) NOT NULL,

customer\_id VARCHAR2(20) NOT NULL,

date\_of\_order DATE,

order\_id NUMBER(4) NOT NULL,

product\_id NUMBER(4) NOT NULL,

payment\_id NUMBER(4) NOT NULL,

customer\_address VARCHAR2(50) NOT NULL,

customer\_phone\_no NUMBER(11) NOT NULL,

CONSTRAINT shipping\_PK PRIMARY KEY(shipping\_id),

CONSTRAINT shipping\_customer\_FK FOREIGN KEY(customer\_id) REFERENCES customer(customer\_id),

CONSTRAINT shipping\_order\_FK FOREIGN KEY(order\_id) REFERENCES order1(order\_id),

CONSTRAINT shipping\_product\_FK FOREIGN KEY(product\_id) REFERENCES product(product\_id),

CONSTRAINT shipping\_payment\_FK FOREIGN KEY(payment\_id) REFERENCES payment(payment\_id),

CONSTRAINT shipping\_unique UNIQUE (shipping\_id, customer\_id, order\_id, payment\_id, product\_id)

);

#

- **Create Sequence:**

CREATE SEQUENCE shipping\_id

START WITH 1230

INCREMENT BY 1

MINVALUE 1230

MAXVALUE 10000

NOCACHE

NOCYCLE;

CREATE SEQUENCE order\_id

START WITH 100

INCREMENT BY 1

MINVALUE 100

MAXVALUE 10000

NOCACHE

NOCYCLE;

CREATE SEQUENCE product\_id

START WITH 0

INCREMENT BY 1

MINVALUE 0

MAXVALUE 10000

NOCACHE

NOCYCLE;

CREATE SEQUENCE payment\_id

START WITH 5550

INCREMENT BY 1

MINVALUE 5550

MAXVALUE 10000

NOCACHE

NOCYCLE;

#

- **Data Insertion in shipping table:**

INSERT INTO shipping (shipping\_id, customer\_id, order\_id, product\_id, payment\_id, date\_of\_order, customer\_phone\_no, customer\_address) VALUES (shipping\_id.NEXTVAL, &#39;masufian&#39;, order\_id.NEXTVAL, product\_id.NEXTVAL, payment\_id.NEXTVAL, DATE &#39;2020-11-22&#39;, 01700000011, &#39;Uttara, Dhaka&#39;);

INSERT INTO shipping (shipping\_id, customer\_id, order\_id, product\_id, payment\_id, date\_of\_order, customer\_phone\_no, customer\_address) VALUES (shipping\_id.NEXTVAL, &#39;smkhan&#39;, order\_id.NEXTVAL, product\_id.NEXTVAL, payment\_id.NEXTVAL, DATE &#39;2020-11-20&#39;, 01700000012, &#39;Dhanmondi, Dhaka&#39;);

INSERT INTO shipping (shipping\_id, customer\_id, order\_id, product\_id, payment\_id, date\_of\_order, customer\_phone\_no, customer\_address) VALUES (shipping\_id.NEXTVAL, &#39;masayeed&#39;, order\_id.NEXTVAL, product\_id.NEXTVAL, payment\_id.NEXTVAL, DATE &#39;2020-11-10&#39;, 01700000013, &#39;Nikunja, Dhaka&#39;);

INSERT INTO shipping (shipping\_id, customer\_id, order\_id, product\_id, payment\_id, date\_of\_order, customer\_phone\_no, customer\_address) VALUES (shipping\_id.NEXTVAL, &#39;sksarkar&#39;, order\_id.NEXTVAL, product\_id.NEXTVAL, payment\_id.NEXTVAL, DATE &#39;2020-11-26&#39;, 01700000014, &#39;Kuril, Dhaka&#39;);

INSERT INTO shipping (shipping\_id, customer\_id, order\_id, product\_id, payment\_id, date\_of\_order, customer\_phone\_no, customer\_address) VALUES (shipping\_id.NEXTVAL, &#39;aira&#39;, order\_id.NEXTVAL, product\_id.NEXTVAL, payment\_id.NEXTVAL, DATE &#39;2020-12-12&#39;, 01700000015, &#39;Bashundhara, Dhaka&#39;);

INSERT INTO shipping (shipping\_id, customer\_id, order\_id, product\_id, payment\_id, date\_of\_order, customer\_phone\_no, customer\_address) VALUES (shipping\_id.NEXTVAL, &#39;dwarner&#39;, order\_id.NEXTVAL, product\_id.NEXTVAL, payment\_id.NEXTVAL, DATE &#39;2020-12-11&#39;, 01700000016, &#39;Mirpur,Dhaka&#39;);

INSERT INTO shipping (shipping\_id, customer\_id, order\_id, product\_id, payment\_id, date\_of\_order, customer\_phone\_no, customer\_address) VALUES (shipping\_id.NEXTVAL, &#39;hamla&#39;, order\_id.NEXTVAL, product\_id.NEXTVAL, payment\_id.NEXTVAL, DATE &#39;2020-12-11&#39;, 01700000017, &#39;Bashundhara,Dhaka&#39;);

INSERT INTO shipping (shipping\_id, customer\_id, order\_id, product\_id, payment\_id, date\_of\_order, customer\_phone\_no, customer\_address) VALUES (shipping\_id.NEXTVAL, &#39;mali&#39;, order\_id.NEXTVAL, product\_id.NEXTVAL, payment\_id.NEXTVAL, DATE &#39;2020-12-17&#39;, 01700000018, &#39;Banani,Dhaka&#39;);

INSERT INTO shipping (shipping\_id, customer\_id, order\_id, product\_id, payment\_id, date\_of\_order, customer\_phone\_no, customer\_address) VALUES (shipping\_id.NEXTVAL, &#39;sali&#39;, order\_id.NEXTVAL, product\_id.NEXTVAL, payment\_id.NEXTVAL, DATE &#39;2020-12-5&#39;, 01700000019, &#39;Baridhara,Dhaka&#39;);

INSERT INTO shipping (shipping\_id, customer\_id, order\_id, product\_id, payment\_id, date\_of\_order, customer\_phone\_no, customer\_address) VALUES (shipping\_id.NEXTVAL, &#39;niqbal&#39;, order\_id.NEXTVAL, product\_id.NEXTVAL, payment\_id.NEXTVAL, DATE &#39;2020-12-4&#39;, 01700000020, &#39;Gulshan,Dhaka&#39;);

select \* from shipping

![](https://i.imgur.com/TKDSoUa.jpg)

# Conclusion

Finally, successfully develop and implement the E-commerce Management System with the help of Oracle Database 10g and SQL query, includes all the features which are the fundamental requirements for an E-commerce Management System.

Finally got success in our attempt to take care of the needs of both the customers as well as the administrator which was our main objective.

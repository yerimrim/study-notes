### 실습

```sql
CREATE DATABASE resDB;
USE resDB;

## address TABLE
CREATE TABLE address (zip_code VARCHAR(6), adress_detail VARCHAR(20));
ALTER TABLE address ADD CONSTRAINT pk_zip_code PRIMARY KEY (zip_code);

## customer TABLE
CREATE TABLE customer(customer_id VARCHAR(10),
					  customer_name VARCHAR(20),
                      phone_number VARCHAR(15),
                      email VARCHAR(20),
                      first_reg_date DATE,
                      sex_code VARCHAR(2),
                      birth VARCHAR(8),
                      job VARCHAR(20),
                      zip_code VARCHAR(6));
ALTER TABLE customer ADD CONSTRAINT pk_customer PRIMARY KEY (customer_id);
ALTER TABLE customer ADD CONSTRAINT fk_customer FOREIGN KEY (zip_code)
REFERENCES address (zip_code);

## item TABLE
CREATE TABLE item (item_id VARCHAR(10),
				   product_name VARCHAR(30),
                   product_desc VARCHAR(50),
                   category_id VARCHAR(10),
                   price DECIMAL(10,0));
ALTER TABLE item ADD CONSTRAINT pk_item PRIMARY KEY (item_id);

## reservation TABLE
CREATE TABLE reservation (reserv_no VARCHAR(30),
						  reserv_date VARCHAR(8),
                          reserv_time VARCHAR(4),
                          customer_id VARCHAR(10) NOT NULL,
                          branch VARCHAR(20),
                          visitor_cnt DECIMAL(3,0),
                          cancel VARCHAR(1));
ALTER TABLE reservation ADD CONSTRAINT pk_reservation PRIMARY KEY (reserv_no);
ALTER TABLE reservation ADD CONSTRAINT fk_reservation_customer_id FOREIGN KEY (customer_id)
REFERENCES customer (customer_id);

##order_info TABLE
CREATE TABLE order_info (order_no VARCHAR(30),
						 item_id VARCHAR(10),
                         reserv_no VARCHAR(30),
                         quantity DECIMAL(3,0),
                         sales DECIMAL(10,0));
ALTER TABLE order_info ADD CONSTRAINT pk_order_info PRIMARY KEY (order_no, item_id);
ALTER TABLE order_info ADD CONSTRAINT fk_order_info_item_id FOREIGN KEY (item_id)
REFERENCES item (item_id);
ALTER TABLE order_info ADD CONSTRAINT fk_order_info_reserv_no FOREIGN KEY (reserv_no)
REFERENCES reservation (reserv_no);
```

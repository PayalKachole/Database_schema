# Database_schema
  
  CREATE TABLE Customer
    (
        Customer_id VARCHAR(6) NOT NULL,
        c_pass VARCHAR(10) NOT NULL,
        Name VARCHAR(20) NOT NULL,
        Address VARCHAR(20) NOT NULL,
        Pincode NUMBER(6) NOT NULL,
        Phone_number_s number(10) NOT NULL,
        PRIMARY KEY (Customer_id),
        Cart_id VARCHAR(7) NOT NULL,
        FOREIGN KEY(Cart_id) REFERENCES cart(Cart_id)
    );
  
  
   CREATE TABLE Cart_item
    (
        Quantity_wished NUMBER(1) NOT NULL,
        Date_Added DATE NOT NULL,
        Cart_id VARCHAR(7) NOT NULL,
        Product_id VARCHAR(7) NOT NULL,
        FOREIGN KEY (Product_id) REFERENCES Product(Product_id),
        Primary key(Cart_id,Product_id)
    );

   CREATE TABLE Product
    ( 
        Product_id VARCHAR(7) NOT NULL,
	productName varchar(70) NOT NULL,
	productLine varchar(50) NOT NULL,
	Type VARCHAR(7) NOT NULL, 
	productVendor varchar(50) NOT NULL,
        Color VARCHAR(15) NOT NULL,
	P_Size VARCHAR(2) NOT NULL,
        Gender CHAR(1) NOT NULL,
        DiscountID INT,
        Cost NUMBER(5) NOT NULL,
        Quantity NUMBER(2) NOT NULL,
        Seller_id VARCHAR(6),
        PRIMARY KEY (Product_id,DiscountID), 
	FOREIGN KEY (DiscountID ) REFERENCES Discount(DiscountID )
	FOREIGN KEY (Seller_id) REFERENCES Seller(Seller_id)
        ON DELETE SET NULL
    );  
       
    
 CREATE TABLE Seller
    (
        Seller_id VARCHAR(6) NOT NULL,
        s_pass VARCHAR(10) NOT NULL,
        Name VARCHAR(20) NOT NULL,
	Phone_num NUMBER(10) NOT NULL,
        Address VARCHAR(10) NOT NULL,
        PRIMARY KEY (Seller_id,Phone_num)
	ON DELETE CASCADE
	ON UPDATE CASCADE 
    );
  
   
   CREATE TABLE Payment
    (
        payment_id VARCHAR(7) NOT NULL,
        payment_date DATE NOT NULL,
        Payment_type VARCHAR(10) NOT NULL,
        Customer_id VARCHAR(6) NOT NULL,
        Cart_id VARCHAR(7) NOT NULL,
        PRIMARY KEY (payment_id),
	paymentType varchar(40) NOT NULL,
        FOREIGN KEY (Customer_id) REFERENCES Customer(Customer_id),
        FOREIGN KEY (Cart_id) REFERENCES Cart(Cart_id),
        total_amount numeric(6)
    );

    
CREATE TABLE Discount (
DiscountID INT,
DiscountPercent DEC(2, 2),
Valid CHAR(1) DEFAULT 'N',
PRIMARY KEY (DiscountID)
);



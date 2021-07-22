# Database_schema

CREATE TABLE products (
  productCode varchar(15) NOT NULL,
  `productName` varchar(70) NOT NULL,
  `productLine` varchar(50) NOT NULL,
  `productScale` varchar(10) NOT NULL,
  `productVendor` varchar(50) NOT NULL,
  `productDescription` text NOT NULL,
  `quantityInStock` smallint(6) NOT NULL,
  `buyPrice` double NOT NULL,
  `MSRP` double NOT NULL,
  PRIMARY KEY  (`productCode`)
);

 CREATE TABLE Seller
    (
        Seller_id VARCHAR(6) NOT NULL,
        s_pass VARCHAR(10) NOT NULL,
        Name VARCHAR(20) NOT NULL,
        Address VARCHAR(10) NOT NULL,
        PRIMARY KEY (Seller_id)
    );
    
    
CREATE TABLE `payments` (
  `customerNumber` int(11) NOT NULL,
  `paymentDate` datetime NOT NULL,
  `amount` double NOT NULL,
  paymentType varchar(40) NOT NULL,
  PRIMARY KEY  (`customerNumber`)
);

CREATE TABLE Discount (
	DiscountID INT,
    DiscountPercent DEC(2, 2),
    Valid CHAR(1) DEFAULT 'N',
    PRIMARY KEY (DiscountID)
);

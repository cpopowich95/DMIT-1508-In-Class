# ESP Document 1

This is a sample solution of the normalizing the **Customer Orders View** in ESP Document 1.

## Customer Orders View

### 0NF - List all Attributes

After performing Zero-Normal form, a single table (entity) was
generated: **Order**.

**Order:** (CustomerNumber. FirstName, LastName, Address, City,
Province, PostalCode, Phone, <b class="pk">OrderNumber</b>, 
<b class="gp">{</b>ItemNumber, Description, Quantity, CurrentPrice, SellingPrice,
 Amount<b class="gp">}</b>, Subtotal GST, Total)

 ### 1NF - Identify Repeating Groups

After performing First-Normal Form, a new table was generated:
OrderDetail.

**Order:** (<b class="pk">OrderNumber</b>, CustomerNumber, FirstName,
 LastName, Address, City, Province, PostalCode, Phone, Date, 
 Subtotal, GST, Total)

 **OrderDetail:** (<b class="pk"><u class = "fk">OrderNumber</u>, ItemNumber</b>,
  Description, Quantity, CurrentPrice, SellingPrice, Amount)

  ### 2NF

  After performing Second-Normal Form, another new table was generated: **Item**.

  **OrderDetail:** (<b class="pk"><u class="fk">OrderNumber</u>, <u class="fk">ItemNumber</u></b>,
  Quantity, SellingPrice, Amount)

  **Item:** (<b class="pk">ItemNumber</b>, Description, CurrentPrice)

### 3NF

After performing Third-Normal Form, another new table was generated: **Customer**.

**order:** (<b class="pk">OrderNumber</b>, <u class="fk">CustomerNumber</u>, Date, Subtotal, GST, Total)

**Customer:** (<b class="pk">CustomerNumber</b>, FirstName, LastName, Address, City, Province, PostalCode,
 Phone)

### Tables after 3<sup>rd</sup> Normal Form
These are the tables/entities after normalizing the Customer Details View.

**Order:** (<b class="pk">OrderNumber</b>, <u class="fk">CustomerNumber</u>, Date, Subtotal, GST, Total)

**OrderDetail:** (<b class="pk"><u class="fk">OrderNumber</u>, <u class="fk">ItemNumber</u></b>, Quantity, SellingPrice, Amount)

**Item:** (<b class="pk">ItemNumber</b>, Description, CurrentPrice)

**Customer:** (<b class="pk">CustomerNumber</b>, FirstName, LastName, Address, City, Province, PostalCode,
 Phone)

----

### 0NF - List all Attributes

After performing Zero-Normal form, a single table (entity) was
generated: **PaymentsLog**.

**PaymentsLog:** (<b class="pk">OrderNumber</b>, OrderDate, OrderTotal, FirstName, LastName, CustomerNumber, <b class="gp">{</b>Date, PaymentAmount, PaymentNumber, BalanceOwing, PaymentType, DepositBatchNumber<b class="gp">}</b>)

### 1NF - Identify Repeating Groups

After performing First-Normal Form, a new table was generated:
**PaymentsMade**.

**PaymentsMade:** (<b class="pk"><u class="fk">OrderNumber</u>, Payment Number</b>, Date, PaymentAmount, BalanceOwing, PaymentType, DepositBatchNumber)

**PaymentsLog:** (<b class="pk">OrderNumber</b>, OrderDate, OrderTotal, FirstName, LastName, CustomerNumber)

### 2NF

After performing Second-Normal Form, a new table was generated:
**Payment**.

**Payment:** (<b class="pk">PaymentNumber</b>, PaymentAmount, PaymentType, DepositBatchNumber)

**PaymentsMade:** (<b class="pk"><u class="fk">OrderNumber, PaymentNumber</u></b>, Date, BalanceOwing)

### 3NF

After performing Third-Normal Form, a new table was generated:
**Customer**.

**Customer:** (<b class="pk">CustomerNumber</b>, FirstName, LastName)

**PaymentsLog:** (<b class="pk">OrderNumber</b>,<u class="fk">CustomerNumber</u>, OrderDate, OrderTotal)

### Tables after 3<sup>rd</sup> Normal Form
These are the tables/entities after normalizing the Payments Log View.

**PaymentsLog:** (<b class="pk">OrderNumber</b>,<u class="fk">CustomerNumber</u>, OrderDate, OrderTotal)

**PaymentsMade:** (<b class="pk"><u class="fk">OrderNumber, PaymentNumber</u></b>, Date, BalanceOwing)

**Payment:** (<b class="pk">PaymentNumber</b>, PaymentAmount, PaymentType, DepositBatchNumber)

**Customer:** (<b class="pk">CustomerNumber</b>, FirstName, LastName)

----

<style type = "text/css">
.pk {
    font-weight: bold;
    display: inline-block;
    border: solid thin blue;
    padding: 0 1px;
}
.fk {
    color: green;
    font-style: italic;
    text-decoration: wavy underline green;
}
.gp {
    color: darkorange;
    font-size: 1.2em;
    font-weight: bold;
}
</style>
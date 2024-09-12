# Data_Modelling
Entities:
1. Branch: Represents each Fufu Republic outlet (e.g., Lekki, Agege).
2. Menu Item: Captures each item on the menu (e.g., Chinese Rice, Fufu, Jollof Rice).
3. Inventory: Tracks stock levels of items at each branch.
4. Customer: Captures customer information.
5. Sales: Represents each sale, including customer, items, payment, and location.
6. Payment Method: Defines the methods of payment (e.g., Cash, Nomba POS, Paystack).
7. Promotion: Contains promotion data, including discounts and target segments.
   
Relationships:
* Branch to Menu Item: One branch can have multiple menu items.
* Branch to Inventory: Each branch maintains its own inventory levels.
* Sales to Branch: A sale is made at one branch.
* Sales to Customer: A customer can make multiple sales.
* Sales to Menu Item: Each sale includes one or more menu items.
* Sales to Payment Method: Every sale involves a single payment method.
* Sales to Promotion: Promotions can be applied to specific sales.

Constraints:
* Some menu items may be available in certain branches but not others.
* Inventory needs to track stock to prevent overstocking or running out of items.
* Sales must be processed using one of the allowed payment methods.
* Customer data must be secure and managed in line with privacy regulations.

Dimensional Model
Business Process: Sales Performance Analysis
Business Questions:
- What are the most popular menu items across different branches?
- How do sales compare for dine-in, take-out, and online orders?
- Which payment methods are used most frequently?
- What are the peak sales periods (e.g., by time of day, day of week, or month)?
- How do promotions impact customer behavior and sales?


Grain: Each record in the fact table represents a unique sale at a specific branch, for a specific menu item, on a particular date, with a chosen payment method.

Dimension Tables:

Branch Dimension
 - Branch ID
 - Branch Name
 - Location
 - Manager
 - Opening Date

Customer Dimension
- Customer ID
- Customer Name
- Loyalty Program Status
- Email
- Phone Number

Menu Item Dimension
- Menu Item ID
- Item Name
- Category (Main Course, Drink, Dessert)
- Price
- Branch-Specific Availability (Yes/No)

Payment Method Dimension
- Payment Method ID
- Payment Type (e.g., Cash, POS, Online)
- Transaction Fees

Date Dimension
- Date Key
- Day
- Month
- Year
- Quarter
- Weekday/Weekend

Promotion Dimension
- Promotion ID
- Promotion Name
- Start Date
- End Date
- Discount Percentage


Fact Table: Sales Fact

Grain: One sale per branch, per menu item, per customer, per time.
Measures:
- Sale ID
- Sale Date
- Branch ID
- Customer ID
- Menu Item ID
- Payment Method ID
- Quantity Sold
- Total Sale Amount
- Order Type (Dine-in, Take-out, Online)

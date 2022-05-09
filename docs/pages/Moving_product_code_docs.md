# **Moving Products Code Documentation.**

## **File in *\recommender_sys\Code\FAST_Moving_Products/* Folder**

### **Fast_Moving_Product_Analysis.py**

This file is useful to analyze the fast moving products. i.e. to understand the which products are sold quickly and which ones are sold  slowly. 

#### no_of_days_product_wasin_warehouse

This function will return the age of the product in warehouse. i.e. it will return no of the day product was in the warehouse.\
Args:
>data[dataFrame] : Important column ["Order Date", "Supply Date"]

Returns:
> date[dataFrame] : important colum ["Days] (int)

Usage:

~~~python
# Product data with no of days product in warehouse
product_data = no_of_days_product_wasin_warehouse(data)
~~~

This file will also return the moving condition of the product by checking how many days product was in warehouse. The moving condition as follow. And product will be saved in excel file.

>"Best seller" : If product is sold within 7 days\
>"Standard" : If the product is sold within 8 to 14 days\
>"Below Standard" : If the product is sold within 15 to 30 days\
>"Slow mover" :If the product is sold after more than 31 day\
> "Not Rated" :  

### **SQL_fetch.py**

This file is useful fetch data from SQL database from the with given column names bellow.\
This file is also useful to save the unsold data from the 

#### Query

This function useful to return  the dataFrame from sql database.\
Args:
>query[string] : SQL query to fetch data.

Return:
> data[dataFrame] : Returns the dataFrame for input query

Usage :

~~~python
# fetching the product_data from the  products table
product_data = Query("select * from products")
~~~

#### Get_Column_Names

Function includes query of getting all the columns from table.\
Args:
> table_name[string] : name of the table from sql database.

Return:
>columns[list] : list of the columns in the given input table.

Usage:

~~~python
# columns name from the product table.
product_columns = Get_Column_Names("'products'") 
~~~

#### Column_Rename_FromSQL

This function is used to the rename and replace the categories from category (product group) column.\
Args:
>df[dataFrame] : Important columns ["Category"]

Return:
>df[dataFrame] : returns the dataFrame with with corrected category or product group name 

Usage : 

~~~python
# correct category name from the DatFrame
corrected_category_name =  Column_Rename_FromSQL(product_data)
~~~

#### Mapping

This function is useful to map the Category according to the  standard  10 category.\
Args
> df[DataFrame] : Important column["Category"]

Returns:
> df[DataFrame] : Category (product group are Mapped in to 10 category)

Usage:

~~~python
# map the category
mapped_category_data = Mapping(product_data)
~~~

### **Customer_nr.py**

#### add_kunden_details

Add details of Customers there names and firm name which we are getting in database.\
Args:
> data[DataFrame]: Important Columns ["Customer Id"]\
>Customer[DataFrame] : Important Columns["Kundennummer", "Vorname", "Nachname", "Firma"]

Returns: 
>data[dataFrame] : dataFrame with added customer Details

Usage:

~~~python
# Add customer details to the data
refined_data_with_customer_details = add_kunden_details(refined_data, Customer)
~~~

This file will also contains further refining of the customer details, And also remove the non-frequent old customer.

### **Plot_Product_Movement.py**
 
Visual presentation of the articles and  their moving conditions. 
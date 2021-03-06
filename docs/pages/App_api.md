# **Application API**

In general, an API (or Application Programming Interface) provides an interface between two systems. It’s like a cog that allows two systems to interact with each other. In this case, the two systems are mobile application and database that interact programmatically through the API.


## **Scan Products**

To scan the products information from database\
Request type : POST\
Input :  { "id": "LagerID", }

~~~python
    # route   
   "URL/scan_product"
~~~

###

#### **Attribute of scan Products**

* *Input*\
    Parameters to Fetch the products as

  * id 
    * column name in database : Article number
    * datatype: string  
 
 ~~~python
# Input Object
{ 
   "id" : "82351048"
}   
 ~~~

* *Return*\
    Scan Product will return following attributes. All the returned object attribute  will be string datatype.  

  * "LagerNumber"\
  Lager number of the Product. Lager number is uniq Id of the product 

  * "ArticleNumber"\
  Product article number. Based on brand and product category. provided by brand.

  * "SupplyID"\
  Supply Number of the Product  

  * "ProductGroup"\
  Product category

  * "BrandName"\
  Brand Name in short.

  * Weight\
  Weight of the product.
    * Data type : String


~~~python 
# Object of the scan product
{
  "ArticleNumber": "82351048", "BrandName": "GOR", 
  "Categories": "3_Kühlgeräte", 
  "Description": "Fridge freezer combination", 
   "LagerNumber": null, 
   "ProductGroup": "Kühl/Gefrierkombination",
  "SupplyID": null, 
  "Weight": "70"
}
~~~

## **Add User**

~~~python
# Route
"URL/add_user"
~~~

Add user to the database\
Request type : POST\
Input :

~~~python
# input object
{ "usr_fname": "vishvajit", "usr_lname": "jambuti", "usr_name": "v.jambuti", "usr_permission": 0, "usr_email": "v.jambuti@elvinci.de", "usr_pwd": "abc123" }
~~~

###

#### **Add User Attribute**

Following are the attribute of the add user\

* usr_fname\
    First name of the user.\
  * Data type : String  
* usr_lname\
    Last name of the user
  * Data type : String
* usr_name\
    Screen name or user name
  * Data type : String
* usr_permission\
    User access level.
  * Data type : int
* usr_email\
    User Email id.
  * Data type : String
* usr_pwd\
    Password Alpha Numeric.
  * Data type : String.

## **Get Users**

~~~python
# route
"URL/get_user_details"
~~~

Get the details of the users stored in database\
Request type : POST\
Input :

~~~python
# Input object
{ 
    "usr_name" : "v.jambuti"
}
~~~

###

#### **Get Users Attribute**

* *Input Parameter*\
  * usr_name\
    User Name
    * Data Type : String  

* *Returns*
  * usr_id\
  User id 
    * Data Type : String
  * usr_name\
  User Name 
    * Data Type : String    
  * usr_fname\
  First name of the User.
    * Data Type : String
  * usr_lname\
  Last Name of the user
    * Data Type : String
  * usr_permission\
  User Access level. 
    * Data Type : int

~~~python
# Return Object
{ "usr_fname": "vishvajit", "usr_lname": "jambuti", "usr_name": "v.jambuti", "usr_permission": 0, }

~~~

## **Delete User**

~~~python
# Route
"URL/delete_user"
~~~

Delete the user from Database.\
Request type : POST\
Input :

~~~python
# Input object
{
    "usr_name" : "v.jambuti"
}
~~~

###

#### **Delete User Attribute**

~~~python
# output Object 
{
     "success": True,
     "message": "Username: v.jambuti is deleted successfully."
}
~~~

## **Login**

User login for application
Request type : POST\
Input : 

~~~python
{ "usr_name": "v.jambuti", "usr_pwd": "abc123" }
~~~

###

#### **Login Attribute**

**Input Parameter*

* usr_name\
    User name as
  * Data type : String

* usr_pwd\
    User Password.
  * Data type : String



## **Product Description**

~~~python
# Route
"URL/all_products_description"
~~~

This endpoint  is useful get all the products from warehouse.

###

#### **Product Description Attribute**

~~~python
# Output Object
{
}
~~~

## **Get Product Description**

~~~python
# Route
"URL/all_products_description"
~~~

Get the product details from the database. 
Request type : POST\
Input :

~~~python
# Input object
{
 "lager_number" : "112808355"
}
~~~

###

#### **Get Product Description Attribute**

following input  and return attribute of the get product description.  

* *Input parameters*
  * lager_number
    Lager number is for the product and used as ID 
    * Data type : String 

* *Return Parameters*
  * lager_number\
  Lager number of the Product. Lager number is uniq Id of the product\
    * Data Type : String

  * article_number\
  Product article number. Based on brand and product category. provided by brand.
    * Data type : String

  * product_group\
  Category of the product
    * Data type :  String

  * brand_name\
  Product brand name
    * Data Type : String

  * description\
  Product Description
    * Data type :  String
  * question_answer_list
  Question Answer List frm the app.
    * Data type :  Dictionary

  * scaling_list
  Scaling list for the product answer
    * Data type : Dictionary

  * final_grade\
  Final Grade  of the product.
    * Data type : String

  * created_by_usr\
  User Who created product entry.
    Data type : String
  * is_Active\
  Is the product Active or the product available for the sale
    * Data type : bool

  * remarks\
  Product Remark
    * Data type : String

  * supply_id\
  Supply number of the product.
    * Data type : String

  * usage\
  Product usage.
    * Data type : String

  * image_list\
  List of the image taken
    * Data type : String

  * datetime_uploaded\
  Time and date the product is uploaded.
    Data type : Time

~~~python
# Return Object
{
"lager_number" : "116224530" , "article_number": "82351048", "product_group" : "Kühl/Gefrierkombination", "brand_name" : "GOR", "description": "Fridge freezer combination",  "question_answer_list" : {"0":"No","10":"No","11":"No","12":"No","13":"Yes","8":"Yes","9":"Yes"}, "scaling_list" : {"17":6}, "final_grade": "B", "created_by_usr" : "2", "is_visible": "1",  "remarks": "",  "supply_id": "8808755", "usage": "gebraucht", "image_list":[0], "datetime_uploaded": 2021-07-03 15:48:29
}
~~~

## **Delete Product Description**

~~~python
# Route
"URL/delete_product_description"
~~~

Delete the product data from database\
Request type : POST\
Input :

~~~python
# Input object
{
    "lager_number" : "112808355"
}
~~~

###

#### **Delete Product Description Attribute**

* *Input Parameter*
  * "LagerNumber"\
  Lager number of the Product. Lager number is uniq Id of the product
    * Data Type : String

* *Return parameter*
  * It returns the following massage after deleting products.

~~~python
# Return Object
{
        "success": True,
        "message": "Product: 112808355 is deleted successfully.",
}
~~~

## **Add Product Description**

~~~python
# Route
"URL/add_product_description"
~~~

Request type : POST, GET\
Input :

~~~python
{
    "lager_number" : "116224530" , "article_number": "82351048", "product_group" : "Kühl/Gefrierkombination", "brand_name" : "GOR", "description": "Fridge freezer combination",  "question_answer_list" : {"0":"No","10":"No","11":"No","12":"No","13":"Yes","8":"Yes","9":"Yes"}, "scaling_list" : {"17":6}, "final_grade": "B", "created_by_usr" : "2", "is_visible": "1",  "remarks": "",  "supply_id": "8808755", "usage": "gebraucht", "image_list":[0], "datetime_uploaded": 2021-07-03 15:48:29
}
~~~

###

#### **Add Product Description Attribute**

* *Input Parameter*
  * lagerNumber\
    Lager number of the Product. Lager number is uniq Id of the product\
    * Data Type : String
  
  * productGroup\
  Category of the product
    * Data type :  String 

  * questionAnswerList\
  Question Answer List frm the app.
    * Data type :  Dictionary

  * scalingList\
  Scaling list for the product answer
    * Data type : Dictionary 

  * finalGrade\
  Final Grade  of the product.
    * Data type : String
  
  * articleNumber\
  Product article number. Based on brand and product category. provided by brand.
    * Data type : String

  * description\
  Product Description
    * Data Type : String

  * brandName\
  Product brand name
    * Data Type : String

  * usrID\
  Id of the user eho uploaded product
    * Data type : int
  
  * isActive\
  Is the product Active or the product available for the sale
    * Data type : bool

  * SupplyID\
  Supply number of the product.
    * Data type : String 

  * Remarks\
  Product Remark
    * Data type : String

  * usage\
  Product usage.
    * Data type : String

  * imageNumberList\
  List of the image taken
    * Data type : String


## **Get Supply Id**

~~~python
# Route
"URL/get_supply_id"
~~~

Request type : POST\
Input : 

~~~python
# Input object
{
    "lager_number_list" : {}
}
~~~

###

#### **Get Supply Id Attribute**

## **Allow Images**

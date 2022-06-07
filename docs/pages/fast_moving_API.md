# **Moving Products API**

## **Moving Products**  

~~~python
# Route
"URL/moving_product"
~~~

Request Type : POST\
Input :

~~~python
{
    # id is product article number
    "id" : "192150"
}
~~~

### **Moving Products Attribute**

* *Input Parameter*
  * "id"\
  id is the article number of the product. Article number is brand and model specific. 

* *Return Parameter*
  * "Artikel Number"\
  This is the id of the product
    * Data type : String
  * "Moving_Condition"\
  This explain product demand. Depending upon the condition as explained bellow.
    * Data type : String
    >"Best seller" : If product is sold within 7 days\
    >"Standard" : If the product is sold within 8 to 14 days\
    >"Below Standard" : If the product is sold within 15 to 30 days\
    >"Slow mover" :If the product is sold after more than 31 day\
    > "Not Rated" : 
  * "quantity"\
  Quantity of the product in package 
    * Data type : int
  * "index"\
  Product index
    * Data type : int

~~~python 
# Return Object
{
    "Moving Condition": {
        "columns": [
            "Artikel Number",
            "Moving_Condition",
            "quantity"
        ],
        "data": [
            [
                "192150",
                "Standard",
                3
            ]
        ],
        "index": [
            571
        ]
    },
    "success": true
}
~~~

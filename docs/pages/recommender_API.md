# **Recommender API**

~~~python
# File Path 

~~~


## **Recommendation** 

This endpoint is useful to recommend product for the customer. This end point requires customer number as input and it will return 50 recommended product. 
Recommender system based on the **Rec_algorithm**. 

~~~python
# Route 
"URL/recommend"
~~~

Request type : POST\
Input :\

~~~python
# Input object
{
    # id is customer ID or Customer nr
    "id" : "70560"
}

~~~

### **Recommendation Attribute**

* *Inputs Parameter*
  * "id"\
  id is customer id or customer number.
    * Data type : String

* *Return Parameter*
  * "data"\
  Returns the lager number. And also returns the warehouse in which product is stored.\
  It return 50 products. It will return list of 50 lager number and the warehouse.
    * Data type : list.

~~~python
# Return object 
{
 "Recommend Items MVL": {
        "data": [
            "118579611",
            "118571234",
            "118569083",.....], "name": "MVL" 
            }
  "Recommend Items STOHR": {
        "data": [
            "900011695",
            "900012617",..], "name": "MVL"
  }
  "success": true

}
~~~

## **Package**

This endpoint is useful to create package for the customer by using recommendation algorithm shown above.

~~~python
# Route 
"URL/packages"
~~~

Request type : POST\
Input :

~~~python
# Input object
{
    # id is customer ID or Customer nr
    "id" : "70560"

}
~~~

### **Package Attribute**

* *Inputs Parameter*
  * "id"\
  id is customer id or customer number.
    * Data type : String

* *Return Parameter*
  * "data"\
  Returns the lager number. And also returns the warehouse in which product is stored.\
  It return around 150 products according to the customer package history. It will return list of lager number and the warehouse.
    * Data type : list.

~~~python
# Return object 
{
"Products MVL": {
        "data": [
            "118579611",
            "118571234",
            "118569083",.....], "name": "MVL" 
            }
  "Products STOHR": {
        "data": [
            "900011695",
            "900012617",..], "name": "MVL"
  }
  "success": true
}
~~~

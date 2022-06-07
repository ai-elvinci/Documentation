# **Recommender System**

Content-Based Filtering Recommender: As its name suggest, this type of recommender uses the similarity among the background information of the items or users to propose recommendations to users. For instance If the user A is an individual who buys a particular product P1 very frequently then, the product recommendation system would likely bale user A as potential customer of product P2.

## **Content_based_for_top_Customer.py**

*ask ahmed about  this functio  n* 

###

#### Top_Customer_Recommendation

Args: 
> None 

Returns: 
>content_df1[DataFrame]:\
>X_test[DataFrame]

Usage:

~~~ Python
# 
content_df, X_test =  Top_Customer_Recommendation()
~~~



## **Customer_Segmentation.py**

### 

#### Customer_Group

This function is used to analyze customer and cluster them in to separate group according to their buying behavior. This function will return dataFrame with customer divided in 6 clusters or segments. K-Means clustering algorithm is used to cluster the customers. Customers are clustered according to their buying capacity i.e. from history.\
Data will be fetched from SQL database by using SQL_connection_cs file.\
Args:
>None 

Returns: 
>customer_segmentation[DataFrame]: dataFrame with customer divided in 6 clusters important\
> column name["clusters"]


Usage:

~~~python
# DataFrame with customer segmentation 
 data = Customer_Group()
~~~

## **Paths**

Paths to the required data for the process. 

## **Preprocess_Packages.py**

###

#### Packages

Args:
>None

Returns:
>

Usage:

~~~python

~~~

## **SQL_fetch.py**

###

#### SQL_Data

This file is useful fetch data from SQL database from the with given column names bellow.\
This file is also useful to save the unsold data from the database.\
This function will also automatically connect to the database and fetch data from database.\
This  Function will return two dataFrame first one is all the sold product with the customer details i.e DataFrame for the training. And the second dataFrame is unsold products in ware house i.e DataFrame for the testing.\
Args: 
>None

Returns: 
>full_df[DataFrame]: DataFrame for the training the  recommendation algorithm\
>X_test[DataFrame]: Dataframe for the testing the  the recommendation algorithm 

Usage:

~~~Python
# Train and test data
X_train, X_test = SQL_Data()
~~~

*This function also contents following subfunctions* 


##### Query

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

##### Get_Column_Names

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

##### Column_Rename_FromSQL

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

## **SQL_Preprocess.py**

###

#### Recommendation_Preprocess

This function is used to preprocess the data for the recommendation. Data will be imported from the SQL_fetch file.\
Data is further preprocessed according the input requirement of the algorithm.\
Function will return two preprocessed dataFrame one training Data. And Second is testing dataFrame\
Args:
> None

Returns : 
>Data[DataFrame]: Training dataFrame\
>X_test[DataFrame]: Testing DataFrame

Usage:

~~~ python
# Pre-processed training and test data for the recommendation
X_train, X_test = Recommendation_Preprocess()
~~~

## **SQL_Connection_CS.py**

###

#### SQL_Connector

This function is used to get data from database and returns with refined dataFrame with renamed column name.\
Args:
> None

Returns: 
> Data[DataFrame]: dataFrame with the refined data column  name. 

Usage:

~~~ Python
# data from database
data =  SQL_Connector()
~~~


*This function also contents following subfunctions* 

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
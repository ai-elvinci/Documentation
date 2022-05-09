# **Grade predict API**

Grade_Classification.py:

- The file contain connection from SQL 94.130.184.90
- Getting all data from product table
- Encode columns ['product_group', 'brand_name','category', 'description', 'remarks', 'usage','final_grade']
- preprocess json columns: question_answer_list and scaling_list
- Each category have different list of these two columns
- In question_answer_list replace 1 for Yes and 2 for No
- In end function returns all dataframes based on unique categories (10)

Model.py:

- The File contain XGBoost Model to tain the model
- Data is spliited into 80, 20 training and testing.
- Save the models for each category data (10 Models)
- dump the model as .sav using joblib
- dump the features of each model as .sav
- Features : usage, question_answer_list, scaling_list
- Target : Grade

app.py:

- The file contains API to run each model based on category
  Model 0 = Backofen_Herd_Set
  Model 1 = Diverse
  Model 2 = FS_Herd
  Model 3 = GS
  Model 4 = Haube
  Model 5 = Kochfelder
  Model 6 = Kuhlgerate
  Model 7 = Trockner
  Model 8 = WM
  Model 9 = WM_Toplader 
- load the model based on category selected.
- load the features based on category selected. 
- As encoded the feature 'usage' values are:
  0 = Nicht gebraucht
  1 = Sehr gebraucht
  2 = Wenig gebraucht
  3 = gebraucht
- for each category selected take the full question answer list and form the dictionary
- now take the selected response od question_answer_list and match the original question_answer_list dictionary.
- replace 1 and 2 based on response and add others with 0 values. so we have whole values will be used as a feature to predict the value.
- example: Response {0:'Yes',1:'No'} and we have for category WM 5 questions (features)
	   so we have input like this [2,1,0,0,0]
- Same procedure we follow for Scaling list
- results from predictions are either 1,2,3
- 0 = A
- 1 = B
- 2 = C 

## **Predict Grade**

~~~python
# Route
"URL/Predict"
~~~

Predict the grade of the product. 
Request type : POST\
Input : Scaling list. 

~~~python
#Input Object
{
  "category" : "3_Kühlgeräte", "usage" : "gebraucht" , "question_answer_list" : {"0":"No","10":"No","11":"No","12":"No","13":"Yes","8":"Yes","9":"Yes"},  "Scaling_list" : {"17":6}

}
~~~

### **Predict Grade Attribute**

- *Input Parameter*
  - "category"\
  Category of the product.
    - Data type : String 

  - "usage"\
  Usage  of the product.
    - Data type : String

  - "question_answer_list"\
  Question Answer list from the app.
    - Data type : Dictionary

  - "Scaling_list"\
  Scaling list from app.
    - Data type : Dictionary

- *Return Parameter*
  - "Predicted Grade"\
  Predicted grade from algorithm.
    - Data type : String.

~~~python
# return Object
{
    "Predicted Grade": "B",
    "success": true
}
~~~

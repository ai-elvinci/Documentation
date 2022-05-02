# **Data Cleaning**

This repository is used to clean data from warehouse.

> This script is used to clean data exported from the JTL

Export data from JTL as given bellow

* Data exported from JTL

  * Artikeldaten

    Select following columns

    * Artikelnummer

    * HAN

    * Artikelname

    * ISBN

    * Hersteller

    * Warengruppe

  * Auftrag

    Select following columns

    * Kunden-Nr

    * Bestell Nr.

    * Artikelnummer

    * Bestelldatum

  * Rechnungen Neu

    Select following columns

    * Rechnungsnummer

    * Bestellnummer

---

## **Files in _script/src_ folder**  

---

### Artikle Nummer Cleaning

#### artikel_number_refine

  This function returns 9 digit lager nr starting with 1 
  first clear all the article number whose length is not 9

 Args:

>article_data [DataFrame] : Important colum [Artikelnummer],

Returns:

>DataFram : Refined "Artikelnummer"

Usage 

~~~python 
# product data with refined Artikel Nummenr 
product_data = artikel_number_refine(artikel_data)
~~~

---

### Bestell  Nummer Cleaning  

#### add_ordernr_to_artikelnr

Add the order number to article number 

Args:

>article_data(DataFrame) : Important columns ['Arikelnummer'] </p>
>auftrag_nr(Dataframe): Important columns ['Artikenummer', 'Bestell Nr.' ]

Returns:

>DataFrame: Returens with Bestellnummer Added column  

Usage:

~~~python
# product data with Added Bestellnummer   
product_data = add_ordernr_to_artikelnr(article_data, auftrag_nr)
~~~

#### merge_orderdate_on_artkelnr

Add the order number to article number 

Args:

>article_data(DataFrame) : Important columns ['Arikelnummer']</p>
>auftrag_nr(Dataframe): Important columns ['Artikenummer', 'Bestell Nr.' ]

Returns:

>DataFrame: Returens with Bestellnummer Added column  

Usage:

~~~python
# product data with Added Bestellnummer   
product_data = merge_orderdate_on_artkelnr(article_data, auftrag_nr)
~~~

#### add_orderdate_to_ordernr


Add the order date to oder number 

Args:

>article_data(DataFrame) : Important columns ['Bestellnummer']</p>
>auftrag_nr(Dataframe): Important columns ['Bestellnummer', 'Erstelldatum Bestellung' ]

Returns:

>DataFrame: Returens with  orderdate ["Bestell Date"] added column  

Usage:

~~~python
# product data with Added order date    
product_data = add_orderdate_to_ordernr(article_data, auftrag_nr)
~~~

#### add_orderdate_to_artkelnr

Add the order date to oder number 

Args:

>article_data(DataFrame) : Important columns ['Arikelnummer']</p>
>auftrag_nr(Dataframe): Important columns ['Artkelnummer', 'Erstelldatum Bestellung' ]

Returns:

>DataFrame: Returens with  orderdate ["Bestell Date"] added column  

Usage:

~~~python
# product data with Added order date    
product_data = add_orderdate_to_ordernr(article_data, auftrag_nr)
~~~

#### add_kunden_nr
 
Add Kunden nummer to article nr (Sold articles)

Args: 

>article_data(DataFrame) : Important columns ['Arikelnummer']</p>
>auftrag_nr(Dataframe): Important columns ['Artkelnummer', 'Kunden-Nr' ]

Returns:

>DataFrame: Returens with  added Kunden nr  ["kunden-nr"]

Usage:

~~~python
# product data with Added Kunden nr    
product_data = add_kunden_nr(article_data, auftrag_nr)
~~~

---

### Plomben Nummer Cleaning

#### add_plomben_nr_to_artikelnr

Add Plomben nummer to article nummer  

Args: 

>article_data(DataFrame) : Important columns ['Arikelnummer']</p>
>plomben_nr(Dataframe): Important columns ['Artkelnummer', 'ISBN' ]

Returns:

>DataFrame: Returens with  added plomben nr  ["PlombenNr"]

Usage:

~~~python
# product data with Added Plumben nummer     
product_data = add_plomben_nr_to_artikelnr(article_data, plomben_nr)
~~~

#### add_missing_plomben_nr

Add Missing Plumben nummer  corrected by Boris 

Args: 

>article_data(DataFrame) : Important columns ['Arikelnummer', 'PlombenNr']</p>
>missing_plomben_nr(Dataframe): Important columns ['Artkelnummer', 'PlombenNr' ]

Returns:

>DataFrame: Returens with adde missing plomben nr ["PlombenNr"]

Usage:

~~~python
# product data with Added Plumben nummer     
product_data =  add_missing_plomben_nr(article_data, missing_plomben_nr)
~~~


#### add_plomben_date_to_plomben_nr

Add Missing Plumben nummer  corrected by Boris 

Args: 

>article_data(DataFrame) : Important columns [ 'PlombenNr']</p>
>plomben_nr_and_date(Dataframe): Important columns ['PlombenNr' ]

Returns:

>DataFrame: Returens with  added plomben date ["PlombenDate"]

Usage:

~~~python
# product data with Added Plumben Date    
product_data =  add_plomben_date_to_plomben_nr(article_data, plomben_nr_and_date)
~~~


---

### Price Refine

Add price to the Articles 

Args: 

>article_data(DataFrame) : Important columns ['Artiklenummer']</p>
>price_data(Dataframe): Important columns [Artikelnummer, "Std. VK Netto"]

Returns:

>DataFrame: Returens with  added price for the articles  ["Onlineprice"]

Usage:

~~~python
# product data with Added price of the products     
product_data =  add_online_price(article_data, price_data)
~~~

---

### Grade Refine

#### grade_mapping

Mapping the grade on file exported from the JTL from the file given by Boris some of the file does not have proper grade so need to mapp the work further

 Args:

>article_data (DataFrame) : Important columns ["Anmerkung"]</p>
>grade_data (DataFrame): Important columns ["Zustand gekürzt"], ["Zustand"]

Returns:

>DataFrame: returens with refined  ['Grade']

Usage 

~~~python 
# product data with refined Grade  
product_data = grade_mapping(artikel_data, grade_map_data)
~~~

#### misslabled_grade_correction

Method to correct missilabled grade from jtl export.
</p> The misslabeled grade file corrected by Boris  


Args:

>article_data(DataFrame) : Important columns [Arikelnummer]</p>
>misslabled_grade(Dataframe): Important columns ['Arikelnummer', 'grade5' ]

Returns:

>DataFrame: Returens with refined  ['Grade']

Usage:

~~~python
# product data with refined Grade  
product_data = misslabled_grade_correction(article_data, misslabled_grade)
~~~

---

### Refine Product Category or Group or Warengruppen

#### refine_category

This funtion is used for refine and map the category of the articles.

Args:

  > artikel_data (DataFrame) :  Important column [Warengruppen]

 Returns:

  > DataFrame : returns with  Column [Group]

Usage 

~~~python 
# product data with refined group or category 
product_data = refine_category(artikel_data)
~~~

---

### Product Age

#### no_of_days_product_wasin_warehouse

This funtion is used for finding the Number of days product was in warehouse

Args:

  > artikel_data (DataFrame) :  Important column ["Bestell Date" , "PlombenDate"]

 Returns:

  > DataFrame : returns with  Column [NoOfDayProductwasInWearhouse]

Usage 

~~~python 
# product data 
product_data = no_of_days_product_wasin_warehouse(article_data)
~~~

---

---

## Main.py

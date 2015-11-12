# County Galway Libraries API
## Data Representation and Querying Project 2015
### Maciej Drabik
7th November 2015

## Introduction
This project provides the design and documentation for the dataset "County Galway Libraries" which is available at [data.gov.ie](https://data.gov.ie/dataset/county-galway-libraries).

This dataset provides usefull information about public libraries such as : location,address,web address, e-mail and opening times in Co.Galway.
Below You will find a breakdown of dataset provided in CSV file.

Column Name | Description
------------|------------
**X** | Map coordinate that provide information that allows to find a place using for example GOOGLE MAPS(X axis, GIS - Geographic Information Systems).
**Y** | Map coordinate(Y axis, GIS - Geographic Information Systems).
**Council_ID**| Refers to unique ID of library.
**Administrative_Authority** | Refers to administrative authority that is responsible for library.
**Address1**| Address of library.
**Address2**| Secondary address.
**Town**| Name of town.
**County**| Name of county.
**Phone**| Contact number.
**Email**| Library address e-mail.
**Website**| HTTP website of library.
**WGS84Latitude**| World Geodetic System **(WGS)**,latitude is defined with respect to an equatorial reference plane.
**WGS84Longitude**| World Geodetic System **(WGS)**,longitude is defined in terms of meridians, which are half-circles running from pole to pole. 
**Opening_Hours**| Opening Hours of library.

User can use ***HTTP*** methods to interact with the API but also ***JSON*** requests will work aswell.

>  ***LIST OF HTTP QUERIES***
------------------------------------------------------------------------------------------------
>-  GET: Gathers information of the selected object. It will not change any value on the server.
>-  POST: Creates new elements in the API. Used to create the different objects in the API.
>-  EDIT: Modifies an existing element in the API. Currently the job element is the only one that allows modifications.
>-  DELETE: Removes existing elements via API.

To access the main page of website user must use **GENERAL URL**(*Uniform Resource Locator*) which for example might be  : http://irishlibraries.ie .

Below you will find an raw example of how data in a rows in table looks like when user is searching information about library using a town name.

**GET URL EXAMPLE**
* http://irishlibraries.ie/[ town+library ]

* http://irishlibraries.ie/town/tuam
 
  Column    | Row
------------|------------
**X** | -8.854160713024363
**Y** | 53.514424483755874
**Council_ID**| GY
**Administrative_Authority** |GALWAY COUNTY COUNCIL
**Name**|TUAM LIBRARY
**Address1**| HIGH STREET
**Address2**| 
**Town**| TUAM
**County**| COUNTY GALWAY
**Phone**| +353 (0) 93 24287
**Email**| tuam@galwaylibrary.ie
**Website**| http://www.galway.ie/en/Services/Library/
**WGS84Latitude**| 53.514413
**WGS84Longitude**| -8.854173
**Opening_Hours**| 10:30 to 13:00 and 14:00 to 17:00

Here is complete list of **URL's** that allows user to manipulate database. Data will be also returned in JSON format.
--------------------------------------------------------------------------
* **EXAMPLE:** if user would like to find a list of libraries in a town.
* **URL:** https://irishlibraries.ie/town/galway/list

Column - TOWN    | Row - NAME
------------|------------
**GALWAY** | *WESTSIDE LIBRARY*
**GALWAY** | *BALLYBANE NEIGHBOURHOOD VILLAGE*
**GALWAY** | *Galway City Library*

**JSON**
```
[
  {"Council_ID": GY,
    "Town": Galway, 
    "Name": WESTSIDE LIBRARY,  
    "Name": BALLYBANE,
    "Name": GC Library,
    "type" : "GET",
    "https://irishlibraries.ie/town/galway/list"
  }
]
```


* **EXAMPLE:** if user would like to find a library by town on a map.
* **URL:** https://map.irishlibraries.ie/place/town/galway
  * [GALWAY ON GOOGLE MAPS](https://www.google.ie/maps/place/Galway/@53.2839229,-9.1888361,11z/data=!3m1!4b1!4m2!3m1!1s0x485b93955a2d5bff:0x32b1b440a495281)
  
* **EXAMPLE:** if user would like to find a opening time of a library searching by a library name.
* **URL:** https://map.irishlibraries.ie/town/galway/name/westsidelibrary/opening_hours

 Column - TOWN    | Row - Name | Row - Opening_Hours
------------|------------------|--------------------
**GALWAY** | *WESTSIDE LIBRARY* | 1.00am to 8.00pm
**GALWAY** | *BALLYBANE NEIGHBOURHOOD VILLAGE* | 10:30 to 13:00 and 14:00 to 17:00 
**GALWAY** | *Galway City Library* | 11.00am to 8.00pm












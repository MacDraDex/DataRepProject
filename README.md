# County Galway Libraries API
## Data Representation and Querying Project 2015
### Maciej Drabik
7th November 2015

## Introduction
This project provides the design and documentation for the dataset "County Galway Libraries" which is available at [data.gov.ie](https://data.gov.ie/dataset/county-galway-libraries).

### Dataset
This dataset provides usefull information about public libraries such as : location,address,web address, e-mail and opening times in Co.Galway. In this dataset information are stored in 27 rows that contains name in the field and 15 columns which contains the names of headers.  

Below You will find a breakdown of dataset provided in [CSV file](https://data.gov.ie/dataset/county-galway-libraries/resource/7b003559-841f-4342-b2be-9a7ed45439cf).

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
>-  POST: Creates new entries in the table database.
>-  PUT: Modifies an existing data stored in table.
>-  DELETE: Removes existing data from table.

To access the main page of website user must use **GENERAL URL**(*Uniform Resource Locator*) which for example might be  : http://irishlibraries.ie .

Below you will find an raw example of how data in a rows in table looks like when user is searching information about library using a town name.

**GET URL EXAMPLE**
---------------------

* http://irishlibraries.ie/[ town+library ]

* http://irishlibraries.ie/town/tuam


##HTTP GET 
* A GET request retrieves data from a web server by specifying parameters in the URL portion of the request.
* A URL to return a list of all libraries and their values. 
```
GET /irishlibraries.ie/town/tuam/ HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.1.5) Gecko/20091102 Firefox/3.5.5 (.NET CLR 3.5.30729)
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Connection: keep-alive
Cookie: PHPSESSID=r2t5uvjq435r4q7ib3vtdjq120
Pragma: no-cache
Cache-Control: no-cache 
```

 
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

**JSON Council_ID/Town/Name/type/url**
```
[
  {"Council_ID": GY,
    "Town": Galway, 
    "Name": WESTSIDE LIBRARY,  
    "Name": BALLYBANE,
    "Name": GC Library,
    "type" : "GET",
    "url":"https://irishlibraries.ie/town/galway/list"
  }
]
```


* **EXAMPLE:** if user would like to find a library by town on a map.
* **URL:** https://map.irishlibraries.ie/place/town/galway
  * [GALWAY ON GOOGLE MAPS](https://www.google.ie/maps/place/Galway/@53.2839229,-9.1888361,11z/data=!3m1!4b1!4m2!3m1!1s0x485b93955a2d5bff:0x32b1b440a495281)
  
 Row - X  | Row - Y | Row - Name | Column - TOWN    
------------|------------|---------------|------------
-9.07446057544246 | 53.277400205441175 |*WESTSIDE LIBRARY* | **GALWAY**
-9.002184575683327 | 53.282740990239205 |*BALLYBANE PUBLIC LIBRARY* | **GALWAY**
-9.052011015315966 | 53.271532932942051 |*Galway City Library* | **GALWAY**
**JSON Council_ID/Town/Name/type/url**
```
[
  {"Council_ID": GY,
    "Town": Galway, 
    "Name": WESTSIDE LIBRARY,  
    "X": -9.07446057544246,
    "Y": 53.277400205441175 ,
    "type" : "GET",
    "url":"https://map.irishlibraries.ie/place/town/galway"
  }
]

[
  {"Council_ID": GY,
    "Town": Galway, 
    "Name": BALLYBANE PUBLIC LIBRARY,  
    "X": -9.002184575683327,
    "Y": 53.282740990239205 ,
    "type" : "GET",
    "url":"https://map.irishlibraries.ie/place/town/galway"
  }
]

[
  {"Council_ID": GY,
    "Town": Galway, 
    "Name": Galway City Library,  
    "X": -9.052011015315966,
    "Y": 53.271532932942051 ,
    "type" : "GET",
    "url":"https://map.irishlibraries.ie/place/town/galway"
  }
]
```


  

  
* **EXAMPLE:** if user would like to find a opening time of a library searching by a library name.
* **URL:** https://irishlibraries.ie/town/galway/name/westsidelibrary/opening_hours

 Column - TOWN    | Row - Name | Row - Opening_Hours
------------|------------------|--------------------
**GALWAY** | *WESTSIDE LIBRARY* | 1.00am to 8.00pm

**JSON**
```
[
  {"Council_ID": GY,
    "Town": Galway, 
    "Name": WESTSIDE LIBRARY,  
    "Opening_Hours": [1.00am to 8.00pm]
    "type" : "GET",
    "url":"https://irishlibraries.ie/town/galway/name/westsidelibrary/opening_hours"
  }
]
```

##HTTP POST - for example when we want to change opening hours

* The POST method is used when you want to send some data to the server, for example, file update, form data, etc. The following example makes use of POST method to send a form data to the server.

```
POST /irishlibraries.ie/town/galway/name/westsidelibrary/opening_hours
Host: localhost
User-Agent: Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.1.5) Gecko/20091102 Firefox/3.5.5 (.NET CLR 3.5.30729)
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Connection: keep-alive
Referer: http://localhost/test.php
Content-Type: application/x-www-form-urlencoded
Content-Length: 43
 
Opening_Hours = 1.00am to 4.00pm&action=Submit
```

Database respond :

```
HTTP/1.1 200 OK
Date: Mon, 09 nov 2015 12:28:53 GMT
Server: Apache/2.2.14 (Win32)
Last-Modified: Fri, 13 Nov 2015 13:15:22 GMT
ETag: "34aa387-d-1568eb00"
Vary: Authorization,Accept
Accept-Ranges: bytes
Content-Length: 88
Content-Type: text/html
Connection: Closed

<html>
<body>
<h1>Request Processed Successfully</h1>
</body>
</html>
```

##DELETE REQUEST - to DELETE URL

* The DELETE method is used to request the server to delete a file at a location specified by the given URL.


```
DELETE /irishlibraries.ie/town/galway/list HTTP/1.1
User-Agent: Mozilla/4.0 (compatible; MSIE5.01; Windows NT)
Host: www.tutorialspoint.com
Accept-Language: en-us
Connection: Keep-Alive

```
Database respond:
```

HTTP/1.1 200 OK
Date: 09 nov 2015 12:28:53 GMT
Server: Apache/2.2.14 (Win32)
Content-type: text/html
Content-length: 30
Connection: Closed
<html>
<body>
<h1>URL deleted.</h1>
</body>
</html>
```


###Final thoughts :
I did this API documentation for my Data Representation and Querying project. During this project I have learned basics of Github Markdown language. My goal was to create easy-to-read document that is going to help all the future users to understand basics of HTTP Requests and how to operate this dataset. I'm more than sure that I'm going to keep this API updated and I will also add new features such as : JS methods and functions and XML code.

###Resources :

* [HTTP METHODS](http://www.tutorialspoint.com/http/http_methods.htm)
* [GITHUB MARKDOWN](https://guides.github.com/features/mastering-markdown/)
* [JSON OVERVIEW](http://www.tutorialspoint.com/json/json_overview.htm)
* [REST API TUTORIAL](http://www.restapitutorial.com/lessons/httpmethods.html)










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

The current methods allowed to interact with the API are:
> - **HTTP** , **JSON**:
> - GET: Gathers information of the selected object. It will not change any value on the server.
> - OST: Creates new elements in the API. Used to create the different objects in the API.
> - EDIT: Modifies an existing element in the API. Currently the job element is the only one that allows modifications.
> - DELETE: Removes existing elements via API.






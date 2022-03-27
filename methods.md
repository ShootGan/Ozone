---
title: All Methods
layout: template
filename: methods
--- 

This page goes over all the methods that Ozone offers to fetch air quality data:

* [get_city_air](#get_city_air) 
* [get_multiple_city_air](#get_multiple_city_air)
* [get_coordinate_air](#get_coordinate_air)
* [get_multiple_coordinate_air](#get_multiple_coordinate_air)
* [get_range_coordinates_air](#get_range_coordinates_air)
* [get_specific_parameter](#get_specific_parameter)
* [reset_token](#reset_token)


## To get air quality data using city names

### get_city_air

This method is used to get the air quality for a single city using its name.

#### Usage Example

```python
data = get_city_air(city='Tokyo', data_format='df', params=['co', 'no2'])
```

#### Arguments

**city** : str

The name of the city/location for which you want air quality data.

**data_format** : str

An optional argument to specify the format that you want the data returned in. You can choose between the following:

df - a Pandas dataframe. Selected by default  
csv - A CSV file (saved to your local directory)  
xlsx - An Excel file (saved to your local directory)  
json - A JSON file (saved to your local directory)  

If this argument is left blank, a dataframe with the data is automatically returned

**df** : pandas.Dataframe

An optional argument to pass in a dataframe that you may have previously retrieved. 

For example:- You previously used this method to get data for Delhi. Now you want to combine this existing dataframe with some new data from London, then you can consolidate both dataframes by passing the old one into this argument as you fetch the new data for London.

**params** List[str]

An optional argument to specifiy which air quality parameters to get data for. If this is left blank then data for every air quality parameter is retrieved.  
You can choose from the following - pm25, aqi, pm10, o3, co, no2, so2, dew, h, p, t, w, wg

---

### get_multiple_city_air

This method is used to get the air quality for a single city using its name.

#### Usage Example

```python
get_multiple_city_air(cities=['Tokyo', 'Seattle', 'Sydney'], data_format='csv', params=['co', 'no2', 'dew', 'co2'])
```

#### Arguments

**city** : str

The name of the city/location for which you want air quality data.

**data_format** : str

An optional argument to specify the format that you want the data returned in. You can choose between the following:

df - a Pandas dataframe. Selected by default  
csv - A CSV file (saved to your local directory)  
xlsx - An Excel file (saved to your local directory)  
json - A JSON file (saved to your local directory)  

If this argument is left blank, a dataframe with the data is automatically returned

**df** : pandas.Dataframe

An optional argument to pass in a dataframe that you may have previously retrieved. 

For example:- You previously used this method to get data for Delhi. Now you want to combine this existing dataframe with some new data from London, then you can consolidate both dataframes by passing the old one into this argument as you fetch the new data for London.

**params** List[str]

An optional argument to specifiy which air quality parameters to get data for. If this is left blank then data for every air quality parameter is retrieved.  
You can choose from the following - pm25, aqi, pm10, o3, co, no2, so2, dew, h, p, t, w, wg

---

### get_specific_parameter

Get a single air quality parameter (example: CO or PM2.5) for a single city, and have it returned as a float.

#### Usage Example

```python
get_specific_parameter('Shanghai', 'pm2.5')
```

#### Arguments

**city** : str

The name of the city that you wish to get air quality data for. This argument is required.

**param** : str

Used to pecifiy which air quality parameter to get data for. This argument is required.
You can choose from the following - pm25, aqi, pm10, o3, co, no2, so2, dew, h, p, t, w, wg

---
## To get air quality data using geographical coordinates

### get_coordinate_air

Gets the air quality data for the closest measuring station to the input coordinate pair (latitude-longitude). 

#### Usage Example

```python
get_coordinate_air(lat=26.2041, long=28.0473, data_format='csv')
```

#### Arguments

**lat** : float

The latitude coordinate

**long** : float

The longitude coordinate

**data_format** : str

An optional argument to specify the format that you want the data returned in. You can choose between the following:

df - a Pandas dataframe. Selected by default  
csv - A CSV file (saved to your local directory)  
xlsx - An Excel file (saved to your local directory)  
json - A JSON file (saved to your local directory)  

If this argument is left blank, a dataframe with the data is automatically returned

**df** : pandas.Dataframe

An optional argument to pass in a dataframe that you may have previously retrieved. 

For example:- You previously used this method to get data for Delhi. Now you want to combine this existing dataframe with some new data from London, then you can consolidate both dataframes by passing the old one into this argument as you fetch the new data for London.

**params** List[str]

An optional argument to specifiy which air quality parameters to get data for. If this is left blank then data for every air quality parameter is retrieved.  
You can choose from the following - pm25, aqi, pm10, o3, co, no2, so2, dew, h, p, t, w, wg

---

### get_multiple_coordinate_air

Get air quality data for several coordinate pairs.  
Input a list of coordinate pairs (lat-long) and get air quality data from the closest measuring station to each one. 

#### Usage Example

```python
get_multiple_coordinate_air(locations=[(12.4783,11.6143), (57.15780,106.75697), (-35.04664, 120.51377)], data_format='csv')
```

#### Arguments

**locations** : List[Tuple[float, float]]

A list of coordinates, entered in tuples in this form (latitude, longitude).

**data_format** : str

An optional argument to specify the format that you want the data returned in. You can choose between the following:

df - a Pandas dataframe. Selected by default  
csv - A CSV file (saved to your local directory)  
xlsx - An Excel file (saved to your local directory)  
json - A JSON file (saved to your local directory)  

If this argument is left blank, a dataframe with the data is automatically returned

**df** : pandas.Dataframe

An optional argument to pass in a dataframe that you may have previously retrieved. 

For example:- You previously used this method to get data for Delhi. Now you want to combine this existing dataframe with some new data from London, then you can consolidate both dataframes by passing the old one into this argument as you fetch the new data for London.

**params** List[str]

An optional argument to specifiy which air quality parameters to get data for. If this is left blank then data for every air quality parameter is retrieved.  
You can choose from the following - pm25, aqi, pm10, o3, co, no2, so2, dew, h, p, t, w, wg

---

### get_range_coordinates_air

Get air quality data for all measuring stations between two latitude-longitude coordinate boundaries. Every station between the latitude bounds, and the longitude bounds will be polled for data.

> **NOTE**: This can be a very large number of stations sometimes and can take quite long - so don't be alarmed if it runs for a bit.

#### Usage Example

```python
get_range_coordinates_air(, data_format='csv')
```

#### Arguments

**lower_bound**: Tuple[float, float]

The lower boundary coordinate pair.

**upper_bound**: Tuple[float, float]

The upper boundary coordinate pair.

**data_format** : str

An optional argument to specify the format that you want the data returned in. You can choose between the following:

df - a Pandas dataframe. Selected by default  
csv - A CSV file (saved to your local directory)  
xlsx - An Excel file (saved to your local directory)  
json - A JSON file (saved to your local directory)  

If this argument is left blank, a dataframe with the data is automatically returned

**df** : pandas.Dataframe

An optional argument to pass in a dataframe that you may have previously retrieved. 

For example:- You previously used this method to get data for Delhi. Now you want to combine this existing dataframe with some new data from London, then you can consolidate both dataframes by passing the old one into this argument as you fetch the new data for London.

**params** : List[str]

An optional argument to specifiy which air quality parameters to get data for. If this is left blank then data for every air quality parameter is retrieved.  
You can choose from the following - pm25, aqi, pm10, o3, co, no2, so2, dew, h, p, t, w, wg

---
## Other methods

### reset_token

Method to change your private API token, if you set an incorrect one at first. 

#### Usage Example

```python
o3 = ooo.Ozone('INCORRECT_TOKEN')   # oh no! now what?

o3.reset_token('YOUR_NEW_TOKEN')   # No worries!
```

***More features coming soon!***
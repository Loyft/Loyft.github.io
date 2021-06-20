---
layout: post
title: Get the current ISS location
excerpt_separator:  <!--more-->
tags:
  - Discord
  - Twitter
  - ISS

---

In this quick guide we will explore how to get the current ISS location.


**Imports**

```python
import json
import urllib.request
from keys import positionstack_api_key
```

**Setting the Endpoints**

Specifying the Endpoints as a constants to access the API
```python
ISS_ENDPOINT = "http://api.open-notify.org/iss-now.json"
POS_ENDPOINT = "http://api.positionstack.com/v1"
```

### Getting the Current Latitude and Longitude of the ISS

To get the current position we need to make an API call to the endpoint.

```python
req = urllib.request.Request(ISS_ENDPOINT)
response = urllib.request.urlopen(req)
```

The response is in a .json format and looks like this:

```json
{
  "timestamp": 1624169097,
  "iss_position": {
    "latitude": "28.2089",
    "longitude": "-7.2213"
  },
  "message": "success"
}
```

Read the .json and set variables for Latitude and Longitude.

```python
obj = json.loads(response.read())
pos_long = obj["iss_position"]["longitude"]
pos_lat = obj["iss_position"]["latitude"]
```

### Calling positionstack to convert lon/lat into a location

To turn the Coordinates into an actual location, we are calling the positionstack api and pass in the current Latitude and Longitude as arguments.

```python
req_pos = urllib.request.Request(f"{POS_ENDPOINT}/reverse?access_key={positionstack_api_key}&query={pos_lat},{pos_long}")
response_pos = urllib.request.urlopen(req_pos)
```

The response comes as .json again and looks something like this:

```json
{
   "data": {
      "results": [
         {
            "latitude": 38.897675,
            "longitude": -77.036547,
            "label": "1600 Pennsylvania Avenue NW, Washington, DC, USA",
            "name": "1600 Pennsylvania Avenue NW",
            "type": "address",
            "number": "1600",
            "street": "Pennsylvania Avenue NW",
            "postal_code": "20500",
            "confidence": 1,
            "region": "District of Columbia",
            "region_code": "DC",
            "administrative_area": null,
            "neighbourhood": "White House Grounds",
            "country": "United States",
            "country_code": "US",
            "map_url": "http://map.positionstack.com/38.897675,-77.036547"
         }
      ]
   }
}
```

Reading the .json and accessing the location

```python
obj_pos = json.loads(response_pos.read())
location = obj_pos['data'][0]['label']
```

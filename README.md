# State-City-Api

Providing a public API for states and cities in Nigeria. Its a Completely free to use web service that fetch all states including cities in Nigeria


----------

About.
-------------

It's just a simple API that returns a list of Nigerian states and cities. In JSON though. It's created for devs who wish to create a basic drop down list of Nigerian locations for any app in any language.

It's built in raw Php .
More about accessing information straight from api is provided below.


URI and Versioning.
-------------

We want to improve this API over time, and because modifications will not always be backward compatible, we will version it. This initial iteration, which is structured as follows, will be available at http://cityng.onlinewebshop.net/v1/


----------


## States

To get a list of all states in Nigeria, call the endpoint at  http://cityng.onlinewebshop.net/v1/state

All states have the following properties:

Field | Description
------|------------
name | The name of the state.
state-code | The state-code.

You can get the states in 2 modes <br>
`~/state/code`-which would fetch the state code for each state.<br>
`~/state/state` - which would fetch only the state.

We have also provided support to fetch both at once using 
`http://cityng.onlinewebshop.net/v1/state` without adding any other additional parameter.


For example, a state: http://cityng.onlinewebshop.net/v1/state

```json
[
	{
		"state": "Abia State",
		"state_code": "AB"
	},
	{
		"state": "Adamawa State",
		"state_code": "AD"
	},
	{
		"state": "Akwa Ibom State",
		"state_code": "AK"
	},
]...
```





## Cities

Cities belong to a state and they are identified by their names.
All cities have the following properties:

Field | Description
------|------------
city | The name of the city.
state | The name of the state the city is in.

For example, Cities in abia:http://cityng.onlinewebshop.net/v1/city/abia

```json
{
	"city": [
		"Aba South",
		"Arochukwu",
		"Bende",
		"Ikwuano",
		"Isiala Ngwa North",
		"Isiala Ngwa South",
		"Isuikwuato",
		"Obi Ngwa",
		"Ohafia"
    /* till infinity*/
	],
	"state": "abia"
}
```


List of endpoints
-------------
##State
This is just a summary of all 3 endpoints you can call for `state`.
- `GET /states` returns a list of all states and state_code in Nigeria.
- `GET /state/state` returns only state. You don't need to pass in anything at the end.
- `GET /state/code` returns the state_code only. You also dont need to pass in any value at the end.

## city

This is just a summary of the endpoints you can call to get `city` for a `state`.
- `GET /city/<state_name>` returns a list of all cities for that particular state in Nigeria.


# Error
Errors occur when the correct parameters are not passed. This errors can be easily fixed. <br> We have done our best to provide details about each error and how to resolve them.

A simple error may occur in this format
---------------------------------------
-`GET`  `http://cityng.onlinewebshop.net/v1/city/` - Here we are trying to get the cities, But not passing any state.
So we get an error in this form

```json
{
	"error": "No parameter provided. you need to provide a state parameter"
}
```

## Status Code 
You can also get the status code from the http header using the provided function for that purpose in your prefered language

eg var_dump(http_response_code()) //for php devs


# Contributing


We welcome any and all contributions, code cleanups and feature requests.

1. Check for open issues or open a fresh issue to start a discussion around a feature idea or a bug.
2. Fork the repository on GitHub to start making your changes to the **master** branch (or branch off of it).
3. Send a pull request and bug the maintainer until it gets merged and published. :).


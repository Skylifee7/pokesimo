---
title: API Reference

language_tabs:
  - shell
  
toc_footers:
- <a href='https://github.com/Skylifee7'>Developed by Skylifee7</a>
  
includes:
  - errors

search: true
---

# Introduction

Welcome to the *Otsimo*'s **Poke-simo API**! :zap: You can use our API to access Pokemon API endpoints, which can get information about various pokemons, types, moves in a huge load of pokemon information database.

Currently our API is only accessible from Shell and therefore we have no language bindings(*for now*)! You can view code examples in the dark area to the right, and try it in your own shell.

This API created from the guys and gals from the [Otsimo](https://otsimo.com) with love!
Feel free to reach out.

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "http://localhost/api/"
  -H "Authorization: lhkJKHlghdGSFS42faewf86"
```

> Make sure to replace `lhkJKHlghdGSFS42faewf86` with your API key. ( currently we don't need it, but we will need :) )

**Pokesimo** uses API keys to allow access to the API. You can register a new Pokesimo API key at our [developer portal](http://otsimo.com/developers).

Pokesimo expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: lhkJKHlghdGSFS42faewf86`

<aside class="notice">
Currently, Pokesimo API does not need Authentication headers for its pre-alpha stage.
</aside>

# Pokemon Types

## Get All Types

```shell
curl "http://localhost/api/list/types"
  -H "Authorization: lhkJKHlghdGSFS42faewf86"
```

> The above command returns JSON structured like this:

```json
{
"name": "Bug",
"effectiveAgainst": [
"Dark",
"Grass",
"Psychic"
],
"weakAgainst": [
"Fairy",
"Fighting",
"Fire",
"Flying",
"Ghost",
"Poison",
"Steel"
]
}
```

This endpoint retrieves all pokemon types(e.g Bug, Electric).

### HTTP Request

`GET http://localhost/api/list/types`

### URL Parameters

Parameter | Description
--------- | -----------
Name | The name of the pokemon to retrieve

## Get Specific Kind of Pokemons

```shell
curl "http://example.com/api/list?type=Electric"
  -H "Authorization: lhkJKHlghdGSFS42faewf86"
```

> The above command returns JSON structured like this:

```json
[{
"Number": "145",
"Name": "Zapdos",
"Type I": [
"Electric"
],,
},
{
"Number": "243",
"Name": "Raikou",
"Type I": [
"Electric"
],,
},
...
..
.
]
```
This endpoint retrieves spesific type of pokemons.

### HTTP Request

Simply send HTTP GET request to our endpoint:

`GET http://example.com/api/list?type=Electric&sortBy=Capture%20Rate`

### Query Parameters

Parameter | Default | Possible Values
--------- | ------- | -----------
sortBy | number | BaseStamina,BaseAttack,FleeRate, etc.
type | N/A | Electric, Bug, etc.

### Some Example Use Cases

`GET http://example.com/api/list?type=Electric&sortBy=Capture%20Rate`

`GET http://example.com/api/list?type=Dragon`

`GET http://example.com/api/list?type=Fire&sortBy=BaseStamina`

<aside class="success">
Remember if you want to sort the response with values with spaces, add "%20" character!
</aside>




---
title: Pokesimo API Reference

language_tabs:
  - shell
  
toc_footers:
- <a href='https://www.linkedin.com/in/gökcan-değirmenci-264674b2/'>Developed by Skylifee7</a>
  
includes:
  - errors

search: true
---

# Introduction

Welcome to the *Otsimo*'s **Poke-simo API**! You can use our API to access Pokemon API endpoints, which can get information about various pokemons, types, moves in a huge load of pokemon information database.

Currently our API is only accessible from Shell and therefore we have no language bindings(*for now*)! You can view code examples in the dark area to the right, and try it in your own shell.

This API created from the guys and gals from the [Otsimo](https://otsimo.com) with love!
Feel free to reach out.

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "https://pokesimo.herokuapp.com/api"
  -H "Authorization: lhkJKHlghdGSFS42faewf86"
```

> Make sure to replace `lhkJKHlghdGSFS42faewf86` with your API key. ( currently we don't need it but we will, soon :) )

**Pokesimo** uses API keys to allow access to the API. You can register a new Pokesimo API key at our [developer portal](http://otsimo.com/developers).

Pokesimo expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: lhkJKHlghdGSFS42faewf86`

<aside class="info">
Currently, Pokesimo API does not need Authentication headers for its pre-alpha stage.
</aside>

# List API

## List All Types

```shell
curl "https://pokesimo.herokuapp.com/api/list/types"
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

`GET https://pokesimo.herokuapp.com/api/list/types`

### URL Parameters

Parameter | Description
--------- | -----------
Name | The name of the pokemon to retrieve

## List Specific Type of Pokemons

```shell
curl "https://pokesimo.herokuapp.com/api/list?type=Electric"
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

`GET https://pokesimo.herokuapp.com/api/list?type=Electric&sortBy=Capture%20Rate`

### Query Parameters

Parameter | Default | Possible Values
--------- | ------- | -----------
sortBy | number | BaseStamina,BaseAttack,FleeRate, etc.
type | N/A | Electric, Bug, etc.

### Some Example Use Cases

`GET https://pokesimo.herokuapp.com/api/list?type=Electric&sortBy=Capture%20Rate`

`GET https://pokesimo.herokuapp.com/api/list?type=Dragon`

`GET https://pokesimo.herokuapp.com/api/list?type=Fire&sortBy=BaseStamina`

<aside class="success">
Remember if you want to sort the response with values which include spaces, add "%20" character!
</aside>

# Get API

## Get Specific Pokemon, Move or Type

```shell
curl "https://pokesimo.herokuapp.com/api/get/pokemon/Pikachu"
-H "Authorization: lhkJKHlghdGSFS42faewf86"
```

> The above command returns JSON structured like this:

```json
[
{
"Number": "025",
"Name": "Pikachu",
"Classification": "DataNotInGameMaster",
"Type I": [
"Electric"
],
...
..
.
```

This endpoint retrieves more detailed info about specific pokemon, move or type.

### HTTP Request

**Entry point**

`GET https://pokesimo.herokuapp.com/api/get/`{one-of-the-three-options}/{name}

### URL Parameters

Parameter | Description
--------------------- | --------------------------------- |
Name |  The name of the (pokemon-move-type) to retrieve

### Some Example Use Cases

`GET https://pokesimo.herokuapp.com/api/get/pokemon/Mewtwo`

`GET https://pokesimo.herokuapp.com/api/get/move/Heat%20Wave`

`GET https://pokesimo.herokuapp.com/api/get/type/Fire`

<aside class="success">
You have 3 options to add after the /get. Those are /pokemon , /move or /type.
</aside>




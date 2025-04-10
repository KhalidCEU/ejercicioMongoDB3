# Ejercicio MongoDB 3

**1)** En `sample_airbnb.listingsAndReviews`, ¿qué "**room types**" existen?

> use sample_airbnb

```
db.listingsAndReviews.aggregate([ { $group: { _id: "$room_type" } }] )
```

**2)** En `sample_training.companies`, haga una query que devuelva el **nombre** y el **año** en el que se **fundaron** las **5** compañías **más antiguas**

> use sample_airbnb

```
db.companies.find({founded_year: {$ne: null}}, {name: 1, founded_year: 1, _id: 0}).sort({"founded_year": 1}).limit(5)
```
(**query**: not equal a null | **projection**: solo dejamos `name` y `founded_year` + excluímos `_id` del resultado) + orden **ascendente** (**1**) + cogemos los **5 primeros** resultados (limit)

**3)** En `sample_training.trips`, ¿en qué año nació el **ciclista más
joven**?

```
db.trips.find({ "birth year": {$ne: ""} }, {"birth year": 1, _id: 0}).sort({"birth year": -1}).limit(1)
```
(**query**: not equal a vacío | **projection**: solo dejamos `birth year` + excluímos `_id` del resultado) + orden **descendente** (**-1**)
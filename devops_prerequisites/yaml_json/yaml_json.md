## Yaml

yaml filr is used to store data
the data is stored in key :vale pairs seperated by :

e.g.
Fruit: Apple
Vegetable: carrot
Liquid: water
Meat: chicken

array/ lists

fruits:
 - oranges
 - apple
 - banana

vegetables:
 - carrot
 - cauliflower
 - tomatoes

Dictionary / map

- set of properties grouped together under one iteam are known as dictionary
e.g
banana:
  calories: 105
  fat: 0.4g
  carbs: 24g

we can have keyvalue/ Dictionary/ lists combined
e.g
fruits:
  - banana:
      calories:105
      fat: 0.4g
      carbs: 27g

Dictionary vs list vs list of dictionaries

- to store different info of properties of a single object we use dictionary
e.g
dictionary
color: Blue
model: corvette
transmisssion: manual
price: $20000

dictionary inside dictionary

color: blue
model:
  name :corvette
  year: 1995
transmission: Manual
price: $20000

to store multiple iteams of same type of object we use list e.g list of cars

- blue corvette
- red corvette
- green corvette
- black corvette

if we want to store ifo of all the cars we use list of dictionaries

e.g
- color: blue
  model:
    name: corvette
    model: 1995
- color : red
  model:
    name: corvette
    model: 1995

dictionaries are unorderd collections
lists are order collections
e.g
dictionary/map

banana:
  calories: 105
  fat: 0.4g
  carbs: 27g

banana:
  calories: 105
  carbs: 27g
  fat: 0.4g

these both directories are same even if the order is not same but till the properties and values match its the same directory.

arrys/lists - orderd collcetion

fruits:
- orange
- apple
- banana

fruits:
- orange
- banana
- apple

these lists are different they are not same as order is important in list

#any line staerting with a # is a comment

## json

yaml and json both stores data, yaml uses indentation while json uses {} curly brackets.

e.g
json
{
 "car":{
    "color":"blue",
    "price": $ 20,000
  }
}

ymal

car:
  color:blue
  price:$20000

in json list/arrys are inside [] square brackets and seperated by , '
while in ymal it is initiated as "-".

we can convert
Json to yaml and ymal to json easily as may converters are available

json path - it is a query language to query data stored in json file.

querys e.g

car
car.color

the top level dictionery or a list of a json file when no dictionary name or list name is mentioned it is the by default the (root element) for this we use $
so we write the query as 
$.car
$.vehical.car

all the results of jason path query is available as on arry in [] square brackets

[
"car"
"bus"
"truck"
"bike"
]

so this an arry as it starts with [ and end with ]  so to get data we use query i.e $[0]

we have to acess arry using number in square [] brackets the arry starts with 0 so for above example arry it is

car =0, bus =1, truck =2, bike =3.

-> criteria 

criteria it is defines indside a () brackets

we will not abe able to always search using numbers in a large data so we use criteria 
e.g

to get all numbers greater than 40
$[check if each iteam > 40]

we can replace check if  with ?()

$ [?(each iteam > 40)]

we will replace each iteam  with @
so the final query is
$[?(@>40)]

we can use similar operators

@ == 40  - returns number equal to 40
@!= 40  - returns number not equal to 40
@ in [40,43,45] - returns number that are 40,43,45
@ nin [40,43,45] - returns number that are not 40,43,45



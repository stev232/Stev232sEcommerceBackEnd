# Stev232sEcommerceBackEnd

## Description

This project demonstrates using sequelize to retreive, update, create, and even delete data by id. If there is a failure to connect to the mysql database then you will get an error 500 code. If the id does not exist then you will get either a 400 or 404 error code. Otherwise if the request is a success then you will get a 200 success code.

## Acceptance Criteria

GIVEN a functional Express.js API <br>
*WHEN* I add my database name, MySQL username, and MySQL password to an environment variable file <br>
__THEN__ I am able to connect to a database using Sequelize <br>
*WHEN* I enter schema and seed commands <br>
__THEN__ a development database is created and is seeded with test data <br>
*WHEN* I enter the command to invoke the application <br>
__THEN__ my server is started and the Sequelize models are synced to the MySQL database <br>
*WHEN* I open API GET routes in Insomnia Core for categories, products, or tags <br>
__THEN__ the data for each of these routes is displayed in a formatted JSON <br>
*WHEN* I test API POST, PUT, and DELETE routes in Insomnia Core <br>
__THEN__ I am able to successfully create, update, and delete data in my database <br>

## Database Modules

* Category
    * id
        * Integer
        * Doesn't allow null values
        * Set as primary key
        * Uses auto increment
    * category_name
        * String
        * Doesn't allow null values
* Product
    * id
        * Integer
        * Doesn't allow null values
        * Set as primary key
        * Uses auto increment
    * product_name
        * String
        * Doesn't allow null values
    * price
        * Decimal
        * Doesn't allow null values
        * Validates that the value is a decimal
    * stock
        * Integer
        * Doesn't allow null values
        * Set a default value of 10
        * Validates that the value is numeric
    * category_id
        * Integer
        * References the category model's id
* Tag
    * id
        * Integer
        * Doesn't allow null values
        * Set as primary key
        * Uses auto increment
    * tag_name
        * String
* ProductTag
    * id
        * Integer
        * Doesn't allow null values
        * Set as primary key
        * Uses auto increment
    * product_id
        * Integer
        * References the product model's id
    * tag_id
        * Integer
        * References the tag model's id

## Associations

__Product__ belongs to __Category__, as a __category__ can have multiple __products__ but a __product__ can only belong to one __category__.

__Category__ has many __Product__ models.

__Product__ belongs to many __Tag__ models. Using the *__ProductTag__* through model, allow __products__ to have multiple __tags__ and __tags__ to have many __products__.

__Tag__ belongs to many __Product__ models.
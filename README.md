# MongoDB Product Queries
This repository contains a set of MongoDB queries to interact with a product database. The database is populated using a JSON file containing various products with attributes such as product name, price, material, and color.

Setup
Clone the Repository
git clone https://github.com/suganyarajes/MongoDb-Query-Day35.git

#Import the Product JSON

Ensure MongoDB is installed and running on your machine. Import the products.json into your MongoDB instance using the following command:
mongoimport --db freshtohome --collection products --file products.json --jsonArray

#MongoDB Queries
Here are the MongoDB queries to perform various tasks on the products collection:

1.Find all the information about each product:
db.products.find({})

2.Find the product price which is between 400 to 800:
db.products.find({ "product_price": { "$gte": 400, "$lte": 800 } })

3.Find the product price which is not between 400 to 600:
db.products.find({ "$or": [{ "product_price": { "$lt": 400 } }, { "product_price": { "$gt": 600 } }] })

4.List the four products which are greater than 500 in price:
db.products.find({ "product_price": { "$gt": 500 } }).limit(4)

5.Find the product name and product material of each product:
db.products.find({}, { "product_name": 1, "product_material": 1, "_id": 0 })

6.Find the product with a row id of 10:
db.products.find({ "id": "10" })

7.Find only the product name and product material:
db.products.find({}, { "product_name": 1, "product_material": 1, "_id": 0 })

8.Find all products which contain the value "soft" in product material:
db.products.find({ "product_material": { "$regex": /soft/i } })

9.Find products which contain product color "indigo" and product price 492.00:
db.products.find({ "product_color": "indigo", "product_price": 492.00 })

10.Delete the products which product price value is 28:
db.products.deleteMany({ "product_price": 28 })

Notes
Ensure you replace the collection and database names if they differ in your setup.
The field names used in the queries (e.g., product_price, product_name, product_material) should match the field names in your imported JSON data.
The id field in query 6 is assumed to be a string. If it's stored as a different type, adjust the query accordingly.
Contributing
Feel free to submit issues or pull requests if you have suggestions for improvements or additional queries.

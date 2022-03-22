# Installation & Loading data:

1. Clone the repository
2. Move to the folder named "app"
3. `npm install`
4. Move back to the root folder of the project

Load Mongo data:

1. Start by running mongodb locally
2. Create new database called `restaurant-reviews`
3. create 2 new collections called `restaurantDB` and `Rating`
4. import [restaurantDB](./db/restaurant.json) to the `restaurantDB` collection
5. import [Rating](./db/rating.json) to the `Rating` collection

Load Redis data:

1. Start redis-server locally
2. Move to folder `app` to install the dependencies using `npm install`
3. run the file [convertData](./app/MongoToRedisData) `node MongoToRedisData/convertData.js`

Start application:

1. `npm start`
2. goto http://localhost:2000/ to view the project


# Phase 3 : Select or Create a Sample Database:

- [Rating database dump](./db/rating.json)
- [Restaurant database dump](./db/restaurant.json)

# Phase 3: Create NoSQL Data using model Data

[convertData](./app/MongoToRedisData)

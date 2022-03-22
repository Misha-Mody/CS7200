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

- [restaurantDB](./db/restaurant.json)
- [Rating](./db/rating.json)


# Phase 3: Model the Database


## 1. HASHES - to Store the Restaurant and their attributes like services, facilities, working days and hours.

KEY: restaurant:restID EG:- restaurant:153 VALUE: {
name: 'tacos los volcanes',
address: 'Francisco I. Madero 145 Centro',
city: 'san luis potosi',
country: 'Mexico',
restID: '56',
state: 'san luis potos',
zip: '78290',
facilities_ambience: 'solitary', facilities_parkingSpace: 'true', facilities_seatingArea: 'open',
services_alcohol: 'false',
services_smoking: 'true',
workingDays: 'Monday',
payments: 'cash',
cuisine: 'Mexican,Chinese,American,Indonesian', priceRangeMin: '17',
priceRangeMax: '73',
openHours: '1:40 AM',
closeHours: '10:27 PM',
dresscode: 'informal'
}

## 2. LISTS - Store all the restaurant ids
EG:- restids [ ‘1,’ ‘2’, ‘3’ ....... ]
Lists are used instead of sets or sorted sets so functions like LRANGE can be performed as SETS output random values

## 3. SETS = Store all the different kind of cuisines
KEY: cuisines
VALUE: ‘American’, ‘Indian’, ‘Chinese’, ‘Mexican’, ‘Cuban ‘....... etc.
1.3.2 Store restids of all restaurants of a particular type of cuisine so we can query the restaurant by cuisine.
KEY: cuisine:cuisineName EG:- cuisine:American VALUE: ‘445’


## 4. Sorted Sets - Keep track of the number of reviews a particular restaurant gets and create a leaderboard with restaurants with most reviews.
KEY: reviewCount
EG: { score : ‘2’ , restID : ‘124’ }
1.4.2 Keep a track of the number of reviews given by customers and create a leaderboard for customers that have given the most reviews.
EG: customerRatingCount


# Phase 3: Create NoSQL Data using model Data

[convertData](./app/MongoToRedisData)


# Finders Keeper
Finders Keeper is an app to help people search for adoptable pets near them. The goal of this app is to help people find their forever soulpet(s). 

## User Story
As a user, I want to be able to search for adoptable pet tailored to user's needs so that I can help the animals in need of a forever home. 

* Adopt an animal searching through Zip Code
* Add an animal to the user's favroite
* Remove an animal from the user's favroite
* Click on the specific animal to view their details 

## Tech Stack Used
* Axios 
* Express 
* Ejs
* Ejs-layouts
* Sequelize 
* Method-override

## Wireframes and ERD
![Finders Keeper Wireframe and ERD](Wireframe_ERD_Project2.png)

## API
https://www.petfinder.com/developers/v2/docs/

## Installation Guide
Get Started
```js
git clone https://github.com/s9001848/Finders-Keeper
```
```js
cd supreme-engine
```
```js
npm install
```
```js
touch .env
```
Add Inside .env File
```js
SECRET_SESSION=finderskeeper
```
```js
APIKEY=TKnPguUdqsf1ivo3i8CxlJeHChxt5O88OadhOMDw2ZjrBVbJZE
```
```js
APISECRET=kMcPJHlouZIvSUmyy7cDxBxOMJxnU2qozHib8BKd
```
Create a Database
```js
npm install sequelize-cl
```
```js
npx sequelize-cli db:create finders-keeper
```
Migrate the Database
```js
npx sequelize-cli db:migrate
```
Seed the Database
```js
npx sequelize-cli db:seed:all
```
Start the Server
```js
npm start
```

## Accessing API
* To access PetFinder API, I must receive the APIKEY AND APISECRET first, then use 
```js
  const params = new URLSearchParams();
  params.append('grant_type', 'client_credentials');
  params.append('client_id', petFinderKey);
  params.append('client_secret', petFinderSecret);
  axios.post(`https://api.petfinder.com/v2/oauth2/token`, params)
    .then(accessToken => {
      const header = "Bearer " + accessToken.data.access_token;
      const options = {
        method: 'GET',
        headers: { 'Authorization': header },
        url: "https://api.petfinder.com/v2/animals?type=dog&page=2"
      }
      axios(options)
        .then((response) => {
          let animals = response.data.animals
          res.render('index', { animals: animals })
        })
        .catch(error => {
          console.log(error)
        })
    })
    .catch(error => {
      console.log(error)
    })
```

## Challenges

* CSS displaying how I would like my website to look like
* Clicking on the animals that do not have pictures
* Organizing my controller files
* Finding a specific Bootstrap that fit my aesthetic

## Homepage Interface
![Finders Keeper Homepage Interface](FK2.png)


## Deployed Here
https://finders-keeper.herokuapp.com/



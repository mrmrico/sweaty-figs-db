# An API built with Nodal and Postgres

This repo is intended for use as an API to power [Good Times](https://github.com/sweaty-figs).

1. [GettingStarted](#gettingstarted)
2. [Requirements](#requirements)
3. [Endpoints] (#endpoints)
4. [Schemas] (#schemas)

## GettingStarted
- [ ] Install [Nodal](https://github.com/keithwhor/nodal) globally

- [ ] Install dependencies

- [ ] Start server

```sh
npm install -g nodal
npm install
nodal s
```
Your app should now be running on [localhost:8080](http://localhost:8080/).

## Requirements
- Nodal 0.1.0
- Postgres 9.5.2.0

## Endpoints

###/v1/users

**GET**     get all users (use query params to match attributes)

**POST**    create user

**PUT**     update user

**DELETE**  delete user

###/v1/users/{id}

**GET**     get user by id

###/v1/activities

**GET**     get all activities (use query params to match attributes)


**POST**   create activity


**PUT**     update activity


**DELETE**  delete  activity

###/v1/activities/{id}


**GET**     get activity by id

###/v1/plans

**GET**     get all plans (use query params to match attributes)

**POST**    create plan

**PUT**     update plan

**DELETE**  delete plan

###/v1/plans/{id}

**GET**     get plan by id

###/v1/comments

**GET**     get all comments (use query params to match attributes)

**POST**    create comment

**PUT**     update comment

**DELETE**  delete comment

###/v1/comments/{id}

**GET**     get comment by id

###/v1/access_tokens

**POST**    generate access_token for user on login for authentication

**DELETE**  delete access_token

## Schemas
> All models come with *created_at* and *updated_at* fields and are generated by with each model without manual specification

###user

id            --> int (created by db)

email         --> string

username      --> string

password      --> string


###activity

id            --> int (created by db)

plan_id       --> int (foreign key, one to many)

user_id       --> int (foreign key, one to many)

user_gen      --> boolean (activity user created, ie, not from external API)

private       --> boolean (user share preference)

desc          --> string (description of activity)

lat           --> string (latitude)

long          --> string (longitude)

address       --> string (activity address)

city          --> string

state         --> string

neighborhood  --> json (array of neighborhoods proximal to activity)

title         --> string

duration      --> int (expected length of time in minutes)

costPerPerson --> int (expected cost per person of activity)

isYelp        --> boolean (activity generated from yelp API call)

categories    --> json (array of categories activity falls under)


###plan

id            --> int (created by db)

user_id       --> int (foreign key, one to many)

title         --> string (plan title)

private       --> boolean (user share preference)

desc          --> string (description of activity)

likes         --> int (number of likes)

activities    --> json (array of activities associated with plan)


###comment

id            --> int (created by db)

plan_id       --> int (foreign key, one to many)

activity_id   --> int (foreign key, one to many)

content       --> string (message)


###access_token

id            --> int (created by db)

user_id       --> int (foreign key, one to many)

token_type    --> string (specify token type, ie. bearer)

expires_at    --> datetime

ip_address    --> string

username      --> string







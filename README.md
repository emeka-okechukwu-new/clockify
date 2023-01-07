<a name="readme-top"></a>

# Task Two: Stocks

<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#introduction">Introduction</a></li>
        <li><a href="#features">Features</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li>
      <a href="#endpoints">API Enpoints</a>
      <ul>
        <li><a href="#users">Users</a></li>
        <li><a href="#actions">Actions</a></li>
      </ul>
    </li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>

## About The Project

### Introduction

This is a simple RestAPI built with Node.js, Express, and MongoDB. It exposes endpoints for users to add to and view their balance. It also allows users to register and log in.

### Features

- [x] User registration using unique username and a password
- [x] User login (including session maintenance using JWT)
- [x] Only logged-in users can perform CRUD functionality
- [x] Users can log out
- [x] View balance
- [x] Add to balance
- [ ] Unit tests with Jest for the functionality (functionality tested with cURL)

<p align="right">(<a href="#readme-top">back to top</a>)</p>


## Getting Started

### Prerequisites

- Node.js
- MongoDB
- Postman

### Installation

1. Clone the repository

```sh
git clone https://github.com/emeka-okechukwu-dev/speer-technologies-assessmemt/task-two.git
```

2. Install the dependencies

```sh
npm install bcryptjs body-parser dotenv express jsonwebtoken mongoose
```

3. Create `.env` file in root folder with the following details

```js
API_PORT = ENTER_YOUR_PORT_NUMBER

JWT_TOKEN = ENTER_YOUR_JWT_TOKEN

MONGODB_URL = ENTER_YOUR_MONGODB_TOKEN
```

4. Start the server

```js
npm start
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>


## Endpoints

The base URL for the API is localhost:{YOUR PORT NUMBER}/

cURL in terminal is recommended for testing these endpoints but Postman can be used too

### Users

#### Register User

POST `/users/register`: API route to register a new user with a specified username and password. The password is first encrypted using the bcrypt library before being stored in the database.

The parameters include:

- `username` (required)
- `password` (required)

Use cURL to send a request to a registration endpoint with a username and password, you can use the following command:

```sh
curl -X POST \
  http://localhost:PORT_NUMBER/users/register \
  -H 'Content-Type: application/json' \
  -d '{
  "username": "USERNAME",
  "password": "PASSWORD"
}'
```
<br/>

#### Login User

`POST /users/login`: API route to log in a user with a specified username and password. If the login is successful, a JSON web token is generated and returned to the client.

The parameters include:

- `username` (required)
- `password` (required)

Use cURL to send a request to a login endpoint with a username and password with the following command:

```sh
curl -X POST \
  http://localhost:PORT_NUMBER/users/login \
  -H 'Content-Type: application/json' \
  -d '{
  "username": "USERNAME",
  "password": "PASSWORD"
}'
```

⚠️ Copy the token generated when you log in successfully and replace with `YOUR_JWT_TOKEN` below.

#### Logout User

`POST /users/logout`: Logs out the authenticated user and invalidates the current JWT.

Use cURL to send a request to log out a user with the following command:

```sh
curl -X POST \
  http://localhost:PORT_NUMBER/users/logout \
  -H 'Authorization: Bearer YOUR_JWT_TOKEN'
```


<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Actions

#### Add Balance

`POST /balance`: Adds a specified amount to the user's balance.

The parameters include:

- `amount` (required): must be a number

Use cURL to send a request to add a balance with the following command:

```sh
curl -X POST \
  http://localhost:PORT_NUMBER/balance \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer YOUR_JWT_TOKEN' \
  -d '{
  "amount": 50
}'
```
<br/>

#### Get Balance

`GET /balance`: Gets the current balance for the authenticated user.

Use cURL to send a request to get the balance with the following command:

```sh
curl -X GET \
  http://localhost:PORT_NUMBER/balance \
  -H 'Authorization: Bearer YOUR_JWT_TOKEN'
```
<br/>

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Contact

Emeka Okechukwu - chuks.egkdev@gmail.com

<p align="right">(<a href="#readme-top">back to top</a>)</p>

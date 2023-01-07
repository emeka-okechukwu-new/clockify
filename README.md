<a name="readme-top"></a>

# Task One: Twitter

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

This is a simple RestAPI built with Node.js, Express, and MongoDB. It exposes endpoints for users to create, read, update, and delete tweet. It also allows users to register and login.

### Features

- [x] User registration using unique username and a password
- [x] User login (including session maintenance using JWT)
- [x] Only logged-in users can perform CRUD functionality
- [x] Create tweet
- [x] Read tweet
- [x] Update tweet
- [x] Delete tweet
- [ ] Unit tests with Jest for the functionality (functionality tested with cURL)

<p align="right">(<a href="#readme-top">back to top</a>)</p>


## Getting Started

### Prerequisites

- Node.js
- MongoDB
- Postman

### Installation

1. Clone the repo inside XAMPP htdocs folder. Make sure the project folder name is `task-one`

```sh
git clone https://github.com/emeka-okechukwu-dev/task-one.git
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

cURL on terminal is recommended for testing these endpoints but Postman can be used too

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

POST `/users/login`: API route to log in a user with a specified username and password. If the login is successful, a JSON web token is generated and returned to the client.

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

⚠️ Copy the token generated when you login successfully and replace with `YOUR_JWT_TOKEN` below.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Actions

#### Create a Tweet

POST `/tweets`: Creates a new tweet with the specified content, and the authenticated user's ID.

The parameters include:

- `content` (required)

Use cURL to send a request to create a tweet with only the content field and an authorization header with the following command:

```sh
curl -X POST \
  http://localhost:PORT_NUMBER/tweets \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer YOUR_JWT_TOKEN' \
  -d '{
  "content": "This is my first tweet"
}'
```
<br/>

#### Read a Tweet

GET `/tweets`: Returns all tweets for the authenticated user.

Use cURL to send a request to get all tweets with the following command:
```sh
curl -X GET \
  http://localhost:PORT_NUMBER/tweets \
  -H 'Authorization: Bearer YOUR_JWT_TOKEN'
```
<br/>

#### Update a Tweet

PATCH `/tweets/:id`: Updates the tweet with the specified ID with the new content.

The parameters include:

- `id` (required)

Use cURL to send a request to update a tweet with the following command:

```sh
curl -X PATCH \
  http://localhost:PORT_NUMBER/tweets/TWEET_ID \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer YOUR_JWT_TOKEN' \
  -d '{
  "content": "Updated Content"
}'
```
<br/>

#### Delete a Tweet

DELETE `/tweets/:id`: Deletes the tweet with the specified ID.

The parameters include:

- `id` (required)

Use cURL to send a request to delete a tweet with the following command:

```sh
curl -X DELETE \
  http://localhost:PORT_NUMBER/tweets/TWEET_ID \
  -H 'Authorization: Bearer YOUR_JWT_TOKEN'
```
<br/>

## Contact

Emeka Okechukwu - chuks.egkdev@gmail.com

<p align="right">(<a href="#readme-top">back to top</a>)</p>

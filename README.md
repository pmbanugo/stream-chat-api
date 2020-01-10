# Open-Source API in Node.js for Stream Chat 💬

## Overview

This API will quickly get you up to speed on best practices for deploying an auth API for [Stream Chat](https://getstream.io/chat/). The API can be deployed Heroku with a single click or to any other hosting environment that supports Node.js.

> Note: This API does not contain auth, therefore it is not escure _at this time_. I'll be adding an auth layer shortly but until then, you can easily add your own with a JWT token.

## Quick Instructions (localhost)

1. Create an free chat trial with [Stream](https://getstream.io/chat/)
2. Clone repo with `git clone git@github.com:nparsons08/stream-chat-api.git`
3. Run yarn to install dependencies `cd stream-chat-api && yarn`
4. Create a `.env` file and reference the `.env.example` file
5. Start the API with `yarn dev` for development mode or `yarn start` for production mode
6. Use [Postman](https://www.getpostman.com/) to hit the API with a `POST` on port `8080` (e.g. `http://localhost:8080/v1/auth/init`) using a variation of the following JSON payload:

```json
{
	"name": {
		"first": "First Name",
		"last": "Last Name"
	},
	"email": "foo@bar.baz",
	"password": "qux"
}
```

If you deployed to Zeit Now, the path will be `https://your-domarin/api/auth

## Technology Used

The following technologies were used to build this API:

-   [Node.js](https://nodejs.org)
-   [Express](https://expressjs.com/)
-   [MongoDB Atlas](https://atlas.mongodb.com)
-   [Mongoose](https://mongoosejs.com/)
-   [Stream Chat](https://getstream.io/chat/)
-   [Stream Chat JS Library](https://www.npmjs.com/package/stream-chat)

## Support

-   User storage via MongoDB database
-   Mongoose schema with validation for user profiles
-   Password validation and hashing with bcrypt
-   Find or create for users within the MongoDB database
-   Easy deployment to [Heroku](https://heroku.com) (optional) or any other environment
-   Token generation for existing and new users (for Stream Chat)
-   Creation of a new channel named `General` if one does not exist
-   Automatic adding of users to the `General` channel
-   Heavily commented modern JavaScript

Please see below for installation requirements.

## Requirements

-   Node.js (latest)
-   Yarn (latest)

## Deployment

This section covers the various requirements for deploying this API in different environments. When in doubt, have a look at the `.env.example` file which outlines what required variables you will need to supply in order for the API to run properly.

### Heroku

The easiest method to deploy this API to Heroku is to click the deploy button below:

<p>
  <a href="https://heroku.com/deploy?template=https://github.com/nparsons08/stream-chat-api" target="_blank">
    <img src="https://www.herokucdn.com/deploy/button.svg" alt="Deploy">
  </a>
</p>

> Note: You will need to spin up a MongoDB cluster and add your MongoDB URI to your environment variables under the `Settings` section of your applications dashboard on Heroku. Ensure that the environment variable is named `MONGODB_URI`. For local installations, you will need to add your MongoDB URI to the `.env` file in the root of this project.

![Heroku Settings](https://i.imgur.com/YtjurK9.png)

### Zeit Now

See this [tutorial](#)

## Docker

> Note: A Dockerfile is also available with associated scripts located in the `scripts` directory. Use this if you would like to deply to AWS/GCP/Kubernetes.

### Required Environment Variables

> Note: Be sure to add your environment variables as shown below and in the `.env.example` file or your build will fail.

```
NODE_ENV=development
PORT=8080

STREAM_API_KEY=YOUR_STREAM_API_KEY
STREAM_API_SECRET=YOUR_STREAM_API_SECRET

MONGODB_URI=YOUR_MONGODB_URI
```

## Anatomy

```
├── controllers
│   └── v1
│       └── auth
│           ├── index.js
│           └── init.action.js
├── index.js
├── models
│   └── user.js
├── routes
│   └── init.js
└── utils
    ├── controllers.js
    └── db
        └── index.js
```

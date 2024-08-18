# Working with Express, Passport, Typescript

### Create your project directory and Initialize
Start your project by running
```bash
npm init -y
```

**Install express, dotenv and nodemon**

- Express for the server developement 
- dotenv can read the .env file
-  nodemon for development
```bash
npm i express dotenv
npm i -D nodemon
```

**Write the script for running the application**

```json
"start:dev": "nodemon ./src/index.js",
"start":"node .src/index.js"
```


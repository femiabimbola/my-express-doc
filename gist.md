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

Create a src folder, .env file and put the index.js in the src folder <br/>

Create a desired port number in the `.env` file

```.env
PORT=8000
```
Paste the following code in the  `src/index.js`
```index.js
const express = require('express');
const dotenv = require('dotenv');

dotenv.config();

const app = express();
const port = process.env.PORT;

app.get('/', (req, res) => {
  res.send('Express with TypeScript Server');
});

app.listen(port, () => {
  console.log(`[server]: Server is running at http://localhost:${port}`);
});

```
**Installing Typescript**

- Typescript for the project
-  @types/express for using types with express
-  @types/node types for nodes

They are all development dependencies

```bash
npm i -D typescript @types/express @types/node
```

**Generate the tsconfig.json file**
Running the following code in `bash`
```bash
npx tsc --init
```

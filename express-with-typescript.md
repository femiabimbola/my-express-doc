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
"dev": "nodemon ./src/index.js",
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

Run the following code in `bash`
```bash
npx tsc --init
```
Check the `tsconfig.json` generated search for `outdir` and enable. It should lead like this

```tsconfig.json
  "outDir": "./dist",  
```
The compiled typescript will be output there

**Install the ts-node and change the code to ts**

Install ts-node. Node cannot run typescript code on it own. It needs ts-node

```bash
npm install ts-node
```
Change the `index.js` to `index.ts` and paste the following code

```index.ts
import express, { Express, Request, Response } from "express";
import dotenv from "dotenv";

dotenv.config();

const app: Express = express();
const port = process.env.PORT || 3000;

app.get("/", (req: Request, res: Response) => {
  res.status(200).send("Express with TypeScript Server");
});

app.listen(port, () => {
  console.log(`[server]: Server is running at http://localhost:${port}`);
});
```
Then rewrite the the scripts to run your application

```json
"dev": "nodemon  src/index.ts",
"build": "npx tsc",
"start":"node dist/index.js"
```
- `dev: nodemon src/index.ts` is to run the code
- `build: npx tsc` to generate the compiled code
- `start:node dist/index.js` to run the complied code

And it is wrap

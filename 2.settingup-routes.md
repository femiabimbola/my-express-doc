# Setting up the routes

At the index file for the application. Write this

```index.ts
import router from "./routes"; //accessing the routes folder

app.use(router)
```

### Create the routes folder
Create `route` folder in the `src` folder <br/>
Then create the `index.ts` in the route folder. Paste the code below

```index.ts
import {Router} from "express";
import userRouter from "./users";

const router = Router();
router.use(userRouter);
export default router;
```
You may now create different file for different routes. For example in our case we created a `user.ts` for all routes pertaining to users

```user.ts
import {Router} from "express";
import { getUsersById } from "../controller/users";

const router = Router();
router.get('/api/users/:id', getUsersById)
export default router;
```

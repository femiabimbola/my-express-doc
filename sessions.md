# Working with Sessions
Session tracks and identify the user. Since HTTP is stateless. It uses cookies 

  Get started by running
  ```bash
  npm i express-session
  ```
Then in the layout file. You start by

```app.tsx
import session from 'express-session'

app.use(session())
```
The session function needs to be called with some parameter

```app.ts
const sessionObject = {
  secret: "some tough secret", // to sign the cookies
  saveUninitialized: false, // Not saving unmodified session storage. No need to save random user
  resave: false,  //if session data is not modified, why store?
  cookies: { maxAge: 6000 * 60,     }
}
```

To get the session when a user is interacting with your app.
```general.tsx
console.log(request.session)
console.log(request.session.id)
```
# Working with Sessions
Session tracks and identify the user. Since HTTP is stateless. It uses cookies 

  Get started by running
  ```bash
  npm i express-session
  ```
Then in the layout file. You start by

```app.tsx
import session from 'express-session'

app.use(session(sessionObject))
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

To get the session when a user is interacting with your app. It is regenerated everytime you `GET` post.
```general.tsx
console.log(request.session) 
console.log(request.session.id)
```
 But you have modify it now to not regenerate. You attached a property to the it to modified it. it prevent it from being regenerated.

 ```index.ts
 request.session.visited = true
 ```

Attaching a user to a session id after gotten from the database. You have modified it, so it won't be regenerate everytime
```index.ts
// find user is gotten from the datatbase during sign in and it attached to the session
request.session.user = findUser
```
For example the status route can findout 

```index.ts
app.get("/api/auth/status", (req, res) => {
  req.sessionStore.get(req.sessionID, (err, session) => {
    console.log(session)
  })
  return req.session.user ? res.status(200).send(req.session.user) : res.status(401).send({msg: 'not auth"})
})
```

A snippet of code in cart and users
```index.ts
app.post("api/cart", (req,res) => {
  if(!req.session.user) return response.status(401).send({msg: "not auth"})
  const {body: item} = req;
  const {cart} = req.session
  if(cart) {
    cart.push(item)
  } else {
    req.session.cart = [item]
  }
  console.log(req.session)
  return res.status(201).send(item)
})
```
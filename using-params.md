## Using the Params & Query in the request
The Mock user database
```
interface User {
  id: number;
  name: string;
  display: string;
  password?: string;
}

export const mockUsers: User[] = [
  {id: 1, name: "Tush", display: "tushy1", password: "tushyy1"},
  {id: 2, name: "Josh", display: "Josshy", password: "joshy3"},
  {id: 3, name: "Michael", display: "Mich43", password: "mich"},
];
```

### Getting user by Id using params

```
router.get("/api/users/:id", getUsersById)
```
The get user by ID function

```users.ts
export const getUsersById = (req: Request, res: Response) => {
  const parseId = parseInt(req.params.id);

  if (isNaN(parseId)) return res.status(400).send({msg: "Invalid Params"});

  const user = mockUsers.find((user) => user.id === parseId);

  if (!user) return res.status(404).send({msg: "No user found"});

  return res.status(200).send({msg: user});
};
```

### Using the query string

```
http://localhost:3000/products/key=value&key2=value2
```
The key is like a variable while the value is kind of attached to it<br/>
It is use to filter the data you get from a source<br/>
`request.query` is used to filter the data

```
app.get('/api/users', getUsersByFilter)
```
36.54
```
export const getUsersByFilter = (req: Request, res: Response) => {
  const {filter, value} = req.query

  if (isNaN(parseId)) return res.status(400).send({msg: "Invalid Params"});

  const user = mockUsers.find((user) => user.id === parseId);

  if (!user) return res.status(404).send({msg: "No user found"});

  return res.status(200).send({msg: user});
};
```

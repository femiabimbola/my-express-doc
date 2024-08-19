## Using the Params in the request

Getting user by Id
```
router.get("/api/users/:id", getUsersById)
```
The get user function

```users.ts
export const getUsersById = (req: Request, res: Response) => {
  const parseId = parseInt(req.params.id);

  if (isNaN(parseId)) return res.status(400).send({msg: "Invalid Params"});

  const user = mockUsers.find((user) => user.id === parseId);

  if (!user) return res.status(404).send({msg: "No user found"});

  return res.status(200).send({msg: user});
};
```
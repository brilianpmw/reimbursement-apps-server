# reimbursement-apps-server


###### BASIC AUTH
for security reason please use header : 

```
headers :{ 
  authorization : token
}
```

response when unauthorize

- without authorization headers

```
{
    "success": false,
    "status": 400,
    "message": "You need login before acces this page"
}
```
- when token invalid or outdated

```
{
    "success": false,
    "status": 400,
    "message": "please login first",
    "err": "invalid token"
}
```

###### login user
request : 

```

body : {
  username:adinda,
  password : xxxxxxx
}
```
response success :

```
{
    "success": true,
    "status": 200,
    "message": "briliantpmw Login successfully ",
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI2MDUwNThkMzFlZWU0N2ZhNDcwYWU4ZWEiLCJ1c2VybmFtZSI6ImJyaWxpYW50cG13Iiwicm9sZV9pZCI6IjYwNTA1N2ZlODVmZTJjZjg3NmY5MmNhZiIsImlhdCI6MTYxNTg4MzI2MSwiZXhwIjoxNjE1OTY5NjYxfQ.kPIHJYkRkEKdyf2yenTXHQRmTIIGzUoqHBRMG0vuboY"
}
```

response username not found : 

```
{
    "success": false,
    "status": 400,
    "message": "username not found"
}
```

response when wrong password : 
```
{
    "success": false,
    "status": "400",
    "message": "wrong password"
}
```

###### Add new user

request : 
```

body : {
  username:'brilian',
  password : '123',
  departement_id : 605057a2e9cda1f66fe21b03,
  role_id : 605057a2e9cda1f66f12121,
  budget : '1000'
}
```

response when username has been taken
```
{
    "success": false,
    "status": 400,
    "message": "username has been used, please select another username"
}
```

response when success 
```
{
    "success": true,
    "status": 200,
    "data": {
        "departement_id": "605057a2e9cda1f66fe21b03",
        "username": "briliantpmw2",
        "password": "$2a$10$9rzqyE/LUQzdCUwZePVivujDxMg7TL0gmec6LKd.HQ7kI5svrDj5i",
        "budget": "1000",
        "role_id": "605057fe85fe2cf876f92caf",
        "modified_at": null,
        "is_delete": false,
        "_id": "60506dffdcb51d2420b6ee10",
        "created_at": "2021-03-16T08:36:15.894Z",
        "__v": 0
    }
}
```









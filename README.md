# reimbursement-apps-server

### Description

(APIX) -> X is a number

the code will be an ID for some API 


### Apps Flow 


**Add Role** : 
```
Login as Super Admin (API0) ->  create role (API1) -> done
```

**Add Departement** : 
```
Login as Super Admin (API0) ->  create departement (API2)-> done
```
**create user** : 
```
Login as Super Admin (API0)-> get department and role list (API3) -> create user (API4) -> done
```

**Create a new transaction by staff** : 

```
Create User (by super admin)(API4) -> Login User (API0)-> create Transaction (API5)-> done
```
**Create a new transaction by SuperAdmin** :

```
Login Super admin -> create Transaction (can with 0 value) -> done
```

```diff
- note : Approval can be update by admin or superadmin
```

**edit  transaction  super admin by staff** : 
```

Login as staff  -> select transaction -> update the data -> done  

```

**Approval by admin** : 
```
Login as admin -> get transaction list -> choose transaction -> update status approval only
```
**Approval by super admin** : 
```
Login as admin -> get transaction list -> choose transaction -> update status approval or change data transaction
```
**Limitation list transaction by super admin** : 
```

Login as super admin  -> choose date range -> update visibility transaction date admin

```

**update outdate approval  : 
```

Login as super admin  -> input number  -> Edit Outdate Approval

```


### Api Docs 




#### BASIC AUTH
for security reason please use header : 

```javascript
headers :{ 
  authorization : token
}
```

response when unauthorize

- without authorization headers

```javascript
{
    "success": false,
    "status": 400,
    "message": "You need login before acces this page"
}
```
- when token invalid or outdated

```javascript
{
    "success": false,
    "status": 400,
    "message": "please login first",
    "err": "invalid token"
}
```

#### login user (API0)

endpoint : /user/login<br>
method : POST<br>
request : 

```javascript

body : {
  username:adinda,
  password : xxxxxxx
}
```
response success :

```javascript
{
    "success": true,
    "status": 200,
    "message": "briliantpmw Login successfully ",
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI2MDUwNThkMzFlZWU0N2ZhNDcwYWU4ZWEiLCJ1c2VybmFtZSI6ImJyaWxpYW50cG13Iiwicm9sZV9pZCI6IjYwNTA1N2ZlODVmZTJjZjg3NmY5MmNhZiIsImlhdCI6MTYxNTg4MzI2MSwiZXhwIjoxNjE1OTY5NjYxfQ.kPIHJYkRkEKdyf2yenTXHQRmTIIGzUoqHBRMG0vuboY"
}
```

response username not found : 

```javascript
{
    "success": false,
    "status": 400,
    "message": "username not found"
}
```

response when wrong password : 
```javascript
{
    "success": false,
    "status": "400",
    "message": "wrong password"
}
```

#### Add new user (API4)

endpoint : /user<br>
method : POST<br>
request : 
```javascript

body : {
  username:'brilian',
  password : '123',
  departement_id : 605057a2e9cda1f66fe21b03,
  role_id : [605057a2e9cda1f66fxxxx],
  budget : '1000'
}
```

```diff
- note : role_id : type Array, 1 user can have more than 1 role_id

```



response when username has been taken
```javascript
{
    "success": false,
    "status": 400,
    "message": "username has been used, please select another username"
}
```

response when success 
```javascript
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

#### Edit user
endpoint : /user/:id<br>
method : PUT<br>

```diff

- you can send attr only attr want to update or fill the attr with null & please DO NOT send password to update


```
example request : 

```
{
    "role_id" : [],
    "username" : "brilianaaa",
    "budget" : null
}
```

will update username and role_id 

```
{
    "success": true,
    "status": 200,
    "data": "update user success"
}
```




#### Edit Visibility Transaction 
endpoint : /role/setvisibility/:id<br>
method : PUT<br>

```diff
- id is role id, only id admin which will working
```

example request : 

```
{
   
    "start_date" : date,
    "end_date" : date
}
```
example response success : 

```
{
    "success": true,
    "status": 200,
    "data": "update admin visibility  success"
}
```

#### Edit Outdate Approval
endpoint : /role/setoutdate/:id<br>
method : PUT<br>

```diff
- id is role id, only id admin which will working
```

example request : 

```
{
   "day" : 5
}
```

day is int, which is indicate super admin and admin will get notification if not approving after 5 days

example response success : 

```
{
    "success": true,
    "status": 200,
    "data": "update outdate Approval  success"
}
```



#### Edit Transacion / approval
endpoint : /transaction/:id<br>
method : PUT<br>

```diff
- id is tra id, only id admin which will working
```

if status created

example request : 

if status created

```
{
"price" : 200000
}
```

if status other

```
{
"status" : status
}
```



example response success : 
if status created

```
{
    "success": true,
    "status": 200,
    "data": "price has been updated"
}
```
if status other
```
{
    "success": true,
    "status": 200,
    "data": "approval has been updated"
}
```









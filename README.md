# reimbursement-apps-server




## Apps Flow 


**Add Role** : 

[Login as super admin](#login-user) ->  [create role](#Add-new-role)  -> done


**Add Departement** : 

[Login as super admin](#login-user) ->  [create departement](#Add-new-departement) -> done

**create user** : 

[Login as super admin ](#login-user) -> [get role](#get-list-role) and [get departement](#get-list-departement)  -> [create user](#Add-new-user)  -> done

**Update user** : 

[Login as super admin ](#login-user) -> [get list user](#get-list-user )-> [update user](#Edit-user)  -> done


**Create a new wallet by superadmin** : 

[login as superadmin](#login-user) ->  create wallet -> done

**update wallet by superadmin** : 

[login as superadmin](#login-user) ->  get list wallet -> update wallet -> done


**Create a new transaction by staff** : 

[create user](#Add-new-user) -> [Login user](#login-user)-> create Transaction -> done

**Create a new transaction by SuperAdmin** :

[Login as super admin ](#login-user) -> create Transaction (can with 0 value) -> done


```diff
- note : Approval can be update by admin or superadmin
```

**edit  transaction  super admin by staff** : 


[Login as staff ](#login-user) -> get list transaction -> [update price data](#Edit-Transacion-or-approval) -> done  

**Approval by admin** : 

[Login as admin ](#login-user) -> get transaction list  ->[update status approval only](#Edit-Transacion-or-approval)

**Approval by super admin** : 

[Login as super admin ](#login-user) -> get transaction list  ->[update status approval or change data transaction](#Edit-Transacion-or-approval) 

**Limitation list transaction by super admin** : 

[Login as super admin ](#login-user)  -> [update visibility transaction date admin](#Edit-Visibility-Transaction)



**update outdate approval  : 


[Login as super admin ](#login-user)    -> [Edit Outdate Approval](#Edit-Outdate-Approval)




## Api Docs 




### BASIC AUTH
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



### login user

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

### Add new departement 

endpoint : /departement<br>
method : POST<br>
request : 
```javascript

body : {
  departement_name : finance
}
```


response when  success
```javascript
{
    "success": true,
    "status": 200,
    "data": {
        "departement_name": "finance",
        "modified_at": null,
        "is_delete": false,
        "_id": "6051d94767ef28cd156fe96d",
        "created_at": "2021-03-17T10:26:15.695Z",
        "__v": 0
    }
}
```
### get list departement 

endpoint : /departement<br>
method : GET<br>



response when  success
```javascript
{
    "success": true,
    "status": 200,
    "data": [
    {
        "departement_name": "finance",
        "modified_at": null,
        "is_delete": false,
        "_id": "6051d94767ef28cd156fe96d",
        "created_at": "2021-03-17T10:26:15.695Z",
        "__v": 0
    },
    {
        "departement_name": "finance",
        "modified_at": null,
        "is_delete": false,
        "_id": "6051d94767ef28cd156fe96d",
        "created_at": "2021-03-17T10:26:15.695Z",
        "__v": 0
    }
    ]
}
```

### get list role 

endpoint : /role<br>
method : GET<br>



response when  success
```javascript
{
    "success": true,
    "status": 200,
    "data": [
    {
        "role_name": "admin",
        "modified_at": null,
        "is_delete": false,
        "_id": "6051d94767ef28cd156fe96d",
        "created_at": "2021-03-17T10:26:15.695Z",
        "__v": 0
    },
    {
        "role_name": "super admin",
        "modified_at": null,
        "is_delete": false,
        "_id": "6051d94767ef28cd156fe96d",
        "created_at": "2021-03-17T10:26:15.695Z",
        "__v": 0
    }
    ]
}
```


### get list user 

endpoint : /user<br>
method : GET<br>



response when  success
```javascript
{
    "success": true,
    "status": 200,
    "data": [
    {
     username:'brilian',
     password : '123',
     departement_id : 605057a2e9cda1f66fe21b03,
     role_id : [605057a2e9cda1f66fxxxx],
     wallet_id : [605057a2e9cda1f66fxxxx],
     budget : '1000'
     "modified_at": null,
     "is_delete": false,
     "_id": "6051d94767ef28cd156fe96d",
     "created_at": "2021-03-17T10:26:15.695Z",
     "__v": 0
    },
    {
      username:'brilianti',
     password : '123',
     departement_id : 605057a2e9cda1f66fe21b03,
     role_id : [605057a2e9cda1f66fxxxx,605057a2e9cda1f66fxxxx,605057a2e9cda1f66fxxxx],
     wallet_id : [605057a2e9cda1f66fxxxx,605057a2e9cda1f66fxxxx],
     budget : '1000'
     "modified_at": null,
     "is_delete": false,
     "_id": "6051d94767ef28cd156fe96d",
     "created_at": "2021-03-17T10:26:15.695Z",
     "__v": 0
    }
    ]
}
```


### Add new role 

endpoint : /role<br>
method : POST<br>
request : 
```javascript

body : {
  role_name : admin
}
```


response when  success
```javascript
{
    "success": true,
    "status": 200,
    "data": {
        "role_name": "admin",
        "modified_at": null,
        "is_delete": false,
        "_id": "6051d94767ef28cd156fe96d",
        "created_at": "2021-03-17T10:26:15.695Z",
        "__v": 0
    }
}
```


### Add new user 

endpoint : /user<br>
method : POST<br>
request : 
```javascript

body : {
  username:'brilian',
  password : '123',
  departement_id : 605057a2e9cda1f66fe21b03,
  role_id : [605057a2e9cda1f66fxxxx],
  wallet_id : [605057a2e9cda1f66fxxxx],
  budget : '1000'
}
```

```diff
- note : role_id & wallet : type Array, 1 user can have more than 1 role_id and wallet_id

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

### Edit user
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




### Edit Visibility Transaction 
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

### Edit Outdate Approval
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



### Edit Transacion or approval
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









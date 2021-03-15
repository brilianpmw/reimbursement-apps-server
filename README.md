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


###### login user

```request : 

body : {
  username:adinda,
  password : xxxxxxx
}
```

```
response :
```

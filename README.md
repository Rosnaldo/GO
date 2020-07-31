# GO

## O jogador que formar 5 casas consecutivas ganha!
### Vale na horizontal, na vertical e na diagonal.

![GitHub Logo](/example.png)

## .env
```
DB_PASSWORD=[DB_PASSWORD]
DB_SCHEMA=[DB_SCHEMA]
PORT=[PORT]
JWT_SECRET=[JWT_SECRET]
```


## Validations
filed    |  Mysql                |   Joi
-------- | ----------------------|-------------
name     | varchar(100) not null | [string] - [min(12)] - [regex(/^[^\s][a-zA-Z\s]*[a-zA-z]$/)] - [required]
email    | varchar(100) not null | [string] - [email] - [required]
password | varchar(100) not null | [string] - [regex(/^.*(.*\d){6,}/)] - [required]
role     | varchar(100) not null | [string] - [required]
confirm  |          -            | [string] - [ref(password)] - [required]


#### POST localhost:3001/user/login
body
```
{
     "email": "joao_neves@gmail.com",
     "password": "123456"
}

```
responses:
**success | status: 200**
```

{
    "token",
    "user": {
        "id",
        "name",
        "email",
        "role""
    }
}
```

## Routes

#### POST localhost:3001/user/register


body:
```
{
     "name": "João das Neves",
     "email": "joao_neves@gmail.com",
     "password": "123456"
     "role" "client",
     "confirm": "123456"
}
```

responses:
**success | status: 201**
```
{
    "message": "User created with sucess!"
}

```

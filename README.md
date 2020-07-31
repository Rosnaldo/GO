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


## Routes

#### POST localhost:3001/user/login [Authorization=NO]
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

#### POST localhost:3001/user/register [Authorization=YES]


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

#### GET localhost:3001/user/profile [Authorization=YES]

responses:
**success | status: 200**
```
{
    "name",
    "email",
}
```

#### PATCH localhost:3001/user/profile [Authorization=YES]
body
```
{
    "name": "joão das Naevs",
    "email": "joao_venes@gmail.com",
}
```

responses:
**success | status: 200**
```
{
    "message": "User update with sucess!"
}










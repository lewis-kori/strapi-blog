# Strapi blog

## setup

have node.js > v12.x installed

run `yarn install`

after dependencies have been installed
create a .env file and populate it with relevant info from the `.env.example`

finally, run

`yarn develop`

## auth endpoints

### register user

    auth/local/register

keys are

- username
- email
- about
- password
- profile_pic(optional)

this will [log you in automatically](#login)

### login

    auth/local

keys are

- identifier (username or email)
- password

expected results are:

    ```
    {
        "jwt": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwiaWF0IjoxNjA4NDk0ODA4LCJleHAiOjE2MTEwODY4MDh9.C-KgKYQcwZvAY4gigyB0-kU7B26Zy6fRe3eh4YU2z7U",
        "user": {
            "id": 1,
            "username": "example@me.com",
            "email": "example@me.com",
            "provider": "local",
            "confirmed": true,
            "blocked": false,
            "role": {
                "id": 1,
                "name": "Authenticated",
                "description": "Default role given to authenticated user.",
                "type": "authenticated"
            },
            "created_at": "2020-12-18T06:54:06.586Z",
            "updated_at": "2020-12-20T19:59:49.908Z"
        }
    }
    ```

use the jwt in request headers in subsequent api calls.

### forgot password

    auth/forgot-password

pass `email` as key and make a POST request to the endpoint

## blog endpoints

### list all articles

    /articles

a GET request lists all the articles in the db

### view article details

    articles/{articles_id}

retrieves a single instance of a articles

### list all articles categories

    /categories

a GET request lists all the article categories in the db.

### view articles category details

    categories/{category_id}

retrieves a single instance of an articles category.

### list all tags

    /tags

### view tag details

    /tags/{tag_id}

---

title: More-Recipes

language_tabs:
   - javascript

toc_footers:

includes:
   - errors

search: true

---

# Introduction
More-Recipes​​ ​provides​ ​a​ ​platform​ ​for​ ​users​ ​to​ ​share​ ​awesome​ ​and​ ​exciting​ ​​ ​recipe​ ​ideas​ ​they  have​ ​invented​ ​or​ ​learnt.​ ​​ ​Suppose​ ​a​ ​user​ ​comes ​up​ ​with​ ​a​ ​recipe,​ ​​ ​he/she​ ​can​ ​post​ ​it​ ​on  More-Recipes​​ ​and​ ​​ ​get​ ​feedback​ ​in​ ​form​ ​of​ ​reviews​ ​and​ ​votes​ ​from​ ​other​ ​users​ ​who​ ​explored​ ​recipe.

**Version:** 1.0

# Making Request

Upon signing up or logging in with the More-Recipes API an authorization token is generated which is used to access other resources from the More-Recipes API.

The generated token expires within 24 hours after it was generated.

This token can be placed in ```req.headers.Authorization```,```req.body.Authorization``` or ```req.query.Authorization```

`Authorization: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6OSwiaWF0IjoxNTE1MTQzMDUwLCJleHAiOjE1MTUyMjk0NTB9.thUTHVj_GDOGlfhhufVRBrzJ4J6gJG6l3xYQaBmJ7Gk"`

<aside class="notice">
Replace <code>"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6OSwiaWF0IjoxNTE1MTQzMDUwLCJleHAiOjE1MTUyMjk0NTB9.thUTHVj_GDOGlfhhufVRBrzJ4J6gJG6l3xYQaBmJ7Gk"</code> with your authorization token.
</aside>

# User

## User Signup
> Request Body:
```json
    {
      "username": "vicki",
      "fullname": "Victoria Doe",
      "email": "vicki@gmail.com",
      "password": "1234567",
    }
```
> Response Body:

```json
 {
    "status": "success",
    "User": {
        "fullname": "Victoria Doe",
        "profilePicture": "none",
        "username": "vicki",
        "email": "vicki@gmail.com",
        "updatedAt": "2017-09-17T04:45:44.084Z",
        "createdAt": "2017-09-17T04:45:44.084Z",
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwiaWF0IjoxNTA1NjIzNTQ0LCJleHAiOjE1MDU3OTYzNDR9.ya4vLYqHQ3zgkgPZo6_9aePh6OhvB2BLlQ9IC-5sNaM"
    }
}
```

This endpoint creates a new user

### Request

* Endpoint: `/api/v1/users/signup`
* Verb: `POST`
* Body: `(application/json)`

### Response
* StatusCode: `201: Created`
* Body: `(application/json)`


## User Signin
> Request Body:
```json
    {
      "username": "vicki",
      "password": "1234567",
    }
```
> Response Body:

```json
 {
    "status": "success",
    "User": {
        "fullname": "Victoria Doe",
        "profilePicture": "none",
        "username": "vicki",
        "email": "vicki@gmail.com",
        "updatedAt": "2017-09-17T04:45:44.084Z",
        "createdAt": "2017-09-17T04:45:44.084Z",
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwiaWF0IjoxNTA1NjIzNTQ0LCJleHAiOjE1MDU3OTYzNDR9.ya4vLYqHQ3zgkgPZo6_9aePh6OhvB2BLlQ9IC-5sNaM"
    }
}
```

This endpoint sign's in a user

### Request

* Endpoint: `/api/v1/users/signin`
* Verb: `POST`
* Body: `(application/json)`

### Response
* StatusCode: `200: Ok`
* Body: `(application/json)`

## User profile update
> Request Body:

```json
    {
      "username": "vicki4u",
      "fullname": "Victoria Banks",
    }
```
> Response Body:

```json
 {
    "status": "success",
    "User": {
        "username": "vicki4u",
        "fullname": "Victoria Banks",        
        "profilePicture": "none",
        "email": "vicki@gmail.com",
        "favRecipes":[]
    }
}
```

This endpoint updates user profile

### Request

* Endpoint: `/api/v1/users/update`
* Verb: `PUT`
* Body: `(application/json)`

### Response
* StatusCode: `200: Ok`
* Body: `(application/json)`

## Get user profile

> Response Body:

```json
 {
    "status": "success",
    "User": {
        "username": "vicki4u",
        "fullname": "Victoria Banks",        
        "profilePicture": "none",
        "email": "vicki@gmail.com",
        "favRecipes":[]
    }
}
```

This endpoint gets user profile

### Request

* Endpoint: `/api/v1/users/:id`
* Verb: `GET`
* Requires: Token
* id: 1

### Response
* StatusCode: `200: Ok`
* Body: `(application/json)`


## Get user's favourite recipes

> Response Body:

```json
 {
      "status": "success",
      "favRecipe": {
          "recipe": {
              "id": 10,
              "name": "onions stew and rice",
              "category": "lunch",
              "ingredients": [
                  "onions",
                  "rice"
              ],
              "directions": [
                  "wash the rice very well"
              ],
              "image": "{\"publicId\":\"\",\"secureUrl\":\"\",\"signature\":\"\",\"thumbnailUrl\":\"\",\"url\":\"\"}",
              "upVotes": 1,
              "downVotes": 0,
              "views": 3,
              "favRecipesId": null,
              "ownerId": 1,
              "createdRecipesId": 1,
              "UserId": null,
              "createdAt": "2017-12-31T15:35:26.969Z",
              "updatedAt": "2018-01-04T14:58:12.696Z"
          },
      }
  }
```

This endpoint gets favourite's recipes

### Request

* Endpoint: `/api/v1/users/recipes/favourite`
* Verb: `GET`
* Requires: Token

### Response
* StatusCode: `200: Ok`
* Body: `(application/json)`

## Get user's created recipes

> Response Body:

```json
 {
      "status": "success",
      "recipes": {
          "recipe": {
              "id": 10,
              "name": "onions stew and rice",
              "category": "lunch",
              "ingredients": [
                  "onions",
                  "rice"
              ],
              "directions": [
                  "wash the rice very well"
              ],
              "image": "{\"publicId\":\"\",\"secureUrl\":\"\",\"signature\":\"\",\"thumbnailUrl\":\"\",\"url\":\"\"}",
              "upVotes": 1,
              "downVotes": 0,
              "views": 3,
              "favRecipesId": null,
              "ownerId": 1,
              "createdRecipesId": 1,
              "UserId": null,
              "createdAt": "2017-12-31T15:35:26.969Z",
              "updatedAt": "2018-01-04T14:58:12.696Z"
          },
      }
  }
```

This endpoint gets favourite's recipes

### Request

* Endpoint: `/api/v1/users/recipes/created`
* Verb: `GET`
* Requires: Token

### Response
* StatusCode: `200: Ok`
* Body: `(application/json)`

# Recipes

## Create recipe
> Request Body

```json
{
  "recipe": {
      "name": " Chicken and Pasta",
      "category":"Dinner",
      "ingredients":["chicken","pasta","vegetable oil"],
      "directions":["wash the chicken", "boil the chicken", "cook the pasta"],
      "image": "none"
  }
}
```

> Response Body

```json
        {
          "status": "success",
          "recipe": {
              "upVotes": 0,
              "downVotes": 0,
              "views": 0,
              "id": 22,
              "name": " Chicken and Pasta",
              "category": "Dinner",
              "ingredients": [
                  "chicken",
                  "pasta",
                  "vegetable oil"
              ],
              "directions": [
                  "wash the chicken",
                  "boil the chicken",
                  "cook the pasta"
              ],
              "image": "none",
              "updatedAt": "2018-01-04T20:03:13.018Z",
              "createdAt": "2018-01-04T20:03:13.002Z",
              "ownerId": 8,
              "favRecipesId": null,
              "createdRecipesId": null,
              "UserId": null,
              "owner": {
                "username": "vicki4u",
                "fullname": "Victoria Banks",
                "profilePicture": "none",
                "email": "vicki@gmail.com"
              }
            }
          }
```

This endpoint creates a new recipe.

### Request

* Endpoint:`/api/v1/recipes`
* Verb: `POST`
* Requires: Token

### Response

* StatusCode: `201: Created`
* Body: `(application/json)`

## Edit recipe
> Request Body

```json
{
  "recipe": {
      "category":"Lunch",
      "ingredients":["chicken","pasta",],
  }
}
```

> Response Body

```json
        {
          "status": "success",
          "recipe": {
              "upVotes": 0,
              "downVotes": 0,
              "views": 0,
              "id": 22,
              "name": " Chicken and Pasta",
              "category": "Lunch",
              "ingredients":["chicken","pasta",],
              "directions": [
                  "wash the chicken",
                  "boil the chicken",
                  "cook the pasta"
              ],
              "image": "none",
              "updatedAt": "2018-01-04T20:03:13.018Z",
              "createdAt": "2018-01-04T20:03:13.002Z",
              "ownerId": 8,
              "favRecipesId": null,
              "createdRecipesId": null,
              "UserId": null,
              "owner": {
                "username": "vicki4u",
                "fullname": "Victoria Banks",
                "profilePicture": "none",
                "email": "vicki@gmail.com"
              }
            }
          }
```

This endpoint updates a recipe.

### Request

* Endpoint:`/api/v1/recipes`
* Verb: `PUT`
* Requires: Token

### Response

* StatusCode: `200: OK`
* Body: `(application/json)`


## Upvote a Recipe

> Response Body

```json
{
    "status": "success",
    "recipe": {
        "id": 1,
        "upVotes": 1,
        "downVotes": 0
    }
}
```

This endpoint upvotes a single recipe.

### Request

* Endpoint:`/api/v1/recipes/1/vote?up={true}`
* Verb: `PUT`
* Requires: Token
* query parameter: {
  up: true
}

### Response

* StatusCode: `200: Ok`
* Body: `(application/json)`

## Downvote a Recipe

> Response Body

```json
{
    "status": "success",
    "recipe": {
        "id": 1,
        "upVotes": 0,
        "downVotes": 1
    }
}
```

This endpoint downvotes a single recipe.

### Request

* Endpoint:`/api/v1/recipes/1/vote?down={true}`
* Verb: `PUT`
* Requires: Token
* query parameter: {
  down: true
}

### Response

* StatusCode: `200: Ok`
* Body: `(application/json)`

## Delete Recipe

> Response Body

```json
{
    "status": "success",
    "message": "Recipe was successfully deleted",
}
```

This endpoint deletes a single recipe.

### Request

* Endpoint:`/recipe/:id`
* Verb: `DELETE`
* Requires: Token
* Accessible only to the recipe owner

### Response

* StatusCode: `200: Ok`
* Body: `(application/json)`

## Post Recipe review
> Request Body
```json
{
  "review": "i love this recipe..!!!"
}
```

> Response Body

```json
  {
    "status": "success",
    "pageCount": 1,
    "reviews": [
        {
            "id": 14,
            "RecipeId": 10,
            "createdAt": "2018-01-05T02:33:27.562Z",
            "review": "i love this recipe..!!!",
            "reviewer": {
                "id": 8,
                "username": "crea",
                "fullname": "crew e"
            }
        },
        {
            "id": 12,
            "RecipeId": 10,
            "createdAt": "2018-01-02T09:26:36.915Z",
            "review": "love this",
            "reviewer": {
                "id": 3,
                "username": "gogo",
                "fullname": "gog gog"
            }
        },
        {
            "id": 11,
            "RecipeId": 10,
            "createdAt": "2018-01-02T09:23:15.174Z",
            "review": "hate it",
            "reviewer": {
                "id": 1,
                "username": "resybaba",
                "fullname": "resy x p"
            }
        },
        {
            "id": 10,
            "RecipeId": 10,
            "createdAt": "2018-01-02T09:20:33.891Z",
            "review": "cool",
            "reviewer": {
                "id": 1,
                "username": "resybaba",
                "fullname": "resy x p"
            }
        }
    ]
}
```

This endpoint downvotes a single recipe.

### Request

* Endpoint:`/api/v1/recipes/{id}/reviews`
* Verb: `POST`
* Requires: Token
* id: 10

### Response

* StatusCode: `201: Ok`
* Body: `(application/json)`

## Get recipes

> Response Body:

```json

  {
      "status": "success",
      "pageCount": 1,
      "recipes": [
          {
              "id": 5,
              "name": "salad",
              "category": "vegeterian",
              "image": "{\"publicId\":\"\",\"secureUrl\":\"\",\"signature\":\"\",\"thumbnailUrl\":\"\",\"url\":\"\"}",
              "ingredients": [
                  "cucumber"
              ],
              "directions": [
                  "wash"
              ],
              "upVotes": 3,
              "downVotes": 0,
              "views": 3
          },
          {
              "id": 12,
              "name": "pizza",
              "category": "lunch",
              "image": "{\"publicId\":\"\",\"secureUrl\":\"\",\"signature\":\"\",\"thumbnailUrl\":\"\",\"url\":\"\"}",
              "ingredients": [
                  "water"
              ],
              "directions": [
                  "wash"
              ],
              "upVotes": 4,
              "downVotes": 2,
              "views": 7
          },
          {
              "id": 10,
              "name": "rice and stew",
              "category": "lunch",
              "image": "{\"publicId\":\"\",\"secureUrl\":\"\",\"signature\":\"\",\"thumbnailUrl\":\"\",\"url\":\"\"}",
              "ingredients": [
                  "egg",
                  "rice"
              ],
              "directions": [
                  "wash"
              ],
              "upVotes": 1,
              "downVotes": 0,
              "views": 3
          },
          {
              "id": 16,
              "name": "pepper soup",
              "category": "lunch",
              "image": "{\"publicId\":\"\",\"secureUrl\":\"\",\"signature\":\"\",\"thumbnailUrl\":\"\",\"url\":\"\"}",
              "ingredients": [
                  "cooking oil",
                  "salt"
              ],
              "directions": [
                  "wash your hands"
              ],
              "upVotes": 1,
              "downVotes": 0,
              "views": 2
          },
          {
              "id": 20,
              "name": "banga rice",
              "category": "snacks",
              "image": "{\"publicId\":\"\",\"secureUrl\":\"\",\"signature\":\"\",\"thumbnailUrl\":\"\",\"url\":\"\"}",
              "ingredients": [
                  "banga"
              ],
              "directions": [
                  "wash"
              ],
              "upVotes": 1,
              "downVotes": 0,
              "views": 1
          },
          {
              "id": 21,
              "name": "beans and yam",
              "category": "brunch",
              "image": "{\"publicId\":\"\",\"secureUrl\":\"\",\"signature\":\"\",\"thumbnailUrl\":\"\",\"url\":\"\"}",
              "ingredients": [
                  "beans"
                  "yam
              ],
              "directions": [
                  "wash"
              ],
              "upVotes": 1,
              "downVotes": 0,
              "views": 1
          }
      ]
  }
```

This endpoint get random recipes from the database

### Request

* Endpoint: `/api/v1/recipes`
* Verb: `GET`
* Requires: Token

### Response
* StatusCode: `200: Ok`
* Body: `(application/json)`

## Get Top recipes

> Response Body:

```json

  {
      "status": "success",
      "pageCount": 1,
      "recipes": [
          {
              "id": 5,
              "name": "salad",
              "category": "vegeterian",
              "image": "{\"publicId\":\"\",\"secureUrl\":\"\",\"signature\":\"\",\"thumbnailUrl\":\"\",\"url\":\"\"}",
              "ingredients": [
                  "cucumber"
              ],
              "directions": [
                  "wash"
              ],
              "upVotes": 3,
              "downVotes": 0,
              "views": 3
          },
          {
              "id": 12,
              "name": "pizza",
              "category": "lunch",
              "image": "{\"publicId\":\"\",\"secureUrl\":\"\",\"signature\":\"\",\"thumbnailUrl\":\"\",\"url\":\"\"}",
              "ingredients": [
                  "water"
              ],
              "directions": [
                  "wash"
              ],
              "upVotes": 4,
              "downVotes": 2,
              "views": 7
          },
          {
              "id": 10,
              "name": "rice and stew",
              "category": "lunch",
              "image": "{\"publicId\":\"\",\"secureUrl\":\"\",\"signature\":\"\",\"thumbnailUrl\":\"\",\"url\":\"\"}",
              "ingredients": [
                  "egg",
                  "rice"
              ],
              "directions": [
                  "wash"
              ],
              "upVotes": 1,
              "downVotes": 0,
              "views": 3
          },
          {
              "id": 16,
              "name": "pepper soup",
              "category": "lunch",
              "image": "{\"publicId\":\"\",\"secureUrl\":\"\",\"signature\":\"\",\"thumbnailUrl\":\"\",\"url\":\"\"}",
              "ingredients": [
                  "cooking oil",
                  "salt"
              ],
              "directions": [
                  "wash your hands"
              ],
              "upVotes": 1,
              "downVotes": 0,
              "views": 2
          },
          {
              "id": 20,
              "name": "banga rice",
              "category": "snacks",
              "image": "{\"publicId\":\"\",\"secureUrl\":\"\",\"signature\":\"\",\"thumbnailUrl\":\"\",\"url\":\"\"}",
              "ingredients": [
                  "banga"
              ],
              "directions": [
                  "wash"
              ],
              "upVotes": 1,
              "downVotes": 0,
              "views": 1
          },
          {
              "id": 21,
              "name": "beans and yam",
              "category": "brunch",
              "image": "{\"publicId\":\"\",\"secureUrl\":\"\",\"signature\":\"\",\"thumbnailUrl\":\"\",\"url\":\"\"}",
              "ingredients": [
                  "beans"
                  "yam
              ],
              "directions": [
                  "wash"
              ],
              "upVotes": 1,
              "downVotes": 0,
              "views": 1
          }
      ]
  }
```

This endpoint get recipe by upvotes

### Request

* Endpoint: `/api/v1/recipes?sort=upvotes&order=ascending`
* Verb: `GET`
* Requires: Token

### Response
* StatusCode: `200: Ok`
* Body: `(application/json)`

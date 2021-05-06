---
description: The one endpoint with GitHub user information retrieval functionality.
---

# GitHub Users

{% hint style="warning" %}
This endpoint is experimental, and required the `EXPERIMENTAL` privileged user flag to be active, as described in the [User Flags](../basics/intents.md#what-are-user-flags) section.
{% endhint %}

{% hint style="danger" %}
This endpoint is experimental and can only be accessed by the developers and other privileged people - and we do not recommend the usage of any experimental endpoints in production environments, this should be used as a reference to let library developers to prepare for this addition - or the developers for adding it in their staging versions of projects ready to go live when the endpoint is removed the `EXPERIMENTAL`flag.

The documentation on this page is subject to change at anytime.
{% endhint %}

> These endpoints requires the privileged `INFORMATION_GITHUB` user permission flag to be active, as described in the [User Flags](../basics/intents.md#what-are-user-flags) section. See information on how to activate privileged flags [here](../basics/intents.md#activating-privileged-flags).

{% api-method method="get" host="https://api.mraugu.xyz" path="/information/github/user" %}
{% api-method-summary %}
Fetch User Information
{% endapi-method-summary %}

{% api-method-description %}
Fetches a user's information from GitHub REST API.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The authorization header as described in the authorization section.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="name" type="string" required=true %}
The username of the user you want to fetch.
{% endapi-method-parameter %}

{% api-method-parameter name="orgs" type="boolean" required=false %}
Whether to fetch the organizations that the user is being fetched is a part of.
{% endapi-method-parameter %}

{% api-method-parameter name="starred" type="boolean" required=false %}
Whether to fetch the repositories that are being starred by the user.
{% endapi-method-parameter %}

{% api-method-parameter name="following" type="boolean" required=false %}
Whether to fetch the users that are being followed by the fetched user.
{% endapi-method-parameter %}

{% api-method-parameter name="followers" type="boolean" required=false %}
Whether to fetch the users that are following the fetched user.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Indicates that the request went through and was successfully fulfilled.
{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 200,
  "error": null,
  "message": "Request fulfileld",
  "data": {
    "exists": true,
    "user": {
      "id": 39545629,
      "name": "MrAugu",
      "username": "MrAugu",
      "avatar": "https://avatars.githubusercontent.com/u/39545629?v=4",
      "profieUrl": "https://github.com/MrAugu",
      "githubAdmin": false,
      "company": null,
      "link": "https://discord.gg/Wwekc2QAzq",
      "location": "Romania",
      "email": "mraugu@yahoo.com",
      "bio": "I'm a high school student, software development is my hobby.",
      "twitterUsername": null,
      "publicRepoCount": 56,
      "publicGistCount": 1,
      "followersCount": 52,
      "followingCount": 10,
      "createdAt": "2018-05-23T04:32:57.000Z",
      "lastUpdatedAt": "2021-05-05T22:49:38.000Z",
      "organizations": [
        {
          "id": 64218952,
          "name": "DiscordRep",
          "icon": "https://avatars.githubusercontent.com/u/64218952?v=4",
          "description": "A reputation service to prevent fraud and scams.",
          "nodeId": "MDEyOk9yZ2FuaXphdGlvbjY0MjE4OTUy"
        },
        {
          "id": 64532228,
          "name": "ModCord",
          "icon": "https://avatars.githubusercontent.com/u/64532228?v=4",
          "description": "GitHub organization that resembles the ModCord's discord bot public repositories and staff team.",
          "nodeId": "MDEyOk9yZ2FuaXphdGlvbjY0NTMyMjI4"
        }
      ],
      "starred": [
        {
          "nodeId": "MDEwOlJlcG9zaXRvcnkzNjM5NTk0MDU=",
          "id": 363959405,
          "name": "weird-to-normal-chars",
          "fullName": "Snowflake107/weird-to-normal-chars",
          "url": "https://github.com/Snowflake107/weird-to-normal-chars",
          "description": "Weird to normal chars converter",
          "language": "JavaScript",
          "stars": 1,
          "watching": 1,
          "forks": 1,
          "watchers": 1,
          "defaultBranch": "master",
          "owner": {
            "name": "Snowflake107",
            "id": 46562212,
            "avatar": "https://avatars.githubusercontent.com/u/46562212?v=4",
            "url": "https://github.com/Snowflake107",
            "githubAdmin": false
          }
        },
        {
          "nodeId": "MDEwOlJlcG9zaXRvcnkxMjIzNzQ0NjA=",
          "id": 122374460,
          "name": "skyra",
          "fullName": "skyra-project/skyra",
          "url": "https://github.com/skyra-project/skyra",
          "description": "All-in-one multipurpose Discord Bot designed to carry out most of your server's needs with great performance and stability.",
          "language": "TypeScript",
          "stars": 97,
          "watching": 97,
          "forks": 36,
          "watchers": 97,
          "defaultBranch": "main",
          "owner": {
            "name": "skyra-project",
            "id": 59655788,
            "avatar": "https://avatars.githubusercontent.com/u/59655788?v=4",
            "url": "https://github.com/skyra-project",
            "githubAdmin": false
          }
        }
      ],
      "following": [
        {
          "name": "cwkhawand",
          "id": 22796675,
          "avatar": "https://avatars.githubusercontent.com/u/22796675?v=4",
          "url": "https://github.com/cwkhawand",
          "githubAdmin": false
        },
        {
          "name": "Myst82015",
          "id": 34489470,
          "avatar": "https://avatars.githubusercontent.com/u/34489470?v=4",
          "url": "https://github.com/Myst82015",
          "githubAdmin": false
        },
        {
          "name": "leny32",
          "id": 40176071,
          "avatar": "https://avatars.githubusercontent.com/u/40176071?v=4",
          "url": "https://github.com/leny32",
          "githubAdmin": false
        }
      ],
      "followers": [
        {
          "name": "kyranet",
          "id": 24852502,
          "avatar": "https://avatars.githubusercontent.com/u/24852502?v=4",
          "url": "https://github.com/kyranet",
          "githubAdmin": false
        },
        {
          "name": "PrincessRavy",
          "id": 29358311,
          "avatar": "https://avatars.githubusercontent.com/u/29358311?v=4",
          "url": "https://github.com/PrincessRavy",
          "githubAdmin": false
        }
      ]
    }
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Indicates a malformed request body, these can be caused by sending the data encoded in a non-compliant data format for that endpoint, missing required parameters, parameters of wrong types or invalid length - usually too large.
{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 400,
  "error": "Bad request",
  "message": "Invalid request body."
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
This status code that you did not properly pass the token in the authorization header, or the token is invalid \(it does not exist/was regenerated\).
{% endapi-method-response-example-description %}

```javascript
{
   "statusCode": 401,
   "error": "Unauthorized",
   "message": "You are not authorized."
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}
Indicates that you have either tried to access an endpoint you don't have the user flag for,  you've hit the ratelimit bad threshold in which case you must wait before sending requests again or yo
{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 403,
  "error": "Forbidden",
  "message": "You do not have the flag required to access this endpoint. Please refer to the documentation at https://docs.mraugu.xyz/ for more information."   
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}


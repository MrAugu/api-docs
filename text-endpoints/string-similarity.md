---
description: The one endpoint that handles string similarity related functionality.
---

# String Similarity

> This endpoint requires the default `TEXT` token flag to be active, as described in the [User Flags](https://docs.mraugu.xyz/basics/intents) specification.

{% api-method method="post" host="https://api.mraugu.xyz" path="/text/similarity/best-match" %}
{% api-method-summary %}
Text Syntax Best Match
{% endapi-method-summary %}

{% api-method-description %}
Checks the similarity of the given choices against a query, and returns everything back accordingly.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The API authorization header, as described in the authorization section.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="query" type="string" required=true %}
The string that all the choices will be compared against, max length 3,000 characters.
{% endapi-method-parameter %}

{% api-method-parameter name="choices" type="array" required=true %}
An array of string that will be compared against the query, max 100 items, each max length 3,000 characters, and cumulated max length 50,000 characters.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Indicates that the request went through and was fulfilled successfully.
{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 200,
  "error": null,
  "message": "Request fulfileld",
  "data": {
    "bestChoices": {
      "content": "help",
      "confidence": 40,
      "index": 0
    },
    "otherChoices": [
      {
        "content": "ping",
        "confidence": 0
      },
      {
        "content": "kick",
        "confidence": 0
      },
      {
         "content": "ban",
         "confidence": 0
      }
    ],
    "took": 81
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Indicates a malformed request body, these can be caused by missing required parameters, parameters of wrong types, or invalid length - usually too large. 
{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 400,
  "error": "Bad request",
  "message": "The request body is invaid."
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
Indicates that you did not properly pass the token in the authorization header, or the token is invalid \(it does not exist/was regenerated\).
{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 401,
  "error": "Unauthorized",
  "message": "You are not authorized."
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

**Returns a data object of type `StringSimilarity`.**


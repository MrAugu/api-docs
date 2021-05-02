---
description: The two endpoints that handle text similarity related functionality.
---

# Text Similarity

> These endpoints requires the privileged `TEXT_SIMILARITY` token flag to be active, as described in the [User Flags](../basics/intents.md#what-are-user-flags) section. See information on how to activate privileged flags [here](../basics/intents.md#activating-privileged-flags).

{% api-method method="post" host="https://api.mraugu.xyz" path="/text/similarity" %}
{% api-method-summary %}
Semantic Text Similarity 
{% endapi-method-summary %}

{% api-method-description %}
Checks the similarity of 2 phrases against one another and returns the % of how semantically similar they are, using machine learning.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The API request authorization header, as described in the authorization section.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="firstSentence " type="string" required=true %}
The second sentence, can have a maximum length of 3,000 characters.
{% endapi-method-parameter %}

{% api-method-parameter name="secondSentence" type="string" required=true %}
The first sentence, can have a maximum length of 3,000 characters.
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
  "message": "Request fulfilled.",
  "data": {
    "similarity": 88.93
    "took": 15
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
  "message": "Invalid content length."
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
This status code indicates that you did not properly pass the token in the authorization header, the token is invalid \(it does not exist/was regenerated\).
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
Indicates that you have either tried to access an endpoint you don't have the user permission flag for, or you've hit the ratelimit ban threshold in which case you must wait a period before sending requests again.
{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 403,
  "error": "Forbidden",
  "message": "You do not have the user flag required to access this endpoint, please refer to https://docs.mraugu.xyz/basics/intents for more information."   
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

**It returns a data object of type `SingleTextSimilarity`.** 

{% api-method method="post" host="https://api.mraugu.xyz" path="/text/similarity/against" %}
{% api-method-summary %}
Semantic Text Similarity Against
{% endapi-method-summary %}

{% api-method-description %}
Checks the similarity of an array of different phrases against a specific phrase and returns the % of how semantically similar they are, using machine learning.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The API request authorization header, as described in the authorization section.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="secondarySentences" type="array" required=true %}
An array of sentences that will be checked against the primary, max 100 items, each max length 3,000 characters, and cumulated max length 50,000 characters.
{% endapi-method-parameter %}

{% api-method-parameter name="primarySentence " type="string" required=true %}
The text other sentences will be checked against, maximum length of 3,000 characters.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Indicated that the request went through and was fulfilled successfully by the server.
{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 200,
  "error": null,
  "message": "Request fulfilled.",
  "data": {
    "primary": "hello dear fiend",
    "similarities": [
      {
        "sentence": "hello my cousin",
        "similarity": 70.94
      },
      {
        "sentence": "i love you",
        "similarity": 47.24
      },
      {
        "sentence": "we are having breakfast",
        "similarity": 32.57
      }
    ],
    "took": 63
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Indicates a malformed request body, these can be caused by missing required parameters, parameters of wrong types or invalid parameter length - usually too large.
{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 400,
  "error": "Bad request",
  "message": "The request body is invalid."
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
This status code indicates that you did not properly pass the token in the authorization header, or the token is invalid \(it does not exist/was regenerated\).
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

**Returns a data object of type `MultipleTextSimilarity`.**

## Data Structures

> **`SingleTextSimilarity`**:

> _Represents a text similarity against response data object returned by the API._

| Property | Type | Description |
| :--- | :--- | :--- |
| `similarity` | `Float32` | The degree of similarity between the two sentences. \(`%`\) |
| `took` | `Integer` | The amount of time taken by the evaluation. |

> **`MultipleTextSimilarity`**:

> _Represents a text similarity against response data object returned by the API._

| Property | Type | Description |
| :--- | :--- | :--- |
| `primary` | `String` | The primary sentence that was passed in the request. |
| `similarities` | `Array[Sentence]` | An array of evaluated sentence objects. |
| `took` | `Integer` | The amount of time taken by the evaluation. |

> **`Sentence`**:

> _Represents an evaluated secondary sentence returned by the API._

| Property | Type | Description |
| :--- | :--- | :--- |
| `sentence` | `String` | A secondary sentence passed in by the user. |
| `similarity` | `Float32` | The degree of similarity between this secondary and the primary. \(`%`\) |


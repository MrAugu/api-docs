---
description: The two endpoints that handle text similarity related functionality.
---

# Text Similarity

> These endpoints requires the privileged `TEXT_SIMIARITY` token flag to be active, as described in the [User Flags](https://docs.mraugu.xyz/basics/intents) specification.

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
The interface request authorization header, as described in the authorization spec.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="firstSentence " type="string" required=true %}
The second sentence, can have a maximum length of 3000 characters.
{% endapi-method-parameter %}

{% api-method-parameter name="secondSentence" type="string" required=true %}
The first sentence, can have a maximum length of 3000 characters.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Any 200: OK status codes mean that the request went through and was fulfilled successfully.
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
Any 400 bad request status codes will indicate a malformed request body, these can be caused by missing required parameters, parameters of wrong types, or invalid length of contents exceeding the allowed limit.
{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 400,
  "error": "Bad Request",
  "message": "Invalid content length."
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
Any 401 unauthorized response status code means that you did not properly pass in the token in the authorization header, the token is invalid, or the token was regenerated and is also no longer valid.
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

**It returns a data object of type `SingleTextSimilarity`.** 

| Property | Type | Description |
| :--- | :--- | :--- |
| similarity | Float32 | How similar they are on a scale from 1 to 100 \(%\), truncated to 2 decimal points. |
| took | Integer | How much time the evaluation of these string took, in milliseconds. |

{% api-method method="post" host="https://api.mraugu.xyz" path="/text/similarity/against" %}
{% api-method-summary %}
Semantic Text Similarity Against
{% endapi-method-summary %}

{% api-method-description %}
Checks the similarity of an array of phrases against a specific phrase.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The interface request authorization header, as described in the authorization spec.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="secondarySentences" type="array" required=true %}
An array of strings containing the sentences that will be checked against the primary.
{% endapi-method-parameter %}

{% api-method-parameter name="primarySentence " type="string" required=true %}
The text other sentences will be checked against, maximum length of 3000 characters.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Any 200: OK mean that the request went through and was fulfilled successfully by the server.
{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 200,
  "error": null,
  "message": "Request fulfilled.",
  "data": {
    
  }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}




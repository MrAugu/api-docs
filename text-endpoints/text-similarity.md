---
description: The two endpoints that handle text similarity related functionality.
---

# Text Similarity

{% api-method method="post" host="https://api.mraugu.xyz" path="/text/similarity" %}
{% api-method-summary %}
Semantic Text Similarity 
{% endapi-method-summary %}

{% api-method-description %}
Checks the similarity of 2 phrases against one another and returns how similar percent on a range from 0% to 100% with 2 decimals.
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
Any 200 requests means that the request went through and was fulfilled successfully.
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Any 400 bad requests will indicate a malformed request body, these can be caused by missing required parameters, parameters of wrong types, or invalid length of contents exceeding the allowed limit.
{% endapi-method-response-example-description %}

```
{
  "statusCode": 400,
  "error": "Bad Request",
  "message": "Invalid content length."
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}


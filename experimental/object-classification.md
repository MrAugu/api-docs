---
description: The one endpoint with image object classification functionality.
---

# Object Classification

{% hint style="warning" %}
This endpoint is experimental, and required the `EXPERIMENTAL` privileged user flag to be active, as described in the [User Flags](../basics/intents.md#what-are-user-flags) section.
{% endhint %}

{% hint style="danger" %}
This endpoint is experimental and can only be accessed by the developers and other privileged people, and we do not recommend using it in production - only staging. 

The documentation found on this page is subject to change at anytime.
{% endhint %}

> These endpoints requires the privileged `IMAGES_OBJECTS` user permission flag to be active, as described in the [User Flags](../basics/intents.md#what-are-user-flags) section. See information on how to activate privileged flags [here](../basics/intents.md#activating-privileged-flags).

{% api-method method="post" host="https://api.mraugu.xyz" path="/images/classify/objects" %}
{% api-method-summary %}
Image Object Classification
{% endapi-method-summary %}

{% api-method-description %}
Can recognize over 80 objects from the photo, returning what it found and where on the image it was found, giving you the ability to draw boxes on the images corresponding to the area the object was found in.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="User-Agent" type="string" required=false %}
The user agent associated with this request, can be used to track different requesters in metrics.
{% endapi-method-parameter %}

{% api-method-parameter name="Authorization" type="string" required=true %}
The authorization header, as described in the authorization section.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="data" type="string" required=true %}
Image base64 encoded binary, as described in the request section. Maximum size is 5MB.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
This indicates that the request went through and was fulfilled successfully.
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

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Indicates a malformed request body, these can be caused by sending the data encoded in a non-compliant format for that endpoint, missing required parameters, parameters of wrong types or invalid parameter length - usually too large.
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
This status code indicates that you did not properly pass the token in the authorization header, or the provided token is invalid.
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

**Returns a data object of type `ImageObjects`.**

## Data Structures




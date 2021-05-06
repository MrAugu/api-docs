---
description: The one endpoint with image object classification functionality.
---

# Object Classification

{% api-method method="post" host="https://api.mraugu.xyz" path="/images/classify/objects" %}
{% api-method-summary %}
Image Object Classification
{% endapi-method-summary %}

{% api-method-description %}
Recognizes objects from the photo, returning what it found and where on the image it was found, giving you the ability to draw boxes on the images corresponding to the area the object was found in. This endpoint only supports the png image format.
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
    "objects" [
      {
        "name": "person",
        "x": 256.34,
        "y": 120.67,
        "width": 47.23,
        "height": 77.38,
        "score": 89.33
      },
      {
        "name": "person",
        "x": 349.49,
        "y": 285.48,
        "width": 84.63,
        "height": 73.96,
        "score": 94.56
      },
      {
        "name": "person",
        "x": 284.29,
        "y": 178.67,
        "width": 61.66,
        "height": 78.18,
        "score": 88.32
      }
    ],
    "took": 134
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

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}
Indicates that you have either trued to access an endpoint you don't have the user flag for, you've hit the ratelimit ban threshold in which case you must wait before sending requests again or you've .
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

### Example request body:

```text
iVBORw0KGgoAAAANSUhEUgAAAIAAAACACAYAAADDPmHLAAAgAElEQVR4nNWdV68sR9WGq2fGGDDBgDE55
yMyFEiSAgJI8EV3PI7/FOQEBfcGAQIkAAThEUQJhkwweScc/Le0/3pbfUz3+NF9+ynPyWfGkefccWMgNj
Zc/Y5NiWNJnVXV9VatfJa1bXWhlbafe5zn3bVVVe1f//7320Yhtb3/fi64oor2na7bV3Xjd9Xq1Vbr9fj
91yXVz7f+973bk95ylPaNddcM/525ZVXttPT0/H+3JfP6Se/5/q0/LbZbNp973vf8ZqTk5Px+z3ucY/d8
/71r3+1pz3tae3hD394+9nPftZ+/etfj+PMczLmq6++ehxPWu7J/Ywv74wxz87Y8znPyWfGkefccccd43
j+/ve/79bknve85zje/P+f//xn7C+v3J/+aHlm5pn/cm36/dvf/jZel9/8rLyzBvk99/Jf+mS8GUvGRMt
v3J/5p99cD5y4nuvScl2uyX9Zx1tuuaV96lOfapsK/DQmxeIAWCaY31gkJg8SpGVAf/nLX0bg5XMWMgNj
ggww/+c3JpyFSx+5Pu/5LwPPvbk2vwXIj33sY3dj+vrXv96+9rWvtYc85CHt2muvbQ996EPHa/OMe93rX
uPz0w8IywICjCwGi+d5BPmZW/5LXwEWgMl1f/3rX3f3gGg8I88E2YIwbCTWzxuKjZT+83/G/s9//nOHAK
wr9+T/tNz329/+drwnmy6/51mMIX1nHvn/d7/73QjPrO3nP//59sMf/rA94QlPmEcA73oGlAFmEbxruBY      
sBbtZYPrxvbkmr/TBf3kG2JkBs+uz6zKxTrq8cc//nH8HgTKrg8y/O..(17KBs later)..VORK5CYII=
```

**Returns a data object of type `ImageObjects`.**

## Data Structures

> ### `ImageObjects`:

> Represents an image classification response returned by the API.

| Property | Type | Description |
| :--- | :--- | :--- |
| `objects` | `Array[Item]` | An array if items that are predicted to be in the supplied photo. |
| `took` | `Integer` | The amount of time taken by the evaluation. |

> ### `Item`:

> Represents a classified item predicted to be inside an image.

| Property | Type | Description |
| :--- | :--- | :--- |
| `name` | `String` | The name of the item/object recognized. |
| `x` | `Integer` | The x coordinate that represents the horizontal margin of the top right corner. |
| `y` | `Integer` | The y coordinate that represents the vertical margin of the top right corner.  |
| `width` | `Integer` | The width of the box the object is located inside the photo. |
| `height` | `Integer` | The height of the box the object is located inside the photo. |
| `score` | `Float32` | Indicates how likely this object is in the actual photo. \(`<60%` means that the object is unlikely to be in the actual photo. |


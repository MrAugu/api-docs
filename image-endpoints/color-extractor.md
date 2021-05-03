---
description: The one endpoint that offers dominant color extraction functionality.
---

# Color Extractor

> This endpoint requires the default `IMAGES` user permission flag to be active, as described in the [User Flags](../basics/intents.md#what-are-user-flags) section.

{% api-method method="post" host="https://api.mraugu.xyz" path="/images/extract/colors" %}
{% api-method-summary %}
Extracting Dominant Image Colors
{% endapi-method-summary %}

{% api-method-description %}
Extracts the most dominant colors of an image and returns them in a plethora of formats you can chose from, extracts up to 50 different colors. This endpoint only supports the png image format.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="User-Agent" type="string" required=false %}
The user agent associated with the request, can be used to track different requesters in the metrics.
{% endapi-method-parameter %}

{% api-method-parameter name="Authorization" type="string" required=true %}
The authorization header, as described in the authorization section.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="format" type="string" required=false %}
The format in which colors should be returned, defaults to hex. Other formats: css-rgb, css-rgba, rgb-array and rgba-array.
{% endapi-method-parameter %}

{% api-method-parameter name="count" type="number" required=false %}
The amount of colors to extract from the image, up to 50 colors - defaults to 5.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="data" type="string" required=true %}
Image base64 encoded binary, as described in the request section. Maximum size is 5MB.
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
  "message": "Request fufilled.",
  "data": {
    "colors": [
      "#56b9h3",
      "#e1a45b",
      "#c1c1c1",
      "#171717"
    ]
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Indicates a malformed request body, these can be caused by sending the data encoded in a non-compliant data format for that endpoint, missing required parameters, parameters of wrong types or invalid parameter length - usually too large.
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

**Returns a data object of type `ImageColors`.**

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

## Data Structures

> ### `ImageColors`:

> Represents a data object containing the image colors returned by the API.

| Property | Type | Description |
| :--- | :--- | :--- |
| `colors` | `Array[Color]` | An array of colors returned in the specified format. |

> ### `Color`:

> Represents a data object type containing the color in the specified format.

Can be of the type  `String` or the type `Array[Number]`.


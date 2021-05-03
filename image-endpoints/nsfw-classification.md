---
description: The one endpoint that handles Image NSFW Classification.
---

# Nsfw Classification

> These endpoints requires the privileged `IMAGES_NSFW` user permission flag to be active, as described in the [User Flags](../basics/intents.md#what-are-user-flags) section. See information on how to activate privileged flags [here](../basics/intents.md#activating-privileged-flags).

{% api-method method="post" host="https://api.mraugu.xyz" path="/images/classify/nsfw" %}
{% api-method-summary %}
Image NSFW Classifier
{% endapi-method-summary %}

{% api-method-description %}
Analyzes the image and how NSFW the API think the image is amongst a several other categories, using machine learning. This endpoint only supports the png image format.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The API authorization header, as described in the authorization section.
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
Indicates that the request went through and was fulfilled successfully.
{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 200,
  "error": null,
  "message": "Request fulfilled.",
  "data": {
    "predictions": {
      "neutral": 92.97,
      "porn": 6.81,
      "sexy": 0.2,
      "hentai": 0.01,
      "drawing": 0.01
    },
    "took": 183
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Indicates a malformed request body, these can be caused by sending the data encoded in a non-compliant data format for that endpoint, missing required parameters, parameters of wrong types or invalid content length - usually too large.
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

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}
Indicates that you have either tried to access an endpoint you don't have the user flag for, or you've hit the ratelimit ban threshold in which case you must wait before sending requests again.
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

**Returns a data object of type `NsfwClassification`.**

## Data Structures

> ### `NsfwClassification`:

> Represents an image nsfw classification data object returned from the API

| Property | Type | Description |
| :--- | :--- | :--- |
| `predictions` | `NsfwPrediction` | The object containing all of the classes evaluated. |
| `took` | `Integer` | The amount of time taken by the evaluation in milliseconds. |

> ### `NsfwPrediction`:

> Represents a list of image nsfw predictions.

| Property | Type | Description |
| :--- | :--- | :--- |
| `neutral` | `Float32` | Represents how likely is for the image to be neural. |
| `porn` | `Float32` | Represents how likely is for the image to be porn. |
| `sexy` | `Floar32` | Represents how likely is for the image to be sexy. |
| `hentai` | `Float32` | Represents how likely is for the image to be hentai. |
| `drawing` | `Float32` | Represents how likely is for the image to be a drawing. |


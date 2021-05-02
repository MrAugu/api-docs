---
description: The one endpoint that handles Image NSFW Classification.
---

# NSFW Classification

> These endpoints requires the privileged `IMAGES_NSFW` token flag to be active, as described in the [User Flags](../basics/intents.md#what-are-user-flags) section. See information on how to activate privileged flags [here](../basics/intents.md#activating-privileged-flags).

{% api-method method="post" host="https://api.mraugu.xyz" path="/images/classify/nsfw" %}
{% api-method-summary %}
Image NSFW Classifier
{% endapi-method-summary %}

{% api-method-description %}
Analyzes the image and how NSFW the API think the image is amongst a several other categories, using machine learning.
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
The request body should be the image data, in the format described in the request section.
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
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Example of a request body:

```text
data:image/png;iVBORw0KGgoAAAANSUhEUgAAAIAAAACACAYAAADDPmHLAAAgAElEQVR4nNWdV68sR9
WGq2fGGDDBgDE555yMyFEiSAgJI8EV3PI7/FOQEBfcGAQIkAAThEUQJhkwweScc/Le0/3pbfUz3+NF9+y
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




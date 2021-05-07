---
description: Valid data formats that can be consumed by the API.
---

# Requests

## Base URL

The Base URL is the domain where the API server is being hosted, and it's the prefix for every endpoint address, this is a constant that changes only in exceptional situations. 

```text
https://api.mraugu.xyz/
```

{% hint style="info" %}
We impose strict HTTPS connections on all of our servers.
{% endhint %}

## 1. JSON Encoded Data

Most of the API endpoints consume JSON encoded data objects with properties that vastly vary between the API endpoints. Example of a valid JSON object:

```javascript
{
  "query": "I have issues with the car.",
  "choices": [
    "Issues related to the car can be reported at phone +9999 999 999.",
    "Plubming system related issues can be reported at phone +8888 888 888.",
    "We don't handle the issues related to sewage system anymore."
  ]
}
```

## 2. Binary Encoded Data

Some of the endpoints are required to consume binary files \(e.g. image endpoints\), the API accepts base64 encoded binary files as the body of the request. You can read more about base64 [here](https://developer.mozilla.org/en-US/docs/Glossary/Base64). Here is an example of a valid base64 encoded image in the request body:

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


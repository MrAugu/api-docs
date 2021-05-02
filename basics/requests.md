---
description: Valid data formats that can be consumed by the API.
---

# Requests

## The Base Url

The API has a base URL to which endpoints path are attached in order to make requests, the base URL we are using for the API is the following:

```text
https://api.mraugu.xyz/
```

{% hint style="success" %}
We impose strict HTTPS connections on all of our servers.
{% endhint %}

## 1. JSON Encoded Data

Most of the API endpoints consume JSON encoded data objects with properties that vastly vary between the API endpoints. Example of a valid JSON object:

```javascript
/* JSON Object Query Example */
{
  "query": "I have issues with the car.",
  "choices": [
    "Issues related to the car can be reported at phone +9999 999 999.",
    "Plubming system related issues can be reported at phone +8888 888 888.",
    "We don't handle the issues related to sewage system anymore."
  ]
}
```

## 2. Data URL Encoded Data

It is used to send the API binary data such as images or gifs, while the API can consume Data URL encoded data, it **DOES NOT USE THE STANDARD FORMAT** used in browsers. Here is the format for Data URL encoded binaries:

```markup
data:<mediatype>;<data>
```

* `<mediatype>` - Is a file's MIME type such as `image/png` or `image/jpeg`, you can learn more about [MIME types here](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types).
* `<data>` - Is a base64 encoded Uint8 array/binary.


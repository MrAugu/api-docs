---
description: Standard response bodies for the API.
---

# Responses

In order to remain consistent, the interface implements a series of conventions that are used when any response body is being returned. All of the responses from the API are minified JSON \(JavaScript Object Notation\) objects with 3 or 4 properties.

| Property Name | Type | Description |
| :--- | :--- | :--- |
| `statusCode` | Number | The HTTP status code representing the state of the response, you can find more details about http status code at the [Mozilla Web Docs](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status). |
| `error` | String\* | If the HTTP status code is different than `2xx` \(in which case is always `null`\) it will be the error in the request that made the server unable to fulfill it. |
| `message` | String | It's the message describing the status of the request, although it does not follow any specific conventions, on successful requests the message is usually `Request fulfilled.` and when the request is not successful, it will contain the specific reason the request was not fulfilled.  |
| `data` | Object\* | If the request was fulfilled, the data returned will always be contained within this object and its contents vary from endpoint to endpoint. |

Exceptions to always receiving the standard format responses are the timeframes where the API server instances are down or there is an ongoing maintenance. To be able to view real time status, [join our discord server.](https://discord.gg/rk7cVyk)


---
description: Details about API ratelimits.
---

# Ratelimits

## Ratelimiting Specification

In order to maintain our service viable and secure, we impose very strict rate limiting rules for our users. The reset timeframe for the ratelimits is `60 seconds` or `1 minute`, by default all of the users have a default cap of `48 requests` per timeframe, after exceeding this quota - all of the requests to the API will be declined with a [429 Too Many Requests](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/429) error response.

{% hint style="warning" %}
Is important to note that we have implemented security precaution that also limits the amount of [429 Too Many Requests](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/429) errors you can receive - after `50 requests` that resulted in a 429 http status code you will be automatically banned for an undisclosed amount of time, further requests failing in a [403 Forbidden](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/403) response code until the ban expires. 
{% endhint %}

## Ratelimiting headers used

| Header Name | Value Type | Description |
| :--- | :--- | :--- |
| `X-Ratelimit-Limit` | Number | The amount of requests a client can make to the API in the reset timeframe before hitting any ratelimits. |
| `X-Ratelimit-Remaining`                      | Number | The amount of requests a client can make in the current timeframe before hitting any ratelimits. |
| `X-Ratelimit-Reset`  | Number | The amount of seconds left in the current timeframe before the ratelimit counter resets.  |
| `X-Retry-After` | Number | After the ratelimit has been hit, it indicates the amount of seconds the client should wait before making further requests to the API. |




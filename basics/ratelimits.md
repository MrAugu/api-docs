---
description: Details about API ratelimits.
---

# Ratelimits

{% hint style="info" %}
This page is scheduled for a rewrite.
{% endhint %}

## Ratelimiting Specification

In order to maintain our service always online and secure for everybody - we impose very strict rate limiting rules for our users. The reset timeframe for the ratelimits is `60 seconds` and by default all of the users have a default cap of `48 requests` they can send in the span of a timeframe. After exceeding this quota all of the requests to the API will be declined with a [429 Too Many Requests](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/429) error response.

{% hint style="danger" %}
Is important to note that the amount of [429 Too Many Requests](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/429) errors you can receive is limited - after `50 requests` that resulted in a 429 HTTP status code you will be automatically banned temporary, while banned any requests will be declined by server with the [403 Forbidden](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/403) response code until the ban expires. 
{% endhint %}

## Ratelimiting headers used

We use a series of _standard_ request headers to let the clients know how close they are to hitting the ratelimit or how much time they have left before the ratelimit gets .

| Header Name | Value Type | Description |
| :--- | :--- | :--- |
| `X-Ratelimit-Limit` | Number | The amount of requests a client can make to the API in the reset timeframe before hitting any ratelimits. |
| `X-Ratelimit-Remaining`                      | Number | The amount of requests a client can make in the current timeframe before hitting any ratelimits. |
| `X-Ratelimit-Reset`  | Number | The amount of seconds left in the current timeframe before the ratelimit counter resets.  |
| `X-Retry-After` | Number | After the ratelimit has been hit, it indicates the amount of seconds the client should wait before making further requests to the API. |

{% hint style="warning" %}
While the API is in not published as a stable version, these specifications are subject to change. The minimal changes that will occur are the seconds being changed to milliseconds for more precision. 
{% endhint %}

## Calculating the request quota & raising it

To count the amount of requests any given user can make in the timeframe before hitting any ratelimit we use the following formula:

```text
RequestsPerSecond = RatelimitQuotaCoefficient * SecondsInAMinute
RequestsPerSecond = QuotaCoeficient * 60
```

Ratelimits are calculated on a per-user basis, where every user has a `QuotaCoefficient` which can be accessed via the session details endpoint as the `ratelimit` property in the data payload. By default the quota coefficient for every new user is `0.8` \(`0.8 * 60 = 48` - this is where the default ratelimit comes from\).

If you wish to increase this ratelimit please join our [Official Discord Server](https://discord.gg/rk7cVyk) and contact \(an administrator\) MrAugu\#7917 or ◢◤Myst◢◤\#4217 with the reason why and the use case you want to increase this ratelimit, any increase of the `QuotaCoefficient` beyond `1.4` requires you to present us with an application or a project and in future billing will be required.


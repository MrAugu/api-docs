---
description: >-
  What are token flags and how we use them to control the access to certain
  endpoints and features of an endpoint.
---

# Token Flags

Token flags are API's way of handling user access to different endpoints or access to different requests options, some of the token flags are enabled by default while others must be granted by an administrator, any abuse of the API will lead to a permanent ban from the service. You can see your intents via the `$intents view` command or via the session details endpoint where the flags are stored as a bitfield as described below:

|  Intent Name | Value | Type | Description |
| :--- | :--- | :--- | :--- |
| TEXT | `0x0000000001` `(1 << 0)` | Default | Indicates whether the user has access to the basic text endpoints. |
| TEXT\_SIMIARITY | `0x0000000002` `(1 << 1)` | Granted | Indicates whether the user has access text similarity analysis endpoints. |
| IMAGES | `0x0000000004` `(1 << 2)` | Default | Indicated whether the user has access to the basic image endpoints. |
| IMAGES\_NSFW | `0x0000000008` `(1 << 3)` | Granted | Indicates whether the user has access to the image nsfw content analysis endpoint. |
| IMAGES\_OBJECTS | `0x0000000010` `(1 << 4)` | Granted | Indicates whether the user has access to image objects content analysis endpoint.  |
| ~~TEXT\_EVALUATION \(N/A yet\)~~ | `0x0000000020` `(1 << 5)` | Granted | Indicates whether the user has access to the text content analysis endpoint.  |
| ~~BANNED \(N/A yet\)~~ | `0x0000000040` `(1 << 6)` | Granted | Indicates whether the user is banned, all requests from a token with this flag will return a HTTP [403 Forbidden](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/403). |
| ~~INFORMATION \(N/A yet\)~~ | `0x0000000080` `(1 << 7)` | Default | Indicates whether the user has access to the information related endpoints. |

While some intents are on by default, to get access to a specific intent you need to join the [official discord server ](https://discord.gg/rk7cVyk)and hit MrAugu\#7917 or ◢◤Myst◢◤\#4217 with your use case you have for wanting this flag enabled for you, if we deem your use case reasonable we'll grant it to you in no time.


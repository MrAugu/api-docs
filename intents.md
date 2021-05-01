---
description: What are intents and how to use them to access our API.
---

# Intents

Intents are API's way of handling user access to different routes, some of the intents are enabled by default, others must be granted by the API's administrators to you, and if abused - revoked, you can see your intents via the `$intents view` command \(or via the token details endpoint as a bitfield\).

| Intent Name | Value | Type |
| :--- | :--- | :--- |
| TEXT | `0x0000000001` `(1 << 0)` | Default |
| TEXT\_SIMIARITY | `0x0000000002` `(1 << 1)` | Granted |
| IMAGES | `0x0000000004` `(1 << 2)` | Default |
| IMAGES\_NSFW | `0x0000000008` `(1 << 3)` | Granted |
| IMAGES\_OBJECTS | `0x0000000010` `(1 << 4)` | Granted |

To get access to a specific intent, you have to join the [official discord server ](https://discord.gg/rk7cVyk)and hit MrAugu\#7917 or ◢◤Myst◢◤\#4217 with the reason/use case you have for wanting this intent enabled for you - and if we deem your use case reasonable we'll grant it to you in no time.


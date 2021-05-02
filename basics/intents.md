---
description: >-
  What are user flags and how we use them to control and limit the users access
  to certain endpoints.
---

# User Flags

User flags are a series of boolean values stored inside a flag bitfield inside the database. Every user access token has a series of flags enabled - some of them come active by default - and the rest of them are considered privileged flags and therefore require admin activation before you are able to access the API endpoints specific to that flag. Flags are also used to store things like whether the token can access _experimental_  endpoints or whether the user is banned from using the API altogether. You can view your token's flags using the `$flags` command or calculate them from the bitfield provided in the session details endpoint.

|  Intent Name | Value | Type |
| :--- | :--- | :--- |
| `TEXT` | `0x1` `(1 << 0)` | Default |
| `TEXT_SIMIARITY` | `0x2` `(1 << 1)` | Granted |
| `IMAGES` | `0x4` `(1 << 2)` | Default |
| `IMAGES_NSFW` | `0x8` `(1 << 3)` | Granted |
| `IMAGES_OBJECTS` | `0x10` `(1 << 4)` | Granted |
| `TEXT_EVALUATION` | `0x20` `(1 << 5)` | Granted |
| `BANNED` | `0x40` `(1 << 6)` | Granted |
| `INFORMATION` | `0x80` `(1 << 7)` | Default |
| `EXPERIMENTAL` | `0x100` `(1 << 8)` | Granted |

Although some flags are active by default - to get access to a specific intent you need to join the [official discord server ](https://discord.gg/rk7cVyk)and send MrAugu\#7917 or ◢◤Myst◢◤\#4217 a direct message with your use case or reason you have for wanting this flag enabled for you, if we deem it reasonable we'll grant it to you in no time.


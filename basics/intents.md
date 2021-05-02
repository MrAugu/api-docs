---
description: >-
  What are user flags and how we use them to control and limit the users access
  to certain endpoints.
---

# User Flags

## What are user flags

User flags are a series of boolean values stored inside a flag bitfield stored in the database, they can be of 2 types: a\) permission flags - they grant access to certain endpoints; b\) state flags - they are used to track a user's state \(such as checking whether they are banned\). Every user access token has a series of permission flags which dictate which endpoints the user with that token can access. Some of the permission flags come active out-of-the-box allowing you to make requests to those endpoints as soon as you get your hands on the shiny authorization token - and others are activated for you by an API administrator. The activation process is fairly simple - first you need to join our server linked [here](../#still-need-some-help), then you have to proceed by DMing an API admin telling them what permission flag you wish to be enabled and **why**, there are no wrong answers - we just want to know what you're using our API for. You can view your token's flags using the `$flags` command or calculate them yourself from the bitfield provided in the session details endpoint.

|  Intent Name | Value | Type | Kind |
| :--- | :--- | :--- | :--- |
| `TEXT` | `0x1` `(1 << 0)` | Default | Permission |
| `TEXT_SIMIARITY` | `0x2` `(1 << 1)` | Granted | Permission |
| `IMAGES` | `0x4` `(1 << 2)` | Default | Permission |
| `IMAGES_NSFW` | `0x8` `(1 << 3)` | Granted | Permission |
| `IMAGES_OBJECTS` | `0x10` `(1 << 4)` | Granted | Permission |
| `eTEXT_EVALUATION` | `0x20` `(1 << 5)` | Granted | Permission |
| `BANNED` | `0x40` `(1 << 6)` | Granted | State |
| `INFORMATION` | `0x80` `(1 << 7)` | Default | Permission |
| `EXPERIMENTAL` | `0x100` `(1 << 8)` | Granted | Permission |

## Activating privileged flags

Although some permission flags are active by default - to get access to a specific permission flag you need to join the [official discord server ](https://discord.gg/rk7cVyk)and send MrAugu\#7917 or ◢◤Myst◢◤\#4217 a direct message with your use case or reason you have for wanting a specific permission flag enabled for you, if we deem it reasonable we'll grant it to you in no time.


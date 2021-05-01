---
description: How to authenticate yourself in order to use the API.
---

# Authorization

The authorization to the application programing interface is done via a bearer token that is passed in as a header of **every request** that is being sent to the API.

```text
Authorization: Bearer <token goes in here>
```

## Obtaining the API Token

The tokens can be obtained from the [Help Tavern Discord Server](https://discord.gg/rk7cVyk)'s discord bot called "Tavern Guard" by using the `$token generate` command in one of the designated channels for bot use.

![Generating Token](.gitbook/assets/image%20%283%29.png)

To view your token, use `$token view` command, and you will receive a direct message from the bot like the one below, containing for API key.

![Token In Direct Messages](.gitbook/assets/image%20%285%29.png)

However for security and safety reasons you have **30 seconds** to view your token in the direct messages before the token gets blurred out. If you token gets compromised you can reset it anytime with the `$token regenerate` command.

{% hint style="info" %}
If it isn't obvious by now, the token in the image has been regenerated and is no longer valid to use.
{% endhint %}


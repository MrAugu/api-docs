---
description: Properly authenticating the requests.
---

# Authorization

The authorization to the API is done via a bearer access token that is passed as a header in **every request** that is being sent to the API by the client. Here is an example of a valid authorization header:

```text
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.MzY3MzAyNTkzNzUzNjQ1MDU3OjE2MTk3ODIzMDA2NjQ.SODrMYULKU9tb8RTzRQpzIzh5UEXaH2v1pZiEbal7i8     
```

## Obtaining an access token

The API access tokens can be obtained from the [Help Tavern Discord Server](https://discord.gg/rk7cVyk)'s through the server's discord bot called Tavern Guard, by using the `$token generate` command, in one of the channels designated for related bot commands.

![Generating an API token](../.gitbook/assets/image%20%286%29%20%283%29.png)

In order to view your access token, use the `$token view` command, and you will receive a direct message from the bot like the one below, containing the API key.

![Viewing an API token in the DMs](../.gitbook/assets/image%20%287%29%20%282%29.png)

However, for security and safety reasons you have only **30 seconds** to grab your access token in the direct messages before the token gets blurred out. And if your token ever gets compromised, you can reset it anytime with the `$token regenerate` command.

{% hint style="info" %}
If it isn't obvious by now, the token in the image has been regenerated and is no longer valid to use.
{% endhint %}




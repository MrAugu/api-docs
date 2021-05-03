---
description: The one endpoint that offers dominant color extraction functionality.
---

# Color Extractor

> This endpoint requires the default `IMAGES` user permission flag to be active, as described in the [User Flags](../basics/intents.md#what-are-user-flags) section.

{% api-method method="post" host="https://api.mraugu.xyz" path="/images/extract/colors" %}
{% api-method-summary %}
Extracting Dominant Image Colors
{% endapi-method-summary %}

{% api-method-description %}
Extracts the most dominant colors of an image and returns them in a plethora of formats you can chose from, extracts up to 50 different colors. This endpoint only supports the png image format.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The authorization header, as described in the authorization section.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="format" type="string" required=false %}
The format in which colors should be returned, defaults to hex. Other formats: css-rgb, css-rgba, rgb-array and rgba-array.
{% endapi-method-parameter %}

{% api-method-parameter name="count" type="number" required=false %}
The amount of colors to extract from the image, up to 50 colors - defaults to 5.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="data" type="string" required=true %}
Image base64 encoded binary, as described in the request section. Maximum size is 5MB.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}


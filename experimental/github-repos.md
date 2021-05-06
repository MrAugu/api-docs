---
description: The one endpoint with GitHub repository information retrieval functionality.
---

# GitHub Repos

{% hint style="warning" %}
This endpoint is experimental, and required the `EXPERIMENTAL` privileged user flag to be active, as described in the [User Flags](../basics/intents.md#what-are-user-flags) section.
{% endhint %}

{% hint style="danger" %}
This endpoint is experimental and can only be accessed by the developers and other privileged people - and we do not recommend the usage of any experimental endpoints in production environments, this should be used as a reference to let library developers to prepare for this addition - or the developers for adding it in their staging versions of projects ready to go live when the endpoint is removed the `EXPERIMENTAL`flag.
{% endhint %}

> These endpoints requires the privileged `INFORMATION_GITHUB` user permission flag to be active, as described in the [User Flags](../basics/intents.md#what-are-user-flags) section. See information on how to activate privileged flags [here](../basics/intents.md#activating-privileged-flags).

{% api-method method="get" host="https://api.mraugu.xyz" path="/information/github/repository" %}
{% api-method-summary %}
Fetch Repository Information
{% endapi-method-summary %}

{% api-method-description %}
Fetches a repository's information from the GitHub's REST API.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
The authorization header, as described in the authorization section.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="owner" type="string" required=true %}
The name of the user or organization owning this repository.
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=true %}
The name of the repository.
{% endapi-method-parameter %}

{% api-method-parameter name="forks" type="boolean" required=false %}
Whether to fetch the repositories that have been forked from this repository.
{% endapi-method-parameter %}

{% api-method-parameter name="tags" type="boolean" required=false %}
Whether to fetch the repository's tags or releases.
{% endapi-method-parameter %}

{% api-method-parameter name="languages" type="boolean" required=false %}
Whether to fetch the programing languages that are being used in the repository and their respective usage percent
{% endapi-method-parameter %}

{% api-method-parameter name="stargazers" type="boolean" required=false %}
Whether to fetch the repository's stargazers.
{% endapi-method-parameter %}

{% api-method-parameter name="contributors" type="boolean" required=false %}
Whether to fetch the repository's contributors.
{% endapi-method-parameter %}

{% api-method-parameter name="commits" type="boolean" required=false %}
Whether to fetch the repository's commits.
{% endapi-method-parameter %}

{% api-method-parameter name="issues" type="boolean" required=false %}
Whether to fetch the repository's open issues and pull requests.
{% endapi-method-parameter %}

{% api-method-parameter name="labels" type="boolean" required=false %}
Whether to fetch the repository's labels.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
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


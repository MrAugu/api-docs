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
This indicates that the request went through and was fulfilled successfully.
{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 200,
  "error": null,
  "message": "Request fulfileld",
  "data": {
    "exists": true,
    "repository": {
      "id": 259904118,
      "nodeId": "MDEwOlJlcG9zaXRvcnkyNTk5MDQxMTg=",
      "fullName": "ModCord/message-parser",
      "owner": {
        "name": "ModCord",
        "id": 64532228,
        "avatar": "https://avatars.githubusercontent.com/u/64532228?v=4",
        "url": "https://github.com/ModCord",
        "githubAdmin": false,
        "type": "Organization"
      },
      "url": "https://github.com/ModCord/message-parser",
      "description": "A message parser for discord using regular expressions and string manipulation.",
      "createdAt": "2020-04-29T11:15:34.000Z",
      "lastUpdatedAt": "2021-04-11T13:38:57.000Z",
      "lastPushedAt": "2021-04-11T13:38:55.000Z",
      "size": 99,
      "stargazerCount": 1,
      "watcherCount": 1,
      "language": "TypeScript",
      "forkCount": 0,
      "openIssuesCount": 0,
      "archived": false,
      "defaultBranch": "master",
      "forks": [
        {
          "id": 361958684,
          "nodeId": "MDEwOlJlcG9zaXRvcnkzNjE5NTg2ODQ=",
          "owner": {
            "name": "felicisimo0913",
            "id": 33395332,
            "nodeId": "MDQ6VXNlcjMzMzk1MzMy",
            "avatar": "https://avatars.githubusercontent.com/u/33395332?v=4",
            "url": "https://github.com/felicisimo0913",
            "type": "User"
          },
          "url": "https://github.com/felicisimo0913/discord-xp",
          "description": "A lightweight and easy to use economy framework for discord bots, uses MongoDB.",
          "createdAt": "2021-04-27T02:42:35.000Z",
          "lastUpdatedAt": "2021-04-27T02:42:36.000Z",
          "lastPushedAt": "2021-04-21T08:28:50.000Z",
          "size": 639,
          "stargazerCount": 0,
          "watcherCount": 0,
          "forkCount": 0,
          "openIssuesCount": 0,
          "archived": false,
          "defaultBranch": "master"
        }
      ],
      "tags": [
        {
          "name": "v1.1.11",
          "zipSource": "https://api.github.com/repos/MrAugu/discord-xp/zipball/refs/tags/v1.1.11",
          "tarSource": "https://api.github.com/repos/MrAugu/discord-xp/tarball/refs/tags/v1.1.11",
          "commitSha": "b4b0409f8ed28427b88bb393743b69e32962e6db",
          "commitUrl": "https://api.github.com/repos/MrAugu/discord-xp/commits/b4b0409f8ed28427b88bb393743b69e32962e6db",
          "nodeId": "MDM6UmVmMjExMzAwMDcxOnJlZnMvdGFncy92MS4xLjEx"
        }
      ],
      "languages": [
        {
          "name": "TypeScript",
          "amount": 100
        }
      ],
      "stargazers": [
        {
          "name": "DieselGaming",
          "id": 44411085,
          "nodeId": "MDQ6VXNlcjQ0NDExMDg1",
          "avatar": "https://avatars.githubusercontent.com/u/44411085?v=4",
          "url": "https://github.com/DieselGaming",
          "type": "User"
        }
      ],
      "contributors": [
        {
          "name": "MrAugu",
          "id": 39545629,
          "nodeId": "MDQ6VXNlcjM5NTQ1NjI5",
          "avatar": "https://avatars.githubusercontent.com/u/39545629?v=4",
          "url": "https://github.com/MrAugu",
          "type": "User",
          "contributions": 29
        }
      ],
      "commits": [
        {
          "author": {
            "name": "Myst82015",
            "id": 34489470,
            "nodeId": "MDQ6VXNlcjM0NDg5NDcw",
            "avatar": "https://avatars.githubusercontent.com/u/34489470?v=4",
            "url": "https://github.com/Myst82015",
            "type": "User",
            "email": "midnight-_-@outlook.com"
          },
          "nodeId": "MDY6Q29tbWl0MjExMzAwMDcxOmMyNzhlYWE5YWEzMzMyYWM0ODMxMTkwMGQwODRjZjI3Yzk5MWFkMzQ=",
          "sha": "c278eaa9aa3332ac48311900d084cf27c991ad34",
          "message": "Update README.md\n\nRemoved a typo",
          "commentCount": 0
        }
      ],
      "issues": [
        {
          "url": "https://github.com/MrAugu/discord-xp/issues/31",
          "id": 849630108,
          "nodeId": "MDU6SXNzdWU4NDk2MzAxMDg=",
          "number": 31,
          "title": "Accepting Suggestions",
          "labels": [
            {
              "id": 1581595688,
              "nodeId": "MDU6TGFiZWwxNTgxNTk1Njg4",
              "url": "https://api.github.com/repos/MrAugu/discord-xp/labels/enhancement",
              "name": "enhancement",
              "color": "a2eeef",
              "default": true,
              "description": "New feature or request"
            }
          ],
          "state": "open",
          "locked": false,
          "body": "Is there anything you would like to see added to `discord-xp` module? If yes, then state any suggestions in this issue.",
          "assignees": [
            {
              "name": "MrAugu",
              "id": 39545629,
              "nodeId": "MDQ6VXNlcjM5NTQ1NjI5",
              "avatar": "https://avatars.githubusercontent.com/u/39545629?v=4",
              "url": "https://github.com/MrAugu",
              "type": "User"
            }
          ]
        }
      ],
      "pulls": [
        {
          "url": "https://github.com/MrAugu/discord-xp/pull/34",
          "id": 856782285,
          "nodeId": "MDExOlB1bGxSZXF1ZXN0NjE0MzA3NTYy",
          "number": 34,
          "title": "Discord Xp Version 2.0.0",
          "labels": [
            {
              "id": 2911132935,
              "nodeId": "MDU6TGFiZWwyOTExMTMyOTM1",
              "url": "https://api.github.com/repos/MrAugu/discord-xp/labels/being%20worked%20on",
              "name": "being worked on",
              "color": "674DD4",
              "default": false,
              "description": ""
            }
          ],
          "state": "open",
          "locked": false,
          "body": "The pull request tracking the progress to discord-xp version 2.",
          "assignees": [
            {
              "name": "MrAugu",
              "id": 39545629,
              "nodeId": "MDQ6VXNlcjM5NTQ1NjI5",
              "avatar": "https://avatars.githubusercontent.com/u/39545629?v=4",
              "url": "https://github.com/MrAugu",
              "type": "User"
            }
          ]
        }
      ],
      "label": [
        {
          "id": 1581595690,
          "nodeId": "MDU6TGFiZWwxNTgxNTk1Njkw",
          "url": "https://api.github.com/repos/MrAugu/discord-xp/labels/good%20first%20issue",
          "name": "good first issue",
          "color": "7057ff",
          "default": true,
          "description": "Good for newcomers"
        }
      ]
    }
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Indicates a malformed request body, these can be caused by sending the data encoded in a non-compliant data format for that endpoint, missing required parameters, parameters of wrong types of invalid length - usually too large.
{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 400,
  "error": "Bad request",
  "message": "Invalid request body."
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
This status code indicates that you did not properly pass the token in the authorization header, or the token is invalid \(it does not exist/was regenerated\).
{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 401,
  "error": "Unauthorized",
  "message": "You are not authorized."
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}
Indicates that you have either tried to access an endpoint you don't have the permission user flag for, you've hit the ratelimit ban threshold in which case you must wait before sending requests again or you have been banned from using the API.
{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 403,
  "error": "Forbidden",
  "message": "You do not have the flag required to access this endpoint. Please refer to the documentation at https://docs.mraugu.xyz/ for more information."   
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

**Returns a `RepositoryData` data object.**

## Data Structures

> ### `RepositoryData`:

> Represents a structure returned by the GitHub Repo Information fetch API.

| Property | Type | Description |
| :--- | :--- | :--- |
| `exists` | `Boolean` | Whether or not the GitHub repository exists or not on GitHub. |
| `repository` | `Repository` | The data for the repository. |

> ### `Repository`

> Represents a repository's GitHub public information.

| Property | Type | Description |
| :--- | :--- | :--- |
| `id` | `Integer` | A repository's GitHub ID. |
| `nodeId` | `String` | The GitHub internal node id for the repository. |
| `fullName` | `String` | The full name for the repository \(in the Owner/Name format\). |
| `owner` | `PatialUser` | The user or organization owning this repository. |
| `url` | `String` | The URL leading to the repository's public GitHub page. |
| `description` | `String` | This repository's description. |
| `createdAt` | `Date` | The date and time this repository was created at. |
| `lastUpdatedAt` | `Date` | The date end time this repository was last updated at. |
| `lastPushedAt` | `Date` | The date and time when the last commit was pushed to this repository. |
| `size` | `Integer` | The size of the repository, in KB. \(?\) |
| `stargazerCount` | `Integer` | The amount of GitHub stars/stargazers this repository has. |
| `watcherCount` | `Integer` | The amount of people watching this repository's activity. |
| `language` | `?String` | The name of the programing language most used in the repository. |
| `forkCount` | `Integer` | The amount of repositories forked from this repository. |
| `openIssuesCount` | `Integer` | The total amount of issues and pull requests open in this repository. |
| `archived` | `Boolean` | Whether this repository was archived by the owner and now is read only. |
| `defaultBranch` | `String` | The name of the repository's main branch. |
| `forks` | `PartialRepository[]` | The list of repositories that have been forked from this repository. This will always be an empty array if the forks query parameter isn't set to true.   |
| `tags` | `Release[]` | A list of releases of this repository. This will always be an empty array if the tags query parameter isn't set to true. |
| `languages` | `ProgramingLang[]` | A list of programing languages used in this repository and their % of how much they represent of the total languages. This will always return an empty array if the languages query parameter isn't set to true. |
| `stargazers` | `PartialUser[]` | A list of stargazers/people who have starred this repository. This will always return an empty array if the stargazers query parameter isn't set to true. |
| `contributors` | `Contributor[]` |  A list of people who have contributed to this repository. This will always return an empty array if contributors query parameter isn't set to true. |
| `commits` | `Commit[]` | A list of commits that have been pushed to this repository. This will always return empty if the commits query parameter isn't set to true. |
| `issues` | `Issues[]` | A list of issues open in this repository. This will always return empty if the issues query parameter isn't set to true. |
| `pulls` | `Issues[]` | A list  of pull requests open in this repository. This will always return empty if the issues query parameter isn't set to true. |
| `labels` | `Labels[]` | A list of labels this repository has. This will always return empty if the labels query parameter isn't set to true. |

> ### `PartialUser`:

> Represents a GitHub user or organization object with partial public properties.

| Property | Type | Description |
| :--- | :--- | :--- |
| `name` | `String` | The name of the user or organization. |
| `id` | `Integer` | The GitHub id of the user or organization. |
| `nodeId` | `String` | GitHub's internal node id for this user or organization. |
| `avatar` | `String` | A link to user's or organization's GitHub avatar. |
| `url` | `String` | A link to user's or organization's public GitHub page. |
| `type` | `String` | The type of structure, can be 'User' or 'Organization'. |

> ### `PartialRepository`:

> A repository object with partial properties.

| Property | Type | Description |
| :--- | :--- | :--- |
| `id` | `Integer` | A repository's GitHub ID. |
| `nodeId` | `String` | The GitHub internal node id for the repository. |
| `owner` | `PartialUser` | The user or organization owning this repository. |
| `url` | `String` | The URL leading to the repository's public GitHub page. |
| `description` | `String` | This repository's description. |
| `createdAt` | `Date` | The date and time this repository was created at. |
| `lastUpdatedAt` | `Date` | The date end time this repository was last updated at. |
| `lastPushedAt` | `Date` | The date and time when the last commit was pushed to this repository. |
| `size` | `Integer` | The size of the repository, in KB. \(?\) |
| `stargazerCount` | `Integer` | The amount of GitHub stars/stargazers this repository has. |
| `watcherCount` | `Integer` | The amount of people watching this repository's activity. |
| `forkCount` | `Integer` | The amount of repositories forked from this repository. |
| `openIssuesCount` | `Integer` | The total amount of issues and pull requests open in this repository. |
| `archived` | `Boolean` | Whether this repository was archived by the owner and now is read only. |
| `defaultBranch` | `String` | The name of the repository's main branch. |

> ### `Release`:

> Represents a GitHub release.

| Property | Type | Description |
| :--- | :--- | :--- |
| `name` | `String` | The name of the release. |
| `zipSource` | `String` | The link to the zip release file download. |
| `tarSource` | `String` | The link to the tar release file download. |
| `commitSha` | `String` | The SHA-1 git signature for the commit.  |
| `commitUrl` | `String` | The URL leading to the commit's page. |
| `nodeId` | `String` | GitHub's internal commit for this release. |

> ### `ProgramingLang`:

> Represents a programing language used.

| Property | Type | Description |
| :--- | :--- | :--- |
| `name` | `String` | The name of the programing language used. |
| `amount` | `Float64` | The percent of this programing language used out of the total programing languages used. |

> ### `Contributor` extends `PartialUser`:

> Represent a contributor, inherits all the properties from the `PartialUser` structure.

| Property | Type | Description |
| :--- | :--- | :--- |
| `contributions` | `Integer` | The amount of commits or contributions this used made in this GitHub repository. |

> `Commit`:

> Represents a GitHub commit.

| Property | Type | Description |
| :--- | :--- | :--- |
| `author` | `CommitAuthor` | The GitHub user that authored this commit. |
| `nodeId` | `String` | The GitHub internal node id for this commit. |
| `message` | `String` | The message that was specified by the user that pushed this request. |
| `commentCount` | `Integer` | The amount of comments on this commit. |

> ### `CommitAuthor` extends `PartialUser`:

> An user that authored a commit.

| Property | Type | Description |
| :--- | :--- | :--- |
| `email` | `?String` | The email of the user that authored this commit. |

> ### `Issue`:

> Represents an issue or pull request.

| Property | Type | Description |
| :--- | :--- | :--- |
| `url` | `String` | The link that leads to the page of this issue. |
| `id` | `Integer` | The GitHub id for this issue. |
| `nodeId` | `String` | GitHub's internal node id for this issue. |
| `number` | `Integer` | The unique issue number for this issue in this repository. |
| `title` | `String` | The title of this issue or pull request. |
| `labels` | `Label[]` | A list of labels assigned to this issue or pull request. |
| `state` | `String` | The state of this issue, "open", "closed" or "merged". \(?\) |
| `locked` | `Boolean` | Whether this issue is locked. |
| `body` | `String` | The contents of this issue or pull request, in markdown syntax. |
| `assignees` | `PartialUser[]` | A list of users or organizations assigned to this issue or pull request. |

> ### `Label`:

> Represents a GitHub label in a certain repository.

| Property | Type | Description |
| :--- | :--- | :--- |
| `id` | `Integer` | The GitHub id for this label. |
| `nodeId` | `String` | GitHub's internal node id for this label. |
| `url` | `String` | The URL leading to label's GitHub page. |
| `name` | `String` | The name of this label. |
| `color` | `String` | The hex color for this label. |
| `default` | `Boolean` | Whether this label was created by GitHub by default on the repository creation. |
| `description` | `?String` | The description for this label. |


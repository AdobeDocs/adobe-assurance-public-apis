---
title: Overview - Adobe Assurance API
description: Service which provides GraphQL endpoints for Experience Cloud Assurance Tools.
contributors:
  - https://github.com/coljtob 
---

<Hero slots="heading, text"/> 

# Adobe Assurance API

Service which provides GraphQL endpoints for Experience Cloud Assurance Tools.

<Resources slots="heading, links"/>

#### Resources

* [Adobe Experience Platform Assurance](https://aep-sdks.gitbook.io/docs/assurance/project-griffon)

## Overview

This documentation provides instructions for Adobe Assurance 1.0 APIs. For working with Adobe Experience Platform Assurance, see [refer here](https://aep-sdks.gitbook.io/docs/assurance/project-griffon).

The Adobe Assurance APIs are a collection of APIs that empower users to test and debug their mobiles apps, when outfitted with the Adobe Assurance Mobile SDK. 
When enabled, the user of these APIs will be able to:

- create, read, and delete sessions
- read events
- read event annotations
- read session annotations

The guide will demonstrate how you can utilize Adobe Assurance APIs to programmatically connect your Adobe Assurance enabled mobile application to our back end services to help you develop and debug your application.

In order to make requests into Assurance API, you must create a JSON Web Token (JWT) within the Adobe Developer Console. For further information on use of JWT, you can view helpful docs and explanations [here](https://jwt.io/).

## Granting Access
Within the [Admin Console](https://adminconsole.adobe.com/), Administrators will have to add new "Developers", and grant each access to "Adobe Experience Platform". With such access, those developers can create other "Projects" within your organization and add "Adobe Assurance API" to those projects.

## Creating A Project
If you do not already have a project defined in your organization, go ahead and create one "Create new project".

![](guides/session_api/create_project.png)

## Adding Adobe Assurance API

Within your project home page, click "Addd API", filter by "Adobe Experience Platform", and click "Assurance".

![](guides/session_api/add_api.png)
![](guides/session_api/product_filter.png)
![](guides/session_api/assurance_api_plugin.png)

## Public-Private Key Pairs
You will be prompted to generate or upload a public/private key pair. Choose "Generate Key Pair".

![](guides/session_api/jwt_account.png)
![](guides/session_api/generate_keypair.png)

A zip file will be generated and downloaded to your computer. Expand the zip file and copy the entire contents of "private.key" to your clipboard.

Click "Next".
Choose applicable Product Profile if requested.
Click "Save configured" API.

## Generating a JWT (JSON Web Token)

Now with you project defined, and associated with Assurance API, with a public/private key pair, you can generate a JWT.

These JSON Web Tokens can be generated within this UI, or using [several tools/libraries](https://jwt.io/libraries).

Paste the entire contents of your private key that was downloaded in an earlier step into the "Private key" text box.

![](guides/session_api/paste_key.png)

## Status Check

Now you should have created/defined:

An access token generated from your unique JSON Web Token
- Client ID
- Client Secret
- Technical Account ID
- Technical Account Email
- Organization ID

## Regenerating JWT-exchanged Access Tokens
To regenerate an access token, within your project, you can always click on "Credentials / Service Account (JWT)".

Click on "Generate JWT" tab, again paste your private key in the available text box, and choose "Generate Token".

In this flow, instead of being presented a ready-to-use access token, you will be presented with your actual JSON Web Token, and a sample cURL command to use that JWT in exchange for an access token.

![](guides/session_api/regenerate.png)

Copy and paste the cURL command into your terminal and execute.

An access token will be returned in your terminal window with an expiration. (check this--24 hours?).

## Try the API 

### Read Sessions:

curl 'http://[adobe.io url]/graffias/graphql' -H 'Accept-Encoding: gzip, deflate, br' -H 'Content-Type: application/json' -H 'Accept: application/json' -H 'Connection: keep-alive' -H 'DNT: 1' -H 'Origin: file://' -H 'x-gw-ims-org-id: [Organization ID]@AdobeOrg' -H 'x-gw-ims-user-id: [tech account ID]@techacct.adobe.com' -H 'x-api-key: [Client ID]' -H 'Authorization: Bearer [Access Token]' --data-binary '{"query":"query {\n  sessions {\n   \tname\n    uuid\n  }\n}"}' --compressed

### Create a Session:

curl 'http://[adobe.io url]/graffias/graphql' -H 'Accept-Encoding: gzip, deflate, br' -H 'Content-Type: application/json' -H 'Accept: application/json' -H 'Connection: keep-alive' -H 'DNT: 1' -H 'Origin: file://' -H 'x-gw-ims-org-id: [Organization ID]@AdobeOrg' -H 'x-gw-ims-user-id: [tech account ID]@techacct.adobe.com' -H 'x-api-key: [Client ID]' -H 'Authorization: Bearer [Access Token]' --data-binary  '{"query":"mutation name($session: SessionInput!) {\n  createSession(session: $session) {\n    orgId\n    uuid\n    name\n    link\n    token\n    firstName\n    lastName\n    createdById\n  }\n}"}' --compressed

### Read Session Annotations:

curl 'http://[adobe.io url]/graffias/graphql' -H 'Accept-Encoding: gzip, deflate, br' -H 'Content-Type: application/json' -H 'Accept: application/json' -H 'Connection: keep-alive' -H 'DNT: 1' -H 'Origin: file://' -H 'x-gw-ims-org-id: [Organization ID]@AdobeOrg' -H 'x-gw-ims-user-id: [tech account ID]@techacct.adobe.com' -H 'x-api-key: [Client ID]' -H 'Authorization: Bearer [Access Token]' --data-binary '{"query":"query {\n  sessions {\n    uuid\n    token\n    name\n    firstName\n    lastName\n    updatedById\n    updatedTs\n    annotations {\n      payload\n    }\n  }\n}"}' --compressed

### Delete a Session:

curl 'http://[adobe.io url]/graffias/graphql' -H 'Accept-Encoding: gzip, deflate, br' -H 'Content-Type: application/json' -H 'Accept: application/json' -H 'Connection: keep-alive' -H 'DNT: 1' -H 'Origin: file://' -H 'x-gw-ims-org-id: [Organization ID]@AdobeOrg' -H 'x-gw-ims-user-id: [tech account ID]@techacct.adobe.com' -H 'x-api-key: [Client ID]' -H 'Authorization: Bearer [Access Token]' --data-binary '{"query":"mutation name($uuid: UUID!) {\n  deleteSession(uuid:$uuid)\n}"}' --compressed

### Read Events:

curl 'http://[adobe.io url]/graffias/graphql' -H 'Accept-Encoding: gzip, deflate, br' -H 'Content-Type: application/json' -H 'Accept: application/json' -H 'Connection: keep-alive' -H 'DNT: 1' -H 'Origin: file://' -H 'x-gw-ims-org-id: [Organization ID]@AdobeOrg' -H 'x-gw-ims-user-id: [tech account ID]@techacct.adobe.com' -H 'x-api-key: [Client ID]' -H 'Authorization: Bearer [Access Token]' --data-binary '{"query":"query {\n  events(sessionUuid:\"00264086-c771-431c-a55a-d2df9eadb89f\",_page:0,_size:50){\n    uuid\n    clientId\n    timestamp\n    vendor\n    type\n    payload\n  }\n}"}' --compressed

### Read Events with Annotations:

curl 'http://[adobe.io url]/graffias/graphql' -H 'Accept-Encoding: gzip, deflate, br' -H 'Content-Type: application/json' -H 'Accept: application/json' -H 'Connection: keep-alive' -H 'DNT: 1' -H 'Origin: file://' -H 'x-gw-ims-org-id: [Organization ID]@AdobeOrg' -H 'x-gw-ims-user-id: [tech account ID]@techacct.adobe.com' -H 'x-api-key: [Client ID]' -H 'Authorization: Bearer [Access Token]' --data-binary --data-binary '{"query":"query {\n  events(sessionUuid:\"00264086-c771-431c-a55a-d2df9eadb89f\",_page:0,_size:50){\n    uuid\n    clientId\n    timestamp\n    vendor\n    type\n    payload\n    annotations {\n      namespace\n      payload\n    }\n  }\n}"}' --compressed

## GLOSSARY OF TERMS

- Access Token: An expiring token that must be sent in the header value for 'Authorization' in the form -H 'Authorization: Bearer [access token value]'
- Adobe Assurance: The service which provides GraphQL endpoints for Experience Cloud Assurance Tools
- Adobe Developer's Console: Gives developers access to the tools needed to build with Adobe, including access to APIs, real-time events, Runtime functions, and plugin IDs
- Client ID: Identifies which user or entity is gaining access to an Adobe Resource, along with an access token, and is passed in the header in the form -H 'x-api-key: [client ID value]'
- Client Secret: Confirms the entity using the Client ID is authorized to do so.
- JSON Web Token (JWT): a method for representing claims securely between two parties
- Organization ID: Alpha-numeric value assigned to your Organization, ending in "@AdobeOrg"
- Public/Private Key Pair: helps to encrypt information that ensures data is protected during transmission

## Contributing 

We encourage you to participate in our open documentation initiative, if you have suggestions, corrections, additions 
or deletions for this documentation, check out the source from [this github repo](https://github.com/adobe/gatsby-theme-spectrum-example), and submit a pull 
request with your contribution. For more information, refer to the [contributing page](support/contribute/).

## API Requests & Rate Limits

The timeout for API requests through adobe.io is currently *60 seconds*.

The default rate limit for an Adobe Assurance API is *120 requests per minute*. (The limit is enforced as *12 requests every 6 seconds*).
When rate limiting is being enforced you will get `429` HTTP response codes with the following response body: `{"error_code":"429050","message":"Too many requests"}`    
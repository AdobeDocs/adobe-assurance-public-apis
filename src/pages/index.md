---
title: Overview - Assurance API
description: Service which provides GraphQL endpoints for Experience Cloud Assurance Tools.
contributors:
  - https://github.com/coljtob 
---

<Hero slots="heading, text"/>

# Assurance API

Service which provides GraphQL endpoints for Experience Cloud Assurance Tools.

<Resources slots="heading, links"/>

#### Resources

- [Adobe Experience Platform Assurance](https://developer.adobe.com/client-sdks/documentation/platform-assurance/)

## Overview

This documentation provides instructions for Assurance 1.0 APIs. For working with Adobe Experience Platform Assurance, please read the [Assurance documentation](https://developer.adobe.com/client-sdks/documentation/platform-assurance/).

The Assurance APIs are a collection of APIs that empower users to test and debug their web and mobile apps, when outfitted with the Adobe Assurance Mobile SDK. When enabled, the user of these APIs will be able to:

- create, read, and delete sessions
- read events
- read event annotations
- read session annotations

The guide will demonstrate how you can utilize Assurance APIs to programmatically connect your Adobe Assurance enabled mobile application to our back end services to help you develop and debug your application.

In order to make requests into Assurance API, you must create a JSON Web Token (JWT) within the Adobe Developer Console. For further information on use of JWT, you can view helpful docs and explanations [here](https://jwt.io/).

## Granting access

Within the [Admin Console](https://adminconsole.adobe.com/), Administrators will have to add new "Developers", and grant each access to "Adobe Experience Platform". With such access, those developers can create other "Projects" within your organization and add "Assurance" to those projects.

## Creating a project

If you do not already have a project defined in your organization, please create one by selecting **Create new project**.

![Create New Project](images/create_project.png)

## Adding Assurance API

Within your project home page, select **Add API** and filter by **Adobe Experience Platform**.

![Add API](images/add_api.png)

![Product Filter](images/product_filter.png)

After filtering for Platform, select **Assurance**.

![Assurance](images/assurance_api_plugin.png)

## Public/Private key pairs

You will be prompted to either generate or upload a public/private key pair. Select **Generate Key Pair**.

![Generate Key Pair](images/generate_keypair.png)

A ZIP file will be generated and downloaded to your computer. Expand the ZIP file and copy the entire contents of "private.key" to your clipboard.

<!-- Do we have images of this? -->

Select **Next** and, if requested, choose an applicable product profile.

<!-- Do we have an image of this? --->

Select **Save configured** API after confirming your details.

<!-- Do we have an image of this? --->

## Generating a JWT (JSON Web Token)

After defining your project, associating it with the Assurance API, and generating a public/private key pair, you can generate your JWT.

![JSON Web Token](images/jwt_account.png)

A JWT can be generated within the UI or using [several tools/libraries](https://jwt.io/libraries).

If you are generating your JWT within the UI, paste the entire contents of your previously downloaded private key into the "Private key" text box.

![Paste Private Key](images/paste_key.png)

## Status check

Now you should have created or defined the following iteas:

- An access token generated from your unique JSON Web Token
- Client ID
- Client Secret
- Technical Account ID
- Technical Account Email
- Organization ID

## Regenerating JWT-exchanged access tokens

To regenerate an access token, select **Credentials / Service Account (JWT)** within your project.

Select the **Generate JWT** tab, paste your private key in the text box, and then select **Generate Token**.

To regenerate your access token, copy and paste the **Sample cURL command** into your terminal and execute it. This command will use the generated JWT and exchanges it for an access token.

![Regenerate Key](images/regenerate.png)

An access token will be returned in your terminal window with an expiration. (check this--24 hours?).

## Glossary

- **Access Token**: An expiring token that must be sent in the header value for 'Authorization' in the form -H 'Authorization: Bearer [access token value]'
- **Assurance**: The service which provides GraphQL endpoints for Experience Cloud Assurance Tools
- **Adobe Developer Console**: Gives developers access to the tools needed to build with Adobe, including access to APIs, real-time events, runtime functions, and plugin IDs
- **Client ID**: Identifies which user or entity is gaining access to an Adobe resource, along with an access token, and is passed in the header in the form -H 'x-api-key: [client ID value]'
- **Client Secret**: Confirms the entity using the Client ID is authorized to do so.
- **JSON Web Token (JWT)**: A method for representing claims securely between two parties
- **Organization ID**: Alpha-numeric value assigned to your Organization, ending in "@AdobeOrg"
- **Public/Private Key Pair**: Helps to encrypt information that ensures data is protected during transmission

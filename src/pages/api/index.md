---
title: Adobe Assurance API Spec 1.0
description: Adobe Assurance API Spec 1.0
--- 

<Hero slots="heading, text"/> 

# Assurance API

Retrieve Assurance GraphQL Schema

### Execute the below cURL request to retrieve an up-to-date GraphQL schema.


`curl -i -X POST 'https://graffias.adobe.io/graffias/graphql' -H 'Accept-Encoding: gzip, deflate, br' -H 'Content-Type: application/json' -H 'Accept: application/json' -H 'Connection: keep-alive' -H 'x-gw-ims-org-id: [OrgId]@AdobeOrg' -H 'x-gw-ims-user-id: [UserId]@techacct.adobe.com' -H 'x-api-key: [clientId]' -H 'Authorization: Bearer [access token]' -d @introspection.json --compressed`

You can download the required "introspection.json" file [here](introspection.json).

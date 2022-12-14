---
title: Assurance API Usage
description: Assurance API Usage
---
<Hero slots="heading, text"/> 

# Assurance API Usage

Commands for queries/mutations

### Read Sessions:

```console
curl 'http://[adobe.io url]/graffias/graphql' 
    -H 'Accept-Encoding: gzip, deflate, br' 
    -H 'Content-Type: application/json' 
    -H 'Accept: application/json' 
    -H 'Connection: keep-alive' 
    -H 'x-gw-ims-org-id: [Organization ID]@AdobeOrg' 
    -H 'x-gw-ims-user-id: [tech account ID]@techacct.adobe.com' 
    -H 'x-api-key: [Client ID]' 
    -H 'Authorization: Bearer [Access Token]' 
    --data-binary '{"query":"query {  sessions {   name    uuid  }}"}'
```

### Create a Session:

```console
curl 'http://[adobe.io url]/graffias/graphql' 
    -H 'Accept-Encoding: gzip, deflate, br' 
    -H 'Content-Type: application/json' 
    -H 'Accept: application/json' 
    -H 'Connection: keep-alive' 
    -H 'x-gw-ims-org-id: [Organization ID]@AdobeOrg'
    -H 'x-gw-ims-user-id: [tech account ID]@techacct.adobe.com' 
    -H 'x-api-key: [Client ID]' 
    -H 'Authorization: Bearer [Access Token]' 
    --data-binary '{"query":"mutation name($session: SessionInput!) {  createSession(session: $session) {    orgId    uuid    name    link    token    firstName    lastName    createdById  }}","variables":{"session":{"name":"test-mutation","link":"testUrl://default"}}}'
```

### Update a Session:

```console
curl 'http://[adobe.io url]/graffias/graphql' 
    -H 'Accept-Encoding: gzip, deflate, br' -H 'Content-Type: application/json' 
    -H 'Accept: application/json' 
    -H 'Connection: keep-alive' 
    -H 'x-gw-ims-org-id: [Organization ID]@AdobeOrg' 
    -H 'x-gw-ims-user-id: [tech account ID]@techacct.adobe.com' 
    -H 'x-api-key: [Client ID]' 
    -H 'Authorization: Bearer [Access Token]' 
    --data-binary '{"query":"mutation name($session: SessionInput!) {  updateSession(session: $session) {    orgId    uuid    name    link    firstName    lastName    createdById  }}","variables":{"session":{"uuid":"[session UUID]","name":"session-renamed","link":"myNewUrl://default"}}}'
```


### Read Session Annotations:

```console
curl 'http://[adobe.io url]/graffias/graphql' 
    -H 'Accept-Encoding: gzip, deflate, br' 
    -H 'Content-Type: application/json' 
    -H 'Accept: application/json' 
    -H 'Connection: keep-alive' 
    -H 'x-gw-ims-org-id: [Organization ID]@AdobeOrg' 
    -H 'x-gw-ims-user-id: [tech account ID]@techacct.adobe.com' 
    -H 'x-api-key: [Client ID]' 
    -H 'Authorization: Bearer [Access Token]' 
    --data-binary '{"query":"query {  sessions {    uuid    token    name    firstName    lastName    updatedById    updatedTs    annotations {      payload    }  }}"}'
```

### Delete a Session:

```console
curl 'http://[adobe.io url]/graffias/graphql' 
    -H 'Accept-Encoding: gzip, deflate, br' 
    -H 'Content-Type: application/json' 
    -H 'Accept: application/json' 
    -H 'Connection: keep-alive' 
    -H 'x-gw-ims-org-id: [Organization ID]@AdobeOrg' 
    -H 'x-gw-ims-user-id: [tech account ID]@techacct.adobe.com' 
    -H 'x-api-key: [Client ID]' 
    -H 'Authorization: Bearer [Access Token]' 
    --data-binary '{"query":"mutation name($uuid: UUID!) {  deleteSession(uuid:$uuid)}"}'
```

### Read Events:

```console
curl 'http://[adobe.io url]/graffias/graphql' 
    -H 'Accept-Encoding: gzip, deflate, br' 
    -H 'Content-Type: application/json' 
    -H 'Accept: application/json' 
    -H 'Connection: keep-alive' 
    -H 'x-gw-ims-org-id: [Organization ID]@AdobeOrg' 
    -H 'x-gw-ims-user-id: [tech account ID]@techacct.adobe.com' 
    -H 'x-api-key: [Client ID]' 
    -H 'Authorization: Bearer [Access Token]' 
    --data-binary '{"query":"query {  events(sessionUuid:\"00264086-c771-431c-a55a-d2df9eadb89f\",_page:0,_size:50){    uuid    clientId    timestamp    vendor    type    payload  }}"}'
```

### Read Events with Annotations:

```console
curl 'http://[adobe.io url]/graffias/graphql' 
    -H 'Accept-Encoding: gzip, deflate, br' 
    -H 'Content-Type: application/json' 
    -H 'Accept: application/json' 
    -H 'Connection: keep-alive' 
    -H 'x-gw-ims-org-id: [Organization ID]@AdobeOrg' 
    -H 'x-gw-ims-user-id: [tech account ID]@techacct.adobe.com' 
    -H 'x-api-key: [Client ID]' 
    -H 'Authorization: Bearer [Access Token]' 
    --data-binary --data-binary '{"query":"query {  events(sessionUuid:\"00264086-c771-431c-a55a-d2df9eadb89f\",_page:0,_size:50){    uuid    clientId    timestamp    vendor    type    payload    annotations {      namespace      payload    }  }}"}'
```

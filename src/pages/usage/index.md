---
title: Assurance API Usage
description: Assurance API Usage
---
<Hero slots="heading, text"/>

# Assurance API Usage

cURL command examples for queries/mutations

## Queries

### Read Sessions

```text
curl 'https://graffias.adobe.io/graffias/graphql' \
  -H 'Content-Type: application/json' \
  -H 'x-gw-ims-org-id: [Organization ID]@Adobe.Org' \
  -H 'x-api-key: [Client ID]' \
  -H 'Authorization: Bearer [Access Token]' \
  --data-binary '{"query":"query { sessions { uuid name }}"}'
```

### Read Session Annotations

```text
curl 'https://graffias.adobe.io/graffias/graphql' \
  -H 'Content-Type: application/json' \
  -H 'x-gw-ims-org-id: [Organization ID]@Adobe.Org' \
  -H 'x-api-key: [Client ID]' \
  -H 'Authorization: Bearer [Access Token]' \
  --data-binary '{"query":"query { sessions { uuid name annotations { payload } }}"}'
```

### Read Events

```text
curl 'https://graffias.adobe.io/graffias/graphql' \
  -H 'Content-Type: application/json' \
  -H 'x-gw-ims-org-id: [Organization ID]@Adobe.Org' \
  -H 'x-api-key: [Client ID]' \
  -H 'Authorization: Bearer [Access Token]' \
  --data-binary '{"query":"query {  events(sessionUuid:\"[session UUID]\",_page:0,_size:50){ uuid clientId timestamp vendor type payload }}"}'
```

### Read Events with Annotations

```text
curl 'https://graffias.adobe.io/graffias/graphql' \
  -H 'Content-Type: application/json' \
  -H 'x-gw-ims-org-id: [Organization ID]@Adobe.Org' \
  -H 'x-api-key: [Client ID]' \
  -H 'Authorization: Bearer [Access Token]' \
  --data-binary '{"query":"query {  events(sessionUuid:\"[session UUID]\",_page:0,_size:50){ uuid clientId timestamp vendor type payload annotations { namespace payload }}}"}'
```

### Read Plugins

```text
curl 'https://graffias.adobe.io/graffias/graphql' \
  -H 'Content-Type: application/json' \
  -H 'x-gw-ims-org-id: [Organization ID]@Adobe.Org' \
  -H 'x-api-key: [Client ID]' \
  -H 'Authorization: Bearer [Access Token]' \
  --data-binary '{"query":"query {  plugins { uuid, namespace, updatedTsAfter, updatedTsBefore, displayName, type } }"}'
```

## Mutations

### Create a Session

```text
curl 'https://graffias.adobe.io/graffias/graphql' \
  -H 'Content-Type: application/json' \
  -H 'x-gw-ims-org-id: [Organization ID]@Adobe.Org' \
  -H 'x-api-key: [Client ID]' \
  -H 'Authorization: Bearer [Access Token]' \
  --data-binary '{"query":"mutation createSession($session: SessionInput!) { createSession(session: $session) { orgId uuid name link token }}","variables":{"session":{"name":"test-mutation","link":"testUrl://default"}}}'
```

### Update a Session

```text
curl 'https://graffias.adobe.io/graffias/graphql' \
  -H 'Content-Type: application/json' \
  -H 'x-gw-ims-org-id: [Organization ID]@Adobe.Org' \
  -H 'x-api-key: [Client ID]' \
  -H 'Authorization: Bearer [Access Token]' \
  --data-binary '{"query":"mutation name($session: SessionInput!) { updateSession(session: $session) { orgId uuid name link }}","variables":{"session":{"uuid":"[session UUID]","name":"session-renamed","link":"myNewUrl://default"}}}'
```

### Delete a Session

```text
curl 'https://graffias.adobe.io/graffias/graphql' \
  -H 'Content-Type: application/json' \
  -H 'x-gw-ims-org-id: [Organization ID]@Adobe.Org' \
  -H 'x-api-key: [Client ID]' \
  -H 'Authorization: Bearer [Access Token]' \
  --data-binary '{"query":"mutation deleteSession($uuid: UUID!) { deleteSession(uuid:$uuid)}"}
```

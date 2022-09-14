---
title: Adobe Assurance API Spec 1.0
description: Adobe Assurance API Spec 1.0
--- 
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

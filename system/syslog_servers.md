# system/syslog_servers

### Location
https://{***host-address***}/api/v2/system/syslog_servers

### Supported methods
GET

### Property types:
 ```text
"address" : string
"id" : int
"is_connected" : boolean
"port" : int
"report_audit" : boolean
"type" : string
"use_tcp" : boolean
 ```

## GET

Example 1:

GET https://{***host-address***}/api/v2/system/syslog_servers
```json
{
  "address": "172.16.1.150",
  "id": 2,
  "is_connected": false,
  "port": 514,
  "report_audit": true,
  "type": "standard",
  "use_tcp": true
}
```


## POST

### Properties:
 ```text
Mandatory: 
address

Optional: 
type
port
use_tcp
report_audit
 ```

Example 1:

POST https://{***host-address***}/api/v2/system/syslog_servers

Body:
```json
{
    "address": "172.16.1.150", 
    "port": "514", 
    "use_tcp": "false", 
    "report_audit": "false"
}
```

## PATCH

### Properties:
 ```text
address
type
port
use_tcp
report_audit
 ```

Example 1:

PATCH https://{***host-address***}/api/v2/system/syslog_servers/{id}

Body:
```json
{
    "use_tcp": "true", 
    "report_audit": "true"
}
```

## DELETE

Example 1:

DELETE https://{***host-address***}/api/v2/system/syslog_servers/{id}

---

## Global modifiers
| Supported Modifiers	| Description|
|-----------------------|------------|
|__contains	|Field contains the exact string given.|
|__contains_some	|Field contains any substring of a given string.|
|__gt	|Greater than; for numeric fields only.|
|__lt	|Less than; for numeric fields only.|
|__gte	|Greater than-equal; for numeric fields only|
|__lte	|Less than-equal; for numeric fields only|
|__neq	|Field value is not equal to the given string.|
|__in	|Accepts a list of comma-separated values (val1,val2,val3);Matches objects having a related field matching any of these values.|
|__m_eq	|Deprecated. Use __in instead.|
|__prefix	|Field value starts with given string.|
|__regexp	|Field value matches given regular expression.|

## Error responses

| Error Responses	| Description |
|-------------------|-------------|
|400 Bad request	|Client tried to do something that cannot be done.
|401 Unauthorized	|Client tried to access a resource without providing authentication information.
|403 Forbidden	|Client does not have permission to execute the requested action.
|404 Not found	|Client requested resource that does not exist.
|405 Method not allowed	|Client tried to execute an action that is not supported by the resource. For example, DELETE on system capacity policy.
|500 Internal server error	|General error returned by server when it fails to complete the operation for some reason.
|502 Bad Gateway	|K2 REST service became unavailable while performing the request. Client should recheck the state of the object.
|503 Service unavailable	|K2 REST service is busy and cannot execute the requested operation. The client should try again later.

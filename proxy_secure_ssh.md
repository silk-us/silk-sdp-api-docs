# proxy_secure_ssh

### Location
https://{***host-address***}/api/v2/proxy_secure_ssh

### Supported methods
GET, PATCH

### Property types:
 ```text
"auto_enable" : boolean
"https_port" : int
"id" : 1
"ip_address" : string
"pmc_comments" : string
"pmc_ssh_port" : int
"smc_comments" : string
"smc_ssh_port" : int
"status": "Disabled",
"time_remaining": null
 ```

## GET

Example 1:

GET https://{***host-address***}/api/v2/proxy_secure_ssh
```json
{
  "hits": [
    {
      "auto_enable": true,
      "https_port": null,
      "id": 1,
      "ip_address": "192.168.40.0",
      "pmc_comments": null,
      "pmc_ssh_port": null,
      "smc_comments": null,
      "smc_ssh_port": null,
      "status": "Disabled",
      "time_remaining": null
    }
  ],
  "limit": 100,
  "offset": 0,
  "total": 1
}
```

## PATCH

### Properties:
 ```text
Mandatory:
proxy_ip_address
proxy_status

Optional: 
connection_timeout
recreate_keys
 ```

Example 1:

PATCH https://{***host-address***}/api/v2/proxy_secure_ssh/{id}

Body:
```json
{
    "proxy_ip_address": "192.168.0.48"
}
```



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

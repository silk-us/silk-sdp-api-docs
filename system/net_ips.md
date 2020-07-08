# system/net_ips

### Location
https://{***host-address***}/api/v2/system/net_ips

### Supported methods
GET, POST, DELETE


### Property types:
 ```text
"id" : int
"ip_address" : string
"net_port" : {
    "ref" : string
},
"net_portchannel" : int
"net_vlan" : int
"network_mask" : string
"wan_port" : int
```

## GET

Example 1:

GET https://{***host-address***}/api/v2/system/net_ips
```json
{
  "hits": [
    {
      "id": 3,
      "ip_address": "10.10.50.203",
      "net_port": {
        "ref": "/system/net_ports/10"
      },
      "net_portchannel": null,
      "net_vlan": null,
      "network_mask": "255.255.0.0",
      "wan_port": null
    }
],
  "limit": 100,
  "offset": 0,
  "total": 4
}
```

## POST

### Properties:
 ```text
Mandatory: 
ip_address
service
network_mask
interface
 ```

Example 1:

POST https://{***host-address***}/api/v2/system/net_ips

Body:
```json
{
    "ip_address": "10.12.1.2", 
    "network_mask": "255.255.0.0", 
    "service": "iscsi", 
    "interface": {
        "ref": "/system/net_ports/10"
    }
}
```

## DELETE

Example 1:

DELETE https://{***host-address***}/api/v2/system/net_ips/{id}


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

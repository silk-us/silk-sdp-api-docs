# system/net_ports

### Location
https://{***host-address***}/api/v2/system/net_ports

### Supported methods
GET, PATCH


### Property types:
 ```text
"auto_negotiation" : boolean
"contained_in" : {
    "ref" : string
}
"flow_control" : boolean
"id" : int
"is_fru" : boolean
"link_state" : {
    "ref" : string
},
"mac_addr" : string
"mtu": string
"name": string
"port_type": string
"server": {
    "ref" : string
}
"speed_state": {
    "ref" : string
}
```

## GET

Example 1:

GET https://{***host-address***}/api/v2/system/net_ports
```json
{
  "hits": [
{
      "auto_negotiation": null,
      "contained_in": {
        "ref": "/system/servers/20"
      },
      "flow_control": null,
      "id": 30,
      "is_fru": false,
      "link_state": {
        "ref": "/system/hardware_states/165"
      },
      "mac_addr": "00:25:90:fc:07:1d",
      "mtu": null,
      "name": "kblock01-knode02-mgmtport02",
      "port_type": "mgmtport",
      "server": {
        "ref": "/system/servers/20"
      },
      "speed_state": {
        "ref": "/system/hardware_states/163"
      }
    },
    {
      "auto_negotiation": null,
      "contained_in": {
        "ref": "/system/servers/20"
      },
      "flow_control": null,
      "id": 31,
      "is_fru": false,
      "link_state": {
        "ref": "/system/hardware_states/172"
      },
      "mac_addr": "54c101",
      "mtu": null,
      "name": "kblock01-knode02-ib01",
      "port_type": "ib",
      "server": {
        "ref": "/system/servers/20"
      },
      "speed_state": {
        "ref": "/system/hardware_states/170"
      }
    }
],
  "limit": 100,
  "offset": 0,
  "total": 2
}
```

## PATCH

### Properties:
```text
Optional:
mtu
flow_control
```

Example 1:

PATCH https://{***host-address***}/api/v2/system/net_ports/{id}

Body:
```json
{
    "flow_control": "on"
}
```

## DELETE

Example 1:

DELETE https://{***host-address***}/api/v2/system/net_ports/{id}


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

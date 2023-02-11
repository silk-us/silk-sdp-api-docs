# system/net_interfaces

### Location
https://{***host-address***}/api/v2/system/net_interfaces

### Supported methods
GET

### Property types:
 ```text
"eth_name" : string
"id" : int
"is_expansion_in_progress" : boolean
"name" : string
"port" : {
    "ref" : string
},
"port_type" : string
"server" : {
    "ref" : string
},
"status" : string
 ```

## GET

Example 1:

GET https://{***host-address***}/api/v2/system/net_interfaces
```json
{
  "hits": [
    {
      "eth_name": "ib0",
      "id": 1,
      "if_ip": "10.112.1.4",
      "if_mask": "255.255.255.192",
      "is_expansion_in_progress": false,
      "name": "c-node04_netif-mgmt01",
      "port": {
        "ref": "/system/net_ports/4"
      },
      "port_type": "netif-mgmt",
      "server": {
        "ref": "/system/servers/3"
      },
      "status": "ok"
    },
    {
      "eth_name": "ib1",
      "id": 2,
      "if_ip": "10.112.1.68",
      "if_mask": "255.255.255.192",
      "is_expansion_in_progress": false,
      "name": "c-node04_netif-mgmt02",
      "port": {
        "ref": "/system/net_ports/5"
      },
      "port_type": "netif-mgmt",
      "server": {
        "ref": "/system/servers/3"
      },
      "status": "ok"
    },
    {
      "eth_name": "eth3",
      "id": 3,
      "if_ip": "10.112.1.164",
      "if_mask": "255.255.255.240",
      "is_expansion_in_progress": false,
      "name": "c-node04_netif-external01",
      "port": {
        "ref": "/system/net_ports/8"
      },
      "port_type": "netif-external",
      "server": {
        "ref": "/system/servers/3"
      },
      "status": "ok"
    },
    {
      "eth_name": "ib0",
      "id": 4,
      "if_ip": "10.112.1.5",
      "if_mask": "255.255.255.192",
      "is_expansion_in_progress": false,
      "name": "c-node05_netif-mgmt01",
      "port": {
        "ref": "/system/net_ports/10"
      },
      "port_type": "netif-mgmt",
      "server": {
        "ref": "/system/servers/9"
      },
      "status": "ok"
    },
    {
      "eth_name": "ib1",
      "id": 5,
      "if_ip": "10.112.1.69",
      "if_mask": "255.255.255.192",
      "is_expansion_in_progress": false,
      "name": "c-node05_netif-mgmt02",
      "port": {
        "ref": "/system/net_ports/11"
      },
      "port_type": "netif-mgmt",
      "server": {
        "ref": "/system/servers/9"
      },
      "status": "ok"
    },
    {
      "eth_name": "eth3",
      "id": 6,
      "if_ip": "10.112.1.165",
      "if_mask": "255.255.255.240",
      "is_expansion_in_progress": false,
      "name": "c-node05_netif-external01",
      "port": {
        "ref": "/system/net_ports/14"
      },
      "port_type": "netif-external",
      "server": {
        "ref": "/system/servers/9"
      },
      "status": "ok"
    }
  ],
  "limit": 1000,
  "offset": 0,
  "total": 6
}
```
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

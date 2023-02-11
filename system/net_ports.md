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
      "contained_in": {
        "ref": "/system/servers/3"
      },
      "flow_control": null,
      "id": 4,
      "is_fru": false,
      "link_state": {
        "ref": "/system/hardware_states/9"
      },
      "mac_addr": "00:0d:3a:3f:6d:ad",
      "mtu": null,
      "name": "c-node04_ib01",
      "port_type": "ib",
      "server": {
        "ref": "/system/servers/3"
      },
      "speed_state": {
        "ref": "/system/hardware_states/7"
      }
    },
    {
      "contained_in": {
        "ref": "/system/servers/3"
      },
      "flow_control": null,
      "id": 5,
      "is_fru": false,
      "link_state": {
        "ref": "/system/hardware_states/17"
      },
      "mac_addr": "60:45:bd:2d:4a:fe",
      "mtu": null,
      "name": "c-node04_ib02",
      "port_type": "ib",
      "server": {
        "ref": "/system/servers/3"
      },
      "speed_state": {
        "ref": "/system/hardware_states/15"
      }
    },
    {
      "contained_in": {
        "ref": "/system/servers/3"
      },
      "flow_control": null,
      "id": 6,
      "is_fru": false,
      "link_state": {
        "ref": "/system/hardware_states/25"
      },
      "mac_addr": "60:45:bd:2d:46:44",
      "mtu": "1500",
      "name": "c-node04_dataport01",
      "port_type": "dataport",
      "server": {
        "ref": "/system/servers/3"
      },
      "speed_state": {
        "ref": "/system/hardware_states/23"
      }
    },
    {
      "contained_in": {
        "ref": "/system/servers/3"
      },
      "flow_control": null,
      "id": 7,
      "is_fru": false,
      "link_state": {
        "ref": "/system/hardware_states/33"
      },
      "mac_addr": "60:45:bd:2d:4a:46",
      "mtu": "1500",
      "name": "c-node04_dataport02",
      "port_type": "dataport",
      "server": {
        "ref": "/system/servers/3"
      },
      "speed_state": {
        "ref": "/system/hardware_states/31"
      }
    },
    {
      "contained_in": {
        "ref": "/system/servers/3"
      },
      "flow_control": null,
      "id": 8,
      "is_fru": false,
      "link_state": {
        "ref": "/system/hardware_states/41"
      },
      "mac_addr": "60:45:bd:2d:49:e9",
      "mtu": null,
      "name": "c-node04_mgmtport01",
      "port_type": "mgmtport",
      "server": {
        "ref": "/system/servers/3"
      },
      "speed_state": {
        "ref": "/system/hardware_states/39"
      }
    },
    {
      "contained_in": {
        "ref": "/system/servers/9"
      },
      "flow_control": null,
      "id": 10,
      "is_fru": false,
      "link_state": {
        "ref": "/system/hardware_states/54"
      },
      "mac_addr": "00:22:48:48:8e:f8",
      "mtu": null,
      "name": "c-node05_ib01",
      "port_type": "ib",
      "server": {
        "ref": "/system/servers/9"
      },
      "speed_state": {
        "ref": "/system/hardware_states/52"
      }
    },
    {
      "contained_in": {
        "ref": "/system/servers/9"
      },
      "flow_control": null,
      "id": 11,
      "is_fru": false,
      "link_state": {
        "ref": "/system/hardware_states/62"
      },
      "mac_addr": "00:22:48:48:85:27",
      "mtu": null,
      "name": "c-node05_ib02",
      "port_type": "ib",
      "server": {
        "ref": "/system/servers/9"
      },
      "speed_state": {
        "ref": "/system/hardware_states/60"
      }
    },
    {
      "contained_in": {
        "ref": "/system/servers/9"
      },
      "flow_control": null,
      "id": 12,
      "is_fru": false,
      "link_state": {
        "ref": "/system/hardware_states/70"
      },
      "mac_addr": "00:22:48:48:81:22",
      "mtu": "1500",
      "name": "c-node05_dataport01",
      "port_type": "dataport",
      "server": {
        "ref": "/system/servers/9"
      },
      "speed_state": {
        "ref": "/system/hardware_states/68"
      }
    },
    {
      "contained_in": {
        "ref": "/system/servers/9"
      },
      "flow_control": null,
      "id": 13,
      "is_fru": false,
      "link_state": {
        "ref": "/system/hardware_states/78"
      },
      "mac_addr": "00:22:48:48:84:61",
      "mtu": "1500",
      "name": "c-node05_dataport02",
      "port_type": "dataport",
      "server": {
        "ref": "/system/servers/9"
      },
      "speed_state": {
        "ref": "/system/hardware_states/76"
      }
    },
    {
      "contained_in": {
        "ref": "/system/servers/9"
      },
      "flow_control": null,
      "id": 14,
      "is_fru": false,
      "link_state": {
        "ref": "/system/hardware_states/86"
      },
      "mac_addr": "00:22:48:48:8d:db",
      "mtu": null,
      "name": "c-node05_mgmtport01",
      "port_type": "mgmtport",
      "server": {
        "ref": "/system/servers/9"
      },
      "speed_state": {
        "ref": "/system/hardware_states/84"
      }
    }
  ],
  "limit": 1000,
  "offset": 0,
  "total": 10
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

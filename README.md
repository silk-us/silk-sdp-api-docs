# Getting Started
The K2 API is open, in that any operator can access it freely, assuming they have an appropriate credential in which to do so. 

Things you will need:
- A K2 appliance, be it in-rack or virtual. 
- A valid user account. 
- A framework to issue the calls. Examples for curl, PowerShell, and python are below. 

## Accessing the API
You can see the API index base at:  
https://{host-address}/api/v2/

This will return the root index for the API, but there is currently no sandboxing available here.  

## Authentication 

The K2 API currently only supports basic authentication. So a username and password pair will be required. 

## Making the call

The K2 REST API supports the following methods:

GET, POST, PATCH, DELETE. 

GET and DELETE require no further headers beyond the authentication header. POST and PATCH both require 'application/json' content-type declaration. 

## URI modifiers 

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
|__limit	|Declare a higher or lower limit of responses (default is 100).|

## Examples
### Curl
```text
curl -k -s 'https://admin:password@{host-address}/api/v2/events?event_id__in=249'

curl -k -s 'https://admin:password@{host-address}/api/v2/system/netvlans' -X POST -H 'Content-type: application/json' -d '{"interface": {"ref": "/system/net_ports/27"}, "tag": "4"}'
```

### Powershell
```powershell
$credentials = get-credential
$uri = 'https://{host-address}/api/v2/events?event_id__in=249'  
Invoke-RestMethod -Method GET -Uri $uri -Credential $credentials 

$body = '{"interface": {"ref": "/system/net_ports/27"}, "tag": "4"}'  
$uri = 'https://{host-address}/api/v2/system/netvlans'  
Invoke-RestMethod -Method POST -Uri $uri -Body $body -Credential $credentials -ContentType 'application/json'
```

### python
```python
URL = 'https://{host-address}/api/v2/events?event_id__in=249'
response = requests.get(URL, auth=('admin', 'password'), verify=False)
```

## Caveat
The basis for this document is a root document that is absent some key information. For example, many DELETE calls were simply not outlined, so I'm assuming convention on many of these calls. I'll be validating most of the calls on a case-by-case basis and updating in-kind. Many supported PATCH parameters are also absent, so YMMV. 

For now, please test any calls prior to deployment. The documentation I based this on seems comprehensive, but it would be a mistake to accept it as gospil just now. 

## Error Responses

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

## Endpoint index

### Events
[events.md](./events.md)  
[events/targets.md](./events/targets.md)  
[events/target_filters.md](./events/target_filters.md)  

### Volume operations
[vg_capacity_policies.md](./vg_capacity_policies.md)  
[volsnaps.md](./volsnaps.md)  
[volumes.md](./volumes.md)  
[volume_groups.md](./volume_groups.md)  
[retention_policies.md](./retention_policies.md)  
[snapshots.md](./snapshots.md)  
[snapshot_scheduler.md](./snapshot_scheduler.md)  
[snapshot_scheduler_mapping.md](./snapshot_scheduler_mapping.md)  

### Host operations
[hosts.md](./hosts.md)  
[host_fc_ports.md](./host_fc_ports.md)  
[host_groups.md](./host_groups.md)  
[host_iqns.md](./host_iqns.md)  
[mappings.md](./mappings.md)  

### Replication
[replication/peer_k2arrays.md](./replication/peer_k2arrays.md)  
[replication/peer_volumes.md](./replication/peer_volumes.md)  
[replication/peer_volume_groups.md](./replication/peer_volume_groups.md)  
[replication/peer_wan_ports.md](./replication/peer_wan_ports.md)  
[replication/rpo_history.md](./replication/rpo_history.md)  
[replication/sessions.md](./replication/sessions.md)  
[replication/stats.md](./replication/stats.md)  
[replication/stats/system.md](./replication/stats/system.md)  
[replication/stats/volumes.md](./replication/stats/volumes.md)  

### System configuration
[proxy_secure_ssh.md](./proxy_secure_ssh.md)  
[static_routes.md](./static_routes.md)  
[system/batteries.md](./system/batteries.md)  
[system/bmcs.md](./system/bmcs.md)  
[system/capacity.md](./system/capacity.md)  
[system/capacity_policy.md](./system/capacity_policy.md)  
[system/disk_groups.md](./system/disk_groups.md)  
[system/encryption.md](./system/encryption.md)  
[system/expanders.md](./system/expanders.md)  
[system/expansion.md](./system/expansion.md)  
[system/fc_connection_mapper.md](./system/fc_connection_mapper.md)  
[system/fc_ports.md](./system/fc_ports.md)  
[system/hardware_states.md](./system/hardware_states.md)  
[system/jbods.md](./system/jbods.md)  
[system/local_storage_devs.md](./system/local_storage_devs.md)  
[system/ndu.md](./system/ndu.md)  
[system/net_interfaces.md](./system/net_interfaces.md)  
[system/net_ips.md](./system/net_ips.md)  
[system/net_portchannels.md](./system/net_portchannels.md)  
[system/net_ports.md](./system/net_ports.md)  
[system/net_vlans.md](./system/net_vlans.md)  
[system/ntp.md](./system/ntp.md)  
[system/nvdimms.md](./system/nvdimms.md)  
[system/pairs.md](./system/pairs.md)  
[system/partial_system_parameters.md](./system/partial_system_parameters.md)  
[system/psus.md](./system/psus.md)  
[system/sas_hbas.md](./system/sas_hbas.md)  
[system/servers.md](./system/servers.md)  
[system/server_jbod_connections.md](./system/server_jbod_connections.md)  
[system/server_jbod_connection_ssd_dev_maps.md](./system/server_jbod_connection_ssd_dev_maps.md)  
[system/server_jbod_expander_connections.md](./system/server_jbod_expander_connections.md)  
[system/software_states.md](./system/software_states.md)  
[system/ssd_devs.md](./system/ssd_devs.md)  
[system/state.md](./system/state.md)  
[system/static_route_iscsi_port_mapper.md](./system/static_route_iscsi_port_mapper.md)  
[system/static_route_net_interface_port_mapper.md](./system/static_route_net_interface_port_mapper.md)  
[system/static_route_wan_port_mapper.md](./system/static_route_wan_port_mapper.md)  
[system/switches.md](./system/switches.md)  
[system/syslog_servers.md](./system/syslog_servers.md)  
[system/vlans.md](./system/vlans.md)  
[system/wan_connections.md](./system/wan_connections.md)  
[system/wan_ports.md](./system/wan_ports.md)  






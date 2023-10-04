# Static_Route

## COMMANDS


### Configuring a static route for a specific destination network:
```
Router(config)# ip route <destination_network> <subnet_mask> <next_hop_ip_address>
```
Example:
```
Router(config)# ip route 192.168.2.0 255.255.255.0 10.0.0.1
```
This command configures a static route for the destination network 192.168.2.0/24, with the next hop IP address of 10.0.0.1.


### Configuring a default static route:
```
Router(config)# ip route 0.0.0.0 0.0.0.0 <next_hop_ip_address>
```
Example:
```
Router(config)# ip route 0.0.0.0 0.0.0.0 10.0.0.1
```
This command configures a default static route with the next hop IP address of 10.0.0.1. It is used when a router needs to forward traffic to any destination that doesn't match any other specific routes.

### Configuring a static route with an exit interface:
```
Router(config)# ip route <destination_network> <subnet_mask> <exit_interface>
```
Example:
```
Router(config)# ip route 192.168.2.0 255.255.255.0 GigabitEthernet0/1
```
This command configures a static route for the destination network 192.168.2.0/24, with the exit interface of GigabitEthernet0/1.

## OTHER VARIANT COMMANDS

### Configure a static route with a specific administrative distance:
```
Router(config)# ip route <destination_network> <subnet_mask> <next_hop_ip_address> <administrative_distance>
```
Example:
```
Router(config)# ip route 192.168.2.0 255.255.255.0 10.0.0.1 120
```
The administrative distance (AD) is a value that represents the trustworthiness or reliability of a routing source. When multiple routing sources provide routes to the same destination, the router selects the route with the lowest AD.

### Configure a floating static route:
```
Router(config)# ip route <destination_network> <subnet_mask> <next_hop_ip_address> <administrative_distance> <floating_value>
```
Example:
```
Router(config)# ip route 192.168.2.0 255.255.255.0 10.0.0.1 120 200
```
A floating static route is a backup route that has a higher administrative distance (AD) than the primary route. It is used when the primary route fails or becomes unavailable. The floating value is higher than the AD of the primary route, allowing the backup route to only come into effect if the primary route fails.

### Configure a recursive static route:
```
Router(config)# ip route <destination_network> <subnet_mask> <recursive_next_hop_ip_address>
```
Example:
```
Router(config)# ip route 192.168.2.0 255.255.255.0 10.0.0.2
```
A recursive static route is used when the next-hop IP address specified is not directly connected to the router. Instead, it relies on the routing table to determine the correct next hop to reach the specified destination network.

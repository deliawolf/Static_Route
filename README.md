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

### BEST PRACTICE

1. Use static routes for specific scenarios: Static routes are best suited for smaller networks or specific scenarios where network changes are infrequent, or when you need to have granular control over the routing paths. For larger networks or dynamic environments, dynamic routing protocols may be more appropriate.

2. Document and maintain static routes: It is crucial to document and keep track of the static routes configured on your Cisco devices. This documentation helps with troubleshooting, network planning, and future changes. Regularly review and update the documentation as changes are made.
3. Route summarization: Whenever possible, use route summarization (also known as route aggregation) to reduce the number of static routes and optimize the routing table. Route summarization allows you to represent a range of IP addresses with a single static route, reducing the size of the routing table and improving network efficiency.
4. Verify next-hop reachability: Ensure that the next-hop IP address specified in the static route is reachable. Verify that the next-hop device is functioning correctly and that there are no connectivity issues before configuring the static route.
5. Use administrative distance appropriately: Static routes have an administrative distance (AD) associated with them, which determines their priority compared to other routing sources. Use appropriate AD values to ensure static routes are preferred over dynamic routing protocols or other routes when necessary.
6. Use backup routes: If redundancy is required, consider configuring backup static routes with higher AD values or floating static routes. These backup routes will only come into effect if the primary route fails, providing failover capability.
7. Regularly review and update static routes: Static routes should be periodically reviewed and updated to reflect any changes in the network topology or requirements. Remove obsolete or unused static routes to maintain a clean and efficient routing table.
8. Implement proper security measures: Ensure that static routes are configured securely and are not vulnerable to unauthorized modifications. Use appropriate access controls, such as privilege levels or access lists, to restrict access to the configuration and modification of static routes.


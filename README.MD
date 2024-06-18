# Networking with docker

Docker has a networking built in feature that allows containers to communicate with each other.

## Types of networks
- **bridge**: Default network that allows containers to communicate with each other inside a subnet.
- **host**: It removes network isolation between the container and the host and allows the container to use the host's network.
- **overlay**: It allows containers to communicate with each other across multiple Docker daemons.


## Subnets
A subnet is a range of IP addresses that allows to create isolated networks inside a network. A subnet has the next components:
- **Network address**: The first IP address of the subnet.
- **Broadcast address**: The last IP address of the subnet.
- **Gateway address**: The IP address of the gateway.
- **Subnet mask**: It defines the range of IP addresses that can be used in the subnet.

### Example
Consider the next subnet: 192.168.0.0/24
- The base address of the subnet is 192.168.0.0
- The subnet mask is/24 or 255.255.255.0 where the 24 indicates that 24 bytes are dedicated to the network portion
- The host portion is 8 bits long (Byte), so the number of hosts is 2^8 - 2 = 254 that means that this subnet can have 254 hosts where the first and last IP addresses are reserved for the network and broadcast addresses respectively.


## Subnetting by funcion
Subnetting by funcion is a technique that allows to define different type of services or categories inside a network.

### Example
Consider the next subnet:
192.168.0.0/16
- The subnet mask is  **255.255.0.0** (or /16 in CIDR notation)
- Broadcast address: **192.168.255.255** (or all the hosts bytes in the subnet are 1)
- The base address of the subnet is 192.168.0.0
- The part 0.0 can be configured with different services or categories like:
    - 10.0/24: Servers
    - 20.0/24: Databases
    - 30.0/24: Workstations

## Commands
### Docker
- **docker network ls**: List all networks.
- **docker network inspect NETWORK_NAME**: Inspect a network.
- **docker network create NETWORK_NAME**: Create a network.
- **docker network connect NETWORK_NAME CONTAINER_NAME**: Connect a container to a network.

### Linux
- **ip addr show**: Show the IP address of the network interfaces.
- **ip route show**: Show the routing table.
- **ifconfig INTERFACE_NAME**: Show the IP address of the network interface.

### Windows
- **ipconfig**: Show the IP address of the network interfaces.
- **route print**: Show the routing table.

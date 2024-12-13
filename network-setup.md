# Network setup for IBU062 Assignment 3

## Devices and Assigned IP Addresses

### Router 
- **Model**: Cisco 1941
- **Interface 0/0**: 168.90.0.1 (Network 1)
- **Interface 0/1**: 210.3.14.1 (Network 2)

### Switch 1
- **Model**: Cisco Catalyst 2960-24TT

### Switch 2 
- **Model**: Cisco Catalyst 2960-24TT

### PC 1
- **Model**: PC
- **IP**: 168.90.0.4 (DHCP assigned IP)

### PC 2
- **Model**: PC
- **IP**: 168.90.0.3 (DHCP assigned IP)

### PC 3
- **Model**: PC
- **IP**: 210.3.14.4 (DHCP assigned IP)

### PC 4
- **Model**: PC
- **IP**: 168.90.0.6 (DHCP assigned IP)

### PC 5
- **Model**: PC
- **IP**: 210.3.14.5 (DHCP assigned IP)

### Server 1
- **Model**: Server
- **IP**: 168.90.0.5 (DHCP assigned IP)

### Server 2
- **Model**: Server
- **IP**: 210.3.14.2 (DHCP assigned IP)

### Server 3
- **Model**: Server
- **IP**: 210.3.14.3 (DHCP assigned IP)

### Laptop
- **Model**: Laptop
- **IP**: 168.90.0.2 (DHCP assigned IP)

## DHCP Configuration on Router
- **Accessing the router CLI by entering the following commands:**
### Configure interface GigabitEthernet 0/0 (Network 1)
Router> enable
- Allows access to configuration commands, enabling us to make changes to the router settings

Router# configure terminal
- Entering global config mode, which lets us do the actual configuring of router's interfaces and some other things.

Enter configuration commands, one per line. End with CNTL/Z.
- If we entered the configuration mode successfully, we get this message. To return to privilege mode, we need to press CTRL+Z.

Router(config)# interface gigabitethernet 0/0
- We are accessing the config mode for GigabitEthernet 0/0 for Network 1.

Router(config-if)# ip address 168.90.0.1 255.255.0.0
- We are setting the IP address 168.90.0.1 with a subnet mask 255.255.0.0 for the GigabitEthernet 0/0 interface.

Router(config-if)# no shutdown
- We are enabling the interface. By using 'no shutdown', we are making sure the interface is ready to establish communication with other devices. 

### Configure interface GigabitEthernet 0/1 (Network 2)
Router(config)# interface gigabitethernet 0/1
- We are accessing the config mode for GigabitEthernet 0/0 for Network 2.

Router(config-if)# ip address 210.3.14.1 255.255.255.0
-  We are setting the IP address 210.3.14.1 with a subnet mask 255.255.255.0 for the GigabitEthernet 0/1 interface

Router(config-if)# no shutdown
- We are enabling the interface. By using 'no shutdown', we are making sure the interface is ready to establish communication with other devices. 

## DHCP Configuration on Router
### First network (168.90.0.0)
Router(config)# ip dhcp pool Network1
- We are creating a DHCP pool named Network1 on the router. A DHCP pool is a group of addresses a DHCP server can hand out to DHCP clients. Here, the DHCP pool is configured for Network1, which means that the router will allocate IP addresses to devices on Network1.

Router(dhcp-config)# network 168.90.0.0 255.255.0.0
- Here we are defining the IP address and subnet mask for Network1.

Router(dhcp-config)# default-router 168.90.0.1
- Here we are specifying the default gateway for devices that receive IP addresses from the DHCP pool.

Router(dhcp-config)# exit
- We are exiting the DHCP config mode and returning to the privileged EXEC mode (global config mode).

### Second network (210.3.14.0)
Router(config)# ip dhcp pool Network2
- We are creating a DHCP pool named Network2. The router will assign IP addresses for devices on this network.

Router(dhcp-config)# network 210.3.14.0 255.255.255.0
- We are defining the IP address and subnet mask for Network2.

Router(dhcp-config)# default-router 210.3.14.1
- Specifying the default gateway for devices that receive Ip addresses from the DHCP pool.

Router(dhcp-config)# exit
- Exiting the DHCP config mode and returning to the privileged EXEC mode (global config mode).
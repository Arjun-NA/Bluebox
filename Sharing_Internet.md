# Sharing Internet to Bluebox with proper IP configurations.

### 1. Sharing the Internet

After opening network configuration for the Host PC, share the internet to the LAN by clicking on Network Status --> Properties --> Sharing TAB. 
This will most likely assign a static IP to the ethernet port of your Host PC.

### 2. Configuring IP addresses properly.

As the ethernet is assigned a static IP, use this IP and create an IP for your bluebox ethernet port which have connected to the PC.

some example configuration    

| /        | IP Address    | Netmask       | Gateway        |      
|----------|---------------|---------------|----------------|      
| Host PC  | 192.168.137.1 | 255.255.255.0 | Leave it empty |    
| Blue BOX | 192.168.137.2 | 255.255.255.0 | 192.168.137.1  |    

| /        | IP Address    | Netmask       | Gateway        |
|----------|---------------|---------------|----------------|
| Host PC  | 192.168.137.1 | 255.255.0.0 | Leave it empty |
| Blue BOX | 192.168.0.91 | 255.255.0.0 | 192.168.137.1  |  

To set nemask and ip address for linux systems use the following example (Replace eth0 with required network interface).
```sudo ifconfig eth0 192.168.137.2 netmask 255.255.255.0 up ``` 
To set default gateway use the following command 
```sudo route add default gw <host-pc-IP> <network interface name>``` example ```sudo route add default gw 192.168.137.1 ni2```

### 3. Configuring Domain Name Server

The Domain Name System is a hierarchical and decentralized naming system for computers, services, or other resources connected to the Internet or a private network. It associates various information with domain names assigned to each of the participating entities.   

To configure it in bluebox use the following example command
```sudo vim /etc/resolv.conf``` and edit the file to add ```namserver 8.8.8.8```

### 4. Ping to confirm

Ping from both sides to verify network settings. then ping www.google.com and confirm that it connects to internet.


### 5. Possible Errors : 
1. Check if the internet access is existing in the shared network from the network status page of the ethernet form Host PC. There should be Internet in ipv4 network.




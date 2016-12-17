#Team Trojan 
# Implementing Mesh Network
 To implement mesh network we have used Byzantium operating System. Byzantium is a live Linux distribution
 that delivers easy-to-use, secure, and robust mesh networking capabilities.
 
Following are the steps involoved in constructing mesh network

1. Run Byzantium OS in the system using live booting or install the operating system.
  
  ISO available at --> http://project-byzantium.org/downloads/v0.5b/

2. While booting up Byzantium configures the mesh network by itself.(Auto-configuration)
    That is Assignment of,
  
  1.Mesh ID
  
  2.BSSID
  
  3.IP Address

3. Once the system boots up completely check if configurations are correct.

4. Repeat steps 1-3 for all the nodes in the network.


###Once all the systems are ready,

1. open the browser goto **localhost:8089**

2. You can see the whole topology 

###Scenario 1 - All the nodes connected

![Image](https://github.com/naveenholla/Mesh-on-Project-Byzantium/blob/master/screen_1.png)


In the above image,

Left side  - Shows all the nodes which are in the mesh network.

Right side - Its the OLSR table of the node (**192.168.159.155**)

  - In the figure you can notice that, there is an edge between all the nodes along with **the cost** of connection mentioned on the edge.



###Scenario 2 - One node disconnected

![Image](https://github.com/naveenholla/Mesh-on-Project-Byzantium/blob/master/screen.png)

In the above figure, 

Left side  - one system is down i.e with IP address **192.168.133.161**

Right side - From the one system(192.168.159.155) trying to ping **192.168.133.161** --> 100% packet loss



Scenario 3 - To demonstrate alternative path 

![Image](https://github.com/naveenholla/Mesh-on-Project-Byzantium/blob/master/screen1.png)

Left side  - Topology of mesh network 

Right side - Its the terminal of the node (**192.168.159.155**)

  - OLSRD Table(Optimised Lisk State Routing Debug)

  - Which shows one-hop and two-hop distance with everynode.

  - We can notice that there are two paths for every node,if one path fails another is automatically followed.

###Scenario 4 - Internet connectivity

![Image](https://github.com/naveenholla/Mesh-on-Project-Byzantium/blob/master/internet.png)

In the above figure, We have connected one of the Byzantium system to Internet using ethernet cable.One which is in red color.
Now this node becomes gateway to other non-Byzantium nodes for internet access.Hence if one of the node has the internet then all of the 
nodes in the mesh network can use internet without any issues. 

##Working of Byzantium - 

  1. Byzantium Nodes
  
  2. Non-Byzantium Nodes

###1. Byzantium Nodes

Basically while booting up it configures the mesh network , 
  - with SSID - **"Byzantium"** and assigns ip address of the network **192.168.0.0/16.**
  - So those who install Byzantium will all come under same network **i.e 192.168.0.0/16.**
 
###2. Non-Byzantium Nodes

Non-Byzantium nodes is basically any system(Linux/Windows) with wifi interface which is connected to Byzantium network.
When it gets connected to Byzantium network it will be assigned a IP address of network **10.0.0.0/8**.This address is assigned by a **Master-Node**.

**Master-Node** - Its one of the Byzantium node which broadcasts SSID over the network and responsible for assigning IP address and providing gateway details.

###Challanges 

1. What if Master-node disconnects
        Byzantium automatically sets another Byzantium node as master-Node which starts broadcasting SSID.But it takes some time to get configured.

2. We can not create a perfect diamond network
        That is since to work as a mesh network, Byzantium implemented in such a way that all nodes must be connected to all the nodes. which is nothing but a complete graph.
        
        Enjoyed Working on this assignment thank you :)
                       
            

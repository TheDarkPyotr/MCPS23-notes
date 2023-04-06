With SDN, one of the key technology that are used to make networks programmable. Changed the way networks are managed, supplied in 5G but in general also in datacenters where traffic growth has to be managed under some requirments: Security and others.
## Introduction
![[Pasted image 20230405184953.png]]
Why telecom operators want to use **virtualization** in their network? **To cope with increase of traffic volume**.

![[Pasted image 20230405185252.png]]
For managing traffic flows, for instance for implementing firewall, loadbalancer and intrusion detection, they were required to process their traffic, they **used specilized hardware for that specific function**. Changing phyisical devices is costly in both money and time.
This hardware devices created a **chain that is reflected in the network, like at the start a firewall and then a load balancer.** 
Problem of **flexibility** given by the physical hardware. Problem of provisioning resources, **overprovision vs under provision (bad when requests are higher that what you excpect).**
Example of network:
![[Pasted image 20230405185940.png]]
**Middleboxes*:** in this case with hardware devices (not flexible)
* Load balancers put in front of your datacenter to divert the traffic to it.
* **WAN optimizier**: function that optimize the traffic towards wide area network, for example by **compressing packets**.
* **IDS**: system that analyze your packets in order to find intrusions.
As you see there are lot of components that manage your flow, not just forwarding packets like the router.
*Middleboxes are devices or software that are inserted into a network to provide a specific function or service. They can be located at any point in the network and are designed to intercept, inspect, and modify network traffic to perform their designated function.

What are the problems:
![[Pasted image 20230405190613.png]]
Users may want  different services like **phone calls**, **text service**, **video services** and so on.
Managing hardware devices makes you infrastructure inflexibile, doesn't cope with the dynamic change of the services demand.
The idea is to **shift from specilized hardware to software.** The idea is to use general purpose hardware and implement on top of it the wanted functions.

## Network function virtualization
![[Pasted image 20230405191846.png]]
Create networks that are capable with coping with dynamic requests load in an agile and cheaper way.
From years to days to deploy new services in the network.

![[Pasted image 20230405192259.png]]
Decouple hardware from software in order to migrate your network functions when needed.
So now the network functions are **provided as plain software**.
Network services can be **composed by a set network functions**, for instance load balancer function plus firewall in a datacenter.
You don't need to **add new hardware, rather you need to relocate your functions to adapt with the demand**.

#### Virtualization with VMs
![[Pasted image 20230405192645.png]]
NFV make use of **virtual machines** in order to implement the network functions on top of general purpose hardware.
As you see in NFV a node can have multiple roles, not just 1 role given by that specific hardware (firewall, loadbalancer ecc..).

Example of use cases:
![[Pasted image 20230406095101.png]]
* Switching elements:
	1) Switching elements: Switching elements such as broadband network gateways (BNGs), which provide subscriber access to broadband services
	2) CG-NAT (Carrier-Grade Network Address Translation): CG-NAT is used to provide IPv4 address sharing among multiple customers. It is used by service providers to conserve public IPv4 addresses
	3) Virtual routers
* Mobile network nodes: The attempt of operators to define functions that can be deployed in the cloud in datacenters using virtualization technology. **The terms are related to 4G but same applies to 5G.**
* functions in home routers: 
	1.  Virtual private network (VPN) server: Allows users to remotely access their home network and its resources, such as printers and files, from anywhere in the world.
	2.  Firewall: Protects home networks from unauthorized access and external threats by monitoring and filtering incoming and outgoing traffic.
	3.  Parental controls: Enables parents to restrict access to specific websites or content based on age appropriateness or other criteria.
* Traffic analysis, they need a copy of the traffic to analyze in order to detect supicious packets or measure QoS.
* SLA monitoring
* NGN signaling, for ip based multimedia system.
* Policy control and charging
* Application level optimization: CDN (content delivery network), Cache servers (useful for CDN).
* Security functions: Firewalls, Intrusion detection system.

**Example NFV on mobile networks 4G:**
![[Pasted image 20230406100118.png]]
The EPS consists of two main components: **the Evolved Packet Core (EPC) and the Radio Access Network (RAN)**. The EPC is **responsible for managing the packet data traffic in the network**, while the **RAN provides the wireless connection between the end devices and the network.**
![[Pasted image 20230406100334.png]]
![[Pasted image 20230406100354.png]]
At the top we have the old approach, with the baseband unit having specific hardware, close to the base station, to implement the functions needed for 4G radio access network. 
Instead in the bottom we have a datacenter where the functions are implemented.

**Benefits:**
![[Pasted image 20230406100609.png]]
1) Innovation is faster, if you want to update your firewall, you just need to install it through software.

**Cons:**
1) overhead, if you have general purpose hardware are **less performant** than **specific hardware** The fact that you have virtualization adds overhead to the hardware.
However there are techniques that mitigate these overhead.

## Network Service:
![[Pasted image 20230406101235.png]]
Tipically when you have a traffic flow, you don't need only a network function to process the flow, but the operator needs to provide **a chain/composition of these functions (the ones on top)**. NFV can provide different treatment to 2 different flows (Red, blue). As you see in the example **the service classifier decides what functions to execute on the specific flow**.
Remember SDN is just a bunch of routers with a central controller.
The **PGW** is responsible for managing data packets between the **mobile devices and the external packet data networks, like internet.**

#### Network service in NFV
![[Pasted image 20230406101656.png]]
* a network service is a graph, a composition of network functions. The edge of this graph rappresent the forwarding edge, so how this function is executed and what next function to execute.
* 
![[Pasted image 20230406102036.png]]
as you see those are **logical links** that connects the network functions together. Underlying there's the **phyisical infrastructure** that connects those functions.
The **functions are implemented on a set of servers in the data center or distrubuited among different datacenters (1-2-3), in reality they are implemented on top of VMs**.
**All of these VNFs run as VMs on physical machines, called points of presence (PoPs).**
The cache can be placed near the functions in order to improve the performance.
![[Pasted image 20230406104125.png]]

## NFV architectural infrastructure
We need to deploy those functions in an infrastructure.
What we need?
![[Pasted image 20230406104209.png]]
3) for instance allocate a set of resources, ask the cloud to allocate a VM, manage the VM ecc...

![[Pasted image 20230406104315.png]]
**NFV orchestration** are functions that oversees and orchestrates the resources in the NFV environment that is working.
As you see there's a virtualization layer, on top of it we implement our network functions.

#### NFV infrastructure
![[Pasted image 20230406104523.png]]
Switch, routers and links.
![[Pasted image 20230406104557.png]]
since we have a virtualization layer, we need **an hypervisor to manage the VMs**.
Nowadays we could use **Containers on top of the VMs**, for faster deployment and scalability **(Cloud native functions).**
![[Pasted image 20230406104808.png]]
1) The links and interconnection devices that connect compute nodes (POP) to the storage devices
2) Links between POPs, for instance Wide area network.

##### openstack example:
![[Pasted image 20230406105202.png]]
1.  Infrastructure Network domain:  **It includes the physical network devices, such as switches and routers, that interconnect the virtualized network components.**  
2. OpenStack Networking deployment: OpenStack Networking is a software component of the OpenStack **platform that provides networking services for virtualized environments**. In this example, an **OpenStack Networking deployment is being used to provide advanced network services such as Firewall as a Service (FWaaS) and Load Balancer as a Service (LBaaS).**
3.  Dedicated OpenStack Networking node: **This node is responsible for performing Layer 3 routing and DHCP (Dynamic Host Configuration Protocol) services for the virtualized environment. It also runs the advanced services, FWaaS and LBaaS.**
4.  **Compute nodes: These are the nodes that host the virtual machines (VMs) running in the virtualized environment.** In this example, there are two Compute nodes, each running the Open vSwitch (openvswitch-agent) software component and having two physical network cards. **One network card is used for tenant traffic (i.e., traffic between the VMs), and the other is used for management connectivity.**
5.  **Open vSwitch: This is a software switch, It is used to connect the VMs to the physical network infrastructure.**
6.  Provider traffic: This refers to the network traffic that is used to connect the virtualized environment to external networks, such as the Internet. In this example, the OpenStack Networking node has a third network card that is specifically used for provider traffic. This network card is connected to the physical network infrastructure and provides connectivity to external networks.

**N.B that is a virtual switch.**
![[Pasted image 20230406105801.png]]
**Vswitchs are inside the server, deployed and defined as software.**

## Managment and orchestration
![[Pasted image 20230406110408.png]]
orchestrators are those components that automatically provide the provision the needed resources to deploy the network service, without any human interaction. **Given a network service description, it can be automatically deployed.**
![[Pasted image 20230406110557.png]]
All these blocks have the job to manage the lifecycle of the VNF (virtual network functions).

#### VIM
![[Pasted image 20230406110718.png]]
the platform that manages the cloud, the datacenter. Like openstack. For instance it provision **the phyisical resources to deploy VMs (CPU, memory)**.

#### VNFM
![[Pasted image 20230406111033.png]]

#### NFV orchestrator:
![[Pasted image 20230406111145.png]]
**it comunicates with the virtual network function manager in order to provision virtual resources in order to run the functions.**
It starts and manage the lifecycle of VNF instances.
**It accepts in input some NFV descriptors that describe the requested service, there's a catalog that defines the functions offered by the operator.**
![[Pasted image 20230406111611.png]]
Remember **a Virtual network service are a composition of Virtual functions**.
In the descriptor of the virtual network service you have name, version ecc.. then the list of virtual functions that you need to implement in order to deliver that service, the functions defines even the scripts to execute in order to manage their lifecycle, useful for the orchestrator.

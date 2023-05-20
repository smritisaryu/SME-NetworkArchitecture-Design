# SME-NetworkArchitecture-Design
Network  

The SME should host three departments, Engineering, Sales, and Management. The Engineering group will initially have 300 computers; these are divided into 260 staff computers. The remaining 40 are production servers. These are deployed in groups of 5, i.e., 8 groups. Each group has two servers deployed in hot-swap load-balancing; the remaining three are used for service production (see Figure 1. Using this service production unit (SPU), the service can scale (add more prod units), and there is resilience since both load balancers and production are duplicated. The customer load is divided equally among the Prod servers, while the load balancers are run in hot-standby. I.e., there is only one serving the customers, but if that fails or needs to be shut down for maintenance, the other takes over directly.   

Picture1.png

 

 

The traffic patterns for the service groups are shown in Table 1. They are roughly equally loaded, except for groups A and B. These are having roughly 10 times as many customers. Groups C—H have between 700 and 1200 customers/h. Service H is the beta-test for A; hence, customers of A will move over to H in a not too long time, making the total customers in the 11-12K range. 

 

  Table 1: Service Traffic Patterns 

 

 

Mbyte/customer 

Mbyte/customer 

Group 

Customers/h 

Load-In 

Load-Out 

A 

10 000 

0,01 

1 

B 

10 000 

0,02 

2 

C 

1 000 

5 

10 

D 

900 

7 

2 

E 

730 

0,001 

1 

F 

100 

5 

10 

G 

1 000 

10 

0,001 

H 

1 200 

0,02 

4 

  

  

 The sales group consists of a back-office of around 10 people; here 4 are technical writers working on documentation and adaptation of documentation, 4 are working as customer support (close cooperation with Engineering group and customers), the last 2 are salespeople that work in the office. In addition to the back-office, the company has around 20 contracted salespeople travelling the world (these are rotated back to the office once every few years). The contracted salespeople are responsible for buying their laptops and peripherals, but they need to set up VPN connections to the main office to do their internal work. Hence, the network for the sales group has four different types of use; writing (4 computers), customer-support (4 computers), visiting-sales (30 computers, each salesperson has a physical desktop in the office), and a VPN server (using an SPU deployment just as in production to ensure operations). The VPN traffic is moderate, at most 30 customers/h. However, they generate around 10Mbps in/out traffic when they are active (using remote desktop). Once a remote salesperson connects, they can start a remote desktop connection to their on-site desktop.  

   

The management consists of a small team of five people; Chief Executive Officer (CEO), Technical Lead (TL, engineering manager), Sales Lead (SL, sales manager), Economic officer, and a secretary. Each has a computer or two for (CEO, TL, and SL).  

   

In addition to this, some shared resources cover all/some of the groups; 10 printers cover all groups, 2 file servers cover sales and management.  

   

Within the nearest 6 months, the company will:  

Move customers from A to H service group, and rename H to A (update A). They anticipate growth of customers of the updated A service, predicting to have 20000 customers/h 12 months after the update has launched (i.e., between 12 and18 months into the future, depending on when the update occurs. They also anticipate the B service to grow, but to 15000 customers/h within the same time region.  

   

Within 12 months:  

The company will start beta tests of I and J services; these will run for 6 months, with around 1000 customers/h, like the current G and C services. When they launch (x+6—12), they expect to have around 7000 customers/h.  

The company also expects to grow the engineering group with 25-50 staff and 5-6 contract salespeople.  

   

Within 24 months:  

The company will expand with purchases of other groups, these will initially remain separate, but during a 6-12 months period, their engineering groups will merge into the existing engineering group. However, they will not change location. Hence, the engineering group will be distributed; the same applies to their services.  

   

  

Propose a network design to match these requests. The design should include layer 2 and layer 3 devices and connectivity and the required layer N infrastructure to support this. There are 3 departments (engineering, sales and management) and these departments are further divided into sub-departments (for example engineering has staff and production servers, so staff and production servers become sub-department). The sub-departments must be present in a subnet which is mandatory.  

   
Monitoring  

We start with the SME network as it would be after 24 months, i.e., it has grown with 25-50 engineering and 5-6 sales staff. Services I and J are deployed with 7500 customers/h.  

The SME wants a simple monitoring solution for its entire network; it should monitor (1) when links go up/down. It should also monitor (2) link utilization, both bit and packet rates (both directions). For normal operations, 5 minutes averages are sufficient. Do an inventory of possible tools/solutions that can meet these requirements; you can propose two different tools/solutions or just one—reason on the architecture for the monitoring.  

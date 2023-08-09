<h1>DevOps Project</h1>

<h2>Project Description</h2>

<h3>Deploying web app using Docker Swarm. (Production Ready).</h3>

<br />
<p align="center">

Follow the steps:

1. First of all, go to the AWS portal and create three new instances. Named:

· Swarm-manager

· Swarm-worker1

· Swarm-worker2 


2. In all three instances, inside the inbound rules, allow

· Custom TCP — 2377 — Anywhere IPv4

· Custom TCP — 8001 — Anywhere IPv4

3. Install docker with docker engine on all three nodes, (Check my other articles for the installation).

4. Now, Open the “Swarm Manager” node and run the command,
  
   <pre><code> sudo docker swarm init </code></pre>
  
This will be creating empty swarm.

<img src="https://i.imgur.com/9V9fAKW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br />
<br />

5. After initializing the swarm on the “swarm-manager” node, there will be one key generated to add other nodes into the swarm as a worker. Copy and run that key on the rest of the servers.

(Now, both machines are added to the swarm as a worker).
   <br/>

<img src="https://i.imgur.com/zEUoXdN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/YZVqDLH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br />
<br />

6. To check about all the nodes in the manager, run

   <pre><code> sudo docker swarm node ls </code></pre>

<img src="https://i.imgur.com/e6qUtPU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

7. Now, on Manager Node we will create a service,

   <pre><code>sudo docker service create --name django-app-service --replicas 3 --publish 8001:8001 trainwithshubham/react-django-app:latest</code></pre>
<br/>

  <img src="https://i.imgur.com/XXngwOI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br/>
<br />

8. Now, run
   <pre><code>sudo docker service ls</code></pre>
 <br/>
 
<img src="https://i.imgur.com/hQ5F9Qo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br />
<br />

9. Now, this service will create a container in the Manager node. To check, run the command:

    <pre><code>sudo docker ps</code></pre>
 <br/>
<img src="https://i.imgur.com/S2csNSS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

10. Now, this service will be running on all three nodes. To check this, just grab the Ip Address of any of the nodes followed by port 8001. As

<Any_ip_of_3_vms>:8001
<br/>
<img src="https://i.imgur.com/SxXBuU1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/SxXBuU1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/SxXBuU1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br />
<br />

11. If you want to remove any node from the environment, just run:

     <pre><code>sudo docker swarm leave</code></pre>
 <br/>

<img src="https://i.imgur.com/GKTc2zE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br/>
</p>
- <b>~Hassanat Hussain</b>
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```

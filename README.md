
# Summary

This is the beginning of my journey to Homelab, this is where I put all my skills to actual use for personal storage, learning, playing around, deploying, etc. My ultimate goal is to become a great Linux Administrator and this sort of project really puts my skills to the test and how well I manage and work under pressure, especially when things go wrong.  

I named my Homelab: **HAVOC**

**Havoc Definition:** Disorder or chaos

**Why:** Sounded cool but also when Homelabbing, things go wrong all the time, it's part of the fun and the learning. 

# Setup

**Hardware:** 
- A used **R430** from Ebay with **20 Cores** and **64GB RAM**, amazing for home server, it can handle great amount of VMs and storage, despite being 10+ years old.  It's great for Enterprise and small business, it's still being used across different companies.  
- Another used **R430** from a Friend with **16 Cores** and **74GB RAM**. That one will serve as overall **offline** backup for everything, offline because it's not suppose to be redundant but rather extra space and resources consumption for my other hardware.
- A used **Lenovo ThinkCentre**  with **4 Cores** and **8GB RAM** for 24/7 Docker Services, like browser, music, drawing, etc. They're small so they consume minor amounts of power and can fully run 24/7 with no issues. 
- Another used **Lenovo ThinkCentre**  with **2 Cores** and **8GB RAM** for more 24/7 Docker Services.
- **Netgear** 8 Port Switch


*Here's my personal Pros and Drawbacks:* 

**Pros:** 
- Handles larges amount of data
- Handles large amounts of task without crashing
- Can easily be upgraded 
- Pretty cheap compare to other servers (bought secondhand)
- Can run many Proxmox VMs and Services
- Looks cool
- Allows IDRAC
- Has many Ethernet Ports
- Easily Rackable 
- Allows RAID

**Some Drawbacks:** 
- Over-powered for a Homelab
- Costly Electric Bill
- Sizable (Takes up decent space)
- Loud
- Only 4 Drive Bays

<img width="1015" height="238" alt="image" src="https://github.com/user-attachments/assets/80672723-0d26-414d-9310-bd0057c9708c" />


**Side Note:** My overall goal is to update this Homelab repository as my Homelab Havoc grows, this repository will naturally be updated when new stuff is added or changed. 

# Infrastructure Diagram (IPs are Removed)

<img width="2100" height="2270" alt="image" src="https://github.com/user-attachments/assets/e9c6be26-f6f4-4d36-ab56-60b5ae247372" />

(This is still works in progress, this diagram will naturally update as I improve my Homelab)


<img width="292" height="578" alt="image" src="https://github.com/user-attachments/assets/aced2ecf-9771-490b-9e69-e639583f21ba" />

(Here's the actual VMs and Containers, some services are new, therefore not included in this project) 

# Infrastructure Diagram Breakdown

**Starting at the top:** 
<img width="348" height="208" alt="image" src="https://github.com/user-attachments/assets/68939ad4-bdc6-4825-9f89-5b67dbbe00f7" />

**Annotations:** We have the internet entering my router, my router is a basic one you get from an ISP, it's not yet upgraded. I have not decided what hardware (Either Netgate or Netgear, or a Workstation with 2 NICS) to upgrade to, however I'm planning to image Pfsense on the hardware.  

**Side Note:** All of the Diagrams are done on Draw.io, the *4/3/2026* is when the Diagram was last updated.  

<img width="1242" height="581" alt="image" src="https://github.com/user-attachments/assets/118b07bd-1f84-4764-93ae-bc34706dd7bd" />

**Annotations:** My server is running Proxmox, it's an amazing OS. It's running on the **Poweredge R430** with *2 WD Blue*, *1 Seagate* (The Exos) with uploaded ISOs, which includes:
- **Ubuntu:** For Docker services and other various stuff
- **Arch Linux:** Testing Environment
- **Debian:** For Docker services and other various stuff
- **Kali Linux:** Pentesing
- **Security Onion Solutions:** SIEM On the OS Level

# Category: Media

**Media:** This category is for file storing of any sort, which includes music, photos, 3D files, videos and etc. 

<img width="423" height="453" alt="image" src="https://github.com/user-attachments/assets/53c3e4bd-672c-4ca4-9e95-c63daeb9fee8" />

**Annotations:** 
**Media:** This category if for file storing of any sort, which includes music, photos, 3D files, videos and etc. 
- **Ubuntu Server 1:** Runs *Navidrome* which is a music storage service that's on docker, it's similar to Spotify, to keep a database of music I've made in the past and present.
- **Ubuntu Server 2:** Runs *NextCloud* which is also storage server but for files, which includes pictures, videos, various other files and etc. It's used as a backup for my personal phone. 
- **Ubuntu Server 3:** Also runs *NextCloud*, this one is for my main PC, as a backup, to backup all my files.

<img width="423" height="397" alt="image" src="https://github.com/user-attachments/assets/a87f04b3-6857-4d2d-9ef3-cce2df9ffa8d" />

**Annotations:** . 
- **Debian Server 1:** Runs *Jellyfin*, which is a video streaming docker service, similar to Netflix but for your digitally and physically owned movies. 
- **Debian Server 2:** Runs *KeePassXC*, which is a password manager for all my passwords, this is much easier then to keep having to install a password manager on each machine. 
- **Debian Server 3:** Runs *Homepage* which is a fun dashboard that's built on YAML that allows you to customize and link your locally hosted service for ease of access.  

**Extra Notes:** Choosing Debian over Ubuntu in this instance was simply for fun sort of choice, they're pretty similar. 

<img width="489" height="336" alt="image" src="https://github.com/user-attachments/assets/abe67edc-fc0f-41a6-a6f7-20aa4a3adbc6" />

**Annotations:** 
- **Debian Server 1:** Runs *SearXG*, which is a search engine that querys all the engine for best results of the search query.
- **Debian Server 2:** Runs *FreshRSS* which is a RSS Feed that allows you to pick out your  favorite article websites and display it on a locally hosted feed, which also allows you to query for things. I like this service as it keeps me up to the latest with CVEs, Daily Breaches, different APTs and etc.

**Important Notes:** By now, this maybe is redundant, I could've made a really heavy machine and installed Portainer or CasaOS on it and called it day but this sort of layout is what truly separates services so that troubleshooting is much easier, Portainer, CasaOS is a single point of failure, if those systems were to corrupt or fail for any reasons then all my work vanishes. 

**Other Aspects:** LXC on Proxmox is relatively new and does not support all docker services, they work but when visiting the service via IP, it fails to connect because some of those services need to be installed on an existing VM, the LXC containers that currently run are so far the only ones that could work and on LXC you can't access the terminal, which makes troubleshooting difficult. 

# Category: Security 

**Security:** This category is for SIEMS, IDS, IPS, Network Traffic, etc. 

<img width="470" height="484" alt="image" src="https://github.com/user-attachments/assets/a98516b4-d1ef-499b-b26b-690ee00ac3f8" />

**Annotations:** 
- **Ubuntu Server 1:** Runs *Wazuh*, which is my SIEM server, it collects logs from hosts when registered as an agent. It allows me to monitor, create rules, create dashboards about how my hosts behaves and whether their is malicious IP trying to attack anything or not. This is not based on docker but rather an installation script. 
- **Debian Server 2:** Runs *Security Onion Solutions* which is an OS for SIEMS, pretty similar to Graylog and Wazuh, I don't have anything on it, it's mainly to learn SIEMS better. 
- **Ubuntu Server 3:** *Kasem Workspace* is a Sandbox app deploying solution, it's like Linode but for browsing, testing files, deploying OSes  and etc then when you're done, it auto or manually wipes them.

<img width="410" height="331" alt="image" src="https://github.com/user-attachments/assets/ffb31b4f-09ec-4637-bae8-8a6d666680e7" />

**Annotations:** 
- **Debian Server 1:** Speaking of *Graylog*, I also run it. Very similar to Wazuh. 
- **Debian Server 2:** *Elasticsearch* is the Enterprise version of "Wazuh", all those tools are pretty similar as they all kinda do the same thing but they all also behave a little differently, I enjoy SIEMS and I want to make sure that I'm getting the most out of them in terms of experience and learning. 

# Category: Monitoring  

**Monitoring:** This category is for monitoring services. 

<img width="631" height="363" alt="image" src="https://github.com/user-attachments/assets/9d9232fc-5a5f-4cc4-bf14-2143a6a92243" />

**Annotations:** 
- **Proxmox:** On the Proxmox itself, it's running these services as LXCs *(Via Docker OCI)*:
	- *2 Excalidraw*: A drawing board for notes, ideas, plans, etc, similar to OneNote.
	- *Speedtest*: This monitors network speed.
	- *Beszel*: Monitors all my VMs, in terms uptime, downtime, CPU, Temp, GPU, Disk and etc.  
	
- **Debian Server 1:** Runs PI-Hole which is DNS monitoring.

<img width="596" height="535" alt="image" src="https://github.com/user-attachments/assets/f90115e7-c94f-4d1f-a9c4-cf0fecca4091" />

**Annotations:** 
- **Debian Server 1:** Runs *Portainer*, to test out docker services before I deploy them on isolated VM or LXC but also I run Netdata for Monitoring the VM itself.
- **Proxmox :** Runs Grafana which is a log gathering service that gathers all system logs for dashboards, status, systems and etc. On Proxmox, it also runs Prometheus, which allows those log extractions via Node Exporter and PVE Exporter  
- **Debian Server 2:** Dockerhand allows you to manage all of your docker services on a GUI, instead of manually managing them on each host, most of my docker services is registered to it. 

# Category: MISC   

**MISC:** This category is for other things. 

<img width="377" height="152" alt="image" src="https://github.com/user-attachments/assets/68c03293-c51a-47e5-84fe-6374a7d4fb65" />

**Annotations:** 
- **Kali Linux:** Used for to learn Ethical Hacking and understand how bad actors do bad actions. **I ONLY Pentest devices I own**. 
- **Arch Linux:** Is to mess around with, to run scripts I wrote and what not, mainly for fun.

**Lastly:**
<img width="172" height="210" alt="image" src="https://github.com/user-attachments/assets/338f5440-4f6f-487d-ac38-3dbdc90b024e" />

**Annotations:** Everything goes to 8.8.8.8 which is my *primary* DNS. My *secondary* is 1.1.1.1. 


# Clusters 

<img width="147" height="112" alt="image" src="https://github.com/user-attachments/assets/c6ffbf5d-4e1e-4d7d-8446-5c2f73ac57bc" />

**Annotations:** 
- **Localhost** is the main server, the R430.
- **ServerB** is the backup R430.
- **ServerC** is the first ThinkCentre.
- **ServerD** is the second ThinkCentre.

<img width="924" height="183" alt="image" src="https://github.com/user-attachments/assets/5aab2f4b-fce2-44c4-aa4d-aa786abfb6ed" />

**Annotations:** Proxmox Clustering is super easy, when you get new hardware, Proxmox allows you to cluster within seconds. 

**Via Homepage Dashboard:** 

<img width="333" height="264" alt="image" src="https://github.com/user-attachments/assets/a4c068d0-acd0-47e4-81e7-96ad6f297f82" />

# Migrations

Services that moved to from **ServerA (Localhost)** to **ServerC**: 
- SearXNG 
- Librewolf
- Navidrome 
- Homepage


# Backup

In Progress...




# Kube Cluster Via VMs 

In Progress...


# Conclusions 

As mentioned, this repository will be updated as the project expands, I want to be able to run every service that I use daily, locally. 

**A.I. Transparency:** AI was used to make this Homelab but ONLY to troubleshoot Docker, OS, Firewall and etc, just basic issues and errors, none of it was used otherwise, to ensure my learning and understanding is accurate and honest of how servers and services work. 

***No AI was used to write this repository.*** 

---

**Estimated Hours:** 200 Hours 
(How much time I've put on this project so far.)

**Estimated Uptime:** 8-12 Hours
(How long is the server on, daily.)

---

**Next Steps:** 
- Purchase 3 small Workstations for a Kubernetes Cluster that must be deployed via Ansible with a fully written out playbook.
- Purchase another Workstation, install NIC card on it to replace current router. 
- Purchase a Server Rack
- 3D print a customized Name Plate for the server. ✅
- Buy several Fans to direct heat outside the closet (yes this is server is in a large closet at home) 
- Purchase 1 more Blade Server with similar spec as a fully online backup for all services and data. ✅
- Use another Blade Server for future Cybersecurity projects. 
- Add all hardware as a Node to the main Proxmox Server. ✅
- Purchase a small display to display the status of all servers, which include uptime, CPU, GPU, downtime, TEMP and etc.
- Purchase a GPU for local AI model.
- Migrate all services to an SSD.
- Purchase a VGA monitor. ✅
- Implement RAID on the backup Server.
- Purchase HDDs and SSDs.
- Document everything.
- Implement a large ISO repository. ✅
- Allow other users (family) to access certain services. 




  




















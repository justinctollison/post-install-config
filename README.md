<p align="center">
  <img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1 align="center">osTicket - Post-Install Configuration</h1>

This tutorial outlines the post-install configuration of the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)  
- Remote Desktop  
- Internet Information Services (IIS)


<h2>Operating Systems Used</h2>

- Windows 10 (21H2)


<h2>Post-Install Configuration Objectives</h2>
- Configure Roles  
- Configure Departments  
- Configure Teams  
- Configure Agents  
- Configure Users  
- Configure SLA  
- Configure Help Topics

---

<h2>Configuration Steps</h2>

Welcome to the Post-Install Configuration tutorial for osTicket! Let's start by using RDP and going into our Azure Virtual Machine. Please refer to the previous installation instructions at [osTicket Prereqs](https://github.com/justinctollison/osticket-prereqs).  

Before we start, you'll want to open up your web browser inside the VM and go to both these links:  
- **Admin/Analyst Login Page:**  
  http://localhost/osTicket/scp/login.php  

- **End Users osTicket URL:**  
  http://localhost/osTicket  

We will be using the first link for configuring roles, departments, teams, users, SLAs, and help topics. The second link will be used as an end-user, viewing it to create tickets.  

<br>

<p align="center">
  <img width="1322" height="589" src="https://github.com/user-attachments/assets/17206fec-1f8b-42c1-8509-ee5a01aa82d1" />
  <br><br>
  <img width="1577" height="629" src="https://github.com/user-attachments/assets/a78b40fa-051f-4415-8342-aeb9c56a8707" />
</p>

---

First step, let's configure Roles inside the Admin Panel. Navigate to the Admin Login page and log in using the credentials you created previously. Make sure on the top-right of the page that you are in Admin view and not Agent view; both will have different settings and permissions.  

Once you are inside the Admin Panel, navigate to **Agents → Roles** and add a new Role. Let's name this role **Supreme Admin**, and in Permissions, check all permissions from Tickets, Tasks, and Knowledgebase. Add the role, and you should now see it in the list of roles.  

<br>

<p align="center">
  <img width="957" height="437" src="https://github.com/user-attachments/assets/e0261502-ec94-49cf-9839-b8245e727a19" />
</p>

---

After setting up the "Supreme Admin" role, navigate to **Departments** inside the same directory: **Admin Panel → Agents → Departments**.  

Create a new Department named **SysAdmins** and leave the Parent setting as **Top Level Department**. You can see in the settings that you can configure their SLA and other options, but leave these alone for now. Head into **Access** and note that we can add agents to this Department. Since we have no agents yet, click **Create Dept** at the bottom.  

<br>

<p align="center">
  <img width="955" height="885" src="https://github.com/user-attachments/assets/4bac11cf-cfa1-4940-b46a-1ddd99e1acbb" />
</p>

---

Next, move to the **Teams** tab inside **Agents → Departments**.  

We'll create a separate team. Teams are groups of people who are from different departments and can cross those boundaries, such as an Online Banking team that consists of Sysadmins and Help Desk support. It's essentially an organizational unit for people from different departments.  

Go ahead and create a new Team named **Online Banking**. Since we have no agents yet, leave **Team Lead** as *None* and create the team.  

<br>

<p align="center">
  <img width="956" height="700" src="https://github.com/user-attachments/assets/28ce84fd-b4e2-4071-a486-3ad7e7f8653e" />
</p>

---

Let's configure some settings to allow any users to create tickets. This way, if customers go to the website, they can immediately create a ticket without having to register.  

Navigate to **Settings → Users → Settings** and make sure **"Require registration and login to create tickets"** is unchecked.  

<br>

<p align="center">
  <img width="959" height="687" src="https://github.com/user-attachments/assets/cbc825a8-588a-4fef-8964-18657c5c37d8" />
</p>

---

Next, we’re going to configure some **Agents**. Agents are the workers inside the organization who handle tickets.  

In the **Admin Panel**, go to **Agents → Agents** and create two new agents, Jane Doe and John Doe. Fill out their details and use placeholder information for their email addresses.  

When you set the password, uncheck **"Send the agent a password reset email"** and manually enter one (for example, `Password1`).  

In **Access**, set their **Primary Department** to *SysAdmin* and assign them the **Supreme Admin** role. Double-check in permissions that they have everything from Supreme Admin.  

In **Teams**, add Jane to the *Online Banking* team and create her account. For John, do the same but assign him to the *Support* department and the *All Access* role. You can leave his team assignment empty.  

<br>

<p align="center">
  <img width="953" height="513" src="https://github.com/user-attachments/assets/398ff2ee-436f-4a44-8185-1c95ef031984" />
  <br><br>
  <img width="953" height="398" src="https://github.com/user-attachments/assets/98391d1d-85c7-41f4-b3a9-7ec3424674be" />
</p>

---

Now let's create some **Users** to simulate end-users creating tickets.  

Switch to the **Agent Panel** (top right corner) to ensure you’re not still in the Admin Panel. Go to **Users** and add a new User named *Karen*, using placeholder information for the email. Do the same for a second user named *Ken*.  

<br>

<p align="center">
  <img width="949" height="329" src="https://github.com/user-attachments/assets/d71fcf72-3901-4122-a9a0-c8ba52cb940b" />
</p>

---

Next, we’re going to configure **SLAs (Service Level Agreements)**. These determine how much time you have to respond to or complete specific tasks, such as tickets.  

Go to **Admin Panel → Manage → SLA** and create three different SLAs to define their severity:  
- **Sev-A** (Grace Period: 1 hour, Schedule: 24/7)  
- **Sev-B** (Grace Period: 4 hours, Schedule: 24/7)  
- **Sev-C** (Grace Period: 8 hours, Business Hours)  

Fill out the information above for each plan.  

<br>

<p align="center">
  <img width="957" height="662" src="https://github.com/user-attachments/assets/1db7c025-6f19-433a-8d67-b575a7d429a9" />
</p>

---

Lastly, let's configure our **Help Topics**.  

Help Topics are the categories that end-users choose when creating tickets. They help organize incoming requests.  

Navigate to **Admin Panel → Manage → Help Topics**. You’ll see a few listed already, but let’s add more:  
- Business Critical Outage (Report a Problem)  
- Personal Computer Issues (Report a Problem)  
- Equipment Request (General Inquiry)  
- Password Reset (Report a Problem)  
- Other (General Inquiry)  

Assign Parent topics to the new ones appropriately (for example, Business Critical Outage → Report a Problem). After adding each new Help Topic, navigate back and click **Add New** to continue.  

<br>

<p align="center">
  <img width="957" height="636" src="https://github.com/user-attachments/assets/be0e2661-8dbf-45c3-8093-07b01e5fb478" />
  <br><br>
  <img width="953" height="638" src="https://github.com/user-attachments/assets/10665d49-4ac6-4773-a4ba-81ae7471b152" />
</p>

---

So that concludes this part of the osTicket tutorial! You now have the initial setup for working and assigning tickets, from Users, Roles, Departments, and Teams to SLAs and Help Topics.  

Feel free to explore more settings or add additional descriptions and information to Help Topics, Departments, or any other configurations.  

We can now move on to simulating ticket creation as an end-user, receiving it as an agent, and completing the workflow.

---

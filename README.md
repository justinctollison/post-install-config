
<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Post-Install Configuration</h1>
This tutorial outlines the post-install configuration of the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Post-Install Configuration Objectives</h2>

- Configure Roles
- Configure Departments
- Configure Teams
- Configure Agents
- Configure Users
- Configure SLA
- Configure Help Topics

<h2>Configuration Steps</h2>

<p>
  Welcome to the Post-Install Configuration tutorial for osTicket! Let's start by using RDP and going into our Azure Virtual Machine. Please refer to the previous installation instructions at https://github.com/justinctollison/osticket-prereqs. Now, before we start, you'll want to open up your web browser inside the VM and go to both these links:
- Admin/Analyst Login Page:
http://localhost/osTicket/scp/login.php 
- End Users osTicket URL:
http://localhost/osTicket

We will be using the first link for configuring roles, departments, teams, users and even SLAs and help topics. Then, the second link will be used as an end-user, viewing it as a user to create tickets.
<br><br/>
<img width="1322" height="589" alt="image" src="https://github.com/user-attachments/assets/17206fec-1f8b-42c1-8509-ee5a01aa82d1" />
<img width="1577" height="629" alt="image" src="https://github.com/user-attachments/assets/a78b40fa-051f-4415-8342-aeb9c56a8707" />
</p>


<p>
First step, let's configure Roles inside the Admin Panel. You want to navigate to the Admin Login page and log in using the credentials you created previously. Make sure on the top-right of the page, that you are in Admin view and not Agent view, both will have different settings and permissions. Once you are inside the Admin Panel, navigate to Agents => Roles and then add a new Role. Let's name the definition for this role as "Supreme Admin," and then in Permissions, check all the permissions from Tickets, Tasks and Knowledgebase. Add the role and you should see it in the list of roles now.
</p>
<br />
<p>
<img width="957" height="437" alt="image" src="https://github.com/user-attachments/assets/e0261502-ec94-49cf-9839-b8245e727a19" />
</p>

<p>
After you're finished setting up the "Supreme Admin" role, we can now navigate to "Departments" inside the same directory, so it will be Admin Panel => Agents => Departments. In here let's create a new Department. We'll naem is "SysAdmins" and leave the Parent setting to Top Level Department. You can see in the settings that we can configure their SLA and other options, but let's leave these alone for now. Head into Access and see that we can add agents to this Department. Right now we have no agents, so go ahead and click Create Dept at the bottom.
</p>
<br />
<p>
<img width="955" height="885" alt="image" src="https://github.com/user-attachments/assets/4bac11cf-cfa1-4940-b46a-1ddd99e1acbb" />
</p>

<p>
Next move to the Teams tab inside Agents => Departments. We'll create a separate team. Teams are groups of people who are all from different departments and can cross those boundaries, like an Online Banking team that consists of Sysadmins and help desk support. It's essentially an organizational unit for people from different departments. So let's go ahead and create a new Team and name it "Online Banking" in our instance. Again, we have no agents yet so go ahead and leave Team Lead as -None- and create the team.
</p>
<br />
<p>
<img width="956" height="700" alt="image" src="https://github.com/user-attachments/assets/28ce84fd-b4e2-4071-a486-3ad7e7f8653e" />
</p>

<p>
Let's configure some settings to allow any users to create tickets, that way if we for instance have any customers that go to the website, they can immediately create a ticket without having to register an account and jump through any hoops. Let's navigate to the Settings tab and go to Users and then Settings. Make sure the "Require registration and login to create tickets" is Unchecked.
</p>
<br />
<p>
<img width="959" height="687" alt="image" src="https://github.com/user-attachments/assets/cbc825a8-588a-4fef-8964-18657c5c37d8" />
</p>

<p>
Next we're going to configure some agents. Agents are the actual workers inside our organization that will handle the tickets, such as Justin at Help Desk. Again, still in Admin panel, let's go to Agents => Agents and create a new Agent. Let's add two new agents, Jane Doe and John Doe. Fill out the details and add in a temporary or fake email, for us we're using janedoe@lognpacific.com. When you go to set the password, uncheck "Send the agent a password reset email" and then manually enter one. For us, we're doing "Password1". Then in Access tab, set their Primary Department to Sysadmin and let's give them the Supreme Admin role. Double-check in permissions that they are given everything that we gave in Supreme Admin. And finally in Teams, let's add jane to the Online Banking team and create her. For John, do the same thing except let's set his Department to Support and then give him the role of All Access. We can leave his assigned team as empty.
</p>
<br />
<p>
<img width="953" height="513" alt="image" src="https://github.com/user-attachments/assets/398ff2ee-436f-4a44-8185-1c95ef031984" />
<img width="953" height="398" alt="image" src="https://github.com/user-attachments/assets/98391d1d-85c7-41f4-b3a9-7ec3424674be" />
</p>

<p>
We'll start creating some Users really quick to simulate a User creating a ticket. Head into the Agent Panel on the top right, make sure you're not inside the Admin Panel still. Then head into Users and let's add a new User. Let's name this user as Karen and give them another fake email address. Do the same for a second user and let's name this one as Ken. Remember to save their credentials.
</p>
<br />
<p>
<img width="949" height="329" alt="image" src="https://github.com/user-attachments/assets/d71fcf72-3901-4122-a9a0-c8ba52cb940b" />
</p>

<p>
Next we're going to configure our SLAs or Service Level Agreements. These determine how much time that you have to do a specific task, if that's responding to a ticket or completing it. These include metrics for response and resolution times for our support tickets. So back into the Admin Panel and then go into Manage => SLA. We'll create 3 different SLAs that will go over their severity, so:
  -  Sev-A (Grace Period: 1 hour, Schedule: 24/7)
  -  Sev-B (Grace Period: 4 hours, Schedule: 24/7)
  -  Sev-C (Grace Period: 8 hours, Business Hours)

Go ahead and create 3 plans, filling out the information above with Name, Grace Period in hours and schedule
</p>
<br />
<p>
<img width="957" height="662" alt="image" src="https://github.com/user-attachments/assets/1db7c025-6f19-433a-8d67-b575a7d429a9" />
</p>

<p>
Lastly, let's configure our Help Topics. Help Topics are the categories that the end-user will choose when creating their ticket, it helps organize the tickets. It'll be inside Admin panel => Manage => Help Topics. You can see a few listed already, but let's add some more:
  - Business Critical Outage (Report a Problem)
  - Personal Computer Issues (Report a Problem)
  - Equipment Request (General Inquiry)
  -  Password Reset (Report a Problem)
  -  Other (General Inquiry)

Remember to assign the Parent topics to the new topics we're creating, for example a Business Critical Outage would be inside Report a Problem. Remember after adding the new Help Topic, to navigate back to the Help Topics and click Add New.
</p>
<br />
<p>
<img width="957" height="636" alt="image" src="https://github.com/user-attachments/assets/be0e2661-8dbf-45c3-8093-07b01e5fb478" />
<img width="953" height="638" alt="image" src="https://github.com/user-attachments/assets/10665d49-4ac6-4773-a4ba-81ae7471b152" />

</p>

<p>
So that concludes this part of the osTicket tutorial! You now have the intial setup for working and assigning tickets, from Users, Roles, Departments, Teams to SLAs and Help Topics. Feel free to dig around in the settings or add more descriptions and information to the Help Topics, Departments or any other settings. We can now move onto simulating creating the ticket as an end-user, getting the ticket as an agent and then working and completing the ticket.
</p>
<br />

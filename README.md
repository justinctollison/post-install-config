<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

# osTicket - Post-Install Configuration

This tutorial outlines the post-install configuration of the open-source help desk ticketing system osTicket.<br />

## Video Demonstration

- [YouTube: How to Install osTicket on an Azure Virtual Machine](https://www.youtube.com/watch?v=rIQClpfiJ70)


## Environments and Technologies Used

- Microsoft Azure (Virtual Machines/Compute)  
- Remote Desktop  
- Internet Information Services (IIS)

## Operating Systems Used

- Windows 10 (21H2)


## Post-Install Configuration Objectives

- 


## Configuration Steps

### Step 1: Create the Azure Virtual Machine

Start by creating a resource group in the Azure Portal and let's name it **osTicket** just for the sake of this lab. After creating the Resource Group, let's create a Virtual Machine inside it so we can keep everything contained. We will be using our Virtual Machine to install osTicket and will be using Remote Desktop Protocol (RDP) to use it. When you create your Virtual Machine, make sure to use Windows 10 in the image and to have at least 2 CPUs and 8gbs of memory. In my instance, I am using Standard D2s v6 (2 vcpus, 8 GiB memory).

<br>
<img width="1640" height="744" alt="image" src="https://github.com/user-attachments/assets/03745795-f018-4d64-8e13-1e18e9a38722" />
<br>

Once your VM is deployed and ready, use Remote Desktop to connect to it. You're going to use the public IPv4 address to sign in to it and whatever username you chose when you set up the Virtual Machine.

<br>
<img width="397" height="480" alt="image" src="https://github.com/user-attachments/assets/1d89cd4f-2e8d-4efb-992f-2222499c5620" />
<br>

---

### Step 2: Enabling Internet Information Services (IIS)

After connecting to your Virtual Machine, you will have to enable the Internet Information Services or IIS and CGI. This can be accessed by searching for the **Control Panel** in the Search Bar and then going to the **Control Panel** → **Uninstall a Program**. From inside here, there will be an option in the left panel called **Turn Windows features on or off**, with a shield icon. Select this option and then a list will appear titled **Windows Features**. Scroll down this list until you find the Internet Information Services and enable it. From inside Internet Information Services, go to **World Wide Web Services → Application Development Features** and then scroll down to **CGI** and enable that. This will enable us to use a web server with osTicket.

<br>
<img width="1141" height="639" alt="image" src="https://github.com/user-attachments/assets/bbeaa54d-e434-4d64-a24b-e0909a84d871" />
<br>

You can check this is working by going to `127.0.0.1` in your Web Bowser, this is the default webpage for IIS.

<br>
<img width="1180" height="725" alt="image" src="https://github.com/user-attachments/assets/a946e197-85c0-4fd3-9c25-ac9a6c3c4040" />
<br>

---

### Step 3: Download and Extract Required Files

Next, we're going to follow this [Google Drive Link](https://drive.usercontent.google.com/download?id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD&export=download&authuser=0) and download a folder that contains osTicket and all the dependencies to get osTicket working such as PHP, mySQL and HeidiSQL. Once the folder is done downloading, extract the entire folder. Feel free to extract it anywhere, but I like to extract it to the Desktop so I don't lose the folder and it's easy to access. The folder should be called **osTicket-Installation-Files**.

<br>
<img width="1121" height="632" alt="image" src="https://github.com/user-attachments/assets/7dadedce-6287-4977-a928-3b87824ce1ef" />
<br>

---

### Step 4: Installing PHP Manager and Rewrite Module

Now we're going to install the PHP Manager and Rewrite Module. PHP is a backend language that osTicket runs on, so we'll need to install it to get osTicket working. Go into the **osTicket-Installation-Files** that we extracted earlier and look for the PHPManager. Click next through all the menus and install it. Next, find the Rewrite Module and same as before, click through all the screens and install it. For the weblinks to work correctly, osTicket needs Rewrite.

<br>
<img width="1295" height="796" alt="image" src="https://github.com/user-attachments/assets/d7a410d1-e87e-40a8-8329-188c9e1de5bb" />
<br>

---

### Step 5: Create a PHP Directory in the C: Drive

We're going to create a new directory in our C: drive called **PHP**, it will look like `C:\PHP`. Navigate to your C: drive by opening up the Windows Explorer, the folder in the task bar. Then navigate to **This PC → C: drive**. Once inside your C: drive, it should list out some folders, such as `inetpub`, `Program Files (x86)`, and `Users`. Right-click inside the C: drive and add a **New Folder** named `PHP`. After you've created the PHP Folder, navigate back to the **osTicket-Installation-Files folder**. Inside here we're going to take the **PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip)** and unzip or extract it INTO the PHP folder we just created. When the Select Destination option comes up, you can just enter `C:\PHP` then extract. These are the binaries needed for the osTicket server to use.

<br>
<img width="1591" height="644" alt="image" src="https://github.com/user-attachments/assets/cf412c20-1251-4fcb-98b9-c8292c541e32" />
<br>

---

## Conclusion

Congratulations! You now have your very own help desk set up and installed on your Virtual Machine using osTicket. This is a great start to practicing with ticketing services.  

You can log in and explore both the admin and end-user portals using the links below:

- **Admin/Login Page:** [http://localhost/osTicket/scp/login.php](http://localhost/osTicket/scp/login.php)  
- **End User Page:** [http://localhost/osTicket/](http://localhost/osTicket/)

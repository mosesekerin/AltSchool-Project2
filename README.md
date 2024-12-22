**Project Documentation**

---

### 1. Project Details

**Project Name:**
Building a Start-up Web Application Prototype  

**Subtitle:**
Innovating the Cloud, Securing the Future  

**Project Overview:**
This project showcases the process of building a functional prototype for a start-up web application. The objective is to demonstrate technical expertise in cloud infrastructure, server provisioning, web development, and server security.  
By setting up a secure and accessible landing page, this project highlights key technical skills essential for cloud engineering, server development, and DevSecOps roles. The core focus is to provision, configure, and secure a Linux-based web server on AWS, while also creating a user-friendly responsive landing page. This page serves as a visual representation of the start-up's potential, designed to impress investors with technical proficiency and creativity.  

---

### 2. Local Development

**Files Created:**
1. **index.html**
   - Purpose: Landing page
   - Associated CSS File: index.css

2. **About-project.html**
   - Purpose: Page detailing the project
   - Associated CSS File: About-project.css

3. **About-Me.html**
   - Purpose: Page providing information about the author
   - Associated CSS File: About-Me.css

**Development Tools and Environments:**
- **Code Editor:** Visual Studio Code (VS Code)
- **Testing Environment:**
  - Virtual machine set up using Vagrant
  - Local server configured for development and testing
- **Cloud Environment:** AWS EC2 instance for deployment and further testing

---

### 3. Server Configuration

**Local Server Configuration:**
- **Software Used:** Vagrant
- **Operating System:** Ubuntu Server
- **Directory Structure:** Project files stored in `/var/www/2nd-Semester-Project/`
- Tested locally before deployment to the AWS EC2 instance.

**Remote Server Configuration:**
- **Instance Type:** t2.micro
- **Operating System:** Linux (Ubuntu)

**EC2 Instance Configuration Steps:**
1. **Launch EC2 Instance:**
   - Configured using AWS Management Console.
   - Selected t2.micro instance with Ubuntu as the operating system.
2. **Networking Configuration:**
   - Configured a security group to allow HTTP (port 80) and SSH (port 22) access.
3. **Set Up the Apache Web Server:**
   - Installed Apache using the command:
     ```bash
     sudo apt install apache2
     ```
   - Verified the installation by accessing the instance's public IP address in a browser.
4. **Project Directory on EC2:**
   - Files were stored in `/var/www/2nd-Semester-Project/` on the EC2 instance.
   - Ensured proper ownership and permissions for the Apache web server.

---

### 4. File Transfer

**Method Used for File Transfer:**
- **Tool:** Secure Copy Protocol (SCP)
- **Command Used:**
  ```bash
  scp -i ~/.ssh/AltSchool.pem -r /var/www/1st-Semester-Project /var/www/2nd-Semester-Project ubuntu@35.179.104.90:/home/ubuntu/
  ```

**File Placement on Remote Server:**
- **Initial Destination Directory:** Files were initially placed in `/home/ubuntu` on the remote server.
- **Final Destination Directory:** Files were moved from `/home/ubuntu` to `/var/www/` on the remote server for proper hosting by the Apache web server.

---

### 5. Networking Configuration

**Public Access Configuration:**
- **Method Used:** Configured via AWS Management Console, specifically through the Security Group settings.
- **Security Group Configuration:**
  - Allowed Port 22 for SSH access.
  - Allowed Port 80 for HTTP access.
  - Allowed Port 443 for HTTPS access.
  - Set access permissions to Anywhere (0.0.0.0/0) for each of these ports.

**Port Details:**
- **Port 22:** Enabled for SSH connections.
- **Port 80:** Enabled for HTTP traffic.
- **Port 443:** Enabled for HTTPS traffic.

**Verification of Public Access:**
- **Method:** Verified by accessing the website via the public IP address: `35.179.104.90`.
- Successfully accessed the hosted website to confirm proper network configuration.

---

### 6. HTTPS/SSL Setup

**Type of SSL Used:**
- A self-signed certificate was used for testing.

**Commands Used:**
- Generated a self-signed certificate and configured it in the web server’s configuration file.
- Set up the file paths for the key and certificate.

**Outcome:**
- HTTPS worked successfully but was marked "Not Secure," as expected with a self-signed certificate.

---

### 7. Version Control

**Local Git Repository:**
- Initialized a Git repository in `/var/www/2nd-Semester-Project/`.
- Commands Used:
  ```bash
  git init
  git add .
  git commit -m "Initial commit"
  ```

**GitHub Repository:**
- **Repository URL:** https://github.com/AltSchool-Project2
- **Steps:**
  - Set up a new repository on GitHub.
  - Generated an SSH key pair on the EC2 instance.
  - Added the public key to the GitHub account for secure access.
  - Pushed the local repository to GitHub using:
    ```bash
     git remote add origin git@github.com:mosesekerin/AltSchool-Project2.git
    git push -u origin main
    ```

---

### 8. Challenges and Solutions

**Challenges:**
1. Difficulty using Let's Encrypt free SSL certificates due to the lack of a valid domain name.
2. Financial constraints prevented purchasing a domain name.

**Solutions:**
- Used a self-signed certificate for testing and configured the server to make HTTPS requests.
- Although the connection was marked "Not Secure," this approach allowed HTTPS functionality during testing.

---

### 9. Final Deliverables

**Public IP Address:** `35.179.104.90`

**GitHub Repository URL:** https://github.com/mosesekerin/AltSchool-Project2/

---

### 10. Acknowledgments

Special thanks to AltSchool’s Cloud Engineering program for providing the resources and guidance to execute this project successfully. Appreciation also goes to my circle lead, and my instructor for their invaluable support throughout the project.


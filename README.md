
**Second Semester Project: Deploying a Multi-Page HTML and CSS Website on AWS EC2 Instance**

This documentation outlines the step-by-step process of provisioning a Linux server, deploying a multi-page website with HTML and CSS files, and configuring networking to make the project accessible. Additionally, it includes integrating the project into a GitHub repository for version control.

**Project Overview**
The objective of this project was to:
1. Create a multi-page website using HTML and CSS.
2. Set up a Linux server on AWS EC2.
3. Transfer the project files securely from a local server to the remote EC2 instance.
4. Configure the EC2 instance to host the website and make it accessible via a public IP.
5. Configure HTTPS using a testing SSL certificate.
6. Push the project to GitHub for version control and future enhancements.


**Steps Undertaken**

**1. Local Development**

Code Editor: Visual Studio Code (VS Code) was used for local development.

Files Created:
-HTML Files:
  index.html (Landing Page)
  about.html (About Me Page)
  project.html (About the Project Page)

-CSS Files:
  style.css (for index.html)
  about.css (for about.html)
  project.css (for project.html)

Each HTML file was linked to its respective CSS file for styling.


**2. Setting Up the Local Server**

-Environment: Vagrant was used to create and manage the local development server.
-Directory Structure: Files were placed in the designated directory on the local server for testing.


**3. Transferring Files to AWS EC2 Instance**

-Tool Used: Secure Copy Protocol (SCP) was utilized to transfer the files securely.
-Command Executed: scp -i <key.pem> -r /path/to/local/project ubuntu@<EC2_PUBLIC_IP>:/var/www/html/second-semester-project/
-Files Location on EC2: /var/www/html/second-semester-project/


**4. Configuring the Remote Server**

-Server Environment: AWS EC2 instance running Ubuntu 20.04.
-Web Server Installed: Apache HTTP Server.
-Installation Command: sudo apt update && sudo apt install apache2 -y
-Default Directory for Files: /var/www/html/

**Networking Configuration:**
a. Allowed inbound HTTP traffic (port 80) using the AWS Management Console.
b. Verified public IP accessibility: http://<EC2_PUBLIC_IP>/second-semester-project/


**5. Configuring HTTPS with Testing SSL**

-Objective: Configure HTTPS using a testing SSL certificate due to financial constraints and the absence of a domain name.

**Challenges:**
a. Free SSL certificates such as Let’s Encrypt require a valid domain name for installation.
b. Financial constraints made it impossible to purchase a domain or premium SSL certificate.

**Solution:**
a. Used a testing SSL certificate.
b. Configured the server to make requests via HTTPS, although the connection was marked as "Not Secure."

**Commands Used:**
-Installed openssl to generate the testing certificate:
  sudo apt install openssl
  sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/apache-selfsigned.key -out /etc/ssl/certs/apache-selfsigned.crt

Configured Apache to use the testing certificate: sudo nano /etc/apache2/sites-available/default-ssl.conf

-Updated the file to include:
  SSLEngine on
  SSLCertificateFile      /etc/ssl/certs/apache-selfsigned.crt
  SSLCertificateKeyFile /etc/ssl/private/apache-selfsigned.key

-Enabled SSL on Apache:
  sudo a2enmod ssl
  sudo a2ensite default-ssl.conf
  sudo systemctl reload apache2

Verified HTTPS accessibility: https://<EC2_PUBLIC_IP>/second-semester-project/
Outcome: While the connection was functional via HTTPS, it was marked as "Not Secure" due to the self-signed certificate.


**6. Version Control with Git**

Local Git Repository:
-Initialized a Git repository on the EC2 instance:
  cd /var/www/html/second-semester-project/
  git init

-Added files to the repository:
  git add .
  git commit -m "Initial commit for second semester project"

GitHub Repository: Created a new repository on GitHub for the project.

-Connected the local repository to the remote GitHub repository using SSH:
  git remote add origin git@github.com:<YourUsername>/<RepositoryName>.git
  git push -u origin main


**7. Final Verification**

Website Access: Verified that the website is accessible via the EC2 public IP or public DNS over HTTP and HTTPS.
GitHub Repository: Ensured that all files are pushed and available for review.

**Deliverables:**
a. Public IP Address: [INSERT_PUBLIC_IP_HERE]
b. GitHub Repository URL: [INSERT_GITHUB_REPO_URL_HERE]
c. Directory Path on Server: /var/www/html/second-semester-project/

**Useful Commands**
a. Restart Apache: sudo systemctl restart apache2
b. Check Apache Status: sudo systemctl status apache2
c. Firewall Rules: sudo ufw allow 'Apache Full'


**Acknowledgments**
Special thanks to the AltSchool Cloud Engineering program for providing the resources and guidance to execute this project successfully.



﻿<!DOCTYPE html>
  <html lang="en">
<head></head>
<body>
    <div class="container">
        <h1>Guide to Deploying a Static Website on AWS EC2 Using Apache</h1>
        
  <h2>Step-by-Step Guide</h2>
        
   <h3>Step 1: Launch an EC2 Instance</h3>
        <ul>
            <li>Log in to AWS Management Console:</li>
            <li>Navigate to the EC2 Dashboard.</li>
            <li>Launch a New Instance:</li>
            <li>Click on "Launch Instance".</li>
            <li>Choose an Amazon Machine Image (AMI). Select the Ubuntu Server AMI (Ubuntu 20.04 LTS recommended).</li>
            <li>Choose an Instance Type (e.g., t2.micro for free tier eligibility).</li>
            <li>Configure Instance:</li>
            <li>Select an existing key pair or create a new one. Download the key pair (.pem file).</li>
            <li>Configure Security Group:</li>
            <li>Create a new security group.</li>
            <li>Add a rule to allow SSH (port 22) and HTTP (port 80) from anywhere (0.0.0.0/0).</li>
            <li>Review your settings and click "Launch".</li>
        </ul>
         <h3>Step 2: Connect to Your EC2 Instance</h3>
        <ul>
            <li>Open a Terminal/PowerShell:</li>
            <li>Navigate to the directory containing your <code>.pem</code> file.</li>
            <li>Connect to the Instance:</li>
             
          ssh -i "path/to/your-key.pem" ubuntu@your-ec2-instance-public-ip
   <h3>Step 3: Install and Configure Apache</h3>
        <ul>
            <li>Update the Package Lists:</li>
          
            sudo apt update
  <li>Install Apache:</li>
  
            sudo apt install apache2 -y
  <li>Check Apache Status:</li>
  
            sudo systemctl status apache2
  <li>Apache should be active (running).</li>
        </ul>
        
   <h3>Step 4: Deploy Your Static Website</h3>
        <ul>
          
   <li>Upload Your Website Files:</li>
            <li>open another Terminal; copy your website files to the server.</li>
            
            scp -i "path/to/your-key.pem" -r path/to/your-website/* ubuntu@your-ec2-instance-public-ip:/tmp/
  <li>Move Files to the Web Root:</li>
            <li>return to the terminal already connected to your Ec2 server and move the files to the Apache web root</li>
            
            sudo mv /tmp/* /var/www/html/
  <li>Verify Deployment:</li>
            <li>Open your web browser and paste your instance's public IP address (e.g., <a href="http://your-ec2-instance-public-ip" target="_blank">http://54.208.104.210/ </a>).</li>
             </ul>
    </div>
</body>
</html>

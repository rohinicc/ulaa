🚀 2-Tier Application Deployment using Tomcat & Maven

This document explains the complete step-by-step process to deploy a Java application on Apache Tomcat using Maven.

🧱 Step 1: Create an EC2 Instance

Launch a Linux instance (Ubuntu preferred)

Allow ports 22 (SSH) and 8080 (Tomcat) in security group

🔗 Step 2: Connect to Instance using MobaXterm
ssh -i key.pem ubuntu@<EC2-PUBLIC-IP>

🔐 Step 3: Switch to Root User
sudo su -

🔄 Step 4: Update the Machine
apt update -y
apt upgrade -y

🌐 Step 5: Download Apache Tomcat Server
wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.115/bin/apache-tomcat-9.0.115.tar.gz

📦 Step 6: Extract Tomcat Tar File
tar -xvzf apache-tomcat-9.0.115.tar.gz

⚙️ Step 7: Configure Tomcat Users (Manager/Admin Access)
🔹 Edit tomcat-users.xml
vi apache-tomcat-9.0.115/conf/tomcat-users.xml

🔹 Add the following roles and user:
<role rolename="manager-gui"/>
<role rolename="manager-script"/>
<role rolename="manager-jmx"/>
<role rolename="manager-status"/>
<user username="admin" password="admin" 
roles="manager-gui,manager-script,manager-jmx,manager-status"/>

🔓 Step 8: Disable IP Restriction for Manager App
🔹 Edit context.xml
vi apache-tomcat-9.0.115/webapps/manager/META-INF/context.xml

🔹 Comment the following lines:
<!--
<Valve className="org.apache.catalina.valves.RemoteAddrValve"
       allow="127\.\d+\.\d+\.\d+|::1"/>
-->

🛠️ Step 9: Install Maven
bash <(curl -sL https://tinyurl.com/52ykfnu5)

🔹 Verify Maven
mvn -version

☕ Step 10: Install Java
apt install openjdk-17-jdk -y

🔹 Verify Java
java -version

🔄 Step 11: Activate Environment Variables
source ~/.bashrc

📥 Step 12: Clone Git Repository & Build Project
git clone <PROJECT-GIT-URL>
cd project
mvn clean package

▶️ Step 13: Start Tomcat Server
sh apache-tomcat-9.0.115/bin/startup.sh

📤 Step 14: Deploy Application to Tomcat
cp target/project.jar apache-tomcat-9.0.115/webapps/

🌍 Step 15: Access Tomcat Server
http://<EC2-PUBLIC-IP>:8080

🔹 Tomcat Manager App
http://<EC2-PUBLIC-IP>:8080/manager


Username: admin

Password: admin

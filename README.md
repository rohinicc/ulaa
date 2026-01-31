🧩 ULAA – Maven Web Application Deployment on Apache Tomcat

This project demonstrates how to build and deploy a Maven-based Java web application (.war) on Apache Tomcat 9 using Java 17.

📌 Prerequisites

Make sure the following are installed on your system:

Java JDK 17

Apache Maven 3.9.12

Apache Tomcat 9.0.115

Git

Linux-based environment (Ubuntu / AWS EC2 preferred)

⚙️ Installation & Setup
1️⃣ Clone the Repository
git clone https://github.com/rohinicc/ulaa.git
cd ulaa

2️⃣ Build the Project Using Maven
mvn clean package


✅ On success, the WAR file will be generated at:

target/ulaa.war

3️⃣ Start Apache Tomcat
sh apache-tomcat-9.0.115/bin/startup.sh


✔️ Tomcat will start on the default port 8080

4️⃣ Deploy the WAR File to Tomcat
cp target/ulaa.war apache-tomcat-9.0.115/webapps/


Tomcat will automatically extract and deploy the application.

🌐 Access the Application

Open your browser and visit:

http://<server-ip>:8080/ulaa


Example:

http://localhost:8080/ulaa

📂 Project Structure
ulaa/
├── src/
│   └── main/
│       └── webapp/
│           └── index.jsp
├── target/
│   └── ulaa.war
├── pom.xml
└── README.md

🛠 Tech Stack

Java 17

Maven

Apache Tomcat 9

JSP / Servlet-based Web App

✅ Build Status

✔ Maven Build: SUCCESS
✔ WAR Packaging: SUCCESS
✔ Deployed on Tomcat: SUCCESS

🚀 Future Enhancements

Add CI/CD using GitHub Actions or Jenkins

Dockerize the application

Add logging and monitoring

Secure with HTTPS & reverse proxy (NGINX)

👩‍💻 Author

Scripted & Deployed with ❤️ by a DevOps learner
Special thanks to the Maven & Tomcat open-source community.

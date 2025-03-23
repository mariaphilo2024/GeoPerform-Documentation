# **SonarQube for GeoPerform**

## **Introduction**
SonarQube is a **quality management tool** developed by **SonarSource**.

- Developed in **Java**, making it platform-independent.  
- Can be installed on **Windows**, **Linux**, and **Mac**.  
- Detects **bugs**, **vulnerabilities**, and **code smells** in over **30 programming languages**.  
### **Key Features:**
- **Static code analysis** to automatically detect bugs.  
- Helps developers fix issues **before production**.  
- Highlights complex code areas with poor unit test coverage.  
- Detects **duplicate code** and suggests improvements.  
- Uses a set of **rules** for:  
   - Security checks  
   - Maintainability checks  
   - Bug detection  
- Manages test quality through **code coverage reports** for:  
   ✅ Unit tests  
   ✅ QA tests  
   ✅ User Acceptance Tests  

---
## **SonarQube Editions**
| Edition | Description |
|---------|-------------|
| **Community Edition** | Free, supports **17 languages** with limited features. |
| **Developer Edition** | Supports more languages and includes security rules. |
| **Enterprise Edition** | Supports more languages and includes advanced features like security analysis and reporting. |

---

## **SonarQube Metrics**
| Metric | Description |
|--------|-------------|
| **Bugs** | Code errors that can lead to malfunction. |
| **Vulnerabilities** | Potential security issues. |
| **Code Smells** | Poor coding practices that reduce maintainability. |
| **Coverage** | Percentage of code covered by unit tests. |
| **Duplications** | Percentage of duplicated code. |
| **Complexity** | Measures how difficult the code is to understand. |

---

## **Architecture of SonarQube**

## **SonarQube has two main parts:**
1. **SonarQube Scanner** – Scans source code and sends analysis reports to the SonarQube server.  
2. **SonarQube Server**  

### **SonarQube Server has three parts:**
1. **Rules** – Contains predefined and custom rule sets for code analysis.  
2. **Web UI** – Displays reports and analysis results.  
3. **Database** – Stores code analysis reports, metrics, and historical data.

   ![image](https://github.com/user-attachments/assets/4d750460-8e80-424f-bb73-7aaaf9d157df)


   ## **How SonarQube Works**
1. **Scanner reads the source code.**  
2. Scanner connects to the **database** to fetch and download rules.  
3. Scanner applies rules to the source code.  
4. Scanner generates reports based on code analysis.  
5. Reports are stored in the **database**.  
6. Reports are accessed through the **dashboard** in the web frontend.  
7. Developers can see:  
   ✅ Who introduced the issue  
   ✅ What the issue is  
   ✅ When the issue was introduced  
   ✅ How to fix the issue  

---

## **Setting Up SonarQube Locally**
### **Step 1: Download SonarQube**
- Download SonarQube from [https://www.sonarqube.org](https://www.sonarqube.org).  
- Requires **Java 8+**.  

---

### **Step 2: Start SonarQube**
1. Go to the **SonarQube Folder**.  
2. Navigate to the **Bin folder** → **Windows 64**.  
3. Double-click on `StartSonar ` - Windows batch file file.  
4. Once **"SonarQube is up"** message appears:  
   - Open browser → Visit **localhost:9000** (default port).  
   - Login using:  
     - **Username:** `admin`  
     - **Password:** `admin`  
   - Update with a new password.
  
     ![image](https://github.com/user-attachments/assets/906e2308-5b78-4207-9a5b-a67e497ec7ca)

     - Select Manually


---

### **Step 3: Create a New Project**
1. Go to **Projects** → **Create Project**.  
2. Enter **Project Display Name** → **Project Key** is generated automatically.  
3. Select **SetUp** → Choose **Local**.

   ![image](https://github.com/user-attachments/assets/dc751e8f-8818-4934-bed8-4e098b867db7)


---

### **Step 4:Select Locally**

![image](https://github.com/user-attachments/assets/bc5f3727-f34d-40f2-8d2c-315f5a0e4c26)

---

### **Step 5: Generate Token**
1. Provide a **Token Name** → Click **Generate**.  
2. Copy the token and keep it safe.  
3. Click **Continue**.

   ![image](https://github.com/user-attachments/assets/05f4275c-8319-43ad-8c21-8096a6719dd1)


---

### **Step 6: Select Language**
1. Choose the programming language for the project.  
2. Copy the executable code provided.

   ![image](https://github.com/user-attachments/assets/0b5843ca-71fd-4d38-9228-af67a47d3430)


---

### **Step 7: Run the Scan**
1. Open **Command Prompt**.  
2. Go to the project folder.  
3. Run the command: - Paste the executable code and enter 

<copied-executable-code>
Once the build is successful:

Go to localhost:9000 in the browser.

View the SonarQube report for the project.

---

# SonarQube Setup on Ubuntu VM using Docker

- This document provides a step-by-step guide to setting up **SonarQube** on an **Ubuntu Virtual Machine (VM)** using **Docker**.

## Step 1: Install PuTTY and Connect to Ubuntu VM Using PPK Key
1. Download and Install **PuTTY**
   - Visit **[PuTTY’s official download page](https://www.putty.org/)** and install the application.
2. Connect to the VM:
   
 -  Open PuTTY.

- Enter your VM’s IP address in the “Host Name (or IP address)” field.

- In the left-hand menu, go to "Connection" > "SSH" > "Auth."

- Under "Auth," click "Browse" and select your . ppk key file.

- Click "Open" to start an SSH session with the VM.

 ## Step 2: Install Docker on the VM and Pull Required Images
 - Install Docker:

**Update the package list:**

 ```
sudo apt update
 ```
- Install Docker:  
 ```
sudo apt install docker.io -y
 ```
### Start and Enable Docker Service:
- Start Docker immediately:

 ```
  sudo systemctl start docker
 ```
- Enable Docker to start on boot:

 ```
  sudo systemctl enable docker
```
### 1. Pull SonarQube and PostgreSQL Images:

- Pull the latest SonarQube image:

 ```
  docker pull sonarqube:latest
 ```
- Pull the latest PostgreSQL image:
 ```
docker pull postgres:latest
 ```

 ## Step 3: Run PostgreSQL and SonarQube Containers

### 1. Start PostgreSQL Container:
- Run the following command to create a PostgreSQL container with a username and password:

    ```
      docker run -d --name postgres -e
      POSTGRES_USER=sonar -e
      POSTGRES_PASSWORD=your_password -e
      POSTGRES_DB=sonar_db postgres:latest
    ```
- Replace your_password with a secure password.

 ### 2. Start SonarQube Container:
 - Run the SonarQube container and link it to the PostgreSQL container:

     ```  
         docker run -d --name sonarqube -p 9000:9000
         --network sonarnet --env
         SONARQUBE_JDBC_URL=jdbc:postgresql://postgres
         :5432/sonar_db --env
         SONARQUBE_JDBC_USERNAME=sonar --env
         SONARQUBE_JDBC_PASSWORD=your_password
         sonarqube:latest
      ```

 ## Step 4: Access SonarQube Web Interface
 ###   1. Open SonarQube:
    
- In a web browser, go to http://<vm-ip>:9000 (replace <vm-ip> with your actual VM IP address).
    
 ###    2. Log In:
 - Use the default username and password: admin / admin.

## SonarQube Analysis Report

SonarQube analysis for the projects displayed on the dashboard. The report includes **Quality Gate status, Security issues, Reliability, Maintainability, Code Coverage, and Duplications**.


   ![image](https://github.com/user-attachments/assets/5f2d3e45-fded-4940-8c9d-0b3557d874c4)

  



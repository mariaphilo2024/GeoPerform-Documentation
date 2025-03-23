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

# SonarQube Setup on Ubuntu VM using Docker

This document provides a step-by-step guide to setting up **SonarQube** on an **Ubuntu Virtual Machine (VM)** using **Docker**.

## Step 1: Install PuTTY and Connect to Ubuntu VM Using PPK Key
1. Download and Install PuTTY
   o Visit PuTTY’s official download page and install the application.





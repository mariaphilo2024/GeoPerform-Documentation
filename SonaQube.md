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



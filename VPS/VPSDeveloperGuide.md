# **Setting Up the Local Development Environment for VPS**

## **Prerequisites**

### **Required Software**
- **Microsoft Visual Studio Community 2022 (64-bit)** – Version 17.12.2  
- **.NET version** – 9.0.100  

---

## **Clone the Repository**
- [https://github.com/Geoservedmcc/gp-master-api.git](https://github.com/Geoservedmcc/gp-master-api.git)  
- [https://github.com/Geoservedmcc/gp-data-model.git](https://github.com/Geoservedmcc/gp-data-model.git)  
- [https://github.com/Geoservedmcc/gp-user-api.git](https://github.com/Geoservedmcc/gp-user-api.git)  
- [https://github.com/Geoservedmcc/gp-voyage-api.git](https://github.com/Geoservedmcc/gp-voyage-api.git)  
- [https://github.com/Geoservedmcc/gp-reportengine-api.git](https://github.com/Geoservedmcc/gp-reportengine-api.git)  

---

## **Open Solution in Visual Studio**
1. Open **VoyagesSolution.sln** (or User API, Master API) in Visual Studio.  
2. Refer to **VPS Backend Dependencies** and install the required packages.  

---

## **Refer Data Solution**
1. In Solution Explorer, under the project, right-click on **Dependencies**.  
2. Select **‘Add Project Reference’** → Select **Browse** → Add **‘Data.Solution.dll’**.  
3. For Report API, no need to connect to Data Solution.  

---

## **Configure Environment**
### **For QA**
1. In Solution Explorer, open **appsettings.json** and enable:

{
  "AllowedHosts": "*",
  "AzureVaultCredentials": {
    "vaultAddress": "https://gp-qa-vault.vault.azure.net/",
    "clientId": "084b5ae2-a0de-40f7-987e-506b71dfed64",
    "clientSecret": 
  }
}

## **Run the Application**
1. Run the application using:  
   **Ctrl + F5**  
2. Swagger will open automatically.  

---

## **Authorization for Swagger UI**
1. Run VPS Application in QA Environment.  
2. Ensure **VPN** is connected.  
3. Right-click → Inspect → Network tab → Select **Headers** → Copy the token.  
4. Paste the token in Swagger authorization → Test CRUD operations.  

---

## **UI Setup – Angular (Web)**
### **Pre-Requirements**
- **Angular version** – 14.0.0  
- **Visual Studio Code**  
- **npm**  
- **Angular CLI**  
- **Node.js**  

---

### **Clone the Frontend Repository**
- [https://github.com/Geoservedmcc/gp-website.git](https://github.com/Geoservedmcc/gp-website.git)  

---

### **Refer to VPS Frontend Dependencies**
- Install required packages.  

---

### **Run the Angular App**
1. Open `gp-website.code-workspace` in VS Code.  
2. Install dependencies:  
```bash
npm install --force
### **Start the Development Server**
```bash
npm start
- Open [http://localhost:4200](http://localhost:4200) to view the app.  
- Check out the Angular CLI Documentation.  

---

## **Logs & Debugging**
- Logs are stored in the **/logs** folder.  

---

## **Troubleshooting**
| Issue | Solution |
|-------|----------|
| **Unable to connect to the database** | Verify VPN connection. |
| **Backend not running** | Check .NET SDK version and installed dependencies. |
| **Frontend build fails** | Run `npm install` and ensure correct Angular CLI version. |

---

## **Conclusion**
By following these steps, you should have a fully functional local QA environment for VPS.  

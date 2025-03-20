# **Setting Up the Local Development Environment for VPS**

## **Prerequisites**

### **Required Software**
- **Microsoft Visual Studio Community 2022 (64-bit)** – Version 17.12.2  
- **.NET version** – 9.0.100  

---

## **Clone the Repository**
- https://github.com/Geoservedmcc/gp-master-api.git  
- https://github.com/Geoservedmcc/gp-data-model.git  
- https://github.com/Geoservedmcc/gp-user-api.git  
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
```json
{
  "AllowedHosts": "*",
  "AzureVaultCredentials": {
    "vaultAddress": "https://gp-qa-vault.vault.azure.net/",
    "clientId": "084b5ae2-a0de-40f7-987e-506b71dfed64",
    "clientSecret": 
  }
}

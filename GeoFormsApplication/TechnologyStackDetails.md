# GeoForms Technology Stack Details

## 1. .NET Version
- **Version:** .NET 9.0.100
- **Target Framework:** .NET 7.0

## 2. Angular Version
- **Version:** 15.0.1

## 3. SQL Server Version
- **Microsoft SQL Server 2022 (RTM-GDR) (KB5046861)**
- **Version:** 16.0.1135.2 (X64)
- **Edition:** Express Edition (64-bit)
- **OS:** Windows 10 Enterprise 10.0 (Build 26100: Hypervisor)

---

## 4. Backend Dependencies (.NET)

### GeoForms.Domain
- Volo.Abp.AuditLogging.Domain (7.0.1)
- Volo.Abp.BackgroundJobs.Domain (7.0.1)
- Volo.Abp.Emailing (7.0.1)
- Volo.Abp.FeatureManagement.Domain (7.0.1)
- Volo.Abp.Identity.Domain (7.0.1)
- Volo.Abp.OpenIddict.Domain (7.0.1)
- Volo.Abp.PermissionManagement.Domain.Identity (7.0.1)
- Volo.Abp.PermissionManagement.Domain.OpenIddict (7.0.1)
- Volo.Abp.SettingManagement.Domain (7.0.1)
- Volo.Abp.TenantManagement.Domain (7.0.1)

### GeoForms.Application
- Azure.Identity (1.8.2)
- HtmlAgilityPack (1.11.46)
- MailKit (3.6.0)
- Microsoft.AspNet.WebApi.Core (5.3.0)
- Microsoft.Extensions.Configuration (7.0.0)
- Microsoft.Graph (5.9.0)
- Microsoft.Graph.Core (3.0.6)
- Microsoft.IdentityModel.Clients.ActiveDirectory (5.3.0)
- Newtonsoft.Json (13.0.3)
- NUnit (3.13.3)
- NUnit3TestAdapter (4.4.2)
- Volo.Abp.Account.Application (7.0.1)
- Volo.Abp.FeatureManagement.Application (7.0.1)
- Volo.Abp.Identity.Application (7.0.1)
- Volo.Abp.PermissionManagement.Application (7.0.1)
- Volo.Abp.SettingManagement.Application (7.0.1)
- Volo.Abp.TenantManagement.Application (7.0.1)

### GeoForms.EntityFrameworkCore
- Microsoft.EntityFrameworkCore.Tools (7.0.1)
- Volo.Abp.AuditLogging.EntityFrameworkCore (7.0.1)
- Volo.Abp.BackgroundJobs.EntityFrameworkCore (7.0.1)
- Volo.Abp.EntityFrameworkCore.SqlServer (7.0.1)
- Volo.Abp.FeatureManagement.EntityFrameworkCore (7.0.1)
- Volo.Abp.Identity.EntityFrameworkCore (7.0.1)
- Volo.Abp.OpenIddict.EntityFrameworkCore (7.0.1)
- Volo.Abp.PermissionManagement.EntityFrameworkCore (7.0.1)
- Volo.Abp.SettingManagement.EntityFrameworkCore (7.0.1)
- Volo.Abp.TenantManagement.EntityFrameworkCore (7.0.1)

### GeoForms.Domain.Shared
- Microsoft.Extensions.FileProviders.Embedded (7.0.0)
- NETStandard.Library (2.0.3)
- Volo.Abp.AuditLogging.Domain.Shared (7.0.1)
- Volo.Abp.BackgroundJobs.Domain.Shared (7.0.1)
- Volo.Abp.FeatureManagement.Domain.Shared (7.0.1)
- Volo.Abp.Identity.Domain.Shared (7.0.1)
- Volo.Abp.OpenIddict.Domain.Shared (7.0.1)
- Volo.Abp.PermissionManagement.Domain.Shared (7.0.1)
- Volo.Abp.SettingManagement.Domain.Shared (7.0.1)
- Volo.Abp.TenantManagement.Domain.Shared (7.0.1)

### GeoForms.Application.Contracts
- NETStandard.Library (2.0.3)
- Volo.Abp.Account.Application.Contracts (7.0.1)
- Volo.Abp.FeatureManagement.Application.Contracts (7.0.1)
- Volo.Abp.Identity.Application.Contracts (7.0.1)
- Volo.Abp.ObjectExtending (7.0.1)
- Volo.Abp.PermissionManagement.Application.Contracts (7.0.1)
- Volo.Abp.SettingManagement.Application.Contracts (7.0.1)
- Volo.Abp.TenantManagement.Application.Contracts (7.0.1)

### GeoForms.HttpApi
- Volo.Abp.Account.HttpApi (7.0.1)
- Volo.Abp.FeatureManagement.HttpApi (7.0.1)
- Volo.Abp.Identity.HttpApi (7.0.1)
- Volo.Abp.PermissionManagement.HttpApi (7.0.1)
- Volo.Abp.SettingManagement.HttpApi (7.0.1)
- Volo.Abp.TenantManagement.HttpApi (7.0.1)

### GeoForms.HttpApi.Client
- NETStandard.Library (2.0.3)
- Volo.Abp.Account.HttpApi.Client (7.0.1)
- Volo.Abp.FeatureManagement.HttpApi.Client (7.0.1)
- Volo.Abp.Identity.HttpApi.Client (7.0.1)
- Volo.Abp.PermissionManagement.HttpApi.Client (7.0.1)
- Volo.Abp.SettingManagement.HttpApi.Client (7.0.1)
- Volo.Abp.TenantManagement.HttpApi.Client (7.0.1)

### GeoForms.DbMigrator
- Microsoft.Extensions.Hosting (7.0.0)
- Serilog.Extensions.Logging (3.1.0)
- Serilog.Sinks.Async (1.5.0)
- Serilog.Sinks.Console (4.0.1)
- Serilog.Sinks.File (5.0.0)
- Volo.Abp.Autofac (7.0.1)

### GeoForms.HttpApi.Host
- Microsoft.EntityFrameworkCore.Design (7.0.11)
- Serilog.AspNetCore (5.0.0)
- Serilog.Sinks.Async (1.5.0)
- Volo.Abp.Account.Web.OpenIddict (7.0.1)
- Volo.Abp.AspNetCore.MultiTenancy (7.0.1)
- Volo.Abp.AspNetCore.Mvc.UI.Theme.Basic (7.0.1)
- Volo.Abp.AspNetCore.Serilog (7.0.1)
- Volo.Abp.Autofac (7.0.1)
- Volo.Abp.Swashbuckle (7.0.1)

---

## 5. Frontend Dependencies (Angular)

### Key Angular Dependencies
- @angular/core (15.0.1)
- @angular/common (15.0.1)
- @angular/forms (15.0.1)
- @angular/router (15.0.1)
- @angular/platform-browser (15.0.1)
- @angular/platform-browser-dynamic (15.0.1)
- primeng (15.2.0)
- primeflex (3.3.0)
- rxjs (7.5.6)
- bootstrap-icons (1.10.3)
- lodash-es (4.17.21)
- ng-keyboard-shortcuts (13.0.8)

### ABP Framework Dependencies
- @abp/ng.account (~7.0.1)
- @abp/ng.components (~7.0.1)
- @abp/ng.core (~7.0.1)
- @abp/ng.identity (~7.0.1)
- @abp/ng.oauth (~7.0.1)
- @abp/ng.setting-management (~7.0.1)
- @abp/ng.tenant-management (~7.0.1)
- @abp/ng.theme.lepton-x (^2.0.4)
- @abp/ng.theme.shared (~7.0.1)

### Dev Dependencies
- @angular-eslint (15.1.0)
- @angular/cli (15.0.1)
- @typescript-eslint/eslint-plugin (5.36.2)
- karma (6.3.0)
- ng-packagr (15.0.1)
- typescript (4.8.3)

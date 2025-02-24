## Create an API
An **API** (Application Programming Interface) is a set of rules and protocols that allows one software application to interact with another. They enable different applications, services, or platforms to communicate and work together, even if they’re built on different technologies.

Most common types of APIs. 
- **Web APIs**: APIs designed to be accessed over the web, typically using **HTTP**.

 - **Database API**: Is an interface that allows applications to interact with a database programmatically. 
 
- **Operating System APIs**: APIs provided by operating systems for application development.
 - **Library or Framework APIs**: APIs exposed by libraries or frameworks for specific functionality.
 

Here are the steps to create an API for **Port Master**. 


## GeoForms Solution Structure

```
GeoForms (Solution)
│── src
│   │── GeoForms.Application
│   │── GeoForms.Application.Contracts
│   │── GeoForms.DbMigrator
│   │── GeoForms.Domain
│   │── GeoForms.Domain.Shared
│   │── GeoForms.EntityFrameworkCore
│   │── GeoForms.HttpApi
│   │── GeoForms.HttpApi.Client
│   │── GeoForms.HttpApi.Host

```

 **Step1: Create the PortMasters folder and PortMaster class in the Domain layer.** 
## GeoForms Solution Structure

```
GeoForms (Solution)
│── src
│   │── GeoForms.Application
│   │── GeoForms.Application.Contracts
│   │── GeoForms.DbMigrator
│   │── GeoForms.Domain
│   │   │── Dependencies
│   │   │── Properties
│   │   │── Admin
│   │   │── ApiKeys
│   │   │── CargoGrades
│   │   │── Clients
│   │   │── ConsumerTypes
│   │   │── Data
│   │   │── DataDictionaries
│   │   │── DataSeed
│   │   │── DataUsers
│   │   │── FormLibraries
│   │   │── FuelTypes
│   │   │── OpenIddict
│   │   │── PortMasters
│   │   │   │── PortMaster.cs
│   │   │── Settings
│   │   │── SubmittedForms
│   │   │── SupplierMasters
│   │── GeoForms.Domain.Shared
│   │── GeoForms.EntityFrameworkCore
│   │── GeoForms.HttpApi
│   │── GeoForms.HttpApi.Client
│   │── GeoForms.HttpApi.Host
```

 
 ```
namespace GeoForms.PortMasters
{
    public  class PortMaster : FullAuditedAggregateRoot<Guid>
    {
        public string PortName { get; set; }
        public string UNCode { get; set; }
        public bool Active { get; set; }
    }
}
```
**Step 2: Add a DbSet for PortMaster in DbContext in EntityFrameWorkCore**
In the **GeoFormsDbContext.cs**, add a **DbSet** property for the PortMaster entity. This will enable Entity Framework Core to track and manage PortMaster entities and will map it to a PortMasters table in the database.

```
│── GeoForms.Domain.Shared
│   │── GeoForms.EntityFrameworkCore
│   │   │── Dependencies
│   │   │── Properties
│   │   │── EntityFrameworkCore
│   │   │   │── EntityFrameworkCoreGeoFormsDb.cs
│   │   │   │── GeoFormsDbContext.cs
│   │   │   │   │── GeoFormsDbContext
│   │   │   │── GeoFormsDbContextFactory.cs
│   │   │   │── GeoFormsEfCoreEntityExtensionMappings.cs
│   │   │   │── GeoFormsEntityFrameworkCoreModule.cs
│   │   │── Migrations
│   │── GeoForms.HttpApi
│   │── GeoForms.HttpApi.Client
│   │── GeoForms.HttpApi.Host
```



```
namespace GeoForms.EntityFrameworkCore;
public class GeoFormsDbContext :
    AbpDbContext<GeoFormsDbContext>,
    IIdentityDbContext,
    ITenantManagementDbContext
{
    /* Add DbSet properties for your Aggregate Roots / Entities here. */

 public DbSet<PortMaster> PortMasters { get; set; }👈
 public DbSet<SupplierMaster> SupplierMasters { get; set; }
 public DbSet<VesselFuelType> VesselFuelTypes { get; set; }
}
```

**Strep 3: Add a configuration for the Country entity to specify the table name and any conditions.**

```
 builder.Entity<PortMaster>(b =>
 {
     b.ToTable(GeoFormsConsts.DbTablePrefix + "PortMasters", GeoFormsConsts.DbSchema);
     b.ConfigureByConvention(); //auto configure for the base class props
     b.Property(p => p.PortName).IsRequired().HasMaxLength(50);
     b.Property(p => p.UNCode).HasMaxLength(100);


     b.HasIndex(u => u.UNCode).IsUnique();
     b.HasIndex(u => u.PortName).IsUnique();
 });
```

**Step 4: Configure the Database Connection String in appsettings.json** 
- Go to GeoForms.DbMigrator. Open appsettings.json.
- Add or update the ConnectionStrings section to include the database connection string.
```
│── GeoForms.DbMigrator
│   │   │── Dependencies
│   │   │── appsettings.json
│   │   │── appsettings.secrets.json
│   │   │── DbMigratorHostedService.cs
│   │   │── GeoFormsDbMigratorModule.cs
│   │   │── Program.cs
```



   ```
  "ConnectionStrings": {
    "Default": "Server=localhost\\SQLEXPRESS;Database=GeoForms;Trusted_Connection=True;TrustServerCertificate=True"
  }
  ```

  **Step 5: Create the Migration**
- Right click on **GeoForms.DbMigrator** project and select **Set as StartUp Project**
- Open **Package Manager Console**.
- Select **EntityFrameworkCore** as a default file.
- Add command 'Add-Migration' "Create-PortMaster"
- Run the project.
  In this step migration files will be created.
- Add Command 'update-database'.
  Table will be created in the database.

  **Step 6: Create DTOs for PortMaster in GeoForms.Application.Contracts**
- DTOs act as a protective layer between the database and the API consumers, ensuring that changes to the database schema do not directly impact the API contracts.
- DTOs are useful for validating input data when creating or updating records.
- create a folder named PortMasters.
- create a file named PortMasterdto.cs.

```
│── GeoForms.Application.Contracts
│   │── Dependencies
│   │── Admin
│   │── CargoGrades
│   │── Clients
│   │── ConsumerTypes
│   │── Core
│   │── DataDictionaries
│   │── DataUsers
│   │── FormLibraries
│   │── FuelTypes
│   │── Permissions
│   │── PortMasters
│   │   │── PortMasterdto.cs
│   │── SubmittedForms
│   │── SupplierMasters
```


```
namespace GeoForms.PortMasters
{
  public class PortMasterdto : AuditedEntityDto<Guid>, IHasConcurrencyStamp
    {
        public string PortName { get; set; }
        public string UNCode { get; set; }
        public bool Active { get; set; }
        public List<Guid> ClientId { get; set; }
        public List<ClientInfoDto> Client { get; set; }
        public string ConcurrencyStamp { get; set; }
    }
    public class PortMasterListdto : EntityDto<Guid>
    {
        public string PortName { get; set; }
        public string UNCode { get; set; }
        public bool Active { get; set; }
    }
    public class CreatePortMasterdto
    {
        [Required]
        [StringLength(50)]
        public string PortName { get; set; }
        public string UNCode { get; set; }
        public bool Active { get; set; }
        public List<Guid> ClientId { get; set; }
    }
    public class UpdatePortMasterdto : CreatePortMasterdto, IHasConcurrencyStamp
    {
        public string ConcurrencyStamp { get; set; } 
    }
}
```

**Step 7: Add Mapping for PortMaster in GeoForms.Application**
- Open GeoFormsApplicationAutoMapperProfile.cs file
- Add Mapping for PortMaster
  
 ``` 
  namespace GeoForms;
public class GeoFormsApplicationAutoMapperProfile : Profile
{
    public GeoFormsApplicationAutoMapperProfile()
    {
        CreateMap<PortMaster, PortMasterdto>().ReverseMap();
        CreateMap<CreatePortMasterdto, PortMaster>();
        CreateMap<UpdatePortMasterdto, PortMaster>();
     }
}
        
```

**Step 8: Manage Permission for PortMaster API in GeoForms.Application.Contracts**
- Go to the Permissions folder
- Open a file named GeoFormsPermissions.cs.
- Add a Permission for PortMaster.

 ```
   public static class Port
 {
     public const string Default = DataMasterGroup + ".Port";
     public const string Create = Default + ".Create";
     //public const string View = Default + ".View";
     public const string Update = Default + ".Update";
     public const string Delete = Default + ".Delete";
 }

```


**Step 9: Create PortMaster Service in GeoForms.Application**
- Go to PortMasters folder
- Open PortMasterService.cs
- Create MasterPermission for PortMaster.

```
namespace GeoForms.PortMasters;
public class PortMasterService : BasePageService<PortMaster, PortMasterdto, CreatePortMasterdto, UpdatePortMasterdto>
{
    private readonly IRepository<Vessel, Guid> vesselRepo;
    private readonly IRepository<ClientVessel, Guid> clientVesselRepo;
    private readonly IRepository<ClientPort, Guid> clientPortRepo;
    private readonly IRepository<Client, Guid> clientRepo;
    private readonly IRepository<FormLibraryClient, Guid> formLibraryClientRepo;
    private readonly IRepository<FormLibrary, Guid> formLibraryRepo;

    public PortMasterService(
        IRepository<PortMaster, Guid> repository,
        IRepository<Vessel, Guid> vesselRepo,
        IRepository<ClientPort, Guid> clientPortRepo,
        IRepository<ClientVessel, Guid> clientVesselRepo,
        IRepository<Client, Guid> clientRepo,
        IRepository<FormLibraryClient, Guid> formLibraryClientRepo,
        IRepository<FormLibrary, Guid> formLibraryRepo) : base(repository)
    {
        this.vesselRepo = vesselRepo;
        this.clientPortRepo = clientPortRepo;
        this.clientVesselRepo = clientVesselRepo;
        this.clientRepo = clientRepo;
        this.formLibraryRepo = formLibraryRepo;
        this.formLibraryClientRepo = formLibraryClientRepo;
    }
  public async Task<List<PortMasterdto>> GetPortListAsync()
  {
      var portMaster = await Repository.GetListAsync();
      var portMasterDto = ObjectMapper.Map<List<PortMaster>, List<PortMasterdto>>(portMaster);
      return portMasterDto;
  }

```
**Step 10: Create API endpoints to perform CRUD operations on PortMaster** 
- Go to GeoForms.HttpApi.Host
- Right click on, Select Set as Starup Project
- Run the Project.

![image](https://github.com/user-attachments/assets/6048ce6d-e1dc-4bb0-bfaa-bd798e7dda8e)
![image](https://github.com/user-attachments/assets/bddb3ed1-4464-477b-ba73-33efa722ca8a)



  


# Reno Tracker - Ex04 - Database Querying Based on Filters

> In this exercises you will be adding to your existing website to query information on renovations. **Reno Tracker** is a web application for those who want to keep information on home renovation projects within their business. To start application development, we will limit the data to maintain in a database to the client, job, material and labour.
>

## Overview

A key aspect of the site is to allow users to search the database to find information on various renovation projects. Your task in this assignment is to provide that functionality.

Use the demos presented in class as a guide to implementing this exercise.

### Database setup

Use the supplied database found in this repository: `Renos.bacpac`. Restore this database to your machine. You will be using this database in this exercise.

### Client Service Web Application DataBase class library

1. Create a .Net Core 8 class library project called `RenoSystemDB`. Create 3 subfolders within this project based on the structure used in class: BLL, DAL, and Entities. Use reverse engineering and the supplied database to create the Entity classes and DAL context class. It is ***strongly*** advised that you review the class demonstration for this process. Add a project reference to your web application for this class library. 

![ERD](./ERD_Renos.png)

1. Create your database connection string in the appsettings.json file.

```csharp
"ConnectionStrings": {
    "RenoDB" : "Server=xxxx;Database=Renos;Trusted_Connection=true;MultipleActiveResultSets=true"
  }
```

1. Setup the service dependency registration for the web application and library class. Use your class lesson demonstration to complete this process. 

### Overview Query Page

Create an `Query.razor`/`Query.razor.cs` Blazor Page. The partial code class must inject the dependency on the `JobServices` and `SupplyServices` classes. Details of your display can be found below. Be sure to add a menu item so that this page can be navigated to using the main menu; use the text "Query" for the link. Add an appropriate title to the page and the title browser tab.

### Reno System: BLL service class 

**JobServices**

Create a new service class called `JobServices` in your BLL folder. This class will contain one service method to return the complete list of Jobs. The query is supplied below. This query list will be sorted alphabetically by Description. Remember to register your service class.

**SupplyServices**

Create a new service class called `SupplyServices` in your BLL folder. This class will contain one service method to return the complete list of supplies for a specified job. The method will receive a filtering parameter for a specified job. Remember to register your service class.

### Query Page to search Supplies needed for a specific Job

The `Query.razor` page will display information on the supply data in an HTML table. Display the `Material`, `Quantity` and `MaterialCost` information. This query page will have Drop Down List filter showing the Job description. The page will have two buttons: searching and clear. Each button will require an event handler. Place the page coding in a separate file called `Query.razor.cs`. Demonstrate either paging or table scrolling by limiting your display to 10 lines at a time. Display a message if no supplies have been found for the selected job id.


Only present the data (sample) as shown below:

![query supplies](./querydisplay.png)

![query supplies error](./nojobselection.png)

To ensure that your web application works, build and run your project.

## Evaluation

> ***NOTE:** Your code **must** compile. Solutions that do not compile will receive an automatic mark of zero (0).*
>
> If you are unable to get a portion of the assignment to compile, you should:
>
> - Comment out the non-compiling portion of code
> - Identify the non-compiling portion in the **Incomplete Requirements** heading, noting the item's
>   - File name (e.g.: "Account.cs")
>   - Line number(s)
>   - Compiler error number and general message

Your assignment will be marked based upon the following weights. 

| Earned | Weight | Deliverable/Requirement | Comments |
| ------ | ---- | --------- |   ------- |
|  | 1 | Create appropriate ASP.NET Core Web Application (.net core 8) |   |
|  | 1 | Create appropriate ASP.NET Core Class Library (.net core 8) |   |
|  | 1 | Create Entity classes using reverse engineering (Entity and DAL classes) |    |
|  | 2 | Setup project references, necessary NuGet packages and service registration code |   |
|  | 2 | `JobServices.cs` BLL service class|   |
|  | 2 | `SupplyServices.cs` BLL service class |    |
|  | 3 | `Query.razor` setup appropriate controls for query agrument (Job) and table display (Supplies) |   |
|  | 3 | `Query.razor.cs` Write appropriate code/post events to handle necessary bind properties, OnInitialize, and query button. |   |
|  | 1 | `Query.cshtml.cs` Write appropriate post event to clear the page |   |
|  | 1 | User friendly error handly: consistent throughout all post events, able to handle a collection of errors   |   |
|   | -4 max | **Penalty** -  Such as but not limited to: missing incremental commits; compile errors; incorrect project types; code separation | |   |
| ------ | ---- | --------- |  -----|
|  | **17** | **Total Weight** |   |

----

## Additional Comments


----

[Return to exercises](../README.md)

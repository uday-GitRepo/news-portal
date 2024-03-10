This repository contains DB scripts and changes reuired to run the POC App.


# Database Script Execution


## Table of Contents

- [Prerequisites](#prerequisites)
- [Database Configuration](#database-configuration)
- [Executing Scripts](#executing-scripts)


## Prerequisites

Before running the database scripts, ensure that the following prerequisites are met:
- [Database Server](#) - Install and configure SQL Server.
- [Client Tool](#) - Install  SQL Server managment studio to execute the SQL scripts.


## Database Configuration

1. **Connect to Database Server:** Use your SQL Server managment studio to connect to the database server.

2. **Create Database:** Create a new database with any name.

3. **User Permissions:** Ensure that the user running the scripts has the necessary permissions to execute schema changes.


## Executing Scripts

1. **Run Scripts:** Execute the scripts using the SQL Server Management Studio tool, following the order provided in the DB folder. You may run scripts individually or a batch.




3. **Verification:** After executing the scripts, verify that the database schema and categories are updated/inserted as expected.

##################################################################################################################################################################

# WEB API project

This project is built with help of Visual Studio using .NET 6 & EF6.

## Prerequisites

Before you begin, ensure you have the following installed on your machine:

- [.NET 6 SDK](https://dotnet.microsoft.com/download/dotnet/6.0)
- [Visual Studio](https://visualstudio.microsoft.com/)

## Getting Started

Follow these steps to set up and run the project locally:

1.  Download the WEB API proj (News-Portal-API.zip) from repository
2.  Unzip and Open the solution file in the Visual Studion
3.  If the NuGet packages are missing, initiate the restoration process as follows
      
	Option 1: 
		Open the Package Manager Console in Visual Studio (View -> Other Windows -> Package Manager Console).
		In the console, navigate to the directory of your solution or project.
		Run the following command:
		dotnet restore

	Options 2: 
		Right-click on your solution in Solution Explorer.
		Choose the Restore NuGet Packages option from the context menu.

4. The following modifications are necessary in the main project.

	Program.cs
   		** Typically, web browsers restrict cross-domain API calls. Therefore, it's essential to include the base URL of the Angular project in the CORS 		   policy of the Web API.

		 builder.WithOrigins("http://localhost:55212") -> update AngularApp base url here		 
		 

	appsettings.json
   		** Update the value of the connection string for both NewsArticleStore in the ConnectionStrings section and connectionString in the Serilog section.

5. Right click on the solution and build
6. Run the WEbB API App by Ctrl + F5

 
## **Verification:** Verify the functionality of the APIs by testing with Postman or Swagger UI.



##################################################################################################################################################################

# Angular App project

This project was developed using Visual Studio Code, incorporating Angular v13 and PrimeNG libraries.

## Prerequisites

Before you begin, ensure you have the following installed on your machine:

- [Visual Studio Code]
- [NodeJs]
- [npm] 
- [Angular CLI]

## Getting Started

Follow these steps to set up and run the project locally:

1.  Download the Angular App project (News-Portal-Prj.zip) from repository.
2.  Unzip and Open the folder in the Visual Studio Code.
3.  Restore the node_modules packages if missing. 
	
 	** Make sure you are running the commands in the root directory of your Angular project, where the package.json file is located.
	** npm install


4. Modify the BASE_URI value with the base URL of the WEB API project in the src/app/core/constants.ts file of the Angular app.
4. Launch a terminal from the menu options in Visual Studio Code.
5. Navigate to the location, where the package.json file is located.
6. Run ng serve to build and run the project.
7. The application URL will be displayed in the console; open it in your browser.

## **Verification:** Verify the Angular UI screen is loaded without errors.


      

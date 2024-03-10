This repository contains DB scripts and changes reuired to run the POC App.


# Database Script Execution


## Table of Contents

- [Prerequisites](#prerequisites)
- [Database Configuration](#database-configuration)
- [Executing Scripts](#executing-scripts)


## Prerequisites

Before running the database scripts, ensure that the following prerequisites are met:
- [Database Server](#) - Install and configure SQL Server.
- [Client Tool](#) - Install a SQL Server managment studio to execute the SQL scripts.


## Database Configuration

1. **Connect to Database Server:** Use your SQL Server managment studio to connect to the database server.

2. **Create Database:** Create a new database with any name.

3. **User Permissions:** Ensure that the user running the scripts has the necessary permissions to execute schema changes.


## Executing Scripts

1. **Run Scripts:** Execute the scripts using SQL Server managment studio tool in the order given below. You may run scripts individually or a batch.


/* Table Name : Category */

CREATE TABLE [dbo].[Category](
	[CategoryId] [int] IDENTITY(1,1) NOT NULL,
	[CategoryName] [nvarchar](50) NOT NULL,
 CONSTRAINT [PK_Category] PRIMARY KEY CLUSTERED 
(
	[CategoryId] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO

/* Categories Master Data*/

INSERT INTO [dbo].[Category]([CategoryName])  VALUES('EDUCATION')
INSERT INTO [dbo].[Category]([CategoryName])  VALUES('ENTERTAINMENT')
INSERT INTO [dbo].[Category]([CategoryName])  VALUES('POLITICS')
INSERT INTO [dbo].[Category]([CategoryName])  VALUES('CRIME')
INSERT INTO [dbo].[Category]([CategoryName])  VALUES('SCIENCE')

/* Table Name : NewsArticle */

CREATE TABLE [dbo].[NewsArticle](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[Title] [nvarchar](100) NOT NULL,
	[Description] [nvarchar](max) NOT NULL,
	[CategoryId] [int] NOT NULL,
	[CreatedOn] [datetime] NOT NULL,
 CONSTRAINT [PK_NewsArticle] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO

ALTER TABLE [dbo].[NewsArticle] ADD  CONSTRAINT [DF_CurrentDate_CreatedOn]  DEFAULT (getdate()) FOR [CreatedOn]
GO

ALTER TABLE [dbo].[NewsArticle]  WITH CHECK ADD  CONSTRAINT [FK_NewsArticle_Category] FOREIGN KEY([CategoryId])
REFERENCES [dbo].[Category] ([CategoryId])
GO

ALTER TABLE [dbo].[NewsArticle] CHECK CONSTRAINT [FK_NewsArticle_Category]
GO



3. **Verification:** After executing the scripts, verify that the database schema and categories are updated/inserted as expected.

########################################################################################################################################################################################
########################################################################################################################################################################################
########################################################################################################################################################################################


# WEB API project

This project is built with help of Visual Studio using .NET 6 & EF6.

## Prerequisites

Before you begin, ensure you have the following installed on your machine:

- [.NET 6 SDK](https://dotnet.microsoft.com/download/dotnet/6.0)
- [Visual Studio](https://visualstudio.microsoft.com/)

## Getting Started

Follow these steps to set up and run the project locally:

1. ** Download the WEB API proj from repository
2. ** Open the solution file in the Visual Studion
3. ** Restore the NuGet packages if missing 
      
	Option 1: 
		Open the Package Manager Console in Visual Studio (View -> Other Windows -> Package Manager Console).
		In the console, navigate to the directory of your solution or project.
		Run the following command:
		dotnet restore

	Options 2: 
		Right-click on your solution in Solution Explorer.
		Choose the Restore NuGet Packages option from the context menu.

4. Required the below changes in main project.

	Program.cs
		> Usually the browser blocks cross doamin API calls. We need to add Angular prj base url in the WEB API cors policy.

		 builder.WithOrigins("http://localhost:55212") -> update AngularApp base url here		 
		 

	appsettings.json
		> Change the connection string value for both NewsArticleStore in the ConnectionStrings section & connectionString in the Serilog section.

5. Build the Solution by clicking Ctrl + F5

 
## **Verification:** Verify the APIs are working by using Postman or Swagger UI



########################################################################################################################################################################################
########################################################################################################################################################################################
########################################################################################################################################################################################

# Angular App project

This project is built with help of Visual Studio Code using Angular v13 & PrimeNG libraries.

## Prerequisites

Before you begin, ensure you have the following installed on your machine:

- [Visual Studio Code]
- [NodeJs] 


## Getting Started

Follow these steps to set up and run the project locally:

1. ** Download the Angular App prj from repository
2. ** Open the folder in the Visual Studion Code
3. ** Restore the node_modules packages if missing 
	
	> Ensure that you have Node.js and npm installed on your machine.
	> Make sure you are running the commands in the root directory of your Angular project, where the package.json file is located.
	> npm install


4. Update the BASE_URI value with WEB API prj base url in the src/app/core/constnts.ts path of ANgular App.
4. Open a Terminal from Visual Studio COde menu options
5. Go to main project directory vid cd path command
6. Run ng serve to build and run the project.

## **Verification:** Verify the ANgular UI screen is loaded witout eroors.


      

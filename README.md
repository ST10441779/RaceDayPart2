🏁 RaceDay Part 2 — RESTful API
📌 Project Overview
RaceDay is an ASP.NET Core Web API prototype designed to support a race event management platform. The system allows event organisers to manage race events, create event categories, manage participant enrolments, and record race results.
Participants can register for an account, browse available events, enrol in race categories, manage their profiles, and view their results.
This project demonstrates RESTful API development, session-based authentication, role-based access control, API documentation, automated testing, and continuous integration using GitHub Actions.
Note: This version uses in-memory storage and does not include SQL Server or Entity Framework Core. All application data is reset when the API application stops.
✨ Features
User registration and authentication: Register and log in as an Organiser or Participant.
Password security: Passwords are hashed before storage and are not stored as plain text.
Role-based access control: Restricts protected operations according to the user’s role.
Event management: Organisers can create, view, update, and delete their own race events.
Category management: Organisers can manage categories associated with their events.
Participant enrolments: Participants can enrol in events and view their own enrolments.
Race results: Organisers can record and update results, while participants can view their results.
Profile management: Users can view and update their own profile information.
Swagger UI: Provides interactive API documentation and endpoint testing.
Automated tests: Tests important authentication, authorisation, event creation, and enrolment scenarios.
GitHub Actions: Automatically restores, builds, and tests the solution when code is pushed or a pull request is opened.
🛠️ Technologies Used
C#
.NET 8
ASP.NET Core Web API
RESTful API architecture
Swagger / OpenAPI
In-memory data storage
Cookie-based session management
ASP.NET Core password hashing
xUnit
Git and GitHub
GitHub Actions
👥 User Roles
1. Organiser
Organisers can:
Register and log in.
View and update their own profile.
Create and manage their own race events.
Create and manage event categories.
View enrolments for events they own.
Record and update race results.
2. Participant
Participants can:
Register and log in.
Browse available race events and categories.
Enrol in an event category.
View their own enrolments.
View their race results.
View and update their own profile.
Access Control
The API uses HTTP status codes to indicate authentication and authorisation outcomes.
200 OK — The request was successful.
201 Created — A resource was created successfully.
400 Bad Request — The request contains invalid data.
401 Unauthorized — Authentication is required or the credentials are invalid.
403 Forbidden — The authenticated user does not have permission to perform the operation.
404 Not Found — The requested resource could not be found.
409 Conflict — The request conflicts with existing data, such as a duplicate email address.
🔗 API Endpoints
The API is organised into the following endpoint groups.
Endpoint
Description
/api/auth
User registration, login, logout, and current account
/api/profile
View and update the authenticated user’s profile
/api/events
Browse and manage race events
/api/events/{eventId}/categories
View and manage event categories
/api/enrolments
Create and view participant enrolments
/api/results
Record, update, and view race results
The exact HTTP methods and available operations are documented in Swagger UI.
⚙️ Prerequisites
Before running the project, ensure you have installed:
.NET 8 SDK (https://dotnet.microsoft.com/en-us/download/dotnet/8.0)
Visual Studio 2022 (https://visualstudio.microsoft.com/) with the ASP.NET and web development workload, or a compatible code editor and the .NET CLI.
Git (https://git-scm.com/) for version control.
🚀 Getting Started
1. Clone the Repository
Open a terminal and run:
git clone <YOUR-GITHUB-REPOSITORY-URL>
Replace <YOUR-GITHUB-REPOSITORY-URL> with the URL of your GitHub repository.
Navigate to the project folder:
cd RaceDay-Part2
2. Restore Dependencies
Run the following command from the folder containing RaceDay.sln:
dotnet restore RaceDay.sln
3. Run the API
Start the application using:
dotnet run --project src/RaceDay.Api/RaceDay.Api.csproj
The terminal will display the local URL where the API is running.
4. Open Swagger UI
Open your browser and navigate to the application URL followed by /swagger.
For example:
https://localhost:7001/swagger
The port may differ on your computer. Use the actual URL displayed in the terminal.
Swagger allows you to explore the API endpoints and send requests directly from your browser.
5. Test the Application
Register an account using /api/auth/register.
Choose either Organiser or Participant as the account role.
Log in using /api/auth/login.
Use the available endpoints to test the functionality permitted for that role.
Log out using /api/auth/logout when finished.
Swagger requests made through the same browser session can retain the session cookie. Use separate browser sessions when demonstrating different user roles.
🧪 Running Automated Tests
The project includes automated tests written with xUnit and ASP.NET Core’s integration testing tools.
To execute the tests, run:
dotnet test RaceDay.sln
The tests cover scenarios including:
Rejecting registration with a short password.
Rejecting invalid login credentials.
Preventing unauthenticated access to protected profile endpoints.
Preventing Participants from creating race events.
Allowing Organisers to create race events.
Allowing Participants to enrol in an event and retrieve their enrolments.
These tests help verify the main application workflows and access control rules.
🔄 Continuous Integration with GitHub Actions
The project includes a GitHub Actions workflow located at:
.github/workflows/dotnet.yml
The workflow automatically performs the following tasks when code is pushed or a pull request is opened:
Checks out the repository.
Installs the .NET 8 SDK.
Restores project dependencies.
Builds the solution in Release configuration.
Runs the automated tests.
To view the workflow results:
Push your project to GitHub.
Open your repository.
Select the Actions tab.
Open the latest RaceDay API CI workflow run.
Check whether the build and tests completed successfully.
A successful workflow run provides evidence that the configured build and test steps passed.
📁 Project Structure
RaceDay-Part2/
├── .github/
│   └── workflows/
│       └── dotnet.yml
├── src/
│   └── RaceDay.Api/
│       ├── Program.cs
│       ├── Models.cs
│       ├── InMemoryStore.cs
│       └── RaceDay.Api.csproj
├── tests/
│   └── RaceDay.Tests/
│       ├── ApiTests.cs
│       └── RaceDay.Tests.csproj
├── RaceDay.sln
├── .gitignore
└── README.md
Key Files
Program.cs: Configures the API, session management, Swagger, authentication, authorisation, and endpoint handlers.
Models.cs: Defines the data models and request objects used by the API.
InMemoryStore.cs: Maintains application data in in-memory collections and provides password hashing.
ApiTests.cs: Contains automated integration tests for key API behaviours.
dotnet.yml: Defines the GitHub Actions continuous integration workflow.
RaceDay.sln: Contains the solution and project references.
.gitignore: Excludes generated files and development-specific files from version control.
🔐 Security and Data Storage
The prototype uses ASP.NET Core session management with a session cookie and a 30-minute inactivity timeout.
Passwords are hashed using ASP.NET Core’s PasswordHasher<User> before being stored.
The application also checks user roles before allowing access to restricted operations.
Important limitations:
Data is stored in memory and is lost when the application stops.
The prototype does not use a persistent database.
In-memory storage is intended for demonstration and development rather than production deployment.
Production use would require additional security hardening, persistent storage, configuration management, and appropriate deployment settings.
⚠️ Project Limitations
This version of RaceDay is a database-free prototype intended to demonstrate core API functionality.
It does not implement SQL Server or Entity Framework Core. If the project is being submitted for an assignment that specifically requires these technologies, the database requirement must still be addressed.
🎥 Project Demonstration
YouTube Demonstration: Add the URL of your recorded demonstration here.
GitHub Actions Build Screenshot: Add a screenshot of your actual successful workflow run here.
These should be added after the demonstration has been recorded and the GitHub Actions workflow has run successfully.
🎯 Learning Outcomes
This project demonstrates practical experience with:
Building RESTful APIs using ASP.NET Core.
Designing endpoints and data models.
Implementing session-based authentication.
Applying role-based access control.
Hashing passwords securely.
Writing automated integration tests.
Documenting APIs with Swagger.
Using GitHub for source control.
Automating builds and tests with GitHub Actions.

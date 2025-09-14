# 📘 Technical Architecture Document (TAD)

## 1. Context and objectives
- **Project name** : Carnage Tracker
- **Description** : Carnage tracker is a mobile app used by Gasland players to build rosters and to track game state.
- **Objectives** : Carnage tracker need to be an intuitive and easy-to-use mobile app that helps players to keep tracks of their games.
- **Challenges** : 
  - The app need to be intuitive, easy-to-use and relatively high-performing
  - This app is a side project that I realise on my free time. Therefore, it is not my main activity
  - Technically, this project is used to implement best practicies and improve development skills 
- **Constraints** : 
  - Costs
  - Time development
  - Best practicies
  - Skills improvement
  - Monitoring
  - Need an offline mode

---

## 2. Global architecture
![Architecture diagram](GlobalArchitecture.png)
- **Mobile application** : Frontend client used by players to interact with the system
- **API** : Backend service that contains all business and application rules
- **Database** : Databse that store application data
- **Google authentication** : Service that store and manage users identity

---

## 3. Technological choices
| Type                | Technologies            | Justifications|
|---------------------|-------------------------|---------------|
| Backend             | C# (.NET 9), ASP.NET    | Wide ecosystem, maintainable and well-known |
| ORM                 | EF Core                 | Support LINQ, migrations |
| Database            | Postgre                 | Open-source, free |
| Mobile              | C# (.NET 9), MAUI       | Cross-platform, improve skills,  |
| Authentication      | JWT / OAuth2            | Security standard |
| CI/CD               | GitHub Actions          | Automate build and deploy|

---

## 4. Software architecture
### 4.1 Clean Architecture
- **Domain** : Business rules and domain entity.
- **Application** : CQS Handlers.
- **Infrastructure** : Database persistance.
- **Presentation** : API controllers and middlewares.

### 4.2 Main modules
- Authentication
- Roster creation
- Game state

---

## 5. Infrastructure and hosting
- **API Hosting** : Docker on premise
- **Database** : PostgreSQL
- **File storage** : Azure Blob Storage
- **CI/CD** : 
  - *CI* : Build docker image, run static code analysis, execute unit test and save docker image to DockerHub
  - *CD* : Deploy the docker image to the on-premise environement and increment the application version

---

## 6. Security
- Authentication : Use OAuth with Google authentication
- Autorisation : Apply permissions on each request of the API
- Encryption : HTTPS (TLS 1.2+)
- Secrets management : 
- Protection against attacks (OWASP) : rate limiting, input validation, token verification, SQL request validation

---

## 7. Conventions
- **Naming** : Use the Microsoft naming conventions
- **Endpoints definition** : All endpoints will follow the RestFul convention
- **Code review** : Pull request are mandatory to push new code to dev or main, it will be used to run CI pipeline.
- **Tools** :
  - **StyleCop** : Use to apply naming conventions automatically
  - **CommitLint** : Use to validate code and commit message before commiting
  - **Sonar** : Static code anaylser to improve the code base
  - **SemanticRelease** : Use to automatically increment application version

---

## 8. Test strategy
- **Unit tests** : Test buisiness rules
- **Integration tests** : API + DB
- **end-to-end tests**
- **Aim code coverage** : 75%

---

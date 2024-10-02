# Tracker Application

## Overview
This tracker application allows managers to create teams, assign roles, define activities, and track the daily hours logged by employees. Higher-ups can view overall team utilization for various time periods.

## Features
- **Team Management**: Create teams and assign members and roles.
- **Activity Definition**: Define activities and specify if they fall under utilization.
- **Time Tracking**: Employees log their daily hours and activities.
- **Manager Monitoring**: Managers view entries for their teams.
- **Utilization Reporting**: Higher-ups view overall team utilization for past week, month, year, etc.

## User Stories
1. **Create Employee with Manager Role**
   - As a manager, I want to create teams and assign members and roles so that I can organize my team effectively and ensure everyone knows their responsibilities.
2. **Manager Creates a Team**
   - As a manager, I want to create a new team by providing a team name so that I can start organizing my team.
3. **Manager Adds Members and Roles**
   - As a manager, I want to add employees to the team and assign them specific roles so that I can ensure everyone has a defined role within the team.
4. **Manager Defines Activities**
   - As a manager, I want to define activities and specify if they fall under utilization so that I can track productive work and measure team performance accurately.
5. **Employee Enters Breakdown of Daily Hours**
   - As an employee, I want to enter the breakdown of my daily hours and activities so that I can keep a record of my work and ensure accurate reporting.
6. **Manager Views Entries for Their Teams**
   - As a manager, I want to view the entries of my team members so that I can monitor their progress and provide support where needed.
7. **Higher-Ups View Overall Utilization**
   - As a higher-up, I want to see the overall utilization of all teams for the past week, month, and year so that I can make informed decisions about resource allocation and strategic planning.

## Workflow Steps
1. **Create Employee with Manager Role**
   - Define the role of “Manager” in the system.
   - Add an employee to the system and assign them the “Manager” role.
2. **Manager Creates a Team**
   - The manager logs into the system.
   - The manager creates a new team by providing a team name.
3. **Manager Adds Members and Roles**
   - Ensure that all employees who will be team members are already added to the system.
   - Define the roles that team members can have (e.g., Developer, Tester).
   - Add employees to the team and assign them specific roles.
4. **Manager Defines Activities**
   - The manager creates activities or tasks that need to be done.
   - Specify whether each activity is part of the team’s utilization (productive work).
5. **Employee Enters Breakdown of Daily Hours**
   - Employees log into the system.
   - They select the activity they worked on from a list of defined activities.
   - They enter the number of hours worked and a description of what they did.
6. **Manager Views Entries for Their Teams**
   - The manager logs into the system.
   - The manager views a report or dashboard showing the entries made by their team members.
   - The manager can filter and review the entries to monitor progress and provide support.
7. **Higher-Ups View Overall Utilization**
   - Higher-ups log into the system.
   - They access reports or dashboards that show the overall utilization of all teams.
   - They can view utilization data for different time periods (e.g., past week, month, year) to make informed decisions about resource allocation and strategic planning.
## DB Design
  - ![Alt text](https://github.com/AbidShaik09/Actalent-Tracker-Design/blob/main/DB-Design.png)
  - <img src="https://github.com/AbidShaik09/Actalent-Tracker-Design/blob/main/DB-Design.png">
## Tech Stack
- **Client-Side**: React, MUI (Material-UI), TypeScript
- **Server-Side**: .NET 8 Web API Microservices
- **Database**: SQL Server (decentralized for each microservice)
- **Deployment**: Docker Containers
- **Security**: JWT

## Milestones and Timelines
1. **Project Setup**: 2-Oct-24 to 4-Oct-24
2. **Design Phase**: 5-Oct-24 to 18-Oct-24
3. **Database Setup**: 19-Oct-24 to 1-Nov-24
4. **Backend Development**: 2-Nov-24 to 29-Nov-24
5. **Frontend Development**: 30-Nov-24 to 27-Dec-24
6. **Testing**: 28-Dec-24 to 10-Jan-25
7. **CI/CD Setup**: 11-Jan-25 to 17-Jan-25
8. **Final Deployment**: 18-Jan-25 to 24-Jan-25

## Microservices Architecture

### User Management Service
- **Responsibilities**: Handle user registration, authentication, authorization, and role management.
- **Database Tables**: Employees, EmployeeRoles
- **Endpoints**:
  - `POST /users/register`
  - `POST /users/login`
  - `GET /users/{id}`
  - `PUT /users/{id}`
  - `DELETE /users/{id}`
  - `GET /roles`
  - `POST /roles`
  - `PUT /roles/{id}`
  - `DELETE /roles/{id}`

### Team Management Service
- **Responsibilities**: Manage teams, team members, and roles within teams.
- **Database Tables**: Team, TeamMembers, TeamMemberRoles, EmployeeTeams
- **Endpoints**:
  - `POST /teams`
  - `GET /teams/{id}`
  - `PUT /teams/{id}`
  - `DELETE /teams/{id}`
  - `POST /teams/{id}/members`
  - `DELETE /teams/{id}/members/{memberId}`
  - `GET /roles`
  - `POST /roles`
  - `PUT /roles/{id}`
  - `DELETE /roles/{id}`

### Activity Management Service
- **Responsibilities**: Define and manage activities, track utilization.
- **Database Tables**: Activities
- **Endpoints**:
  - `POST /activities`
  - `GET /activities/{id}`
  - `PUT /activities/{id}`
  - `DELETE /activities/{id}`
  - `GET /activities`

### Time Tracking Service
- **Responsibilities**: Log and manage daily hours and activities.
- **Database Tables**: Hours, Entry
- **Endpoints**:
  - `POST /hours`
  - `GET /hours/{id}`
  - `PUT /hours/{id}`
  - `DELETE /hours/{id}`
  - `POST /entries`
  - `GET /entries/{id}`
  - `PUT /entries/{id}`
  - `DELETE /entries/{id}`

### Reporting Service
- **Responsibilities**: Generate utilization reports for managers and higher-ups.
- **Database Tables**: Aggregates data from other services' databases
- **Endpoints**:
  - `GET /reports/utilization`
  - `GET /reports/team/{teamId}/utilization`
  - `GET /reports/employee/{employeeId}/utilization`

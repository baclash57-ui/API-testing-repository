

# Trello API Testing Project

## Project Objective

This project demonstrates end-to-end API testing of the Trello REST API using Postman and Newman. It validates complete CRUD (Create, Read, Update, Delete) workflows while showcasing automated assertions, dynamic data generation, request chaining, environment variable management, and command-line test execution.

---

## Overview

This repository contains a Postman collection designed to test the functionality of the Trello REST API. The collection validates key endpoints through automated assertions, HTTP status code verification, response schema validation, and performance checks.

To support reliable end-to-end execution, dynamic variables and pre-request scripts are used to automatically generate board names and capture resource IDs (boards, lists, cards, and checklists) for use in subsequent requests.

---

## Tools Used

| Tool             | Purpose                                                             |
| ---------------- | ------------------------------------------------------------------- |
| **Postman**      | API development, request creation, automated testing, and scripting |
| **Newman**       | Command-line execution of Postman collections and report generation |
| **Git & GitHub** | Version control and project hosting                                 |

---

## Key Features

* End-to-end automated API testing
* Full CRUD workflow validation
* HTTP status code verification
* Response body validation
* Response time validation (target: **< 2000 ms**)
* Dynamic test data generation
* Request chaining using collection and environment variables
* Automated execution using Newman
* Secure credential management through environment variables

---

## Test Coverage

The collection validates the following Trello resources:

### Boards

* Create Board
* Retrieve Board
* Update Board
* Delete Board
* Verify Deleted Board (404)

### Lists

* Create List
* Retrieve List
* Update List
* Archive List

### Cards

* Create Card
* Retrieve Card
* Update Card

### Checklists

* Create Checklist
* Retrieve Checklist

---

## Validation Performed

Automated assertions verify:

* Successful HTTP status codes
* Expected response body structure
* Required fields are present
* Data type validation
* Response time below **2 seconds**
* Board name matches generated test data
* Correct resource IDs returned
* Proper handling of deleted resources (404 responses)
* Validation of important fields including:

```
id
name
desc
closed
url
shortUrl
```

---

## Dynamic Variable Management

To enable complete workflow automation, the collection stores dynamically generated values for reuse throughout execution.

| Variable    | Description                       |
| ----------- | --------------------------------- |
| `BoardID`   | Captured after board creation     |
| `ListID`    | Captured after list creation      |
| `cardId`    | Captured after card creation      |
| `checkID`   | Captured after checklist creation |
| `boardName` | Randomly generated board name     |

Dynamic values are managed using Postman collection and environment variables, eliminating the need for manual input between requests.

---

## Security

Sensitive credentials have been removed from this repository before publication.

Authentication values are managed through environment variables, including:

* `Tkey`
* `trelloToken`

This approach follows security best practices by preventing API keys and tokens from being committed to source control.

---

## Running the Project

### Using Postman

1. Clone this repository.
2. Import the Postman collection.
3. Create or import an environment.
4. Configure the following environment variables:

```
Trello Url
Tkey
trelloToken
```

5. Run the collection using the Collection Runner.

---

### Using Newman

Install Newman globally:

```bash
npm install -g newman
```

Run the collection:

```bash
newman run Trello_API.postman_collection.json \
-e Trello_Environment.postman_environment.json
```

Generate an HTML report (if using the HTML reporter):

```bash
newman run Trello_API.postman_collection.json \
-e Trello_Environment.postman_environment.json \
-r cli,htmlextra
```

---



## Sample Workflow

```text
Create Board
      │
      ▼
Retrieve Board
      │
      ▼
Update Board
      │
      ▼
Create List
      │
      ▼
Retrieve List
      │
      ▼
Update List
      │
      ▼
Archive List
      │
      ▼
Create Card
      │
      ▼
Retrieve Card
      │
      ▼
Update Card
      │
      ▼
Create Checklist
      │
      ▼
Retrieve Checklist
      │
      ▼
Delete Board
      │
      ▼
Verify 404 Response
```

## API Order of execution

For this execution we will be using the LIFO principle. 

| **Requests** | **Order of execution** | **Dependencies** |
| --- | --- | --- |
| **Create a board** | **Create a board** | **None** |
|  | Read board | Create board |
|  | Update board | Created board |
|  | Read the board | Created board |
| **Create a list** | **Create a list** | **Created board** |
|  | Read list | Create List |
|  | Update list. | Created List |
|  | Read list | Create List |
| **Create a card.** | **Create a card.** | **Create List** |
|  | Read card  | Create List |
|  | Update Card | Create List |
|  | Read Card | Create List |
| **Create a checklist.** | **Create a checklist.** | **Created List** |
|  | Read the Checklist | Created Checklist |
|  | Update  Checklist | Created Checklist |
|  | Read checklist | Created Checklist |
|  | Delete check list | Created Checklist |
|  | Get the deleted checklist | Created Checklist |
| **Delete card** | **Delete card** | **Create List** |
|  |  |  |
| **Archive List** | **Archive List** | **Create board** |
|  |  |  |
| **Delete board** | **Delete board** | **Create Board** |


---

## Skills Demonstrated

* REST API Testing
* API Automation
* Postman Scripting
* Newman CLI
* JavaScript Test Scripts
* CRUD Validation
* Response Validation
* HTTP Protocol
* Environment Variable Management
* Request Chaining
* Performance Validation
* Git & GitHub
* API Security Best Practices

---

## Future Improvements

* Integrate automated execution with GitHub Actions for Continuous Integration (CI).
* Add JSON schema validation for API responses.
* Generate JUnit and HTML reports for CI pipelines.
* Expand test coverage to include negative and edge-case scenarios.
* Parameterize additional test data for broader automation coverage.

---

## Author

**Obinna Japhet**

API Testing • Postman • Newman • QA Automation

# ReqRes API Testing

This is an API testing project using Postman to validate endpoints from the ReqRes practice API. The collection includes automated test scripts with assertions to verify response status codes, response bodies, and error handling behavior. Environment variables are used to manage configuration values such as the base URL and reduce hardcoded data.

## What's Included

* Requests covering List Users, Single User, Invalid User, List Resource, Single Resource, Login (successful and unsuccessful), Register (successful and unsuccessful), Update User (PUT and PATCH), Delete User, and Delayed Response
* Separate folders for successful and unsuccessful test scenarios to improve organization and maintainability
* Automated assertions validating status codes, response data, and expected error responses
* Environment variables for configurable values and easier collection portability

## Tools Used

* Postman
* ReqRes API

## Key Learning Outcomes

* Developed and executed API test cases for both positive and negative scenarios
* Implemented Postman test scripts using JavaScript assertions to validate API behavior
* Utilized environment variables to improve maintainability and eliminate hardcoded values
* Gained experience validating error handling, response structures, and HTTP status codes

## Challenges Encountered

One challenge was validating negative test scenarios, such as requests that return 404 responses or failed authentication attempts. Additional assertions were implemented to ensure both the status codes and response bodies matched expected behavior.

## How to Run

1. Import `ReqResCollection.json` and `ReqResEnvironment.json` into Postman
2. Select the ReqRes environment
3. Run the collection using the Collection Runner
4. Review the test results to verify that all assertions pass

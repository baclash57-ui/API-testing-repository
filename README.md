# API Testing Portfolio

This repository contains Postman collections developed to test the functionality of three different APIs. Each project demonstrates a practical approach to API testing through automated assertions, HTTP status code verification, response body validation, and dynamic variable handling. The collections are structured to simulate real-world testing scenarios, including both expected success flows and deliberate failure cases.

---

## Projects

### 1. Simple Books API
This collection tests the Simple Books API end-to-end, covering everything from authentication to full order lifecycle management. Tests validate status codes, response accuracy, and data integrity across key workflows including book catalog retrieval, individual book lookup, and order creation, retrieval, update, and deletion. Collection variables are used to dynamically store and reuse authentication tokens and order IDs generated during execution, enabling seamless request chaining without manual intervention.

### 2. Reqres API
This collection tests the Reqres API across a wide range of scenarios, organized into two folders — passed requests and intentionally failing requests. It covers user management, authentication, registration, resource retrieval, pagination validation, and delayed response handling. Assertions go beyond basic status codes to verify response structure, field types, email format, avatar URL validity, and error messages. Pre-request scripts are used to randomly generate user IDs, making each test run dynamic and reducing hardcoded dependencies.

### 3. Trello API
This collection tests the Trello API through a complete end-to-end workflow, simulating how a real user would interact with the platform — from creating a board all the way through to deleting it. It covers boards, lists, cards, and checklists, with assertions validating status codes, response fields, data types, and response times. Pre-request scripts randomly select board names from a predefined list to keep each run unique. The collection was executed using both Postman and Newman, with HTML reports generated to document test results.

---

## Tools Used
- **Postman** — API collection development, manual test execution, and assertion scripting
- **Newman** — Command-line runner used to automate collection execution and generate detailed HTML test reports

## Security
All authentication tokens, API keys, and sensitive credentials have been removed from this repository before publication and are managed through environment variables.

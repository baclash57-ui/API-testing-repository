This document highlights the order of executing the API requests for Trello APIs and the dependencies for each request.

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


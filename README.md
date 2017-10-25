Requirement Report for Ghost
----------------

#### Final Assurance claims

* 	[Ghost Login module successfully averts session hijacking.](https://www.lucidchart.com/invitations/accept/0a976aa4-6349-48fc-8ed8-dc3c684c11d4)

* 	[Ghost Login Module has no exploitable SQL_injection weaknesses.](https://www.lucidchart.com/invitations/accept/0a976aa4-6349-48fc-8ed8-dc3c684c11d4)

* 	[The Ghost User Story Module has mitigated all privilege escalations.](https://www.lucidchart.com/invitations/accept/0a976aa4-6349-48fc-8ed8-dc3c684c11d4)

* 	[Ghost code injection module has no exploitable XSS Weaknesses.](https://www.lucidchart.com/invitations/accept/0a976aa4-6349-48fc-8ed8-dc3c684c11d4)

* 	[Ghost system has no API Authentication weaknesses.](https://www.lucidchart.com/invitations/accept/0a976aa4-6349-48fc-8ed8-dc3c684c11d4)

#### Security Requirements

###### [Privilege escalation](https://www.lucidchart.com/invitations/accept/12f66949-a4b7-4950-84f2-78229cdff59d)

* The system should enforce access control list for to handle privilege roles in the application.
* Implement data sanitization to avoid injection of malicious scripts in the data fields in the system.

###### [User authentication](https://www.lucidchart.com/invitations/accept/12f66949-a4b7-4950-84f2-78229cdff59d)

* The system should use a pseudorandom number generator to create session ID of higher entropy.
* The system should use https to encrypt all traffic end to end during session management.
* The system should use captcha for user authentication to prevent unwanted access to ghost admin.
* The system should enforce a security question, when the user performs critical tasks related to the database.

###### [API](https://www.lucidchart.com/invitations/accept/12f66949-a4b7-4950-84f2-78229cdff59d)

* The system should make sure that the API calls are authenticated with secret key.
* The system should ensure that the requests made to the API are restricted to select list of IP addresses.

###### [SQL Injecttion](https://www.lucidchart.com/invitations/accept/12f66949-a4b7-4950-84f2-78229cdff59d)

* The system should have protection against user and password enumeration attack.
* The system should implement generic error messages to avoid exposing system sensitive data.
* The system should use cookie based authentication for users.

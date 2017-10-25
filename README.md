# Requirement Report for Ghost


### Final Assurance claims

* 	[Ghost Login module successfully averts session hijacking.](https://www.lucidchart.com/invitations/accept/0a976aa4-6349-48fc-8ed8-dc3c684c11d4)

* 	[Ghost Login Module has no exploitable SQL_injection weaknesses.](https://www.lucidchart.com/invitations/accept/0a976aa4-6349-48fc-8ed8-dc3c684c11d4)

* 	[The Ghost User Story Module has mitigated all privilege escalations.](https://www.lucidchart.com/invitations/accept/0a976aa4-6349-48fc-8ed8-dc3c684c11d4)

* 	[Ghost code injection module has no exploitable XSS Weaknesses.](https://www.lucidchart.com/invitations/accept/0a976aa4-6349-48fc-8ed8-dc3c684c11d4)

* 	[Ghost system has no API Authentication weaknesses.](https://www.lucidchart.com/invitations/accept/0a976aa4-6349-48fc-8ed8-dc3c684c11d4)

### Security Requirements

#### [Privilege escalation](https://www.lucidchart.com/invitations/accept/12f66949-a4b7-4950-84f2-78229cdff59d)

* The system should enforce access control list for to handle privilege roles in the application.
* Implement data sanitization to avoid injection of malicious scripts in the data fields in the system.

#### [User authentication](https://www.lucidchart.com/invitations/accept/12f66949-a4b7-4950-84f2-78229cdff59d)

* The system should use a pseudorandom number generator to create session ID of higher entropy.
* The system should use https to encrypt all traffic end to end during session management.
* The system should use captcha for user authentication to prevent unwanted access to ghost admin.
* The system should enforce a security question, when the user performs critical tasks related to the database.

#### [API](https://www.lucidchart.com/invitations/accept/12f66949-a4b7-4950-84f2-78229cdff59d)

* The system should make sure that the API calls are authenticated with secret key.
* The system should ensure that the requests made to the API are restricted to select list of IP addresses.

#### [SQL Injecttion](https://www.lucidchart.com/invitations/accept/12f66949-a4b7-4950-84f2-78229cdff59d)

* The system should have protection against user and password enumeration attack.
* The system should implement generic error messages to avoid exposing system sensitive data.
* The system should use cookie based authentication for users.

### Security Requirements specified in Ghost Documentation

Ghost advertises itself as a Platform as a service for hosting a blog. Some of the features advertised under Pass are ensuring data security, role privilege access. Also, Ghost advertises of providing SSL by default and isolated applications, firewalls and spam protection. 

Ghost is built on Restful JSON API, and the data access is handled by the API. Since Ghost uses RESTFUL principles, SSL plays a vital role in securing the data access over the resource oriented URLS. The URLS are easily guessable.

The security requirements we could extract from the documentation were related to the use of the Restful Json API for secure access of data over the blog. The restful json API makes use of the HTTP authorizations provide private access.

To provide better secure access to the data hosted, ghost divides the API in to two, a Public API and a private API. The data access is provided by client authentication a oAuth client authentication for authentication by public clients which are not secure.

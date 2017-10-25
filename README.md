Requirement Report for Ghost
----------------

#### Final Assurance claims

1. 		Ghost Login module successfully averts session hijacking.
2. 		Ghost Login Module has no exploitable SQL_injection weaknesses
3. 		The Ghost User Story Module has mitigated all privilege escalations
4. 		Ghost code injection module has no exploitable XSS Weaknesses
5. 		Ghost system has no API Authentication weaknesses

#### Security Requirements

[Click here for Misuse Cases](https://www.lucidchart.com/users/registerOrLogin/free?showLogin=false&instructionMessage=Accept+invitation+to+%27Team+Spark+Misusecases%27&psuedoEditorTitle=Team+Spark+Misusecases)


###### Privilege escalation

* The system should enforce access control list for to handle privilege roles in the application.
* Implement data sanitization to avoid injection of malicious scripts in the data fields in the system.

###### User authentication

* The system should use a pseudorandom number generator to create session ID of higher entropy.
* The system should use https to encrypt all traffic end to end during session management.
* The system should use captcha for user authentication to prevent unwanted access to ghost admin.
* The system should enforce a security question, when the user performs critical tasks related to the database.

###### API

* The system should make sure that the API calls are authenticated with secret key.
* The system should ensure that the requests made to the API are restricted to select list of IP addresses.

###### SQL Injecttion

* The system should have protection against user and password enumeration attack.
* The system should implement generic error messages to avoid exposing system sensitive data.
* The system should use cookie based authentication for users.

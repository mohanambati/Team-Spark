# Requirement Report for Ghost


### Final Assurance claims
* 	[Ghost Login module successfully averts session hijacking.](https://www.lucidchart.com/invitations/accept/0a976aa4-6349-48fc-8ed8-dc3c684c11d4)
* 	[Ghost Login Module has no exploitable SQL_injection weaknesses.](https://www.lucidchart.com/invitations/accept/0a976aa4-6349-48fc-8ed8-dc3c684c11d4)
* 	[The Ghost User Story Module has mitigated all privilege escalations.](https://www.lucidchart.com/invitations/accept/0a976aa4-6349-48fc-8ed8-dc3c684c11d4)
* 	[Ghost code injection module has no exploitable XSS Weaknesses.](https://www.lucidchart.com/invitations/accept/0a976aa4-6349-48fc-8ed8-dc3c684c11d4)
* 	[Ghost system has no API Authentication weaknesses.](https://www.lucidchart.com/invitations/accept/0a976aa4-6349-48fc-8ed8-dc3c684c11d4)

### Security Requirements

#### [Privilege Escalation](https://www.lucidchart.com/invitations/accept/12f66949-a4b7-4950-84f2-78229cdff59d)
* The system should enforce access control list for to handle privilege roles in the application.
* Implement data sanitization to avoid injection of malicious scripts in the data fields in the system.

#### [User Authentication](https://www.lucidchart.com/invitations/accept/12f66949-a4b7-4950-84f2-78229cdff59d)
* The system should use a pseudorandom number generator to create session ID of higher entropy.
* The system should use https to encrypt all traffic end to end during session management.
* The system should use captcha for user authentication to prevent unwanted access to ghost admin.
* The system should enforce a security question, when the user performs critical tasks related to the database.

#### [API](https://www.lucidchart.com/invitations/accept/12f66949-a4b7-4950-84f2-78229cdff59d)
* The system should make sure that the API calls are authenticated with secret key.
* The system should ensure that the requests made to the API are restricted to select list of IP addresses.

#### [SQL Injection](https://www.lucidchart.com/invitations/accept/12f66949-a4b7-4950-84f2-78229cdff59d)
* The system should have protection against user and password enumeration attack.
* The system should implement generic error messages to avoid exposing system sensitive data.
* The system should use cookie based authentication for users.

### Security Requirements specified in Ghost Documentation

Ghost advertises itself as a Platform as a service for hosting a blog. Some of the features advertised under Pass are ensuring data security, role privilege access. Also, Ghost advertises of providing SSL by default and isolated applications, firewalls and spam protection. 

Ghost is built on Restful JSON API, and the data access is handled by the API. Since Ghost uses RESTFUL principles, SSL plays a vital role in securing the data access over the resource oriented URLS. The URLS are easily guessable.
#### [Privilege Escalation]()

#### [User Authentication](https://api.ghost.org/docs/user-authentication)


#### [API Authentication](https://api.ghost.org/docs/client-authentication)
The security requirements we could extract from the documentation were related to the use of the Restful Json API for secure access of data over the blog. The restful json API makes use of the HTTP authorizations provide private access.

To provide better secure access to the data hosted, ghost divides the API in to two, a Public API and a private API. The data access is provided by client authentication a oAuth client authentication for authentication by public clients which are not secure.

#### [SQL Injection]()


### Security related Configiration

We can add a custom configuration file to override Ghost's default behaviour. Ghost's configuration is managed by [nconf](https://github.com/indexzero/nconf) which is a custom configuration JSON file and must be located in the root folder.

#### [Ghost Environment](https://docs.ghost.org/docs/config) 

Ghost uses Node.js which has the concept of environments. It has two built in environment modes development and production. 

development environment | production environment
---|---
config.development.json | config.production.json


Development environment is used when developing and debugging ghost where as production environment is used in live blog. By default ghost is configured in development mode. In production we need to set a configuration variable NODE_ENV to production. This will mitigates the loss of sensitive data.

#### [Mail Config](https://docs.ghost.org/docs/mail-config)
A mail service should be configured in ghost so that ghost sends email such as forgotten password and user invitation mail. Wrong configuration of this service will lead to loss of sensitive data and privilages.

#### [Admin URL](https://docs.ghost.org/docs/cli-knowledge-base#section-ssl)
Ghost has congiration option for securing URL's using SSL. We need to specify that admin URL as HTTPS instead of HTTP because without SSL the username and password entered in any URL is a plain text. By this network sniffers will not able to interpret the exchanged data.

#### Privacy Config
Ghost provides a mechanisam where we can turn off all the unused featured in the application. This features should be listed a [PRIVACY.md](https://github.com/TryGhost/Ghost/blob/master/PRIVACY.md) file.

##### *Automatic Update check*
Ghost introduced an automatic update check service to let you know when a new version of Ghost is available (woo!). Ghost.org collects basic anonymous usage statistics from update check requests.

See [PRIVACY.md#automatic-update-checks](https://github.com/TryGhost/Ghost/blob/master/PRIVACY.md#automatic-update-checks) for more details.

##### *Third party services*
Ghost uses other third party services for specific functionality within ghost. 
1. Gravatar [PRIVACY.md#gravatar](https://github.com/TryGhost/Ghost/blob/master/PRIVACY.md#gravatar)
2. RPC Pings [PRIVACY.md#rpc-pings](https://github.com/TryGhost/Ghost/blob/master/PRIVACY.md#rpc-pings)
3. Structured Data[PRIVACY.md#structured-data](https://github.com/TryGhost/Ghost/blob/master/PRIVACY.md#structured-data)
4. Default Theme

These can be disabled if they are not used.

#### Maintainence Mode
Ghost has a Maintainance Mode that will serve 503 HTTP response. We need to make sure that Maintainence Mode should be turn on while debugging the application.

#### Logging
We can configure what detailed should be logged. We need to take care of logs so that they should not reveal any sensitive data.

#### Spam and Cache settings
You can tell Ghost how to treat spam requests. See [spam configuration in Ghost](https://github.com/TryGhost/Ghost/blob/master/core/server/config/defaults.json#L26).

Caching for sitemaps, redirects or assets can be configured via the caching property.
See [caching configuration in Ghost](https://github.com/TryGhost/Ghost/blob/master/core/server/config/defaults.json#L57).

### Installation Issues
* Ghost documentation for installing ghost in local server is mainly focued on ghost theme development. It lacks more information about Ghost-Admin installation procedure.
* In Ghost-Admin installation procedure, documentation is missing the details of SQL Server installation that needs to be installed before installing the application. 

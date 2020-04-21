Access tokens
--------
The Registration Module is a server used to register users in the SCAIFE system.
Users at the UI module register and login through this server to receive an access token that is
intended in the future to enable the UI Module to communicate securely with the Statistics, DataHub, and
Prioritization Modules that are connected to the Registration Module.

Note: The SCAIFE Registration Module utilizes JSON Web Tokens (JWTs) to grant access to its users. Currently, the access tokens
used to interact with the Statistics, Prioritization, and DataHub modules are intended to be validated to ensure they are not expired
and that they contain the correct security keys for server access; however, access tokens are not validated against
the SCAIFE user database in the Registration module. Currently, security weaknesses in the system include:

- If any user anywhere in the distributed system gains access to the security key, which is the same and shared by all modules,
then that user can create a token of the acceptable format and can interact with all the other non-Registration SCAIFE servers. (For example, a malicious user who gained access to the security key could create API messages that would appear to come from any of the types of SCAIFE modules. By sending incorrect data such a malicious user could corrupt the system and data within all the servers. Also, such a malicious user could gain access to data they should not have access to, if the security key were not shared by all modules and not otherwise protected as in the current system.)
- The current system setup does not accommodate de-registering a user in the Registration Module. Although expiration is enforced by examining timestamps,
a malicious user (e.g., a malicious user at the UI Module) could get around that simply by creating a new token using the same security key to successfully communicate with the other non-Registration SCAIFE servers. (An example of a way to more securely handle de-registering a user follows: The non-Registration SCAIFE server modules could check with the Registration Module to find out if a token was authorized by the Registration module. The Registration module could handle de-registering a user, e.g., if a SCAIFE system administrator decides to de-authorize a previously-authorized user. After that, queries to the Registration Module about that user would show they were not authorized.)

To provide more security within the SCAIFE system future iterations may implement validation of access tokens at the Registration Module,
and/or enable the Transport Layer Security (TLS) protocol for server communications.





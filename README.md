#secure auth


Develop an HTTP server to function as an authentication server. This server should support the following essential operations:

User Authentication: This involves generating a JWT for users as detailed under the /auth endpoint.
User Management: To manage user accounts and permissions, refer to the User Management endpoints.
Due to potential security threats, implement robust mechanisms at the /auth endpoint to mitigate unauthorized access by:

Blocking IP subnets;
Restricting specific users;
To prevent a DOS attack, the server must enforce limits for request size:

10*1024 bytes for headers: If headers exceed this length, the server must return HTTP status code 431.
100*1024 bytes for the body: If the body exceeds this length, the server must return HTTP status code 413.
For user IP address identification, utilize the X-Forwarded-For HTTP header.

The check order is:

Check if IP is on the blacklist;
Authenticate, if applicable;
Verify if a user from the JWT is on the blacklist, if applicable;
Authorize, if applicable;

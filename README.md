![CanaryBg](https://github.com/user-attachments/assets/9b13ca27-a225-4ea8-9d13-855112b31b00)

# canary
Canary Php Framework .
https://canary.ebznz.com/


This PHP code defines a class CANARY that seems to serve as a utility class for handling HTTP requests, logging, token management, and database interactions. Here’s a brief breakdown of the class:

Constructor and Basic Methods:

__construct(): An empty constructor, possibly used as a placeholder.
var($var): Static method to return a global variable.
SET($var, $val): Sets a value in the global $canary array.
GET(), POST(), REQUEST(), REQUESTW(): Methods to handle HTTP GET, POST, and REQUEST variables, respectively. They process incoming data, sanitize it using htmlspecialchars, and log the result.
Token and Language Methods:

getToken(): Retrieves the token from the global canary array if the appropriate libraries are imported.
getLang(): Retrieves the language from the global canary array.
Token Verification and Maintenance:

checkToken($dbtbl, $dbtoken, $dbexpier): Checks the validity of a token and logs the result.
VERSION($minVersion, $lastVersion, $lastVersionName): Checks if the application version is up-to-date and prompts the user to update if necessary.
MAINTENANCE($maintenance): Provides a maintenance notice if maintenance is scheduled.
Diagnostics:

doctor() and doctori(): Methods for setting up diagnostic reports.
Logging Methods:

listening($res, $data): Logs successful operations.
listeninge($res, $data): Logs failed operations.
Database Interaction Methods:

Methods like conn(), SQL($sql), SELECT($sql), INSERT($sql), UPDATE($sql), and DELETE($sql) are used for various database operations using MySQLi.
Utility and Helper Methods:

lastSQL(), lastId(): Retrieve the last SQL query or ID.
checkLibImport($lib): Checks if a specific library is imported.
geo($ip): Attempts to perform a geolocation lookup.
Routing and Validation:

Route($key, $class, $parameters): Routes requests to specified class methods based on a key.
VALIDATE($prm, $type): Validates the data type of a parameter and throws an error if it doesn’t match the expected type.
Notes for Improvement:
Security:

Although htmlspecialchars is used for sanitizing user input, additional measures like parameterized queries for SQL operations are advisable to prevent SQL injection attacks.
The use of global variables is generally discouraged as it can lead to unexpected side effects and security issues.
Error Handling:

The code uses basic try-catch blocks, but the exception handling could be more robust with specific error messages and logging mechanisms.
Modularity:

Consider separating concerns into different classes or modules (e.g., a separate class for database operations, another for HTTP request handling).
Documentation:

Adding comments and PHPDoc annotations would be helpful for maintaining and understanding the code.
Use of Modern PHP Practices:

Use of namespaces, type declarations, and strict typing where possible could improve code readability and reliability.
The class provides a lot of functionality, but careful attention should be paid to security, error handling, and modern coding practices.


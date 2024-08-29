![CanaryBg](https://github.com/user-attachments/assets/9b13ca27-a225-4ea8-9d13-855112b31b00)

# canary
Canary Php Framework .
https://canary.ebznz.com/

Canary Framework
Canary is a PHP framework designed for efficient data handling and database operations. This README provides a comprehensive guide on how to use the Canary framework, including its installation, configuration, and features.

Table of Contents
Introduction
Requirements
Installation
Usage
Features
Data Handling
Database Operations
Token Management
Versioning
Maintenance
Validation
Examples
Contributing
License
Introduction
The Canary framework is designed to simplify PHP development by providing a set of tools for handling HTTP requests, managing tokens, and interacting with databases. It aims to streamline the development process and improve code maintainability.

Requirements
PHP 7.4 or higher
MySQL or MariaDB
Composer (for dependency management, if needed)
Installation
To install the Canary framework, follow these steps:

Download the framework: Clone or download the Canary repository.

bash
Copy code
git clone https://github.com/yourusername/canary.git
Include the framework: Require the lib/main.php in your project to use Canary.

php
Copy code
require 'path/to/canary/lib/main.php';
Configure the database connection: Ensure that the lib/main.php includes your database configuration.

Usage
Basic Setup
To use Canary in your PHP project, include the framework and configure it as needed.

php
Copy code
require 'path/to/canary/lib/main.php';

// Example usage
$canary = new CANARY();
Data Handling
Canary provides methods to handle HTTP GET, POST, and REQUEST data.

GET Data:

php
Copy code
$data = CANARY::GET();
POST Data:

php
Copy code
$data = CANARY::POST();
REQUEST Data:

php
Copy code
$data = CANARY::REQUEST();
Database Operations
Canary supports various SQL operations:

SELECT:

php
Copy code
$result = CANARY::SELECT('table_name');
INSERT:

php
Copy code
$result = CANARY::INSERT('table_name (column1, column2) VALUES (value1, value2)');
UPDATE:

php
Copy code
$result = CANARY::UPDATE('table_name SET column1 = value1 WHERE condition');
DELETE:

php
Copy code
$result = CANARY::DELETE('table_name WHERE condition');
Token Management
Canary provides functionality to manage and verify tokens:

Get Token:

php
Copy code
$token = CANARY::getToken();
Check Token:

php
Copy code
$result = CANARY::checkToken('table_name', 'token_column');
Versioning
Ensure users are running the correct version of your application:

php
Copy code
CANARY::VERSION('1.0.0', '1.2.0', 'Version 1.2.0');
Maintenance
Notify users of maintenance periods:

php
Copy code
CANARY::MAINTENANCE(30); // Maintenance for 30 minutes
Validation
Validate various data types with Canary's validation methods:

String:

php
Copy code
CANARY::VALIDATE($data, 'string');
Email:

php
Copy code
CANARY::VALIDATE($data, 'email');
Examples
Example 1: Basic Data Retrieval
php
Copy code
require 'path/to/canary/lib/main.php';

$data = CANARY::GET();
print_r($data);
Example 2: Database Query
php
Copy code
require 'path/to/canary/lib/main.php';

$result = CANARY::SELECT('users WHERE id = 1');
print_r($result);
Contributing
We welcome contributions to the Canary framework. If you have any improvements or bug fixes, please fork the repository and submit a pull request.

License
This project is licensed under the MIT License. See the LICENSE file for details.

Feel free to modify this template according to your specific needs and project structure. If you need additional sections or more detailed explanations for certain features, let me know!





Canary Framework Documentation
The Canary Framework provides a set of utility functions that streamline various tasks in PHP. Below is a description of each function available in the CANARY class.

1. var($var)
Description: Retrieves a global variable from the $GLOBALS array using the provided variable name.
Parameters:
$var: The name of the global variable to retrieve.
Returns: The value of the specified global variable.
2. SET($var, $val)
Description: Stores a value in the $GLOBALS['canary'] array under the specified key.
Parameters:
$var: The key to set in the $GLOBALS['canary'] array.
$val: The value to assign to the key.
Returns: void.
3. GET()
Description: Collects data sent via the GET method, sanitizes it, and returns it as a JSON object. It also logs the success or failure of data collection.
Parameters: None.
Returns: A JSON object containing the GET data.
4. POST()
Description: Similar to the GET() function, but collects data sent via the POST method. The data is sanitized and returned as a JSON object.
Parameters: None.
Returns: A JSON object containing the POST data.
5. REQUEST()
Description: Collects data sent via the REQUEST method (GET, POST, and other methods combined), sanitizes it, and returns it as a JSON object. Logs the success or failure of data collection.
Parameters: None.
Returns: A JSON object containing the REQUEST data.
6. REQUESTW()
Description: Collects and sanitizes data sent via the REQUEST method, but does not log the success or failure of data collection. Returns the data as a JSON object.
Parameters: None.
Returns: A JSON object containing the REQUEST data.
7. ENV($var = null)
Description: Retrieves environment variables from the .env file.
Parameters:
$var: The name of the environment variable to retrieve. If null, returns all environment variables.
Returns: A JSON object containing the specified environment variable or all variables if $var is null.
8. sendOTPEmail($toEmail, $otp)
Description: Sends an OTP (One-Time Password) to the specified email address using SMTP settings from the environment variables.
Parameters:
$toEmail: The recipient's email address.
$otp: The OTP to send.
Returns: void.
9. sendOTPWhatsApp($toWhatsapp, $otp)
Description: Sends an OTP to the specified WhatsApp number using the WhatsApp API and settings from the environment variables.
Parameters:
$toWhatsapp: The recipient's WhatsApp number.
$otp: The OTP to send.
Returns: void.
10. sendFCM($deviceToken, $title, $body, $image = null)
markdown
نسخ الكود
- **Description**: Sends a Firebase Cloud Messaging (FCM) notification to a specified device.
- **Parameters**: 
  - `$deviceToken`: The FCM token of the device.
  - `$title`: The notification title.
  - `$body`: The notification body.
  - `$image`: (Optional) The URL of an image to include in the notification.
- **Returns**: `void`.
11. getLang()
markdown
نسخ الكود
- **Description**: Retrieves the language setting stored in the `canary` global array.
- **Parameters**: None.
- **Returns**: The current language setting.
12. getToken()
markdown
نسخ الكود
- **Description**: Retrieves the token stored in the `canary` global array.
- **Parameters**: None.
- **Returns**: The current token.
13. checkToken($dbtbl, $dbtoken = null, $dbexpier = null)
markdown
نسخ الكود
- **Description**: Checks if a provided token is valid by comparing it against tokens in a database table. Logs the result and returns the validation status.
- **Parameters**: 
  - `$dbtbl`: The database table to check.
  - `$dbtoken`: The column in the database that stores tokens.
  - `$dbexpier`: The column in the database that stores token expiry times.
- **Returns**: The result of the token check.
14. VERSION($minVersion, $lastVersion, $lastVersionName)
markdown
نسخ الكود
- **Description**: Checks if the client's application version is up to date. If not, it prompts the user to update.
- **Parameters**: 
  - `$minVersion`: The minimum supported version.
  - `$lastVersion`: The latest version available.
  - `$lastVersionName`: The name of the latest version.
- **Returns**: `void`.
15. MAINTENANCE($maintenance = null)
markdown
نسخ الكود
- **Description**: Forces a maintenance mode message if the system is under maintenance.
- **Parameters**: 
  - `$maintenance`: The duration of the maintenance.
- **Returns**: `void`.
16. allowedReport()
markdown
نسخ الكود
- **Description**: Calls the `allowedReport()` function to determine if reporting is allowed.
- **Parameters**: None.
- **Returns**: `void`.
17. allowedDoctor()
markdown
نسخ الكود
- **Description**: Calls the `allowedDoctor()` function to determine if the doctor report is allowed.
- **Parameters**: None.
- **Returns**: `void`.
18. doctor()
markdown
نسخ الكود
- **Description**: Enables the doctor report mode and returns the status.
- **Parameters**: None.
- **Returns**: The status of the doctor report mode.
19. doctori()
markdown
نسخ الكود
- **Description**: Enables the doctor-info report mode and returns the status.
- **Parameters**: None.
- **Returns**: The status of the doctor-info report mode.
20. listening($res, $data = null)
markdown
نسخ الكود
- **Description**: Logs successful operations with an optional data payload.
- **Parameters**: 
  - `$res`: The message to log.
  - `$data`: (Optional) Additional data to log.
- **Returns**: `void`.
21. listeninge($res, $data = null)
markdown
نسخ الكود
- **Description**: Logs failed operations with an optional data payload.
- **Parameters**: 
  - `$res`: The error message to log.
  - `$data`: (Optional) Additional data to log.
- **Returns**: `void`.
22. export($jsonMsg, $code = null, $data = null, $jsonMsgAr = null)
markdown
نسخ الكود
- **Description**: Exports a response message, status code, and optional data to the client.
- **Parameters**: 
  - `$jsonMsg`: The message to export.
  - `$code`: (Optional) The status code to return.
  - `$data`: (Optional) Additional data to return.
  - `$jsonMsgAr`: (Optional) An Arabic version of the message.
- **Returns**: `void`.
23. conn()
markdown
نسخ الكود
- **Description**: Returns the database connection stored in the `canary` global array.
- **Parameters**: None.
- **Returns**: The database connection.
24. SQL($sql)
markdown
نسخ الكود
- **Description**: Executes a SQL query and logs the results, including the number of rows affected.
- **Parameters**: 
  - `$sql`: The SQL query to execute.
- **Returns**: The result set or `null` if the query fails.
25. SELECT($sql)
markdown
نسخ الكود
- **Description**: Executes a `SELECT` SQL query and logs the results, including the number of rows retrieved.
- **Parameters**: 
  - `$sql`: The SQL `SELECT` query to execute.
- **Returns**: The result set or `null` if the query fails.
26. SELECTW($sql)
sql
نسخ الكود
- **Description**: Executes a `SELECT` SQL query with additional WHERE conditions and logs the results.
- **Parameters**: 
  - `$sql`: The SQL `SELECT` query with WHERE conditions to execute.
- **Returns**: The result set or `null` if the query fails.

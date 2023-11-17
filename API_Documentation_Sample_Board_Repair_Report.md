# Board Repair Verification Report API Documentation Sample
### Introduction:
The Board Repair Verification Report API allows users to automate the process of creating detailed reports on the operational status of boards after repair. This API simplifies the post-repair verification process, making it more efficient and accurate.
### Base URL example:
https://api.boardrepairapp.com#
### Authentication:
To use the Board Repair Verification Report API, obtain an API key by registering on our developer portal.
### Endpoints:
  + `/verify-board`: Submit board verification data and generate a report.
  + `/report-status`: Check the status of a generated report.
  + `/download-report`: Download a generated report in PDF format.
### Request Methods:
Endpoints support HTTP GET, POST, PUT, and DELETE requests.
### Request Parameters:
**/verify-board** endpoint:
  + `board_serial` *(required)*: The serial number of the repaired board.
  + `api_key` *(required)*: Your API key for authentication.
  + `test_results` *(required)*: JSON object containing the test results.
##### Sample Request JSON:
````
POST /verify-board
{
  "board_serial": "BRD12345789",
  "api_key": "user-api-key",
  "test_results": {
    "power_test": "passed",
    "connection_test": "passed",
    // Additional test results...
  }
}
````
**/report-status**, 
**/download-report** endpoints:
+ `report_id` *(required)*: The unique identifier of the generated report.
+ `api_key` *(required)*: Your API key for authentication.
##### Sample Request JSON:
````
POST /report-status
{
  "report_id": 987,
  "api_key": "user-api-key"
}
````
### Responses:
+ The API returns data in JSON format.
+ Successful responses will have a 200 status code.
+ Error responses include detailed error messages for troubleshooting.
##### Sample Response:
````
{
  "report_id": 987,
  "board_serial": "BRD12345789",
  "report_data": 
  {
    "verification_date": "2022-10-25",
    "tested_by": "John Luther",
    "test_results": 
    {
      "power_test": "passed",
      "connection_test": "passed",
      // Additional test results...
    }
  }
}
````
### Other possible requests: 
+ **Get a Report (GET):**
   - **Endpoint:** `/reports/{report_id}`
   - **Description:** Retrieves information about a specific report by its identifier.
   - **Request Parameters:**
     - `report_id` (number): Identifier of the report.

+ **List of Reports (GET):**
   - **Endpoint:** `/reports`
   - **Description:** Retrieves a list of all board check reports.

+ **Update a Report (PUT):**
   - **Endpoint:** `/reports/{report_id}`
   - **Description:** Updates information about an existing report.
   - **Request Parameters:**
     - `report_id` (number): Identifier of the report.
   - **Example Request Body to update the result of Test 2:**
     ```json
     {
       "test_results": {
         "test2": true
       }
     }
     ```

+ **Delete a Report (DELETE):**
   - **Endpoint:** `/reports/{report_id}`
   - **Description:** Deletes a report by its identifier.
   - **Request Parameters:**
     - `report_id` (number): Identifier of the report.


### Error Handling:
If an error occurs, the API returns an error response with a corresponding HTTP status code and an error message.
### Conclusion:
The Board Repair Verification Report API simplifies the verification process for repaired boards by automating report generation, helping businesses ensure the quality and reliability of their repaired electronic components.


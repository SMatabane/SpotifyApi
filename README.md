# Spotify_API_Testing
    This project tests various functionalities of the Spotify Web API using Rest Assured, TestNG, Log4j, and Allure Reporting. It includes positive and negative test scenarios for Player, Playlist, User, and 
    Artists endpoints. **check master branch**

## Test Identifier
    SPOTIFY-API-TP-001

## Objectives
    - Validate API functionality for all supported endpoints.
    - Ensure compliance with Spotify API documentation and expected response formats.
    - Test authentication mechanisms and token management.
    - Verify data integrity and accuracy in responses.
    - Handle and validate edge cases and error scenarios.

## Scope
    Player:
      Positive Tests:
        - Resume Playback
        - Skip to Next/Previous Track

      Negative Tests:
         - Invalid or expired token (401 Unauthorized).

    PlayList:
       Positive Tests:
         - Create new playlist.
         - Add items to a playlist.
         - Get playlist details.
         - Update playlist details.
    
      Negative Tests:
        - Invalid playlist ID (404 Not Found).
        - Invalid token (401 Unauthorized).
        - Invalid body parameters (400 Bad Request)

    User
      Positive Tests:
        - Retrieve user profile.
    
     Negative Tests:
        - Invalid user ID (404 Not Found).
        - Missing authorization (401 Unauthorized).

    Artists
      Positive Tests:
       - Get artist details.
       - Retrieve artist albums.
   
      Negative Tests*:
        - Invalid artist ID (404 Not Found).
        - Invalid query parameters (400 Bad Request).

## Risks
    - **Rate Limiting**: Too many requests may temporarily block access.

       **Mitigation**: Implement wait times and adhere to API rate limits.

    - **API Changes**: Updates to endpoints may break existing tests.

       **Mitigation**: Monitor API change logs regularly.

## Test Approach
    1. Test Tools
       - Rest Assured: API testing framework.
       - Java: Programming language for scripting.
       - TestNG: Test execution framework.
       - Allure: Reporting tool.
    2. Types of testing
       - Functional Testing: Verify the correctness of API endpoints.
       - Boundary Testing: Test APIs with edge-case inputs.
       - Error Handling Testing: Ensure proper error messages and codes.
    3. Execution Plan
       - Automate test scripts for core API functionalities.
       - Use data-driven testing to test multiple scenarios efficiently.
       - Validate API responses against expected results.

## Entry/Exit Criteria
    1. Entry Criteria
      - API documentation is available.
      - API endpoints are functional and accessible.
      - Test data (e.g., valid tokens, IDs) is prepared.
    2. Exit Criteria
      - All test cases have been executed.
      - Test reports have been reviewed and shared.

## Deliverables
      - Automated test scripts.
      - Test execution report (pass/fail status, response validation).
      - Logs for errors and failures.
      - Summary of defects found during testing.

## Resources
      - Team: QA Engineer (Rest Assured expertise), Test Lead
      - Environment: Local environment with API access
      - Tools: Java, Rest Assured, TestNG, Allure, IDE (e.g., IntelliJ IDEA)

## Test Schedule
| **Test Phase**        | **Duration** | **Responsible** |
|------------------------|--------------|------------------|
| Test Planning          | 1 day        | Test Lead        |
| Environment Setup      | 2 days       | QA Engineer      |
| Test Case Scripting    | 3 days       | QA Engineer      |
| Test Execution         | 3 days       | QA Engineer      |
| Reporting              | 1 day        | QA Engineer      |


## Test Scenarios

| **ID**   | **Test Scenario**       | **Priority** | **Expected Results**                          |
|----------|-------------------------|--------------|-----------------------------------------------|
| TC001    | Fetch user profile      | High         | User details are retrieved successfully.      |
| TC002    | Search item             | Medium       | Tracks are retrieved.                         |
| TC003    | Create Playlist         | High         | Playlist is created with given details.       |
| TC004    | Category filtering      | Medium       | A paged set of categories is displayed.       |
| TC005    | Playback queue          | Medium       | Command is received successfully.             |



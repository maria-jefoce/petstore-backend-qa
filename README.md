# Manual Test Cases for User Endpoint

## Test Case 1
- **Title**: Verify that the server successfully processes the request to create a new user
- **Test Data**: `{ "id": 0, "username": "string", "firstName": "string", "lastName": "string", "email": "string", "password": "string", "phone": "string", "userStatus": 0 }`
- **Steps**:
  1. Send a `POST` request to `/user` with test data.
  2. Check the status code.
- **Expected Result**: Response status 200.

## Test Case 2
- **Title**: Verify that the response contains a message with the ID of the created user
- **Test Data**: `{ "id": 0, "username": "string", "firstName": "string", "lastName": "string", "email": "string", "password": "string", "phone": "string", "userStatus": 0 }`
- **Steps**:
  1. Send a `POST` request to `/user` with test data.
  2. Check the response.
- **Expected Result**: The response contains a `message` field that includes the user ID.

## Test Case 3
- **Title**: Verify that a request to get user data is successful
- **Test Data**: Username of the created user
- **Steps**:
  1. Send a `GET` request to `/user/{username}`.
  2. Check the status code.
- **Expected Result**: Response status 200.

## Test Case 4
- **Title**: Verify that the response contains all required fields
- **Test Data**: Username of the created user
- **Steps**:
  1. Send a `GET` request to `/user/{username}`.
  2. Check the response.
- **Expected Result**: The response contains the fields: `id`, `username`, `email`, `password`, `phone`, `userStatus`.

## Test Case 5
- **Title**: Verify that the data matches the data that was created
- **Test Data**: Username of the created user, data of created user
- **Steps**:
  1. Send a `GET` request to `/user/{username}`.
  2. Compare user data from the response with the previously sent user data.
- **Expected Result**: The user data values match the created values.

## Test Case 6
- **Title**: Verify that the server successfully processes the user update request
- **Test Data**: Username of the created user, new data (username, email)
- **Steps**:
  1. Send a `PUT` request to `/user/{username}`.
  2. Check the status code.
- **Expected Result**: Response status 200.

## Test Case 7
- **Title**: Verify that the updated user data is indeed updated
- **Test Data**: Username of the created user, new data (username, email)
- **Steps**:
  1. Send a `PUT` request to `/user/{username}`.
  2. Send a `GET` request to `/user/{username}`.
  3. Check the response.
- **Expected Result**: User data in the response matches the new values.

## Test Case 8
- **Title**: Verify that the server successfully processes the user deletion request
- **Test Data**: Username of the created user
- **Steps**:
  1. Send a `DELETE` request to `/user/{username}`.
  2. Check the status code.
- **Expected Result**: Response status 200.

## Test Case 9
- **Title**: Verify that the response to a user deletion request contains the username in the message
- **Test Data**: Username of the created user
- **Steps**:
  1. Send a `DELETE` request to `/user/{username}`.
  2. Check the response.
- **Expected Result**: The response contains a `message` field that includes the username.

## Test Case 10
- **Title**: Verify that the deletion of the user is successful
- **Test Data**: Username of the deleted user
- **Steps**:
  1. Send a `GET` request to `/user/{username}` after the deletion.
  2. Check the status code.
- **Expected Result**: Response status 404.

# Additional Negative Test Cases

## Test Case 11
- **Title**: Verify that the server processes a request to update a user that does not exist
- **Test Data**: Username of the non-existent user
- **Steps**:
  1. Send a `PUT` request to `/user/{username}` with non-existent username.
  2. Check the status code.
- **Expected Result**: Response status 404.

## Test Case 12
- **Title**: Verify that the server processes a request to delete a user that does not exist
- **Test Data**: Username of the non-existent user
- **Steps**:
  1. Send a `DELETE` request to `/user/{username}` with non-existent username.
  2. Check the status code.
- **Expected Result**: Response status 404.

## Test Case 13
- **Title**: Verify that the server correctly handles an attempt to create a user with an existing username
- **Test Data**: Data of a user with an existing username, `{ "id": 0, "username": "string", "firstName": "string", "lastName": "string", "email": "string", "password": "string", "phone": "string", "userStatus": 0 }`
- **Steps**:
  1. Send a `POST` request to `/user` with an existing username.
  2. Check the status code.
- **Expected Result**: Response status 409.

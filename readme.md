# API Documentation

## Overview

This API provides services related to country information and phone number validation. It offers endpoints to retrieve country details, list countries with pagination, and validate phone numbers.

## Base URL

All URLs referenced in the documentation have the base part:

/api

## Endpoints

### 1. List Countries

- **URL**: `/countries`
- **Method**: `GET`
- **Query Parameters**:
  - `page`: The page number of the pagination.
  - `limit`: The number of items per page.
- **Success Response**:
  - **Code**: 200
  - **Content**: `{ message: 'get countries success', data: [countries] }`
- **Error Response**:
  - **Code**: 400
  - **Content**: `{ message: 'insufficient parameters' }`
  - **Code**: 500
  - **Content**: `{ message: 'get countries failed' }`
- **Description**: Fetches a paginated list of countries.

### 2. Get Country Details

- **URL**: `/country`
- **Method**: `GET`
- **Query Parameters**:
  - `iso`: ISO code of the country (optional).
  - `name`: Name of the country (optional).
  - `prefix`: Phone number prefix of the country (optional).
- **Success Response**:
  - **Code**: 200
  - **Content**: `{ message: 'get country success', data: country }`
- **Error Response**:
  - **Code**: 400
  - **Content**: `{ message: 'insufficient parameters' }`
  - **Code**: 500
  - **Content**: `{ message: 'get country failed' }`
- **Description**: Retrieves details of a specific country using either ISO code, name, or phone prefix.

### 3. Validate Phone Number

- **URL**: `/validate`
- **Method**: `GET`
- **Query Parameters**:
  - `number`: The phone number to validate.
- **Success Response**:
  - **Code**: 200
  - **Content**: `{ message: 'validate number success', data: validationResponse }`
- **Error Response**:
  - **Code**: 400
  - **Content**: `{ message: 'insufficient parameters' }`
  - **Code**: 500
  - **Content**: `{ message: 'validate number failed' }`
- **Description**: Validates the format of a given phone number.

## Status Codes

The API uses the following status codes:

- `200 OK`: The request was successful.
- `400 Bad Request`: The request was invalid or missing required parameters.
- `500 Internal Server Error`: An error occurred on the server.

## Notes

- Pagination parameters (`page` and `limit`) are required for the `/countries` endpoint to control the volume of data returned.
- At least one query parameter (`iso`, `name`, or `prefix`) is required for the `/country` endpoint.
- The `/validate` endpoint requires the `number` query parameter for phone number validation.
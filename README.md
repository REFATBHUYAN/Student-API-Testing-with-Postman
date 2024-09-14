# Student API Testing Documentation

This documentation provides a detailed overview of the Postman collection for testing the **Student API**. The collection includes requests for retrieving student data, creating new student records, updating technical skills, and other operations. It uses the Postman test scripts to validate the responses.

---

## Table of Contents
- [Prerequisites](#prerequisites)
- [Postman Collection](#postman-collection)
- [Endpoints](#endpoints)
  - [1. Get Student](#1-get-student)
  - [2. Create Student](#2-create-student)
  - [3. Get Specific Student](#3-get-specific-student)
  - [4. Create Technical Skills](#4-create-technical-skills)
  - [5. Create Student Address](#5-create-student-address)
  - [6. Final Student Details](#6-final-student-details)
- [Running Tests with Newman](#running-tests-with-newman)
- [Newman Report](#newman-report)

---

## Prerequisites

Before you begin, ensure you have met the following requirements:

- [Postman](https://www.postman.com/downloads/) installed on your local machine.
- [Newman](https://www.npmjs.com/package/newman) installed globally using `npm install -g newman`.

## Postman Collection

Download the Postman collection file for this project:

- **Collection Name**: `Bookin-website-API-Testing-with-Postman - Student API Collection`
- [Download the collection here](https://github.com/REFATBHUYAN/Student-API-Testing-with-Postman)

## Endpoints

### 1. Get Student

- **Method**: `GET`
- **URL**: `{{base_url}}/api/studentsDetails`
- **Description**: Fetches all student details.
- **Tests**:
  - Checks if the response status code is `200`.
  - Logs the length of the response.

### 2. Create Student

- **Method**: `POST`
- **URL**: `{{base_url}}/api/studentsDetails`
- **Body**: 
  ```json
  {
    "first_name": "Md",
    "middle_name": "Refat",
    "last_name": "Bhuyan",
    "date_of_birth": "1995-02-07"
  }
  ```
- **Description**: Creates a new student entry.
- **Tests**:
  - Checks if the response status code is `201`.
  - Saves the student `id` in an environment variable for later use.

### 3. Get Specific Student

- **Method**: `GET`
- **URL**: `{{base_url}}/api/studentsDetails/{{id}}`
- **Description**: Fetches a specific student's details using the `id`.
- **Tests**:
  - Checks if the response status code is `200`.
  - Verifies that the student's first, middle, last names, and date of birth are correct.

### 4. Create Technical Skills

- **Method**: `POST`
- **URL**: `{{base_url}}/api/technicalskills`
- **Body**: 
  ```json
  {
    "id": 1,
    "language": ["Java", "JavaScript"],
    "yearexp": "2",
    "lastused": "2024-09-09",
    "st_id": {{id}}
  }
  ```
- **Description**: Adds technical skills for the student.
- **Tests**:
  - Verifies the response status code is `200`.

### 5. Create Student Address

- **Method**: `POST`
- **URL**: `{{base_url}}/api/addresses`
- **Body**: 
  ```json
  {
    "Permanent_Address": {
      "House_Number": "27",
      "City": "Mirpur",
      "State": "1216",
      "Country": "Bangladesh",
      "PhoneNumber": [
        {"Std_Code": "+880", "Home": "01575267132", "Mobile": "01620453303"},
        {"Std_Code": "+880", "Home": "01575267133", "Mobile": "01620453304"}
      ]
    },
    "stId": {{id}}
  }
  ```
- **Description**: Adds an address for the student.
- **Tests**:
  - Validates the response's status and message.

### 6. Final Student Details

- **Method**: `GET`
- **URL**: `{{base_url}}/api/FinalStudentDetails/{{id}}`
- **Description**: Fetches final student details, including technical skills and address.
- **Tests**:
  - Verifies technical details and address fields for correctness.



### To Run the Collection:
```bash
newman run students.postman_collection.json -e students.postman_environment.json
```

## Newman Report

Here is a screenshot of the Newman test execution report:

![Newman Report](../Students-API-Testing-with-Postman/photos/newman_report_screenshots.png)

---

## Author

**Md. Refat Bhuyan**  
Full-stack Developer at Cunard Consulting Ltd and Senior QA at Quantanite
Contact: 01575267132  
Email: refatbubt@gmail.com
LinkedIn: [[LinkedIn URL](https://www.linkedin.com/in/refat-bhuyan/)]

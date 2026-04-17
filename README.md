# API Testing with Postman

This project contains API test scenarios designed to validate the behavior of the `/api/v1/kits/:id/products` endpoint.

The focus is on verifying how the system handles valid, invalid, and edge-case inputs.

---

## Objective

To ensure the API behaves correctly under different conditions, including boundary values, incorrect data types, and invalid requests.

---

## What Was Tested

- Valid requests with correct parameters  
- Boundary value testing (e.g., quantity = 0)  
- Invalid data types (e.g., string instead of number)  
- Missing or incorrect parameters  
- Invalid product IDs  
- API response behavior (status codes and error handling)  

---

## Test Approach

- Positive and negative test scenarios  
- Boundary value analysis  
- Validation of expected vs actual results  
- Identification of unexpected server behavior  

---

## Key Findings

During testing, several issues were identified:

- API accepted invalid values such as `quantity = 0`  
- Incorrect data types were not properly validated  
- Server returned `500 Internal Server Error` instead of `400 Bad Request` in some cases  
- Invalid product IDs were accepted without proper validation  

---

## Tools Used

- Postman  
- REST API  
- JSON  

---

## Project Purpose

This project was developed as part of a QA training program.

It demonstrates practical knowledge of:

- API testing  
- Test case design  
- Boundary and negative testing  
- Bug identification and reporting  

---

## Author

João Sampaio

# API Testing with Postman

This project contains API test scenarios designed to validate the behavior of two endpoints
from the Urban Routes and Order and Go services.

The focus is on verifying how the system handles valid, invalid, and edge-case inputs.

---

## Objective

To ensure both APIs behave correctly under different conditions, including boundary values,
incorrect data types, invalid requests, and edge cases related to delivery rules.

---

## Endpoints Tested

- `POST /api/v1/kits/:id/products` — adds products to a kit and validates list behavior
- `POST /order-and-go/v1/delivery` — validates delivery availability, pricing tiers, and field types

---

## What Was Tested

**`/api/v1/kits/:id/products`**
- Boundary value testing on kit product limits (0 to 30+ items)
- Duplicate product handling in the product list
- Validation of quantity field (zero, negative, string, missing)
- Validation of product ID field (string, special characters, boolean, empty, missing)
- Invalid product list structure (object instead of array, empty object)
- Non-existent kit handling
- Request consistency with repeated payloads and different item orders

**`/order-and-go/v1/delivery`**
- Boundary value testing on delivery time window (08h–22h)
- Pricing tier validation based on product count and weight
- Penalty cost validation when count or weight exceeds limits
- Validation of field types (string, boolean, zero, negative values)

---

## Test Approach

- Positive and negative test scenarios
- Boundary value analysis
- Validation of expected vs actual results
- Identification of unexpected server behavior

---

## Key Findings

During testing, several issues were identified:

- Duplicate product IDs incorrectly increased the product count
- `quantity = 0` and `quantity = -1` were accepted without validation
- String quantity caused concatenation instead of rejection (`productsCount: "191"`)
- Missing fields returned `500 Internal Server Error` instead of `400 Bad Request`
- Invalid product IDs (string, boolean, empty, special characters) returned `500` with HTML body
- Delivery time outside the valid window (07h, 23h) incorrectly returned `isItPossibleToDeliver: true`
- Penalty cost (`clientDeliveryCost = 9`) was not applied when count or weight exceeded limits
- Invalid field types for delivery parameters were accepted without validation

---

## Tools Used

- Postman
- REST API
- JSON

---

## Project Purpose

This project was developed as part of a QA engineering bootcamp.

It demonstrates practical knowledge of:

- API testing
- Test case design
- Boundary and negative testing
- Bug identification and reporting

---

## Author

João Sampaio

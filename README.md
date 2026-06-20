# Trello API Test Suite

## Overview

This project is an automated API test suite built using **Postman** and executed via **Newman CLI**, designed to validate core workflows of the Trello REST API.

It demonstrates real-world QA automation practices including:

- End-to-end API workflow testing  
- Environment-driven test execution  
- CI/CD pipeline compatibility (Jenkins-ready)  
- Dynamic data chaining across requests  
- Negative and positive validation strategies  

---

## Workflow Under Test

The suite validates a full Trello lifecycle:

1. Retrieve all boards  
2. Create a board (dynamic naming)  
3. Fetch and validate board schema  
4. Create TODO list linked to board  
5. Create card linked to list  
6. Move card to DONE  
7. Delete board (cleanup step)  
8. Validate deleted board returns `404`  

---

## What This Project Validates

### Functional Testing
- API status codes (200, 201, 404)
- CRUD operations across Trello resources

### Data Integrity
- Schema validation (boards, lists, cards)
- Nested object validation

### State Management
- Environment variable chaining:
  boardId → listId → cardId

### Test Design
- Dynamic data generation (no hardcoded values)
- Reusable environment configuration

### Negative Testing
- Validates deletion behavior (404 response)

---

## Tech Stack

- Postman (Test design)
- Newman CLI (Execution engine)
- Jenkins (CI/CD runner - Docker)
- Git & GitHub (Version control)
- HTML Extra Reporter (Reporting)

---

## Setup Instructions

### 1. Clone repository 

### 2. Import into Postman
Import postman_collection.json
Import postman_environment.json


### 3. Configure environment variables

Add:
- key
- token

Get credentials:
https://trello.com/power-ups/admin

Run Tests Locally (Newman)
newman run postman/postman_collection.json \
  -e postman/postman_environment.json \
  --reporters cli,htmlextra \
  --reporter-htmlextra-export reports/newman-report.html

CI/CD Execution (Jenkins Ready)
**Pipeline trigger flow:**
GitHub Push → Jenkins Webhook → Newman Execution → Report Generated
**Jenkins runs:**
newman run postman/postman_collection.json -e postman/postman_environment.json

Test Evidence
<img width="1557" height="961" alt="Trello API - run results 1" src="https://github.com/user-attachments/assets/81dcfd9c-40f6-41c1-824e-04097b448e49" />

Security Notes
- No credentials stored in repository
- API keys injected via environment variables
- Supports secure CI/CD execution via Jenkins credentials

# Trello API Test Suite

Automated API test suite against the live Trello REST API, built with Postman.

## Workflow Under Test

1. Get all boards
2. Create board (dynamic name via pre-request script)
3. Get single board — validate schema
4. Create TODO list scoped to board
5. Create card scoped to TODO list
6. Move card to DONE list
7. Delete board (teardown)
8. GET deleted board — assert 404

## What's Tested

- Status codes on all requests
- Nested schema validation (prefs, switcherViews, badges)
- State chaining via environment variables (boardId → toDoListId → cardId)
- Dynamic data generation (no hardcoded board or card names)
- Negative test: confirms deletion returns 404

## Setup

1. Import `Trello API.postman_collection.json` into Postman
2. Import `TrelloEnv.postman_environment.json` and rename it to `Trello API - Local`
3. Add your Trello API key and token to the environment
   - Get yours at: https://trello.com/power-ups/admin
4. Run the collection in order from top to bottom

## Auth

Key and token are stored as environment variables — never hardcoded.
Do not commit your real credentials. The template file has placeholders only.

## Results
<img width="1557" height="961" alt="Trello API - run results 1" src="https://github.com/user-attachments/assets/8737e040-5d31-4567-9700-847eaf2438ae" />

<img width="1561" height="997" alt="Trello API - run results 2" src="https://github.com/user-attachments/assets/48b99425-99b3-4bd3-b0df-7213441a7b9b" />


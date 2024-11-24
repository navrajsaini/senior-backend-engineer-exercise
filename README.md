# Syndio Backend App

Using the `employees.db` sqlite database in this repository with the following table/data:

```
sqlite> .open employees.db
sqlite> .schema employees
CREATE TABLE employees (id INTEGER PRIMARY KEY, gender TEXT not null);
sqlite> SELECT * FROM employees;
1|male
2|male
3|male
4|female
5|female
6|female
7|non-binary
```

Create an API endpoint that saves job data for the corresponding employees.

Example job data:

```json
[
  { "employee_id": 1, "department": "Engineering", "job_title": "Senior Enginer" },
  { "employee_id": 2, "department": "Engineering", "job_title": "Super Senior Enginer" },
  { "employee_id": 3, "department": "Sales", "job_title": "Head of Sales"},
  { "employee_id": 4, "department": "Support", "job_title": "Tech Support" },
  { "employee_id": 5, "department": "Engineering", "job_title": "Junior Enginer" },
  { "employee_id": 6, "department": "Sales", "job_title": "Sales Rep" },
  { "employee_id": 7, "department": "Marketing", "job_title": "Senior Marketer" }
]
```

## Requirements

- The API must take an environment variable `PORT` and respond to requests on that port.
- You provide:
  - Basic setup instructions required to run the API
  - Guide on how to ingest the data through the endpoint
  - A way to update the existing database given to you

## Success

- We can run the API and ingest database on your setup instructions
- The API is written in Golang

## Not Required

- Tests
- Logging, monitoring, or anything more than basic error handling

## Submission

- Respond to the email you received giving you this with:
  - a zip file, or link to a git repo
  - instructions on how to setup and run the code (could be included w/ zip/git)
- We'll follow the instructions to test it on a local machine, then we'll get back to you

## Notes

- Keep it simple
- If the API does what we requested, then it's a success
- Anything extra (tests, other endpoints, ...) is not worth bonus/etc
- We expect this to take less than two hours, please try and limit your effort to that window
- We truly value your time and just want a basic benchmark and common piece of code to use in future interviews
- If we bring you in for in-person interviews, your submission might be revisited and built on during the interview process


# Solution info
# Setup:
- set PORT env variable
- start the api (I used `go run .` in the api working directory)

All api expoints are under:/api/v1

# Creating a new entry:
- make POST request to /api/v1/employee
- request body must be a in json format
- the employee_id must be unique otherwise a 400 response will be returned
ex:
'''
{
    "employee_id": 8,
    "department": "Engineering",
    "job_title": "Senior Enginer",
    "gender": "male"
}
'''

# Reading employee entries:
Read all employee entries:
- make GET reques to /api/v1/employees

Read unique employee entry:
- make GET request to /api/v1/employee/<id>
- 200 response with the employee data will be returned

# Updating employee entry:
- make a PUT request to /api/v1/employee/<id>
- Request body must be in json format with the new data needed
ex:
'''
{
    "employee_id": 1,
    "department": "Engineering",
    "job_title": "Senior Enginer",
    "gender": "male"
}
'''

# Deleting a employee entry:
- make a DELETE request to /api/v1/employee/<id>
- with the specific id to be deleted
- 200 response with a short description will be returned on success

# NOTE
The original database was edited to include the missing fields

# Mergington High School Activities API

A super simple FastAPI application that allows students to view and sign up for extracurricular activities.

## Features

- View all available extracurricular activities
- Sign up for activities as an authenticated teacher
- View participants without logging in

## Getting Started

1. Install the dependencies:

   ```
   pip install fastapi uvicorn
   ```

2. Run the application:

   ```
   uvicorn src.app:app --reload
   ```

3. Open your browser and go to:
   - API documentation: http://localhost:8000/docs
   - Alternative documentation: http://localhost:8000/redoc

## API Endpoints

| Method | Endpoint                                                          | Description                                                         |
| ------ | ----------------------------------------------------------------- | ------------------------------------------------------------------- |
| GET    | `/activities`                                                     | Get all activities with their details and current participant count |
| POST   | `/auth/login`                                                       | Log in as a teacher                                                  |
| POST   | `/auth/logout`                                                      | Log out the current teacher                                          |
| POST   | `/activities/{activity_name}/signup?email=student@mergington.edu` | Sign up a student; requires teacher authentication                  |
| DELETE | `/activities/{activity_name}/unregister?email=student@mergington.edu` | Unregister a student; requires teacher authentication                |

## Data Model

The application uses a simple data model with meaningful identifiers:

1. **Activities** - Uses activity name as identifier:

   - Description
   - Schedule
   - Maximum number of participants allowed
   - List of student emails who are signed up

2. **Students** - Uses email as identifier:
   - Name
   - Grade level

All data is stored in memory, which means data will be reset when the server restarts.

Teacher authentication is configured in `src/teachers.json`. For local exercise use, the demo credentials are:

- Username: `teacher`
- Password: `mergington-admin`

Students can view activities and participants without logging in, but only authenticated teachers can register or unregister students.

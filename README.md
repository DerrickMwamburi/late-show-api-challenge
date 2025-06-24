Late Show API
A Flask REST API for managing a Late Night TV show system.
Setup Instructions

Clone the repository:

git clone https://github.com/<username>/late-show-api-challenge.git
cd late-show-api-challenge


Install dependencies:

pipenv install
pipenv shell


Set up PostgreSQL:

CREATE DATABASE late_show_db;


Configure environment:


Update server/config.py with your PostgreSQL credentials
Set JWT_SECRET_KEY environment variable:

export JWT_SECRET_KEY='your-secret-key'


Run migrations and seed data:

export FLASK_APP=server/app.py
flask db init
flask db migrate -m "initial migration"
flask db upgrade
python server/seed.py


Start the server:

python server/app.py

Authentication Flow

Register: POST /register with username and password
Login: POST /login with credentials to receive JWT token
Use token in protected routes with header: Authorization: Bearer <token>

API Routes



Route
Method
Auth Required
Description



/register
POST
No
Register a new user


/login
POST
No
Login and get JWT token


/episodes
GET
No
List all episodes


/episodes/
GET
No
Get episode details with appearances


/episodes/
DELETE
Yes
Delete episode and its appearances


/guests
GET
No
List all guests


/appearances
POST
Yes
Create new appearance


Sample Request/Response
POST /registerRequest:
{
    "username": "testuser",
    "password": "testpass"
}

Response:
{
    "message": "User registered successfully"
}

Postman Usage

Import challenge-4-lateshow.postman_collection.json
Set base_url variable to your server URL
Use Register and Login requests first
Copy token from Login response
Set token variable in Postman
Test all other endpoints

GitHub Repository
https://github.com/DerrickMwamburi/late-show-api-challenge.git
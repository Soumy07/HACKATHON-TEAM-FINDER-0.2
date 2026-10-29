# HACKATHON-TEAM-FINDER-0.2

A web application that helps college students find teammates for hackathons. Users can create a profile with their skills, browse hackathons, create teams or request to join existing ones, and team leaders can accept or reject those requests.

## Tech Stack

- **Frontend:** HTML, CSS, JavaScript, Bootstrap 5.3.3
- **Backend:** Python 3, Flask, Flask-CORS
- **Database:** MySQL 8, PyMySQL
- **Auth:** JWT (PyJWT) + Werkzeug password hashing

## Setup and Installation

### Prerequisites

- Python 3.10 or higher
- MySQL Server 8 or higher
- A code editor (VS Code recommended)
- A web browser

### Steps

**1. Create the database**

Open MySQL and run the schema file:

```bash
mysql -u root -p < database/schema.sql
```

This creates the `hackathon_team_finder` database with all tables and inserts seed data (15 skills and 4 hackathons).

**2. Set up the backend**

```bash
cd backend
python -m venv venv
venv\Scripts\activate          # On Mac/Linux: source venv/bin/activate
pip install -r requirements.txt
```

**3. Configure environment variables**

Edit `backend/.env` and set your MySQL password:

```
SECRET_KEY=my_super_secret_key_123
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_actual_password
DB_NAME=hackathon_team_finder
```

**4. Start the backend server**

```bash
cd backend
python app.py
```

The API runs at `http://localhost:5000`.

**5. Start the frontend**

Open a new terminal:

```bash
cd frontend
python -m http.server 5500
```

Open `http://localhost:5500` in your browser.

## Folder Structure

```
HACKATHON-TEAM-FINDER-0.2/
├── backend/
│   ├── app.py                  # Flask app entry point
│   ├── config.py               # Reads .env config values
│   ├── db.py                   # PyMySQL connection helper
│   ├── requirements.txt        # Python dependencies
│   ├── .env                    # Secrets (not committed)
│   ├── .env.example            # Template for .env
│   ├── routes/
│   │   ├── __init__.py
│   │   ├── auth_routes.py      # Register, login, /auth/me
│   │   ├── profile_routes.py   # Profile, skills, users
│   │   ├── hackathon_routes.py # Hackathon listing
│   │   ├── team_routes.py      # Team CRUD, members
│   │   └── request_routes.py   # Join requests
│   └── utils/
│       ├── auth_utils.py       # JWT token and @token_required
│       └── validators.py       # Email and password validation
├── frontend/
│   ├── index.html              # Landing page
│   ├── login.html              # Login form
│   ├── register.html           # Registration form
│   ├── dashboard.html          # My teams and requests
│   ├── profile.html            # Edit profile and skills
│   ├── hackathons.html         # Browse hackathons
│   ├── teams.html              # Find and filter teams
│   ├── users.html              # Find teammates
│   ├── create_team.html        # Create a new team
│   ├── team_details.html       # Team info, members, requests
│   ├── css/
│   │   └── style.css           # Custom styles
│   └── js/
│       ├── api.js              # fetch() wrapper with JWT
│       ├── auth.js             # Login, register, logout
│       ├── profile.js          # Profile page logic
│       ├── teams.js            # Teams, hackathons, users logic
│       └── requests.js         # Dashboard and request handling
├── database/
│   └── schema.sql              # Tables and seed data
├── docs/
│   └── Hackathon Team Finder.md  # Full project documentation
├── .gitignore
└── README.md
```

## Features

- User registration and login with JWT authentication
- Profile management with skills selection
- Browse hackathons and filter teams by hackathon or skill
- Create teams with required skills
- Send join requests with optional messages
- Team leaders can accept or reject requests
- Dashboard showing teams, sent requests, and received requests
- Responsive design using Bootstrap 5

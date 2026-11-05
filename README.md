# SkillSwap – Peer-to-Peer Student Skill Exchange Platform

> **Your Skills. Someone's Opportunity.**
> Learn a new skill by sharing the skill you already know.

SkillSwap is a full-stack web application where college students teach what they know and learn what they want, with no money involved. For example, a student who knows Python and wants to learn UI/UX Design is matched with a student who knows UI/UX Design and wants to learn Python. They connect, chat and schedule learning sessions.

Developed as a B.Tech Software Engineering mini project at Guru Nanak University, Hyderabad (UIEMT).

---

## Features

- **Authentication** – registration, login, logout, forgot-password page, hashed passwords, protected routes
- **Student profiles** – avatar, college, department, year, bio, availability, interests
- **Skill management** – skills to teach and to learn, 12 categories, proficiency level, description
- **Smart matching** – rule-based compatibility score, ranked recommendations, filters by skill, department, year and proficiency
- **Discover students** – profile cards with search, filters and a Connect button
- **Connection requests** – send, accept, reject, cancel, pending and accepted lists
- **Chat** – one-to-one messaging, history, timestamps, unread indicators (polling)
- **Learning sessions** – schedule, reschedule, cancel, mark completed
- **Reviews and ratings** – one review per completed session
- **Gamification** – points, badges, achievements, leaderboard
- **Notifications** – requests, acceptances, messages, sessions, reviews
- **Admin dashboard** – platform statistics, user management, reported users

## Tech Stack

| Layer | Technology |
|-------|------------|
| Frontend | React.js, React Router, HTML5, CSS3, JavaScript |
| Backend | Python, Flask, REST APIs |
| Database | SQLite with Flask-SQLAlchemy |
| Other | Flask-CORS, Werkzeug (password hashing) |

## Matching Algorithm

For students A and B:

```
f = |A.teach ∩ B.learn| / max(1, |B.learn|)
r = |B.teach ∩ A.learn| / max(1, |A.learn|)
score = 40*f + 40*r
if f > 0 and r > 0: score += 10          # mutual exchange bonus
score += 10 * (avg level of matching skills / 3)   # Beginner=1 … Advanced=3
score = min(100, round(score))
```

The scoring function is isolated so it can later be replaced by an AI-based model.

## Database Tables

`users`, `skills`, `teaching_skills`, `learning_skills`, `connection_requests`, `matches`, `messages`, `learning_sessions`, `reviews`, `notifications`, `achievements`, `user_achievements`

## Project Structure

```
SkillSwap/
├── backend/            # Flask REST API
│   ├── app.py
│   ├── models.py
│   ├── routes/
│   ├── requirements.txt
│   └── seed.py         # sample data
├── frontend/           # React application
│   ├── src/
│   └── package.json
├── docs/               # SRS, SDD, SCM, UML, test cases (project report)
├── README.md
└── .gitignore
```

## Getting Started

### Prerequisites

- Python 3.10+
- Node.js 18+ and npm
- Git

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/SkillSwap.git
cd SkillSwap
```

### 2. Run the backend

```bash
cd backend
python -m venv venv
# Windows:  venv\Scripts\activate
# Linux/macOS:  source venv/bin/activate
pip install -r requirements.txt
python seed.py        # optional: load sample data
python app.py
```

The API runs at `http://localhost:5000`.

### 3. Run the frontend

Open a new terminal:

```bash
cd frontend
npm install
npm start
```

The app opens at `http://localhost:3000`.

## Security

- Passwords stored as salted hashes (Werkzeug)
- Authenticated routes and role-based admin access
- Input validation on all forms and API endpoints
- ORM queries prevent SQL injection

## Documentation

The full project report (SRS, SDD, SCM, UML diagrams and test cases) is in the `docs/` folder.

## Future Scope

- AI-powered matching and recommendations
- Real-time chat using WebSockets
- In-app video sessions
- Mobile application
- Email/OTP verification
- PostgreSQL for large-scale deployment

## Author

**Sayyada Farhath Anjum**
Roll No: 24EM115063 · B.Tech 3rd Year, AIML-01 · Group 43
University Institute of Emerging Technologies (UIEMT), Guru Nanak University, Hyderabad
Course: Software Engineering (24EMAMPC505U) · Guide: Mr. Anuj Garg, Assistant Professor


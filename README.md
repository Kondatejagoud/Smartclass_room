# 🎓 Smart Virtual Classroom

A real-time virtual classroom platform with AI-powered focus monitoring, live video streaming, and classroom management tools for teachers and students.

## ✨ Features

- **Authentication** — Register/login as Teacher or Student with JWT-based auth
- **Classroom Management** — Teachers create classrooms with a shareable 6-digit code
- **Live Video Streaming** — WebRTC-based peer-to-peer video between teacher and students
- **Focus Monitoring** — Detects tab switching and irregular movement, updates focus scores in real-time
- **Behavior System** — Strike system with auto-timeout and auto-removal after repeated violations
- **Real-time Alerts** — WebSocket-powered instant notifications to the teacher dashboard

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React 19, Vite, React Router, Bootstrap 5 |
| Backend | FastAPI, Python |
| Real-time | WebSockets, WebRTC |
| Auth | JWT (python-jose) |
| Storage | JSON file (db.json) |

## 📁 Project Structure

```
Smartrclass_room/
├── backend/
│   ├── main.py           # FastAPI app — REST + WebSocket endpoints
│   ├── requirements.txt  # Python dependencies
│   ├── db.json           # Persistent JSON storage
│   └── .env              # Environment variables (not committed)
├── frontend-react/
│   ├── src/              # React components and pages
│   ├── public/
│   └── package.json
└── QUICK_START.md
```

## 🚀 Getting Started

### Prerequisites
- Python 3.8+
- Node.js 18+

### 1. Backend Setup

```bash
cd backend
pip install -r requirements.txt
```

Create a `.env` file in the `backend/` folder:

```env
SECRET_KEY=your_secret_key_here
ACCESS_TOKEN_EXPIRE_HOURS=24
```

Start the backend:

```bash
python main.py
```

Backend runs at: `http://localhost:8001`

### 2. Frontend Setup

```bash
cd frontend-react
npm install
npm run dev
```

Frontend runs at: `http://localhost:5173`

## 🧪 How to Use

### Teacher
1. Register with role **Teacher**
2. Create a classroom — you'll get a 6-digit Class ID
3. Share the Class ID with students
4. Allow camera access and monitor the dashboard

### Student
1. Register with role **Student**
2. Enter the Class ID from your teacher
3. Allow camera access
4. Stay focused — tab switches and movement are tracked!

## ⚙️ Behavior & Strike System

| Strikes | Auto Action |
|---------|------------|
| 2 | 2-minute timeout |
| 4 | 5-minute timeout |
| 5+ | Auto-removed from class |

Focus score starts at **100%** and drops **5% per warning**.

## 📡 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/register` | Register a new user |
| POST | `/login` | Login and get JWT token |
| POST | `/create-classroom` | Create a classroom (teacher only) |
| POST | `/join-classroom` | Join a classroom (student) |
| WS | `/ws/{class_id}/{user_id}/{role}` | WebSocket connection |

## 🔧 Troubleshooting

- **Camera not working** — Allow camera permissions in browser; use Chrome
- **Connection issues** — Make sure both backend and frontend servers are running
- **Port conflict** — Backend uses port `8001`, change in `main.py` if needed

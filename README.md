# Online Quiz Application for Placement Preparation

A professional, responsive, full-stack web application developed using **React.js, Node.js, Express.js, and MySQL** to help college students prepare for campus placement examinations by practising topic-wise questions, attending timed mock tests, evaluating performance, and identifying weak areas.

---

## 🌟 Key Features

### 👨‍🎓 1. Student Portal
- **Secure Registration & Login**: Multi-field registration (Name, Email, Password, College, Branch, Graduation Year) with JWT authentication and bcrypt password hashing.
- **Personalized Student Dashboard**:
  - Welcome banner with student name and batch.
  - 4 Key metric cards: Total Quizzes Attempted, Average Score, Highest Score, Overall Accuracy.
  - Interactive performance bar chart across the 5 placement categories.
  - AI placement insights highlighting strongest and weakest sections.
  - Recent quiz attempts table with status and review buttons.
  - Quick Start Quiz & Mock Test shortcuts.
- **5 Placement Categories**:
  1. **Quantitative Aptitude** (Percentage, Profit & Loss, Simple Interest, Compound Interest, Time & Work, Time & Distance, Ratio & Proportion, Average, Number System)
  2. **Logical Reasoning** (Number Series, Coding-Decoding, Blood Relations, Directions, Seating Arrangements, Puzzles, Syllogisms)
  3. **Verbal Ability** (Grammar, Vocabulary, Synonyms & Antonyms, Sentence Correction, Reading Comprehension, Error Detection)
  4. **Technical Knowledge** (C, C++, Java, Python, SQL, DBMS, Operating Systems, Computer Networks)
  5. **Programming Fundamentals** (Basic Programming, Loops, Arrays, Strings, Functions, OOP Concepts)
- **3 Difficulty Levels**: Easy (10 mins), Medium (15 mins), Hard (20 mins).
- **Interactive Examination Interface**:
  - Live countdown timer with auto-submit on timeout.
  - Question navigation palette with color indicators: Answered, Unanswered, Marked for Review, Not Visited.
  - Next, Previous, Clear Answer, and Mark for Review buttons.
  - Negative marking calculation (-0.25 to -0.50 marks per wrong answer).
- **Automatic Scorecard & Detailed Review**:
  - Score summary cards, percentage, and qualification status.
  - Question-by-question review with correct answer badges and step-by-step explanations.
- **Performance Analytics**: Section-wise accuracy, progress over time, and targeted practice suggestions.

---

### 🛡️ 2. Admin Management Panel
- **Separate Admin Access**: Secure administrative portal.
- **System Statistics**: Total students, questions in bank, categories, and exams taken.
- **Question Management**: Add new questions with 4 options, difficulty, correct answer, marks, and explanation. Delete questions.
- **Category & Topic Explorer**: View and organize topics under each category.
- **Student Directory**: View registered candidates, college, branch, quizzes attempted, and average score.

---

## 🏗️ Technology Stack

| Component | Technology |
|---|---|
| **Frontend** | React.js (Vite), React Router DOM v6, Lucide Icons, Custom Responsive CSS |
| **Backend** | Node.js, Express.js REST API, JWT Authentication, bcryptjs, CORS, Dotenv |
| **Database** | MySQL 8.0, MySQL Workbench, `mysql2` connection pool |

---

## 📁 Project Folder Structure

```
online-quiz-application/
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── context/
│   │   │   └── AuthContext.jsx       # Global Auth state, token & user session
│   │   ├── layouts/
│   │   │   └── DashboardLayout.jsx   # Sidebar, Navbar, Dark Mode, Responsive Drawer
│   │   ├── pages/
│   │   │   ├── Login.jsx             # Student & Admin login with demo quick-fill
│   │   │   ├── Register.jsx          # Comprehensive student registration
│   │   │   ├── Dashboard.jsx         # Performance stats, category cards, recent tests
│   │   │   ├── Practice.jsx          # Category & difficulty selector (Easy/Med/Hard)
│   │   │   ├── MockTests.jsx         # Full-length placement company simulators
│   │   │   ├── Quiz.jsx              # Timed exam interface with question palette
│   │   │   ├── Results.jsx           # All past quiz attempts history
│   │   │   ├── ResultDetail.jsx      # Scorecard, review & explanations
│   │   │   ├── Analytics.jsx         # Weakest/strongest section insights
│   │   │   ├── Profile.jsx           # Student profile & college info
│   │   │   └── AdminDashboard.jsx    # Question management & student directory
│   │   ├── services/
│   │   │   └── api.js                # Axios instance with JWT interceptor
│   │   ├── App.jsx                   # React Router with protected routes
│   │   ├── index.css                 # Modern CSS design tokens & glassmorphism
│   │   └── main.jsx                  # React entry point
│   ├── index.html
│   ├── package.json
│   └── vite.config.js
│
├── backend/
│   ├── config/
│   │   └── db.js                     # MySQL2 connection pool & fallback store
│   ├── controllers/
│   │   ├── authController.js         # Register, Login, Profile endpoints
│   │   ├── categoryController.js     # Category CRUD endpoints
│   │   ├── questionController.js     # Question CRUD endpoints
│   │   ├── quizController.js         # Start, Submit, Score calculation
│   │   ├── resultController.js       # Attempt scorecard & review
│   │   └── analyticsController.js    # Performance & section diagnostics
│   ├── middleware/
│   │   └── authMiddleware.js         # JWT verification & role authorization
│   ├── routes/
│   │   ├── authRoutes.js
│   │   ├── categoryRoutes.js
│   │   ├── questionRoutes.js
│   │   ├── quizRoutes.js
│   │   ├── resultRoutes.js
│   │   └── analyticsRoutes.js
│   ├── .env                          # Server & MySQL environment variables
│   ├── package.json
│   └── server.js                     # Express server entry point
│
├── database/
│   └── online_quiz_db.sql            # Full MySQL schema with seed data
└── README.md
```

---

## 🚀 Step-by-Step Setup and Execution Instructions

### Step 1: Clone or Navigate to the Project Directory
```powershell
cd "c:\Users\anitha\OneDrive\Desktop\online quize application"
```

---

### Step 2: Database Setup (MySQL)
1. Open **MySQL Workbench** or command line.
2. Open and execute the script located at:
   `database/online_quiz_db.sql`
   Or run using MySQL CLI:
   ```powershell
   & "C:\Program Files\MySQL\MySQL Server 8.0\bin\mysql.exe" -u root -p < database/online_quiz_db.sql
   ```
3. This creates the database `online_quiz_db` with all 9 normalized tables:
   - `users`
   - `categories`
   - `topics`
   - `questions`
   - `options`
   - `quizzes`
   - `quiz_questions`
   - `quiz_attempts`
   - `student_answers`
   And automatically seeds placement categories, topics, questions, and options.

---

### Step 3: Start the Node.js Backend Server
1. Navigate to the `backend` folder:
   ```powershell
   cd backend
   ```
2. Verify environment settings in `backend/.env` (update MySQL password if needed):
   ```env
   PORT=5000
   DB_HOST=localhost
   DB_USER=root
   DB_PASSWORD=root
   DB_NAME=online_quiz_db
   DB_PORT=3306
   JWT_SECRET=placement_prep_jwt_super_secret_key_2026
   ```
3. Run the backend server:
   ```powershell
   node server.js
   ```
   Output:
   ```
   🚀 Placement Prep Backend Server running on port 5000
   📡 Base URL: http://localhost:5000/api
   ✅ Connected to MySQL database successfully!
   ```

---

### Step 4: Start the React Frontend Application
1. In a new terminal window, navigate to the `frontend` folder:
   ```powershell
   cd frontend
   ```
2. Start the Vite development server:
   ```powershell
   npm run dev
   ```
3. Open your browser and navigate to:
   ```
   http://localhost:3000
   ```

---

## 🔑 Demo Login Credentials

For quick testing, the login page features one-click demo fill buttons:

| Role | Email | Password |
|---|---|---|
| **Student** | `student@placementprep.com` | `student123` |
| **Admin** | `admin@placementprep.com` | `admin123` |

You can also click **Register** to register a new student account with your college and branch details.

---

## 🧪 Testing the Application Workflow

1. **Open the Website**: Browse to `http://localhost:3000/login`.
2. **Register a Student Account**: Enter full name, college name, branch, graduation batch, email, and password.
3. **Log In**: Authenticate using your registered credentials or click "Demo Student".
4. **Student Dashboard**: Review your personalized metrics, performance bar chart, and recent tests.
5. **Select Category & Difficulty**:
   - Click **Quick Start Quiz** or navigate to **Practice Tests**.
   - Select a placement category (e.g. *Quantitative Aptitude*).
   - Select difficulty (*Easy*, *Medium*, or *Hard*).
   - Choose a topic or select *All Topics*.
6. **Attend the Timed Quiz**:
   - Answer MCQs with options A, B, C, D.
   - Use **Mark for Review** or **Clear Answer**.
   - Jump directly between questions using the Question Palette.
   - Watch the live countdown timer.
7. **Submit the Quiz**: Click **Submit Quiz**.
8. **View Scorecard & Review**:
   - View your total score, accuracy percentage, time taken, and qualification status.
   - Inspect question-by-question solutions with detailed explanations.
9. **Check Performance Analytics**: Navigate to **Performance Analysis** to view your strongest and weakest categories and personalized placement preparation advice.
10. **Test Admin Console**: Log in as `admin@placementprep.com` and visit **Admin Dashboard** to add new placement questions and monitor enrolled students.
#   o n l i n e - q u i z e - a p p l i c a t i o n  
 
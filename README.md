# Smart Education System

A full-featured web-based education platform built with HTML, CSS, JavaScript, and PHP. This system provides a complete learning management solution for students and teachers.

## Features

### Student Features
- Browse and search courses
- Enroll in courses
- Track learning progress
- Take quizzes and complete assignments
- Participate in discussions
- View course materials and lessons

### Teacher Features
- Create and manage courses
- Upload course materials and lessons
- Track student progress and enrollment
- Create quizzes and assignments
- Grade submissions
- View analytics and insights

### Admin Features
- Manage users (students and teachers)
- Oversee all courses
- System administration

## Technology Stack

- **Frontend**: HTML5, CSS3, JavaScript (Vanilla)
- **Backend**: PHP 7.4+
- **Database**: MySQL
- **Design**: Responsive, mobile-first CSS

## Project Structure

```
smart_education_system/
├── index.html              # Homepage
├── courses.html            # Course listing page
├── login.html              # User login page
├── register.html           # User registration page
├── student-dashboard.html  # Student dashboard
├── teacher-dashboard.html  # Teacher dashboard
├── database.sql            # MySQL database schema
├── css/
│   └── style.css          # All styles
├── js/
│   └── main.js            # JavaScript functionality
├── api/
│   ├── auth.php           # Authentication API
│   ├── courses.php        # Course management API
│   └── dashboard.php      # Dashboard data API
├── config/
│   └── database.php       # Database configuration
├── uploads/               # User uploaded files
└── assets/                # Images and other assets
```

## Installation

### Prerequisites
- PHP 7.4 or higher
- MySQL 5.7 or higher
- Web server (Apache/Nginx) or PHP's built-in server

### Step 1: Clone or Download
Download the project files to your web server directory.

### Step 2: Database Setup
1. Create a MySQL database named `smart_education`
2. Import the database schema:
   ```bash
   mysql -u root -p smart_education < database.sql
   ```

### Step 3: Configure Database Connection
Edit `config/database.php` and update the database credentials:
```php
define('DB_HOST', 'localhost');
define('DB_USER', 'your_username');
define('DB_PASS', 'your_password');
define('DB_NAME', 'smart_education');
```

### Step 4: Set Up File Permissions
Ensure the web server has write permissions to the `uploads` directory:
```bash
chmod 755 uploads/
chmod 755 uploads/courses/  # Create this folder
chmod 755 uploads/avatars/  # Create this folder
```

### Step 5: Start the Server
**Option A: Using PHP's built-in server (for testing):**
```bash
cd smart_education_system
php -S localhost:8000
```

**Option B: Using Apache/Nginx:**
Configure your web server to point to the project directory.

### Step 6: Access the Application
Open your browser and navigate to:
- Frontend: `http://localhost:8000`
- Or your configured domain

## Demo Accounts

After running the database.sql file, you can log in with these demo accounts:

| Role | Email | Password |
|------|-------|----------|
| Teacher | teacher@education.com | teacher123 |
| Student | student@education.com | student123 |
| Admin | admin@education.com | admin123 |

## API Endpoints

### Authentication
- `POST /api/auth.php?action=register` - Register new user
- `POST /api/auth.php?action=login` - Login user
- `POST /api/auth.php?action=logout` - Logout user
- `GET /api/auth.php?action=me` - Get current user
- `POST /api/auth.php?action=update-profile` - Update profile
- `POST /api/auth.php?action=change-password` - Change password

### Courses
- `GET /api/courses.php` - List all published courses
- `GET /api/courses.php?action=featured` - Get featured courses
- `GET /api/courses.php?action=details&id={id}` - Get course details
- `POST /api/courses.php?action=create` - Create new course (teacher)
- `POST /api/courses.php?action=update&id={id}` - Update course (teacher)
- `DELETE /api/courses.php?id={id}` - Delete course (teacher)
- `POST /api/courses.php?action=enroll&id={id}` - Enroll in course (student)
- `POST /api/courses.php?action=unenroll&id={id}` - Unenroll from course
- `GET /api/courses.php?action=my-courses` - Get teacher's courses
- `GET /api/courses.php?action=enrolled` - Get student's enrolled courses
- `GET /api/courses.php?action=categories` - Get all categories

### Dashboard
- `GET /api/dashboard.php?action=student` - Get student dashboard data
- `GET /api/dashboard.php?action=teacher` - Get teacher dashboard data
- `GET /api/dashboard.php?action=student-progress&course_id={id}` - Get student progress (teacher)
- `POST /api/dashboard.php?action=update-progress` - Update enrollment progress

## Key Features Explained

### User Authentication
The system uses PHP sessions for authentication. Passwords are hashed using bcrypt for security. The `requireLogin()` helper function protects pages that require authentication.

### Course Management
Teachers can create courses with multiple lessons, set pricing, categorize content, and track enrollment. Students can browse, search, and enroll in courses.

### Progress Tracking
The system tracks student progress through enrollments, storing completion percentages and timestamps. Teachers can view detailed progress reports.

### Responsive Design
The CSS uses modern flexbox and grid layouts with mobile-first media queries. The dashboard adapts to different screen sizes with a collapsible sidebar on mobile.

## Security Considerations

1. **Password Hashing**: Uses PHP's `password_hash()` with bcrypt
2. **Input Sanitization**: All user inputs are sanitized using the `sanitize()` function
3. **SQL Injection Prevention**: Uses PDO prepared statements throughout
4. **Access Control**: Role-based access control (RBAC) for students, teachers, and admins
5. **Session Management**: Secure PHP session handling

## Extending the System

### Adding New Features
1. Create new API endpoints in the `api/` directory
2. Add corresponding frontend pages or sections
3. Update the database schema if needed
4. Follow the existing patterns for consistency

### Database Schema
The database includes tables for:
- Users (students, teachers, admins)
- Courses and lessons
- Enrollments
- Quizzes and questions
- Assignments and submissions
- Discussions and replies

## Troubleshooting

1. **Database Connection Error**: Check credentials in `config/database.php`
2. **Upload Permissions**: Ensure `uploads/` directory is writable
3. **Session Issues**: Check PHP session configuration in `php.ini`
4. **API Errors**: Check browser console and PHP error logs

## License

This project is for educational purposes. Feel free to use and modify as needed.

## Support

For questions or issues, please refer to the code comments or create an issue in the project repository.

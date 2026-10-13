[mohamed amin hassan] - Assignment: Practical Development Setup

Name: [mohamed amin hassan]
Date: October 13, 2026
Course/Class Title: Practical Software Development Environments

------------------------------------------------------------------
SECTION 1: TASK 1 - FLUTTER & DART SETUP
------------------------------------------------------------------

1. flutter doctor Output Summary
Command: flutter doctor
Output:
[✓] Flutter (Channel stable, 3.19.0, on macOS 14.2.1 23C71 darwin-arm64, locale en-US)
[✓] Android Toolchain - develop for Android devices (Android SDK version 34.0.0)
[✓] Xcode - develop for iOS and macOS (Xcode 15.2)
[✓] Chrome - develop for the web
[✓] VS Code (version 1.86.0)
[✓] Connected device (2 available)
• No issues found!

2. Project Initialization and Target Devices Commands
Commands:
flutter create my_first_app
cd my_first_app
flutter devices

Output for flutter devices:
2 connected devices:
  macOS (desktop) • macos • darwin-arm64 • macOS
  Chrome (web)    • chrome • web-javascript • Google Chrome

3. Conceptual Question: Hot Reload vs. Hot Restart
- Hot Reload: Injects updated source code files into the running Dart Virtual Machine (VM). It preserves the app's current state (e.g., user input, navigation stack, form contents), making UI tweaks and bug fixing extremely fast.
  * When to use: Use Hot Reload when making UI adjustments, changing widget properties, or updating layout styles.
- Hot Restart: Resets the app completely, wiping out the current state and restarting the app from main(). It takes slightly longer than a hot reload because it reloads code and resets app state.
  * When to use: Use Hot Restart when modifying global variables, static initializers, application state architecture, or modifying app initialization logic.

------------------------------------------------------------------
SECTION 2: TASK 2 - MYSQL DATABASE MANAGEMENT
------------------------------------------------------------------

1 & 2. Complete SQL Script & Query Results
SQL Commands:
CREATE DATABASE school;
USE school;
CREATE TABLE students (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(150) UNIQUE NOT NULL,
    enrolled_on DATE NOT NULL
);
INSERT INTO students (name, email, enrolled_on) VALUES 
('Alice Smith', 'alice.smith@example.com', '2026-09-01'),
('Bob Jones', 'bob.jones@example.com', '2026-09-02');
SELECT * FROM students;

SELECT * Output:
+----+-------------+-------------------------+-------------+
| id | name        | email                   | enrolled_on |
+----+-------------+-------------------------+-------------+
|  1 | Alice Smith | alice.smith@example.com | 2026-09-01  |
|  2 | Bob Jones   | bob.jones@example.com   | 2026-09-02  |
+----+-------------+-------------------------+-------------+
2 rows in set (0.00 sec)

3. Security Reflection: Why Root Connection is Poor Practice & Least-Privileged User Creation
- Security Risks of Using root: The root user possesses ultimate administrative privileges over the entire database management system. If an application backend connects using root credentials and suffers a security vulnerability (such as SQL injection or credential leakage), an attacker gains full control over the database server, including the ability to drop tables, access other databases, read sensitive system files, or execute administrative commands.
- Creating a Dedicated, Least-Privileged User:
  CREATE USER 'school_app_user'@'localhost' IDENTIFIED BY 'StrongSecurePassword123!';
  GRANT SELECT, INSERT, UPDATE, DELETE ON school.* TO 'school_app_user'@'localhost';
  FLUSH PRIVILEGES;

------------------------------------------------------------------
SECTION 3: TASK 3 - PYTHON ENVIRONMENT & DEPENDENCY ISOLATION
------------------------------------------------------------------

Terminal Commands Used:
mkdir python_setup_lab
cd python_setup_lab
python3 -m venv venv
source venv/bin/activate    # On Windows: venv\Scripts\activate
pip install requests
pip list
pip freeze > requirements.txt

------------------------------------------------------------------
SECTION 4: TASK 4 - VS CODE WORKSPACE CONFIGURATION
------------------------------------------------------------------

Setup Steps & Verification:
1. Extensions Installed: Flutter, Dart, Python, Pylance, and MySQL.
2. Python Interpreter Selection: Selected interpreter path pointing to python_setup_lab/venv/bin/python.
3. Screenshot Requirement: Insert full-screen VS Code screenshot showing extensions sidebar, integrated terminal with (venv) prompt, and status bar Python interpreter path.

------------------------------------------------------------------
GOOGLE DOCS SUBMISSION REMINDERS
------------------------------------------------------------------
1. Document Name: [Your Full Name] - Assignment: Practical Development Setup
2. Sharing Settings: Change General access from Restricted to "Anyone with the link", set role to "Viewer" or "Commenter", and copy the link for submission.

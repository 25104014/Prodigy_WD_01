PRODIGY_WD_01 - Secure User Authentication System

Description

A Secure User Authentication System developed to demonstrate modern authentication and authorization techniques used in web applications. The project provides separate User and Admin modules with secure registration, login, role-based access control, protected routes, session management, and email verification. Users can access their personal dashboard after successful authentication, while administrators can manage users through a dedicated admin panel.

website link:https://role-guard-auth.preview.emergentagent.com/admin/dashboard

Features

User Features

- User Registration
- User Login
- Secure Logout
- Email Verification
- User Dashboard
- Profile Management
- Protected Routes
- Session Management

Admin Features

- Admin Registration
- Admin Login
- Admin Dashboard
- View All Users
- Search Users
- Activate/Deactivate Users
- Delete Users
- Manage User Access

Security Features

- Password Hashing using bcrypt
- JWT Authentication
- Protected Routes
- Session Management
- Role-Based Authorization
- Input Validation
- Secure User Access

---

How It Works

1. User opens the application.
2. Homepage displays two options:
   - Continue as User
   - Continue as Admin
3. Users and Admins can register and log in separately.
4. Passwords are hashed before storage.
5. After successful login, JWT tokens and sessions are created.
6. Users are redirected to their dashboard.
7. Admins are redirected to the admin dashboard.
8. Protected routes prevent unauthorized access.
9. Admins can manage all registered users.
10. Email verification validates new registrations.

---

Code Explanation

User Registration

const newUser = new User({
  name,
  email,
  password: hashedPassword,
  role
});

Creates a new user account and stores the user information in the database.

Password Hashing

const hashedPassword = await bcrypt.hash(password, 10);

Encrypts the password before storing it to improve security.

User Login

const isMatch = await bcrypt.compare(password, user.password);

Compares the entered password with the encrypted password stored in the database.

JWT Authentication

const token = jwt.sign(
  { id: user._id, role: user.role },
  SECRET_KEY
);

Generates a secure authentication token after successful login.

Protected Routes

if (!token) {
  return res.status(401).json({
    message: "Unauthorized Access"
  });
}

Prevents unauthenticated users from accessing protected pages.

Role-Based Access Control

if(user.role !== "admin"){
  return res.status(403).json({
    message: "Access Denied"
  });
}

Allows only administrators to access admin-specific pages.

Session Management

req.session.userId = user._id;

Maintains active user sessions after successful login.

Email Verification

transporter.sendMail(mailOptions);

Sends verification emails to newly registered users.

Search Users

const users = await User.find({
  name: {
    $regex: search,
    $options: "i"
  }
});

Allows admins to search users efficiently.

Delete User

await User.findByIdAndDelete(userId);

Allows administrators to remove users from the system.

---

Technologies Used

Frontend

- HTML5
- CSS3
- JavaScript
- React.js

Backend

- Node.js
- Express.js

Database

- MongoDB
- Mongoose

Authentication & Security

- bcrypt.js
- JSON Web Token (JWT)
- Express Session

Additional Tools

- Nodemailer
- Git
- GitHub
- VS Code

---

Project Structure

Secure-User-Authentication/
│
├── frontend/
│   ├── Login
│   ├── Register
│   ├── User Dashboard
│   ├── Admin Dashboard
│   └── Profile Pages
│
├── backend/
│   ├── Routes
│   ├── Controllers
│   ├── Middleware
│   ├── Models
│   └── Authentication Logic
│
└── Database

---

How to Run

1. Clone the repository.

git clone repository-link

2. Install dependencies.

npm install

3. Configure environment variables.

4. Start backend server.

npm start

5. Start frontend application.

npm run dev

6. Open the application in your browser.

---

Example Workflow

- Select User or Admin.
- Register an account.
- Verify em

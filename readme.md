# 🔐 Advanced MERN Authentication System

A complete **MERN-stack authentication service** built from scratch with **secure token-based authentication**, **email verification**, and **password reset via email link** — all implemented using **Node.js, Express, MongoDB, JWT, and Nodemailer**.

---

## 🚀 Features

✅ Secure user **signup and login**  
✅ **JWT**-based authentication (stored in HTTP-only cookies)  
✅ **Email verification** with clickable link  
✅ **Forgot and Reset Password** flow (via email link)  
✅ **Password encryption** using bcrypt  
✅ **Protected routes** via middleware token validation  
✅ Clean modular folder structure  
✅ Uses **Gmail SMTP** for sending emails  
✅ Ready for production deployment

---

## 🧠 Tech Stack

**Frontend:** React.js  
**Backend:** Node.js + Express.js  
**Database:** MongoDB (Mongoose ODM)  
**Authentication:** JWT (JSON Web Token)  
**Mail Service:** Nodemailer with Gmail SMTP  
**Security:** bcrypt.js + Cookie-based auth  
**Environment Management:** dotenv  

---

## 🏗️ Folder Structure

```bash
backend/
│
├── controllers/
│   ├── auth.controller.js
│   ├── verifyEmail.controller.js
│   ├── forget.controller.js
│   ├── resetPassword.controller.js
│
├── mailer/
│   ├── sendWelcomeEmail.js
│   ├── sendPasswordResetEmail.js
│   ├── sendResetSuccessEmail.js
│
├── middleware/
│   ├── auth.middleware.js
│
├── models/
│   ├── user.model.js
│
├── routes/
│   ├── auth.routes.js
│
├── utils/
│   ├── generateAndSetToken.js
│
├── .env
├── server.js
└── package.json



```

---

## ⚙️ Environment Variables

Create a `.env` file in your backend root:

```

PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_super_secret_key
EMAIL_USER=[your_gmail@gmail.com](mailto:your_gmail@gmail.com)
EMAIL_PASS=your_app_password
CLIENT_URL=[http://localhost:5173](http://localhost:5173)
NODE_ENV=development

```

---

## 🔑 Core Functionalities Explained

### 1. **User Registration**
- On signup, user details are validated and password is hashed using bcrypt.
- A **JWT token** and **verification email** are generated.
- Verification link example:
```

${process.env.CLIENT_URL}/verify/${verificationToken}

```

### 2. **Email Verification**
- User clicks the link → backend decodes the token → marks user as verified → redirects to dashboard.

### 3. **Login**
- Credentials are verified.
- On success → issues a **JWT token**, stored as HTTP-only cookie.
- Ensures **CSRF-safe authentication**.

### 4. **Forgot Password**
- User enters email → receives reset link.
- Example link:
```

${process.env.CLIENT_URL}/reset-password/${resetToken}

````
- Token expires after **1 hour**.

### 5. **Reset Password**
- User sets a new password (hashed again before saving).
- A **“Password Reset Successful”** email is sent.

### 6. **Logout**
- Clears cookie:
```js
res.clearCookie("token", { httpOnly: true });
````

---

## 🧰 Commands

| Command       | Description             |
| ------------- | ----------------------- |
| `npm install` | Install dependencies    |
| `npm run dev` | Run backend in dev mode |
| `npm start`   | Run production build    |

---

## 📡 API Endpoints

| Method | Endpoint                             | Description      |
| ------ | ------------------------------------ | ---------------- |
| POST   | `/api/v1/auth/sign-up`               | Register user    |
| POST   | `/api/v1/auth/sign-in`               | Login user       |
| GET    | `/api/v1/auth/verify/:token`         | Verify email     |
| POST   | `/api/v1/auth/forgot-password`       | Send reset email |
| PUT    | `/api/v1/auth/reset-password/:token` | Reset password   |
| POST   | `/api/v1/auth/logout`                | Logout user      |

---

## 📬 Email Templates

Each email is HTML-styled and responsive:

* **Welcome Email** – Sent after signup
* **Verification Email** – Contains clickable verification link
* **Reset Password Email** – Contains reset password link
* **Success Email** – Confirmation after password reset

---

## 🧱 Security Practices

* All JWTs stored in **HTTP-only cookies**
* Passwords **hashed with bcrypt (12 rounds)**
* Expiry times for JWTs and reset tokens
* `.env` used for all sensitive credentials
* Verification links expire after **24 hours**

---

## 🎯 Future Improvements

* Role-based access control (Admin/User)
* OAuth2 login (Google, GitHub)
* Account lockout after repeated failed attempts
* 2FA using OTP or authenticator apps

---

## 🤝 Contributing

1. Fork this repo
2. Create your feature branch
3. Commit your changes
4. Submit a pull request

---

## 🧑‍💻 Author

**Rup**
Final-year B.Tech, IIT Patna
Building secure & production-grade MERN stacks 🚀

---

## 🌐 Live Demo


---

## 🪪 License

**MIT License © 2025 Rup**

```

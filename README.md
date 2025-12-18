/shop-site
 ├── index.html
 ├── auth.html
 ├── style.css
 └── auth.js
 <!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>SimpleShop</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

<header>
  <h1>SimpleShop</h1>
  <nav>
    <a href="auth.html">Login</a>
    <a href="auth.html">Sign Up</a>
  </nav>
</header>

<section class="hero">
  <h2>Quality Products. Honest Prices.</h2>
  <p>Affordable items with good quality. No photos yet — just value.</p>
</section>

<section class="features">
  <div>✔ Cheap & fair prices</div>
  <div>✔ Trusted quality</div>
  <div>✔ Simple shopping</div>
</section>

<footer>
  <p>© 2025 SimpleShop</p>
</footer>

</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Account</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

<div class="auth-box">
  <h2>Account</h2>

  <input type="email" id="email" placeholder="Email">
  <input type="password" id="password" placeholder="Password">

  <button onclick="signUp()">Sign Up</button>
  <button onclick="logIn()">Log In</button>
  <button onclick="resetPassword()">Forgot Password</button>

  <p id="message"></p>
</div>

<script type="module" src="auth.js"></script>
</body>
</html>
body {
  font-family: Arial, sans-serif;
  background: #f7f9fc;
  color: #333;
  margin: 0;
}

header {
  background: white;
  padding: 15px 30px;
  display: flex;
  justify-content: space-between;
  box-shadow: 0 2px 5px rgba(0,0,0,0.05);
}

nav a {
  margin-left: 15px;
  text-decoration: none;
  color: #555;
}

.hero {
  padding: 60px;
  text-align: center;
}

.features {
  display: flex;
  justify-content: center;
  gap: 40px;
  padding-bottom: 40px;
}

.auth-box {
  width: 300px;
  margin: 100px auto;
  background: white;
  padding: 25px;
  border-radius: 8px;
  box-shadow: 0 5px 20px rgba(0,0,0,0.1);
}

.auth-box input, button {
  width: 100%;
  margin-top: 10px;
  padding: 10px;
}
import { initializeApp } from "https://www.gstatic.com/firebasejs/10.7.1/firebase-app.js";
import { 
  getAuth, 
  createUserWithEmailAndPassword, 
  signInWithEmailAndPassword,
  sendPasswordResetEmail
} from "https://www.gstatic.com/firebasejs/10.7.1/firebase-auth.js";

// 🔴 PUT YOUR FIREBASE CONFIG HERE
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  projectId: "YOUR_PROJECT",
  appId: "YOUR_APP_ID"
};

const app = initializeApp(firebaseConfig);
const auth = getAuth(app);

window.signUp = () => {
  createUserWithEmailAndPassword(auth, email.value, password.value)
    .then(() => message.innerText = "Account created!")
    .catch(err => message.innerText = err.message);
};

window.logIn = () => {
  signInWithEmailAndPassword(auth, email.value, password.value)
    .then(() => message.innerText = "Logged in!")
    .catch(err => message.innerText = err.message);
};

window.resetPassword = () => {
  sendPasswordResetEmail(auth, email.value)
    .then(() => message.innerText = "Password reset email sent!")
    .catch(err => message.innerText = err.message);
};

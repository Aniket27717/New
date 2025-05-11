<!DOCTYPE html>
<html>
<head>
  <title>Sign Up</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f2f2f2;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }
    .container {
      background: #fff;
      padding: 30px 40px;
      border-radius: 10px;
      box-shadow: 0 0 15px rgba(0,0,0,0.1);
      text-align: center;
      width: 300px;
    }
    h2 { margin-bottom: 20px; }
    input, button {
      width: 100%; padding: 10px; margin: 10px 0;
      border-radius: 5px; border: 1px solid #ccc;
    }
    button {
      background-color: #4CAF50; color: white; border: none;
      font-weight: bold; cursor: pointer;
    }
    button:hover { background-color: #45a049; }
    a { color: #4CAF50; text-decoration: none; }
  </style>
</head>
<body>
  <div class="container">
    <h2>Sign Up</h2>
    <input type="email" id="signupEmail" placeholder="Email" required>
    <input type="password" id="signupPass" placeholder="Password" required>
    <button onclick="signup()">Sign Up</button>
    <p>Already have an account? <a href="index.html">Login</a></p>
  </div>

  <script type="module">
    // Import Firebase modules
    import { initializeApp } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-app.js";
    import { getAuth, createUserWithEmailAndPassword } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-auth.js";

    // Firebase config
    const firebaseConfig = {
      apiKey: "AIzaSyAkef4YRIeJSMpmL4Mm-Y5TOMG_sy0KVc4",
      authDomain: "chat-45809.firebaseapp.com",
      databaseURL: "https://chat-45809-default-rtdb.firebaseio.com",
      projectId: "chat-45809",
      storageBucket: "chat-45809.firebasestorage.app",
      messagingSenderId: "110882798857",
      appId: "1:110882798857:web:98ba57db5c40588231a7d8",
      measurementId: "G-N4TZLZPGCZ"
    };

    // Initialize Firebase
    const app = initializeApp(firebaseConfig);
    const auth = getAuth(app);

    // Signup function
    window.signup = function () {
      const email = document.getElementById("signupEmail").value;
      const password = document.getElementById("signupPass").value;

      createUserWithEmailAndPassword(auth, email, password)
        .then(() => {
          alert("Signup successful!");
          window.location.href = "dashboard.html";
        })
        .catch((error) => {
          alert("Error: " + error.message);
        });
    };
  </script>
</body>
</html>

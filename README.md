<!DOCTYPE html>
<html>
<head><title>Signup</title></head>
<body>
  <h2>Signup</h2>
  <input id="signupEmail" placeholder="Email" />
  <input id="signupPassword" placeholder="Password" type="password" />
  <button onclick="signup()">Signup</button>
  <p>Already have an account? <a href="index.html">Login</a></p>

  <script src="https://www.gstatic.com/firebasejs/8.10.1/firebase-app.js"></script>
  <script src="https://www.gstatic.com/firebasejs/8.10.1/firebase-auth.js"></script>
  <script src="https://www.gstatic.com/firebasejs/8.10.1/firebase-database.js"></script>
  <script src="script.js"></script>
  <script>
    function signup() {
      const email = document.getElementById("signupEmail").value;
      const password = document.getElementById("signupPassword").value;

      firebase.auth().createUserWithEmailAndPassword(email, password)
        .then(userCredential => {
          const uid = userCredential.user.uid;
          return firebase.database().ref("users/" + uid).set({
            email: email,
            balance: 1000
          });
        })
        .then(() => {
          alert("Signup successful!");
          window.location.href = "dashboard.html";
        })
        .catch(error => alert(error.message));
    }
  </script>
</body>
</html>

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Register and Login</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f2f2f2;
        }
        .container {
            max-width: 400px;
            margin: 50px auto;
            background: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            display: none;
        }
        .container.active {
            display: block;
        }
        h2 {
            text-align: center;
            margin-bottom: 20px;
        }
        label {
            font-weight: bold;
            margin-bottom: 5px;
            display: block;
        }
        input {
            width: 100%;
            padding: 10px;
            margin-bottom: 15px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        button {
            width: 100%;
            padding: 10px;
            background-color: #007BFF;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
        .link {
            text-align: center;
            margin-top: 10px;
        }
        .link a {
            color: #007BFF;
            text-decoration: none;
        }
        .link a:hover {
            text-decoration: underline;
        }
        .message {
            text-align: center;
            font-weight: bold;
            margin-top: 10px;
        }
        .success {
            color: green;
        }
        .error {
            color: red;
        }
        .sent-code-box {
            background-color: #e0f7fa;
            padding: 10px;
            border-radius: 5px;
            border: 1px solid #00acc1;
            text-align: center;
            font-weight: bold;
            margin-top: 20px;
        }
        .code-reset-container {
            display: none;
            margin-top: 20px;
            text-align: center;
        }
        .code-reset-container input {
            width: 80%;
            margin-bottom: 10px;
        }
        .code-reset-container button {
            width: 80%;
        }
        .random-code {
            font-size: 20px;
            font-weight: bold;
            margin-top: 10px;
        }
    </style>
</head>
<body>
    <div class="container active" id="register-container">
        <h2>Register</h2>
        <form id="register-form">
            <label for="email">Email</label>
            <input type="email" id="email" name="email" placeholder="Enter your email" required>

            <label for="password">Password</label>
            <input type="password" id="password" name="password" placeholder="Enter your password" required>

            <button type="submit">Register</button>
        </form>
        <div class="link">
            Already a member? <a href="#" onclick="showLogin()">Login here</a>
        </div>
    </div>

    <div class="container" id="login-container">
        <h2>Login</h2>
        <form id="login-form">
            <label for="login-email">Email</label>
            <input type="email" id="login-email" name="login-email" placeholder="Enter your email" required>

            <label for="login-password">Password</label>
            <input type="password" id="login-password" name="login-password" placeholder="Enter your password" required>

            <button type="submit">Login</button>
        </form>
        <div class="link">
            Forgot Password? <a href="#" onclick="showForgotPassword()">Click here</a>
        </div>
        <div class="link">
            New user? <a href="#" onclick="showRegister()">Register now</a>
        </div>
    </div>

    <div class="container" id="forgot-password-container">
        <h2>Forgot Password</h2>
        <form id="forgot-password-form">
            <label for="forgot-email">Email</label>
            <input type="email" id="forgot-email" name="forgot-email" placeholder="Enter your email" required>

            <button type="submit">Send Code</button>
        </form>
    </div>

    <div id="sent-code-box" class="sent-code-box" style="display: none;">
        <p>SENT CODE to: <span id="sent-email"></span></p>
        <p class="random-code" id="random-code"></p>
        <button onclick="showCodeInput()">OK</button>
    </div>

    <div id="code-reset-container" class="code-reset-container">
        <h3>Enter the Code</h3>
        <input type="text" id="reset-code" placeholder="Enter the code" maxlength="4" required>
        <input type="password" id="new-password" placeholder="Enter new password" required>
        <button onclick="resetPassword()">Reset Password</button>
    </div>

    <div class="message" id="message"></div>

    <script>
        function showLogin() {
            document.getElementById('register-container').classList.remove('active');
            document.getElementById('login-container').classList.add('active');
            document.getElementById('forgot-password-container').classList.remove('active');
            document.getElementById('message').innerText = '';
        }

        function showRegister() {
            document.getElementById('login-container').classList.remove('active');
            document.getElementById('register-container').classList.add('active');
            document.getElementById('forgot-password-container').classList.remove('active');
            document.getElementById('message').innerText = '';
        }

        function showForgotPassword() {
            document.getElementById('login-container').classList.remove('active');
            document.getElementById('register-container').classList.remove('active');
            document.getElementById('forgot-password-container').classList.add('active');
            document.getElementById('message').innerText = '';
        }

        document.getElementById('register-form').addEventListener('submit', function(e) {
            e.preventDefault();
            const email = document.getElementById('email').value;
            const password = document.getElementById('password').value;

            if (!email.endsWith('@gmail.com')) {
                document.getElementById('message').innerHTML = '<span class="error">Only Gmail accounts are allowed.</span>';
                return;
            }

            if (password.length < 4 || password.length > 12) {
                document.getElementById('message').innerHTML = '<span class="error">Password must be between 4 and 12 characters.</span>';
                return;
            }

            if (localStorage.getItem(email)) {
                document.getElementById('message').innerHTML = '<span class="error">This email is already registered.</span>';
            } else {
                localStorage.setItem(email, password);
                document.getElementById('message').innerHTML = '<span class="success">Registration successful! You can now log in.</span>';
                showLogin();
            }
        });

        document.getElementById('login-form').addEventListener('submit', function(e) {
            e.preventDefault();
            const email = document.getElementById('login-email').value;
            const password = document.getElementById('login-password').value;

            const storedPassword = localStorage.getItem(email);
            if (storedPassword && storedPassword === password) {
                document.getElementById('message').innerHTML = '<span class="success">✅ Login Successful!</span>';
            } else {
                document.getElementById('message').innerHTML = '<span class="error">Invalid email or password.</span>';
            }
        });

        document.getElementById('forgot-password-form').addEventListener('submit', function(e) {
            e.preventDefault();
            const email = document.getElementById('forgot-email').value;

            if (!localStorage.getItem(email)) {
                document.getElementById('message').innerHTML = '<span class="error">Email not registered. Redirecting to Register...</span>';
                setTimeout(showRegister, 2000);
            } else {
                const code = Math.floor(1000 + Math.random() * 9000); 
                localStorage.setItem(email + '-code', code);
                document.getElementById('sent-email').innerText = email;
                document.getElementById('random-code').innerText = code;
                document.getElementById('forgot-password-container').style.display = 'none';
                document.getElementById('sent-code-box').style.display = 'block';
            }
        });

        function showCodeInput() {
            document.getElementById('sent-code-box').style.display = 'none';
            document.getElementById('code-reset-container').style.display = 'block';
        }

        function resetPassword() {
            const email = document.getElementById('forgot-email').value;
            const enteredCode = document.getElementById('reset-code').value;
            const newPassword = document.getElementById('new-password').value;
            const storedCode = localStorage.getItem(email + '-code');

            if (enteredCode === storedCode) {
                if (newPassword.length >= 4 && newPassword.length <= 12) {
                    localStorage.setItem(email, newPassword);
                    document.getElementById('message').innerHTML = '<span class="success">Password changed successfully!</span>';
                    document.getElementById('code-reset-container').style.display = 'none';
                } else {
                    document.getElementById('message').innerHTML = '<span class="error">Password must be between 4 and 12 characters long.</span>';
                }
            } else {
                document.getElementById('message').innerHTML = '<span class="error">Invalid code.</span>';
            }
        }
    </script>
</body>
</html>

# Expense-Tracker-students-
Student Expense Tracker Web Application 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Student Expense Tracker</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: white;
            border-radius: 15px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.2);
            overflow: hidden;
        }

        /* Header */
        header {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 20px 30px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        header h1 {
            font-size: 24px;
        }

        .user-info {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .logout-btn {
            background: rgba(255,255,255,0.2);
            color: white;
            border: none;
            padding: 8px 20px;
            border-radius: 20px;
            cursor: pointer;
            font-size: 14px;
            transition: background 0.3s;
        }

        .logout-btn:hover {
            background: rgba(255,255,255,0.3);
        }

        /* Navigation */
        nav {
            background: #f8f9fa;
            padding: 15px 30px;
            border-bottom: 2px solid #e9ecef;
        }

        nav button {
            background: none;
            border: none;
            padding: 10px 20px;
            margin-right: 10px;
            cursor: pointer;
            font-size: 15px;
            color: #495057;
            border-radius: 5px;
            transition: all 0.3s;
        }

        nav button:hover {
            background: #e9ecef;
        }

        nav button.active {
            background: #667eea;
            color: white;
        }

        /* Content Area */
        .content {
            padding: 30px;
        }

        .page {
            display: none;
        }

        .page.active {
            display: block;
        }

        /* Login/Register Page */
        .auth-container {
            max-width: 400px;
            margin: 100px auto;
            background: white;
            padding: 40px;
            border-radius: 15px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.2);
        }

        .auth-container h2 {
            color: #667eea;
            margin-bottom: 30px;
            text-align: center;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            color: #495057;
            font-weight: 500;
        }

        .form-group input, .form-group select, .form-group textarea {
            width: 100%;
            padding: 12px;
            border: 2px solid #e9ecef;
            border-radius: 8px;
            font-size: 14px;
            transition: border-color 0.3s;
        }

        .form-group input:focus, .form-group select:focus, .form-group textarea:focus {
            outline: none;
            border-color: #667eea;
        }

        .btn {
            width: 100%;
            padding: 12px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            cursor: pointer;
            transition: transform 0.2s;
        }

        .btn:hover {
            transform: translateY(-2px);
        }

        .auth-toggle {
            text-align: center;
            margin-top: 20px;
            color: #6c757d;
        }

        .auth-toggle a {
            color: #667eea;
            text-decoration: none;
            font-weight: 600;
            cursor: pointer;
        }

        /* Dashboard Cards */
        .dashboard-cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .card {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 25px;
            border-radius: 12px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .card h3 {
            font-size: 16px;
            margin-bottom: 10px;
            opacity: 0.9;
        }

        .card .amount {
            font-size: 32px;
            font-weight: bold;
        }

        /* Chart Container */
        .chart-container {
            background: #f8f9fa;
            padding: 25px;
            border-radius: 12px;
            margin-bottom: 30px;
        }

        .chart-container h3 {
            color: #495057;
            margin-bottom: 20px;
        }

        .chart-bar {
            margin-bottom: 15px;
        }

        .chart-label {
            display: flex;
            justify-content: space-between;
            margin-bottom: 5px;
            color: #495057;
            font-size: 14px;
        }

        .bar {
            height: 30px;
            background: linear-gradient(90deg, #667eea 0%, #764ba2 100%);
            border-radius: 5px;
            transition: width 0.5s ease;
        }

        /* Expense List Table */
        .expense-table {
            width: 100%;
            border-collapse: collapse;
            background: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
        }

        .expense-table thead {
            background: #667eea;
            color: white;
        }

        .expense-table th, .expense-table td {
            padding: 15px;
            text-align: left;
        }

        .expense-table tbody tr:hover {
            background: #f8f9fa;
        }

        .expense-table tbody tr {
            border-bottom: 1px solid #e9ecef;
        }

        .delete-btn {
            background: #dc3545;
            color: white;
            border: none;
            padding: 6px 15px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 13px;
        }

        .delete-btn:hover {
            background: #c82333;
        }

        .category-badge {
            padding: 5px 12px;
            border-radius: 15px;
            font-size: 12px;
            font-weight: 600;
        }

        .category-food { background: #ffeaa7; color: #2d3436; }
        .category-travel { background: #74b9ff; color: #2d3436; }
        .category-shopping { background: #fab1a0; color: #2d3436; }
        .category-others { background: #dfe6e9; color: #2d3436; }

        .empty-state {
            text-align: center;
            padding: 60px 20px;
            color: #6c757d;
        }

        .empty-state svg {
            width: 120px;
            height: 120px;
            margin-bottom: 20px;
            opacity: 0.3;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .dashboard-cards {
                grid-template-columns: 1fr;
            }
            
            .expense-table {
                font-size: 14px;
            }
            
            .expense-table th, .expense-table td {
                padding: 10px;
            }
        }

        .error-message {
            color: #dc3545;
            font-size: 14px;
            margin-top: 5px;
        }
    </style>
</head>
<body>
    <!-- Auth Container (Login/Register) -->
    <div id="authContainer" class="auth-container">
        <h2 id="authTitle">Student Expense Tracker</h2>
        <form id="authForm">
            <div class="form-group">
                <label for="username">Username</label>
                <input type="text" id="username" required minlength="3">
                <span class="error-message" id="usernameError"></span>
            </div>
            <div class="form-group">
                <label for="password">Password</label>
                <input type="password" id="password" required minlength="6">
                <span class="error-message" id="passwordError"></span>
            </div>
            <button type="submit" class="btn" id="authBtn">Login</button>
        </form>
        <div class="auth-toggle">
            <span id="toggleText">Don't have an account?</span>
            <a id="toggleLink">Register</a>
        </div>
    </div>

    <!-- Main App Container -->
    <div id="appContainer" class="container" style="display: none;">
        <header>
            <h1>💰 Student Expense Tracker</h1>
            <div class="user-info">
                <span id="welcomeUser">Welcome, User!</span>
                <button class="logout-btn" onclick="logout()">Logout</button>
            </div>
        </header>

        <nav>
            <button class="active" onclick="showPage('dashboard')">Dashboard</button>
            <button onclick="showPage('addExpense')">Add Expense</button>
            <button onclick="showPage('expenseList')">Expense List</button>
            <button onclick="showPage('summary')">Summary</button>
        </nav>

        <div class="content">
            <!-- Dashboard Page -->
            <div id="dashboard" class="page active">
                <div class="dashboard-cards">
                    <div class="card">
                        <h3>Total Expenses</h3>
                        <div class="amount" id="totalExpenses">₹0</div>
                    </div>
                    <div class="card">
                        <h3>This Month</h3>
                        <div class="amount" id="monthExpenses">₹0</div>
                    </div>
                    <div class="card">
                        <h3>Total Transactions</h3>
                        <div class="amount" id="totalTransactions">0</div>
                    </div>
                </div>

                <div class="chart-container">
                    <h3>Recent Expenses (Last 5)</h3>
                    <div id="recentExpenses"></div>
                </div>
            </div>

            <!-- Add Expense Page -->
            <div id="addExpense" class="page">
                <h2 style="margin-bottom: 25px; color: #495057;">Add New Expense</h2>
                <form id="expenseForm" style="max-width: 600px;">
                    <div class="form-group">
                        <label for="expenseDate">Date</label>
                        <input type="date" id="expenseDate" required>
                    </div>
                    <div class="form-group">
                        <label for="expenseAmount">Amount (₹)</label>
                        <input type="number" id="expenseAmount" required min="0" step="0.01">
                    </div>
                    <div class="form-group">
                        <label for="expenseCategory">Category</label>
                        <select id="expenseCategory" required>
                            <option value="">Select Category</option>
                            <option value="Food">Food</option>
                            <option value="Travel">Travel</option>
                            <option value="Shopping">Shopping</option>
                            <option value="Others">Others</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="expenseDescription">Description</label>
                        <textarea id="expenseDescription" rows="3" required></textarea>
                    </div>
                    <button type="submit" class="btn">Add Expense</button>
                </form>
            </div>

            <!-- Expense List Page -->
            <div id="expenseList" class="page">
                <h2 style="margin-bottom: 25px; color: #495057;">All Expenses</h2>
                <div id="expenseTableContainer"></div>
            </div>

            <!-- Summary Page -->
            <div id="summary" class="page">
                <h2 style="margin-bottom: 25px; color: #495057;">Category-wise Summary</h2>
                <div class="chart-container">
                    <h3>Spending by Category</h3>
                    <div id="categoryChart"></div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // State Management - stores current user and authentication mode
        let isLoginMode = true;
        let currentUser = null;

        // Initialize app on page load
        document.addEventListener('DOMContentLoaded', function() {
            checkAuth();
            setupAuthForm();
            setupExpenseForm();
            setTodayDate();
        });

        // Check if user is already logged in
        function checkAuth() {
            const loggedInUser = localStorage.getItem('currentUser');
            if (loggedInUser) {
                currentUser = loggedInUser;
                showApp();
            }
        }

        // Setup authentication form (login/register toggle)
        function setupAuthForm() {
            const toggleLink = document.getElementById('toggleLink');
            const authForm = document.getElementById('authForm');
            
            toggleLink.addEventListener('click', function() {
                isLoginMode = !isLoginMode;
                updateAuthUI();
            });

            authForm.addEventListener('submit', handleAuth);
        }

        // Update UI based on login/register mode
        function updateAuthUI() {
            const authTitle = document.getElementById('authTitle');
            const authBtn = document.getElementById('authBtn');
            const toggleText = document.getElementById('toggleText');
            const toggleLink = document.getElementById('toggleLink');

            if (isLoginMode) {
                authTitle.textContent = 'Student Expense Tracker';
                authBtn.textContent = 'Login';
                toggleText.textContent = "Don't have an account?";
                toggleLink.textContent = 'Register';
            } else {
                authTitle.textContent = 'Create Account';
                authBtn.textContent = 'Register';
                toggleText.textContent = 'Already have an account?';
                toggleLink.textContent = 'Login';
            }
        }

        // Handle login/register form submission
        function handleAuth(e) {
            e.preventDefault();
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;

            // Clear previous errors
            document.getElementById('usernameError').textContent = '';
            document.getElementById('passwordError').textContent = '';

            // Validation
            if (username.length < 3) {
                document.getElementById('usernameError').textContent = 'Username must be at least 3 characters';
                return;
            }

            if (password.length < 6) {
                document.getElementById('passwordError').textContent = 'Password must be at least 6 characters';
                return;
            }

            if (isLoginMode) {
                // Login logic - check if user exists
                const users = JSON.parse(localStorage.getItem('users') || '{}');
                if (users[username] && users[username] === password) {
                    currentUser = username;
                    localStorage.setItem('currentUser', username);
                    showApp();
                } else {
                    document.getElementById('passwordError').textContent = 'Invalid username or password';
                }
            } else {
                // Register logic - create new user
                const users = JSON.parse(localStorage.getItem('users') || '{}');
                if (users[username]) {
                    document.getElementById('usernameError').textContent = 'Username already exists';
                } else {
                    users[username] = password;
                    localStorage.setItem('users', JSON.stringify(users));
                    alert('Account created successfully! Please login.');
                    isLoginMode = true;
                    updateAuthUI();
                    document.getElementById('authForm').reset();
                }
            }
        }

        // Show main application after successful login
        function showApp() {
            document.getElementById('authContainer').style.display = 'none';
            document.getElementById('appContainer').style.display = 'block';
            document.getElementById('welcomeUser').textContent = `Welcome, ${currentUser}!`;
            loadDashboard();
        }

        // Logout function
        function logout() {
            localStorage.removeItem('currentUser');
            currentUser = null;
            document.getElementById('authContainer').style.display = 'block';
            document.getElementById('appContainer').style.display = 'none';
            document.getElementById('authForm').reset();
        }

        // Navigation between pages
        function showPage(pageName) {
            // Hide all pages
            const pages = document.querySelectorAll('.page');
            pages.forEach(page => page.classList.remove('active'));

            // Remove active class from all nav buttons
            const navButtons = document.querySelectorAll('nav button');
            navButtons.forEach(btn => btn.classList.remove('active'));

            // Show selected page
            document.getElementById(pageName).classList.add('active');
            event.target.classList.add('active');

            // Load content based on page
            if (pageName === 'dashboard') {
                loadDashboard();
            } else if (pageName === 'expenseList') {
                loadExpenseList();
            } else if (pageName === 'summary') {
                loadSummary();
            }
        }

        // Setup expense form submission
        function setupExpenseForm() {
            const expenseForm = document.getElementById('expenseForm');
            expenseForm.addEventListener('submit', function(e) {
                e.preventDefault();
                addExpense();
            });
        }

        // Set today's date as default in date input
        function setTodayDate() {
            const today = new Date().toISOString().split('T')[0];
            document.getElementById('expenseDate').value = today;
        }

        // Add new expense to storage
        function addExpense() {
            const date = document.getElementById('expenseDate').value;
            const amount = parseFloat(document.getElementById('expenseAmount').value);
            const category = document.getElementById('expenseCategory').value;
            const description = document.getElementById('expenseDescription').value;

            // Create expense object
            const expense = {
                id: Date.now(),
                date: date,
                amount: amount,
                category: category,
                description: description,
                user: currentUser
            };

            // Get existing expenses or initialize empty array
            const expenses = JSON.parse(localStorage.getItem('expenses') || '[]');
            expenses.push(expense);
            localStorage.setItem('expenses', JSON.stringify(expenses));

            // Reset form and show success message
            document.getElementById('expenseForm').rese

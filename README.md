<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ألعاب أونلاين - 200 لعبة مجانية</title>
    <meta name="description" content="أكبر موقع ألعاب عربي - أكثر من 200 لعبة مجانية في مختلف التصنيفات">
    <meta property="og:title" content="ألعاب أونلاين - 200 لعبة مجانية">
    <meta property="og:description" content="استمتع بأفضل الألعاب الإلكترونية المجانية">
    <meta http-equiv="Content-Security-Policy" 
          content="default-src 'self';
                   script-src 'self' 'unsafe-eval' cdnjs.cloudflare.com;
                   style-src 'self' 'unsafe-inline' cdnjs.cloudflare.com;
                   img-src 'self' data:;
                   font-src 'self' cdnjs.cloudflare.com;
                   frame-src 'none';
                   object-src 'none';
                   report-uri /csp-report">
    <meta name="csrf-token" id="csrfToken" content="">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link rel="manifest" href="/manifest.json">
    <style>
        /* التنسيق العام */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: #f5f5f5;
            color: #333;
            line-height: 1.6;
            transition: background-color 0.3s, color 0.3s;
        }

        @media (prefers-color-scheme: dark) {
            body {
                background-color: #121212;
                color: #f5f5f5;
            }
            
            .game-card, .auth-form, .category-card {
                background-color: #1e1e1e;
                color: #f5f5f5;
                border: 1px solid #333;
            }
            
            .search-box input {
                background-color: #333;
                color: #fff;
            }
        }

        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 15px;
        }

        /* الهيدر */
        header {
            background-color: #2c3e50;
            color: white;
            padding: 1rem 0;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        header h1 {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 1rem;
        }

        nav ul {
            display: flex;
            list-style: none;
            gap: 20px;
        }

        nav a {
            color: white;
            text-decoration: none;
            display: flex;
            align-items: center;
            gap: 5px;
            padding: 5px 10px;
            border-radius: 5px;
            transition: all 0.3s;
        }

        nav a:hover, nav a.active {
            background-color: #3498db;
            transform: translateY(-2px);
        }

        .search-box {
            display: flex;
            margin-top: 1rem;
        }

        .search-box input {
            padding: 8px;
            border: none;
            border-radius: 5px 0 0 5px;
            width: 300px;
            transition: all 0.3s;
        }

        .search-box button {
            background-color: #3498db;
            color: white;
            border: none;
            padding: 0 15px;
            border-radius: 0 5px 5px 0;
            cursor: pointer;
            transition: all 0.3s;
        }

        .search-box button:hover {
            background-color: #2980b9;
        }

        /* قسم الألعاب */
        .games-grid, .categories-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .game-card, .category-card {
            background: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            cursor: pointer;
        }

        .game-card:hover, .category-card:hover {
            transform: translateY(-5px) scale(1.02);
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
        }

        .game-card img {
            width: 100%;
            height: 150px;
            object-fit: cover;
        }

        .game-card h3, .category-card h3 {
            padding: 10px;
            font-size: 1.1rem;
        }

        .rating {
            padding: 0 10px 10px;
            color: #f39c12;
            display: flex;
            align-items: center;
            gap: 3px;
        }

        .category-card {
            text-align: center;
            padding: 20px;
        }

        .category-card i {
            font-size: 2.5rem;
            color: #3498db;
            margin-bottom: 10px;
            transition: transform 0.3s;
        }

        .category-card:hover i {
            transform: scale(1.1);
        }

        .category-card p {
            color: #7f8c8d;
            font-size: 0.9rem;
        }

        /* حاوية اللعبة */
        #game-container {
            background: white;
            border-radius: 10px;
            padding: 20px;
            margin: 20px 0;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
        }

        @media (prefers-color-scheme: dark) {
            #game-container {
                background-color: #1e1e1e;
                border: 1px solid #333;
            }
        }

        .game-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 1px solid #eee;
        }

        .game-header button {
            background: #e74c3c;
            color: white;
            border: none;
            padding: 8px 15px;
            border-radius: 5px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 5px;
            transition: all 0.3s;
        }

        .game-header button:hover {
            background: #c0392b;
            transform: translateY(-2px);
        }

        /* نظام التسجيل */
        .auth-container {
            display: flex;
            justify-content: center;
            margin: 2rem 0;
        }

        .auth-form {
            background: white;
            padding: 2rem;
            border-radius: 10px;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
            width: 100%;
            max-width: 400px;
        }

        @media (prefers-color-scheme: dark) {
            .auth-form {
                background-color: #1e1e1e;
                border: 1px solid #333;
            }
        }

        .auth-form h2 {
            margin-bottom: 1.5rem;
            text-align: center;
        }

        .form-group {
            margin-bottom: 1rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
        }

        .form-group input {
            width: 100%;
            padding: 0.75rem;
            border: 1px solid #ddd;
            border-radius: 5px;
            transition: all 0.3s;
        }

        @media (prefers-color-scheme: dark) {
            .form-group input {
                background-color: #333;
                color: #fff;
                border-color: #555;
            }
        }

        .auth-button {
            width: 100%;
            padding: 0.75rem;
            background: #3498db;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1rem;
            margin-top: 1rem;
            transition: all 0.3s;
        }

        .auth-button:hover {
            background: #2980b9;
            transform: translateY(-2px);
        }

        .auth-toggle {
            text-align: center;
            margin-top: 1rem;
        }

        .auth-toggle a {
            color: #3498db;
            cursor: pointer;
            transition: all 0.3s;
        }

        .auth-toggle a:hover {
            text-decoration: underline;
        }

        /* لوحة المستخدم */
        .user-panel {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .user-avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: #3498db;
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            transition: all 0.3s;
            cursor: pointer;
        }

        .user-avatar:hover {
            transform: scale(1.1);
        }

        .user-menu {
            position: relative;
        }

        .user-menu-content {
            display: none;
            position: absolute;
            background: white;
            min-width: 160px;
            box-shadow: 0 8px 16px rgba(0,0,0,0.2);
            z-index: 1;
            border-radius: 5px;
            right: 0;
        }

        @media (prefers-color-scheme: dark) {
            .user-menu-content {
                background-color: #1e1e1e;
                border: 1px solid #333;
            }
        }

        .user-menu:hover .user-menu-content {
            display: block;
        }

        .user-menu-content a {
            color: #333;
            padding: 12px 16px;
            text-decoration: none;
            display: block;
            transition: all 0.3s;
        }

        @media (prefers-color-scheme: dark) {
            .user-menu-content a {
                color: #f5f5f5;
            }
        }

        .user-menu-content a:hover {
            background: #f1f1f1;
        }

        @media (prefers-color-scheme: dark) {
            .user-menu-content a:hover {
                background: #333;
            }
        }

        /* نظام التقييمات */
        .game-reviews {
            margin-top: 30px;
            padding-top: 20px;
            border-top: 1px solid #eee;
        }

        .add-review {
            margin-bottom: 20px;
        }

        .add-review textarea {
            width: 100%;
            padding: 10px;
            border-radius: 5px;
            border: 1px solid #ddd;
            margin-bottom: 10px;
            resize: vertical;
            min-height: 100px;
        }

        @media (prefers-color-scheme: dark) {
            .add-review textarea {
                background-color: #333;
                color: #fff;
                border-color: #555;
            }
        }

        .rating-stars {
            display: flex;
            gap: 5px;
            margin-bottom: 10px;
        }

        .rating-stars i {
            cursor: pointer;
            font-size: 1.5rem;
            color: #ddd;
            transition: all 0.3s;
        }

        .rating-stars i.active {
            color: #f39c12;
        }

        .reviews-list {
            margin-top: 20px;
        }

        .review-item {
            background: #f9f9f9;
            padding: 15px;
            border-radius: 5px;
            margin-bottom: 15px;
        }

        @media (prefers-color-scheme: dark) {
            .review-item {
                background-color: #252525;
            }
        }

        .review-header {
            display: flex;
            justify-content: space-between;
            margin-bottom: 10px;
        }

        .review-author {
            font-weight: bold;
        }

        .review-rating {
            color: #f39c12;
        }

        /* الإشعارات */
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            background: #2ecc71;
            color: white;
            padding: 15px 20px;
            border-radius: 5px;
            box-shadow: 0 3px 10px rgba(0,0,0,0.2);
            z-index: 1000;
            display: flex;
            align-items: center;
            gap: 10px;
            transform: translateX(150%);
            transition: transform 0.3s ease;
        }

        .notification.show {
            transform: translateX(0);
        }

        .notification.error {
            background: #e74c3c;
        }

        .notification.warning {
            background: #f39c12;
        }

        /* الفوتر */
        footer {
            background-color: #2c3e50;
            color: white;
            text-align: center;
            padding: 20px 0;
            margin-top: 40px;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-top: 10px;
        }

        .social-links a {
            color: white;
            font-size: 1.2rem;
            transition: all 0.3s;
        }

        .social-links a:hover {
            transform: translateY(-3px);
        }

        /* التكيف مع الشاشات الصغيرة */
        @media (max-width: 768px) {
            nav ul {
                flex-direction: column;
                gap: 10px;
            }
            
            .search-box input {
                width: 100%;
            }
            
            .games-grid, .categories-grid {
                grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            }

            .user-panel {
                flex-direction: column;
                align-items: flex-end;
            }

            .user-menu-content {
                right: -50px;
            }
        }

        @media (max-width: 576px) {
            .game-card {
                width: 100%;
                margin-bottom: 15px;
            }
            
            .search-box {
                width: 100%;
            }
            
            .auth-form {
                padding: 1rem;
            }
        }

        /* تحميل */
        .loader {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            z-index: 9999;
            justify-content: center;
            align-items: center;
        }

        .loader-content {
            background: white;
            padding: 20px;
            border-radius: 5px;
            text-align: center;
        }

        .spinner {
            border: 5px solid #f3f3f3;
            border-top: 5px solid #3498db;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            animation: spin 1s linear infinite;
            margin: 0 auto 15px;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
    </style>
</head>
<body>
    <div class="loader" id="loader">
        <div class="loader-content">
            <div class="spinner"></div>
            <p>جاري التحميل...</p>
        </div>
    </div>

    <div class="notification" id="notification">
        <i class="fas fa-check-circle"></i>
        <span id="notificationText"></span>
    </div>

    <header>
        <div class="container">
            <h1><i class="fas fa-gamepad"></i> ألعاب أونلاين</h1>
            <nav>
                <ul>
                    <li><a href="#" class="active"><i class="fas fa-home"></i> الرئيسية</a></li>
                    <li><a href="#categories"><i class="fas fa-list"></i> التصنيفات</a></li>
                    <li><a href="#new-games"><i class="fas fa-star"></i> ألعاب جديدة</a></li>
                    <li><a href="#top-games"><i class="fas fa-trophy"></i> الأكثر لعباً</a></li>
                </ul>
            </nav>
            <div class="user-panel" id="userPanel" style="display:none;">
                <div class="user-menu">
                    <div class="user-avatar" id="userAvatar">?</div>
                    <div class="user-menu-content">
                        <a href="#profile"><i class="fas fa-user"></i> الملف الشخصي</a>
                        <a href="#settings"><i class="fas fa-cog"></i> الإعدادات</a>
                        <a href="#" id="logoutBtn"><i class="fas fa-sign-out-alt"></i> تسجيل خروج</a>
                    </div>
                </div>
                <span id="usernameDisplay"></span>
            </div>
            <div class="search-box">
                <input type="text" placeholder="ابحث عن لعبة..." id="searchInput">
                <button id="searchBtn"><i class="fas fa-search"></i></button>
            </div>
        </div>
    </header>

    <main class="container">
        <!-- قسم تسجيل الدخول / التسجيل -->
        <div class="auth-container" id="authContainer">
            <div class="auth-form" id="loginForm">
                <h2><i class="fas fa-sign-in-alt"></i> تسجيل الدخول</h2>
                <input type="hidden" name="_csrf" id="loginCsrf">
                <div class="form-group">
                    <label for="loginEmail">البريد الإلكتروني</label>
                    <input type="email" id="loginEmail" required>
                </div>
                <div class="form-group">
                    <label for="loginPassword">كلمة المرور</label>
                    <input type="password" id="loginPassword" required>
                </div>
                <button class="auth-button" id="loginBtn">تسجيل الدخول</button>
                <div class="auth-toggle">
                    ليس لديك حساب؟ <a id="showRegister">إنشاء حساب</a>
                </div>
            </div>

            <div class="auth-form" id="registerForm" style="display:none;">
                <h2><i class="fas fa-user-plus"></i> إنشاء حساب</h2>
                <input type="hidden" name="_csrf" id="registerCsrf">
                <div class="form-group">
                    <label for="registerName">الاسم الكامل</label>
                    <input type="text" id="registerName" required>
                </div>
                <div class="form-group">
                    <label for="registerEmail">البريد الإلكتروني</label>
                    <input type="email" id="registerEmail" required>
                </div>
                <div class="form-group">
                    <label for="registerPassword">كلمة المرور</label>
                    <input type="password" id="registerPassword" required>
                </div>
                <div class="form-group">
                    <label for="registerConfirmPassword">تأكيد كلمة المرور</label>
                    <input type="password" id="registerConfirmPassword" required>
                </div>
                <button class="auth-button" id="registerBtn">إنشاء حساب</button>
                <div class="auth-toggle">
                    لديك حساب بالفعل؟ <a id="showLogin">تسجيل الدخول</a>
                </div>
            </div>
        </div>

        <!-- قسم الألعاب (يظهر بعد التسجيل) -->
        <div id="gamesContent" style="display:none;">
            <section id="featured-games">
                <h2><i class="fas fa-crown"></i> ألعاب مميزة</h2>
                <div class="games-grid">
                    <!-- لعبة 1: سوبر ماريو -->
                    <div class="game-card" onclick="loadGame('mario')">
                        <img src="https://via.placeholder.com/300x150?text=Super+Mario" alt="سوبر ماريو" loading="lazy">
                        <h3>سوبر ماريو</h3>
                        <div class="rating">4.8 <i class="fas fa-star"></i></div>
                    </div>

                    <!-- لعبة 2: التتريس -->
                    <div class="game-card" onclick="loadGame('tetris')">
                        <img src="https://via.placeholder.com/300x150?text=Tetris" alt="لعبة التتريس" loading="lazy">
                        <h3>التتريس</h3>
                        <div class="rating">4.7 <i class="fas fa-star"></i></div>
                    </div>

                    <!-- لعبة 3: سناك (الأفعى) -->
                    <div class="game-card" onclick="loadGame('snake')">
                        <img src="https://via.placeholder.com/300x150?text=Snake+Game" alt="لعبة الأفعى" loading="lazy">
                        <h3>لعبة الأفعى</h3>
                        <div class="rating">4.5 <i class="fas fa-star"></i></div>
                    </div>

                    <!-- لعبة 4: كاندي كراش -->
                    <div class="game-card" onclick="loadGame('candy')">
                        <img src="https://via.placeholder.com/300x150?text=Candy+Crush" alt="كاندي كراش" loading="lazy">
                        <h3>كاندي كراش</h3>
                        <div class="rating">4.3 <i class="fas fa-star"></i></div>
                    </div>
                </div>
            </section>

            <section id="game-container" style="display:none;">
                <div class="game-header">
                    <button onclick="closeGame()"><i class="fas fa-times"></i> إغلاق اللعبة</button>
                    <h2 id="game-title">اسم اللعبة</h2>
                </div>
                <div id="game-content"></div>
                
                <!-- قسم التقييمات -->
                <div class="game-reviews" id="gameReviews" style="display:none;">
                    <h3><i class="fas fa-comments"></i> التقييمات</h3>
                    <div class="add-review">
                        <textarea id="reviewText" placeholder="اكتب تعليقك..."></textarea>
                        <div class="rating-stars" id="ratingStars">
                            <i class="far fa-star" data-rating="1"></i>
                            <i class="far fa-star" data-rating="2"></i>
                            <i class="far fa-star" data-rating="3"></i>
                            <i class="far fa-star" data-rating="4"></i>
                            <i class="far fa-star" data-rating="5"></i>
                        </div>
                        <button class="auth-button" id="submitReview">إرسال التقييم</button>
                    </div>
                    <div class="reviews-list" id="reviewsList"></div>
                </div>
            </section>

            <section id="categories">
                <h2><i class="fas fa-tags"></i> تصنيفات الألعاب</h2>
                <div class="categories-grid">
                    <div class="category-card" onclick="filterGames('action')">
                        <i class="fas fa-running"></i>
                        <h3>أكشن</h3>
                        <p>120 لعبة</p>
                    </div>
                    <div class="category-card" onclick="filterGames('puzzle')">
                        <i class="fas fa-puzzle-piece"></i>
                        <h3>ألغاز</h3>
                        <p>85 لعبة</p>
                    </div>
                    <div class="category-card" onclick="filterGames('sports')">
                        <i class="fas fa-futbol"></i>
                        <h3>رياضية</h3>
                        <p>45 لعبة</p>
                    </div>
                    <div class="category-card" onclick="filterGames('adventure')">
                        <i class="fas fa-mountain"></i>
                        <h3>مغامرات</h3>
                        <p>60 لعبة</p>
                    </div>
                </div>
            </section>
        </div>
    </main>

    <footer>
        <div class="container">
            <p>&copy; <span id="currentYear"></span> موقع ألعاب أونلاين. جميع الحقوق محفوظة.</p>
            <div class="social-links">
                <a href="#"><i class="fab fa-facebook"></i></a>
                <a href="#"><i class="fab fa-twitter"></i></a>
                <a href="#"><i class="fab fa-instagram"></i></a>
            </div>
        </div>
    </footer>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/dompurify/3.0.5/purify.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/bcryptjs/2.4.3/bcrypt.min.js"></script>
    <script>
        // DOM Elements
        const authContainer = document.getElementById('authContainer');
        const gamesContent = document.getElementById('gamesContent');
        const userPanel = document.getElementById('userPanel');
        const userAvatar = document.getElementById('userAvatar');
        const usernameDisplay = document.getElementById('usernameDisplay');
        const loginForm = document.getElementById('loginForm');
        const registerForm = document.getElementById('registerForm');
        const showRegister = document.getElementById('showRegister');
        const showLogin = document.getElementById('showLogin');
        const loginBtn = document.getElementById('loginBtn');
        const registerBtn = document.getElementById('registerBtn');
        const logoutBtn = document.getElementById('logoutBtn');
        const currentYear = document.getElementById('currentYear');
        const loader = document.getElementById('loader');
        const notification = document.getElementById('notification');
        const notificationText = document.getElementById('notificationText');
        const searchInput = document.getElementById('searchInput');
        const searchBtn = document.getElementById('searchBtn');
        const loginCsrf = document.getElementById('loginCsrf');
        const registerCsrf = document.getElementById('registerCsrf');
        const csrfToken = document.getElementById('csrfToken');
        const gameReviews = document.getElementById('gameReviews');
        const reviewText = document.getElementById('reviewText');
        const ratingStars = document.getElementById('ratingStars');
        const submitReview = document.getElementById('submitReview');
        const reviewsList = document.getElementById('reviewsList');

        // Set current year
        currentYear.textContent = new Date().getFullYear();

        // Generate CSRF token
        function generateCSRFToken() {
            return crypto.randomUUID().replace(/-/g, '');
        }

        // Initialize CSRF token
        const token = generateCSRFToken();
        csrfToken.content = token;
        loginCsrf.value = token;
        registerCsrf.value = token;

        // Show notification
        function showNotification(message, type = 'success') {
            notification.className = `notification ${type}`;
            notificationText.textContent = message;
            notification.classList.add('show');
            
            setTimeout(() => {
                notification.classList.remove('show');
            }, 3000);
        }

        // Show loader
        function showLoader() {
            loader.style.display = 'flex';
        }

        // Hide loader
        function hideLoader() {
            loader.style.display = 'none';
        }

        // Initialize IndexedDB
        let db;
        const DB_NAME = 'GamesDB';
        const DB_VERSION = 2;
        const USER_STORE = 'users';
        const SESSION_STORE = 'sessions';
        const GAME_PROGRESS = 'gameProgress';
        const REVIEWS_STORE = 'reviews';

        // Initialize database
        function initDB() {
            return new Promise((resolve, reject) => {
                const request = indexedDB.open(DB_NAME, DB_VERSION);

                request.onupgradeneeded = (event) => {
                    db = event.target.result;

                    // Create users store
                    if (!db.objectStoreNames.contains(USER_STORE)) {
                        const usersStore = db.createObjectStore(USER_STORE, { keyPath: 'email' });
                        usersStore.createIndex('name', 'name', { unique: false });
                    }

                    // Create sessions store
                    if (!db.objectStoreNames.contains(SESSION_STORE)) {
                        db.createObjectStore(SESSION_STORE, { keyPath: 'id' });
                    }
                    
                    // Create game progress store
                    if (!db.objectStoreNames.contains(GAME_PROGRESS)) {
                        const progressStore = db.createObjectStore(GAME_PROGRESS, { keyPath: 'id', autoIncrement: true });
                        progressStore.createIndex('userId_gameId', ['userId', 'gameId'], { unique: true });
                    }
                    
                    // Create reviews store
                    if (!db.objectStoreNames.contains(REVIEWS_STORE)) {
                        const reviewsStore = db.createObjectStore(REVIEWS_STORE, { keyPath: 'id', autoIncrement: true });
                        reviewsStore.createIndex('gameId', 'gameId', { unique: false });
                        reviewsStore.createIndex('userId', 'userId', { unique: false });
                    }
                };

                request.onsuccess = (event) => {
                    db = event.target.result;
                    resolve(db);
                };

                request.onerror = (event) => {
                    console.error('Error opening DB', event.target.error);
                    reject('Error opening DB');
                };
            });
        }

        // Check active session
        async function checkSession() {
            try {
                showLoader();
                await initDB();
                const session = await getSession();
                
                if (session) {
                    authContainer.style.display = 'none';
                    gamesContent.style.display = 'block';
                    userPanel.style.display = 'flex';
                    usernameDisplay.textContent = session.name;
                    userAvatar.textContent = session.name.charAt(0).toUpperCase();
                }
                hideLoader();
            } catch (error) {
                console.error('Session check error:', error);
                hideLoader();
            }
        }

        // Get current session
        function getSession() {
            return new Promise((resolve, reject) => {
                const transaction = db.transaction(SESSION_STORE, 'readonly');
                const store = transaction.objectStore(SESSION_STORE);
                const request = store.get(1);

                request.onsuccess = () => {
                    resolve(request.result);
                };

                request.onerror = () => {
                    reject('Error getting session');
                };
            });
        }

        // Set session
        function setSession(user) {
            return new Promise((resolve, reject) => {
                const transaction = db.transaction(SESSION_STORE, 'readwrite');
                const store = transaction.objectStore(SESSION_STORE);
                const session = { 
                    id: 1, 
                    email: user.email,
                    name: user.name,
                    lastActive: new Date(),
                    token: generateCSRFToken()
                };
                const request = store.put(session);

                request.onsuccess = () => {
                    resolve(session.token);
                };

                request.onerror = () => {
                    reject('Error setting session');
                };
            });
        }

        // Clear session
        function clearSession() {
            return new Promise((resolve, reject) => {
                const transaction = db.transaction(SESSION_STORE, 'readwrite');
                const store = transaction.objectStore(SESSION_STORE);
                const request = store.delete(1);

                request.onsuccess = () => {
                    resolve();
                };

                request.onerror = () => {
                    reject('Error clearing session');
                };
            });
        }

        // Register user
        async function registerUser(name, email, password) {
            return new Promise((resolve, reject) => {
                const transaction = db.transaction(USER_STORE, 'readwrite');
                const store = transaction.objectStore(USER_STORE);
                
                // Check if user exists
                const checkRequest = store.get(email);

                checkRequest.onsuccess = async () => {
                    if (checkRequest.result) {
                        reject('البريد الإلكتروني مسجل بالفعل');
                        return;
                    }

                    try {
                        const salt = await bcrypt.genSalt(10);
                        const hashedPassword = await bcrypt.hash(password, salt);
                        
                        const user = {
                            email: DOMPurify.sanitize(email),
                            name: DOMPurify.sanitize(name),
                            password: hashedPassword,
                            salt: salt,
                            createdAt: new Date(),
                            lastLogin: null,
                            failedAttempts: 0,
                            achievements: []
                        };

                        const addRequest = store.add(user);

                        addRequest.onsuccess = () => {
                            resolve();
                        };

                        addRequest.onerror = () => {
                            reject('خطأ في تسجيل المستخدم');
                        };
                    } catch (error) {
                        reject('خطأ في معالجة كلمة المرور');
                    }
                };

                checkRequest.onerror = () => {
                    reject('خطأ في التحقق من المستخدم');
                };
            });
        }

        // Login user
        async function loginUser(email, password) {
            return new Promise((resolve, reject) => {
                const transaction = db.transaction(USER_STORE, 'readonly');
                const store = transaction.objectStore(USER_STORE);
                const request = store.get(email);

                request.onsuccess = async () => {
                    const user = request.result;
                    
                    if (!user) {
                        reject('البريد الإلكتروني أو كلمة المرور غير صحيحة');
                        return;
                    }

                    try {
                        const isMatch = await bcrypt.compare(password, user.password);
                        
                        if (!isMatch) {
                            // Update failed attempts
                            if (user.failedAttempts >= 4) {
                                reject('تم تجاوز عدد المحاولات المسموح بها، الرجاء المحاولة لاحقاً');
                            } else {
                                reject('البريد الإلكتروني أو كلمة المرور غير صحيحة');
                            }
                            return;
                        }

                        // Update last login
                        user.lastLogin = new Date();
                        user.failedAttempts = 0;
                        
                        const updateTransaction = db.transaction(USER_STORE, 'readwrite');
                        const updateStore = updateTransaction.objectStore(USER_STORE);
                        updateStore.put(user);

                        // Set session
                        const token = await setSession({
                            email: user.email,
                            name: user.name
                        });
                        
                        resolve({user, token});
                    } catch (error) {
                        reject('خطأ في تسجيل الدخول');
                    }
                };

                request.onerror = () => {
                    reject('خطأ في تسجيل الدخول');
                };
            });
        }

        // Save game progress
        function saveGameProgress(userId, gameId, progress) {
            return new Promise((resolve, reject) => {
                const transaction = db.transaction(GAME_PROGRESS, 'readwrite');
                const store = transaction.objectStore(GAME_PROGRESS);
                
                // Check if progress exists
                const index = store.index('userId_gameId');
                const checkRequest = index.get([userId, gameId]);
                
                checkRequest.onsuccess = () => {
                    const existing = checkRequest.result;
                    const progressData = {
                        userId,
                        gameId,
                        progress,
                        lastPlayed: new Date(),
                        highScore: Math.max(progress.score || 0, existing?.highScore || 0)
                    };
                    
                    if (existing) {
                        progressData.id = existing.id;
                    }
                    
                    const request = store.put(progressData);
                    
                    request.onsuccess = () => {
                        resolve();
                    };
                    
                    request.onerror = () => {
                        reject('Error saving progress');
                    };
                };
                
                checkRequest.onerror = () => {
                    reject('Error checking progress');
                };
            });
        }

        // Add game review
        function addGameReview(userId, gameId, rating, comment) {
            return new Promise((resolve, reject) => {
                const transaction = db.transaction(REVIEWS_STORE, 'readwrite');
                const store = transaction.objectStore(REVIEWS_STORE);
                
                const review = {
                    userId,
                    gameId,
                    userName: usernameDisplay.textContent,
                    rating,
                    comment: DOMPurify.sanitize(comment),
                    date: new Date()
                };
                
                const request = store.add(review);
                
                request.onsuccess = () => {
                    resolve();
                };
                
                request.onerror = () => {
                    reject('Error adding review');
                };
            });
        }

        // Get game reviews
        function getGameReviews(gameId) {
            return new Promise((resolve, reject) => {
                const transaction = db.transaction(REVIEWS_STORE, 'readonly');
                const store = transaction.objectStore(REVIEWS_STORE);
                const index = store.index('gameId');
                const request = index.getAll(gameId);
                
                request.onsuccess = () => {
                    resolve(request.result || []);
                };
                
                request.onerror = () => {
                    reject('Error getting reviews');
                };
            });
        }

        // Event Listeners
        showRegister.addEventListener('click', () => {
            loginForm.style.display = 'none';
            registerForm.style.display = 'block';
            registerCsrf.value = generateCSRFToken();
        });

        showLogin.addEventListener('click', () => {
            registerForm.style.display = 'none';
            loginForm.style.display = 'block';
            loginCsrf.value = generateCSRFToken();
        });

        registerBtn.addEventListener('click', async () => {
            const name = document.getElementById('registerName').value;
            const email = document.getElementById('registerEmail').value;
            const password = document.getElementById('registerPassword').value;
            const confirmPassword = document.getElementById('registerConfirmPassword').value;

            if (!name || !email || !password || !confirmPassword) {
                showNotification('الرجاء ملء جميع الحقول', 'error');
                return;
            }

            if (password !== confirmPassword) {
                showNotification('كلمة المرور غير متطابقة', 'error');
                return;
            }

            if (password.length < 6) {
                showNotification('كلمة المرور يجب أن تكون 6 أحرف على الأقل', 'error');
                return;
            }

            try {
                showLoader();
                await registerUser(name, email, password);
                showNotification('تم إنشاء الحساب بنجاح! الرجاء تسجيل الدخول');
                registerForm.style.display = 'none';
                loginForm.style.display = 'block';
                document.getElementById('registerName').value = '';
                document.getElementById('registerEmail').value = '';
                document.getElementById('registerPassword').value = '';
                document.getElementById('registerConfirmPassword').value = '';
                loginCsrf.value = generateCSRFToken();
                hideLoader();
            } catch (error) {
                showNotification(error, 'error');
                hideLoader();
            }
        });

        loginBtn.addEventListener('click', async () => {
            const email = document.getElementById('loginEmail').value;
            const password = document.getElementById('loginPassword').value;

            if (!email || !password) {
                showNotification('الرجاء إدخال البريد الإلكتروني وكلمة المرور', 'error');
                return;
            }

            try {
                showLoader();
                const { user, token } = await loginUser(email, password);
                csrfToken.content = token;
                authContainer.style.display = 'none';
                gamesContent.style.display = 'block';
                userPanel.style.display = 'flex';
                usernameDisplay.textContent = user.name;
                userAvatar.textContent = user.name.charAt(0).toUpperCase();
                document.getElementById('loginEmail').value = '';
                document.getElementById('loginPassword').value = '';
                showNotification(`مرحباً ${user.name}!`, 'success');
                hideLoader();
                
                // Request notification permission
                if ('Notification' in window && Notification.permission !== 'denied') {
                    Notification.requestPermission();
                }
            } catch (error) {
                showNotification(error, 'error');
                hideLoader();
            }
        });

        logoutBtn.addEventListener('click', async () => {
            try {
                showLoader();
                await clearSession();
                userPanel.style.display = 'none';
                gamesContent.style.display = 'none';
                authContainer.style.display = 'flex';
                loginForm.style.display = 'block';
                registerForm.style.display = 'none';
                document.getElementById('game-container').style.display = 'none';
                showNotification('تم تسجيل الخروج بنجاح');
                hideLoader();
            } catch (error) {
                console.error('Logout error:', error);
                showNotification('حدث خطأ أثناء تسجيل الخروج', 'error');
                hideLoader();
            }
        });

        // Search functionality
        searchBtn.addEventListener('click', searchGames);
        searchInput.addEventListener('keyup', (e) => {
            if (e.key === 'Enter') searchGames();
        });

        // Rating stars
        ratingStars.querySelectorAll('i').forEach(star => {
            star.addEventListener('click', function() {
                const rating = parseInt(this.getAttribute('data-rating'));
                ratingStars.querySelectorAll('i').forEach((s, i) => {
                    if (i < rating) {
                        s.classList.remove('far');
                        s.classList.add('fas', 'active');
                    } else {
                        s.classList.remove('fas', 'active');
                        s.classList.add('far');
                    }
                });
            });
        });

        // Submit review
        submitReview.addEventListener('click', async () => {
            const stars = ratingStars.querySelectorAll('.active');
            if (stars.length === 0) {
                showNotification('الرجاء اختيار تقييم', 'error');
                return;
            }

            const comment = reviewText.value.trim();
            if (!comment) {
                showNotification('الرجاء كتابة تعليق', 'error');
                return;
            }

            try {
                showLoader();
                const session = await getSession();
                const gameTitle = document.getElementById('game-title').textContent;
                await addGameReview(session.email, gameTitle, stars.length, comment);
                
                // Refresh reviews
                await displayGameReviews(gameTitle);
                
                // Reset form
                ratingStars.querySelectorAll('i').forEach(s => {
                    s.classList.remove('fas', 'active');
                    s.classList.add('far');
                });
                reviewText.value = '';
                
                showNotification('شكراً لتقييمك!', 'success');
                hideLoader();
            } catch (error) {
                showNotification('حدث خطأ أثناء إضافة التقييم', 'error');
                hideLoader();
            }
        });

        // Game Functions
        const allowedGames = ['mario', 'tetris', 'snake', 'candy'];
        let gameInterval;
        let currentGame = null;

        function searchGames() {
            const query = searchInput.value.trim().toLowerCase();
            if (query.length < 2) return;
            
            const cards = document.querySelectorAll('.game-card h3');
            let found = false;
            
            cards.forEach(card => {
                const gameName = card.textContent.toLowerCase();
                const gameCard = card.closest('.game-card');
                
                if (gameName.includes(query)) {
                    gameCard.style.display = 'block';
                    found = true;
                    // Add animation
                    gameCard.style.animation = 'highlight 1s';
                    setTimeout(() => {
                        gameCard.style.animation = '';
                    }, 1000);
                } else {
                    gameCard.style.display = 'none';
                }
            });
            
            if (!found) {
                showNotification('لا توجد نتائج مطابقة', 'warning');
            }
        }

        async function loadGame(gameName) {
            if (!allowedGames.includes(gameName)) {
                console.error("محاولة تحميل لعبة غير مصرح بها");
                return;
            }
            
            document.getElementById('featured-games').style.display = 'none';
            document.getElementById('categories').style.display = 'none';
            document.getElementById('game-container').style.display = 'block';
            
            const gameTitle = document.getElementById('game-title');
            const gameContent = document.getElementById('game-content');
            
            gameContent.innerHTML = '';
            gameTitle.textContent = '';
            gameReviews.style.display = 'none';
            currentGame = gameName;
            
            try {
                showLoader();
                
                // Load game progress if logged in
                const session = await getSession();
                if (session) {
                    gameReviews.style.display = 'block';
                    await displayGameReviews(gameName);
                }
                
                switch(gameName) {
                    case 'mario':
                        gameTitle.textContent = 'سوبر ماريو';
                        loadMarioGame(gameContent);
                        break;
                    case 'tetris':
                        gameTitle.textContent = 'التتريس';
                        loadTetrisGame(gameContent);
                        break;
                    case 'snake':
                        gameTitle.textContent = 'لعبة الأفعى';
                        loadSnakeGame(gameContent);
                        break;
                    case 'candy':
                        gameTitle.textContent = 'كاندي كراش';
                        loadCandyGame(gameContent);
                        break;
                    default:
                        gameContent.innerHTML = '<p>اللعبة غير متوفرة حالياً</p>';
                }
                
                hideLoader();
            } catch (error) {
                console.error('Error loading game:', error);
                hideLoader();
            }
        }

        async function displayGameReviews(gameId) {
            try {
                const reviews = await getGameReviews(gameId);
                reviewsList.innerHTML = '';
                
                if (reviews.length === 0) {
                    reviewsList.innerHTML = '<p>لا توجد تقييمات بعد. كن أول من يقيم!</p>';
                    return;
                }
                
                reviews.forEach(review => {
                    const reviewItem = document.createElement('div');
                    reviewItem.className = 'review-item';
                    
                    const stars = '★'.repeat(review.rating) + '☆'.repeat(5 - review.rating);
                    
                    reviewItem.innerHTML = `
                        <div class="review-header">
                            <span class="review-author">${review.userName}</span>
                            <span class="review-rating">${stars}</span>
                        </div>
                        <p>${review.comment}</p>
                        <small>${new Date(review.date).toLocaleDateString('ar-EG')}</small>
                    `;
                    
                    reviewsList.appendChild(reviewItem);
                });
            } catch (error) {
                console.error('Error displaying reviews:', error);
            }
        }

        function closeGame() {
            stopGame();
            document.getElementById('featured-games').style.display = 'block';
            document.getElementById('categories').style.display = 'block';
            document.getElementById('game-container').style.display = 'none';
            currentGame = null;
            
            // Save game progress if logged in
            saveProgressIfNeeded();
        }

        async function saveProgressIfNeeded() {
            try {
                const session = await getSession();
                if (!session || !currentGame) return;
                
                // In a real app, you would save actual game progress
                await saveGameProgress(session.email, currentGame, {
                    score: Math.floor(Math.random() * 1000),
                    level: Math.floor(Math.random() * 10) + 1,
                    lastPlayed: new Date()
                });
                
                console.log('Game progress saved');
            } catch (error) {
                console.error('Error saving progress:', error);
            }
        }

        function stopGame() {
            if (gameInterval) {
                clearInterval(gameInterval);
                gameInterval = null;
            }
        }

        function filterGames(category) {
            showNotification(`سيتم عرض الألعاب في تصنيف ${category}`, 'info');
        }

        // لعبة سوبر ماريو البسيطة
        function loadMarioGame(container) {
            container.innerHTML = `
                <div style="text-align: center;">
                    <h3>سوبر ماريو (نسخة مبسطة)</h3>
                    <canvas id="marioCanvas" width="400" height="300" style="border:1px solid #000; background: #87CEEB;"></canvas>
                    <p>استخدم مفاتيح الأسهم للتحرك والقفز</p>
                </div>
            `;
            
            showNotification('لعبة سوبر ماريو قيد التطوير', 'info');
        }

        // لعبة التتريس
        function loadTetrisGame(container) {
            container.innerHTML = `
                <div style="text-align: center;">
                    <h3>لعبة التتريس</h3>
                    <canvas id="tetrisCanvas" width="300" height="600" style="border:1px solid #000; background: #000;"></canvas>
                    <p>استخدم مفاتيح الأسهم للتحكم</p>
                </div>
            `;
            
            showNotification('لعبة التتريس قيد التطوير', 'info');
        }

        // لعبة الأفعى (سناك)
        function loadSnakeGame(container) {
            container.innerHTML = `
                <div style="text-align: center;">
                    <h3>لعبة الأفعى</h3>
                    <canvas id="snakeCanvas" width="400" height="400" style="border:1px solid #000; background: #f0f0f0;"></canvas>
                    <p>استخدم مفاتيح الأسهم للتحكم</p>
                    <p id="snakeScore">النقاط: 0</p>
                </div>
            `;
            
            const canvas = document.getElementById('snakeCanvas');
            const ctx = canvas.getContext('2d');
            const scoreElement = document.getElementById('snakeScore');
            
            const box = 20;
            let snake = [{x: 9 * box, y: 10 * box}];
            let food = {
                x: Math.floor(Math.random() * 20) * box,
                y: Math.floor(Math.random() * 20) * box
            };
            let d;
            let score = 0;
            
            document.addEventListener('keydown', direction);
            
            function direction(event) {
                if(event.keyCode == 37 && d != "RIGHT") d = "LEFT";
                else if(event.keyCode == 38 && d != "DOWN") d = "UP";
                else if(event.keyCode == 39 && d != "LEFT") d = "RIGHT";
                else if(event.keyCode == 40 && d != "UP") d = "DOWN";
            }
            
            function drawGame() {
                ctx.fillStyle = "#f0f0f0";
                ctx.fillRect(0, 0, canvas.width, canvas.height);
                
                for(let i = 0; i < snake.length; i++) {
                    ctx.fillStyle = i == 0 ? "green" : "white";
                    ctx.fillRect(snake[i].x, snake[i].y, box, box);
                    
                    ctx.strokeStyle = "black";
                    ctx.strokeRect(snake[i].x, snake[i].y, box, box);
                }
                
                ctx.fillStyle = "red";
                ctx.fillRect(food.x, food.y, box, box);
                
                let snakeX = snake[0].x;
                let snakeY = snake[0].y;
                
                if(d == "LEFT") snakeX -= box;
                if(d == "UP") snakeY -= box;
                if(d == "RIGHT") snakeX += box;
                if(d == "DOWN") snakeY += box;
                
                if(snakeX == food.x && snakeY == food.y) {
                    food = {
                        x: Math.floor(Math.random() * 20) * box,
                        y: Math.floor(Math.random() * 20) * box
                    };
                    score++;
                    scoreElement.textContent = `النقاط: ${score}`;
                } else {
                    snake.pop();
                }
                
                let newHead = {x: snakeX, y: snakeY};
                
                if(snakeX < 0 || snakeY < 0 || snakeX >= canvas.width || snakeY >= canvas.height 
                   || collision(newHead, snake)) {
                    clearInterval(gameInterval);
                    showNotification(`Game Over! النقاط النهائية: ${score}`, 'error');
                    
                    // Save score if logged in
                    saveProgressIfNeeded();
                }
                
                snake.unshift(newHead);
            }
            
            function collision(head, array) {
                for(let i = 0; i < array.length; i++) {
                    if(head.x == array[i].x && head.y == array[i].y) {
                        return true;
                    }
                }
                return false;
            }
            
            gameInterval = setInterval(drawGame, 100);
        }

        // لعبة كاندي كراش
        function loadCandyGame(container) {
            container.innerHTML = `
                <div style="text-align: center;">
                    <h3>كاندي كراش</h3>
                    <div id="candyGrid" style="display: grid; grid-template-columns: repeat(8, 50px); gap: 2px; margin: 20px auto; width: 416px;"></div>
                    <p>انقر على مجموعات من الحلوى المتشابهة</p>
                    <p id="candyScore">النقاط: 0</p>
                </div>
            `;
            
            const candyGrid = document.getElementById('candyGrid');
            const scoreElement = document.getElementById('candyScore');
            const colors = ['red', 'blue', 'green', 'yellow', 'purple'];
            let score = 0;
            
            for(let i = 0; i < 64; i++) {
                const candy = document.createElement('div');
                candy.className = 'candy';
                candy.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                candy.style.height = '50px';
                candy.style.borderRadius = '10px';
                candy.style.cursor = 'pointer';
                candy.addEventListener('click', function() {
                    if (this.style.opacity === '0.5') {
                        this.style.opacity = '1';
                        score--;
                    } else {
                        this.style.opacity = '0.5';
                        score++;
                    }
                    scoreElement.textContent = `النقاط: ${score}`;
                });
                candyGrid.appendChild(candy);
            }
        }

        // Initialize the app
        document.addEventListener('DOMContentLoaded', async () => {
            // Check for service worker support
            if ('serviceWorker' in navigator) {
                try {
                    await navigator.serviceWorker.register('/sw.js');
                    console.log('Service Worker registered');
                } catch (error) {
                    console.log('Service Worker registration failed:', error);
                }
            }
            
            await checkSession();
            
            // Secure all event handlers
            const cards = document.querySelectorAll('.game-card');
            cards.forEach(card => {
                const originalHandler = card.onclick;
                card.onclick = function(e) {
                    e.stopImmediatePropagation();
                    if (originalHandler) originalHandler.call(this, e);
                };
            });
            
            // Request notification permission
            if ('Notification' in window && Notification.permission !== 'denied') {
                Notification.requestPermission();
            }
        });

        // Handle beforeunload to save progress
        window.addEventListener('beforeunload', (e) => {
            if (currentGame) {
                saveProgressIfNeeded();
            }
        });
    </script>
</body>
</html>

```html
<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: Arial, sans-serif;
        }

        body {
            background-color: #f4f7f6;
            color: #333;
        }

        header {
            background-color: #1a365d;
            color: white;
            padding: 15px 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        header h1 {
            font-size: 24px;
            color: #63b3ed;
        }

        .container {
            max-width: 750px;
            margin: 30px auto;
            background: white;
            padding: 25px;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        h2 {
            color: #2c5282;
            margin-bottom: 15px;
            border-bottom: 2px solid #3182ce;
            padding-bottom: 5px;
        }

        #dashboard {
            display: none;
        }

        .form-row {
            display: flex;
            gap: 15px;
        }

        .form-row .form-group {
            flex: 1;
        }

        .form-group {
            margin-bottom: 15px;
        }

        .form-group label {
            display: block;
            font-weight: bold;
            margin-bottom: 5px;
            font-size: 13px;
            color: #4a5568;
        }

        .form-group input,
        .form-group select,
        .form-group textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid #cbd5e0;
            border-radius: 4px;
            font-size: 14px;
        }

        .btn {
            background-color: #3182ce;
            color: white;
            padding: 12px;
            border: none;
            border-radius: 4px;
            font-weight: bold;
            cursor: pointer;
            width: 100%;
            font-size: 16px;
            margin-top: 10px;
        }

        .btn:hover {
            background-color: #2b6cb0;
        }

        .btn-logout {
            background-color: #e53e3e;
            padding: 6px 12px;
            font-size: 13px;
            width: auto;
        }

        .alert {
            display: none;
            padding: 10px;
            background-color: #fed7d7;
            color: #9b2c2c;
            border-radius: 4px;
            margin-bottom: 15px;
            text-align: center;
            font-weight: bold;
        }

        .alert-success {
            background-color: #c6f6d5;
            color: #22543d;
        }

        /* Published Forms */
        .posts-section {
            margin-top: 35px;
            border-top: 2px solid #e2e8f0;
            padding-top: 20px;
        }

        .post-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            gap: 15px;
            background: #f7fafc;
            border: 1px solid #e2e8f0;
            border-radius: 6px;
            padding: 12px;
            margin-bottom: 10px;
        }

        .post-info {
            flex: 1;
        }

        .post-title {
            font-weight: bold;
            color: #2d3748;
            font-size: 14px;
            margin-bottom: 5px;
        }

        .post-category {
            color: #718096;
            font-size: 12px;
        }

        .remove-btn {
            background-color: #e53e3e;
            color: white;
            border: none;
            border-radius: 4px;
            padding: 8px 12px;
            cursor: pointer;
            font-weight: bold;
            white-space: nowrap;
        }

        .remove-btn:hover {
            background-color: #c53030;
        }

        .empty-message {
            text-align: center;
            color: #718096;
            padding: 15px;
        }

        @media (max-width: 600px) {
            .form-row {
                flex-direction: column;
                gap: 0;
            }

            .post-item {
                flex-direction: column;
                align-items: stretch;
            }

            .remove-btn {
                width: 100%;
            }
        }
    </style>
</head>

<body>

<header>
    <h1>Dforms803 - Admin Panel</h1>
    <button id="logoutBtn"
            class="btn btn-logout"
            style="display: none;"
            onclick="logout()">
        Logout
    </button>
</header>

<!-- LOGIN SECTION -->
<div id="loginBox" class="container">
    <h2>Admin Login</h2>

    <div id="loginError" class="alert">
        गलत पासवर्ड
    </div>

    <form id="loginForm">
        <div class="form-group">
            <label>Admin Password:</label>
            <input type="password"
                   id="adminPass"
                   placeholder="Enter Password"
                   required>
        </div>

        <button type="submit" class="btn">
            Login
        </button>
    </form>
</div>

<!-- DASHBOARD -->
<div id="dashboard" class="container">

    <div id="successMsg" class="alert alert-success">
        Post Successfully Published!
    </div>

    <div id="removeMsg" class="alert alert-success">
        Post Successfully Removed!
    </div>
<h1><a href="index.html">Home</a>

    <h2>Publish New Detailed Form</h2>

    <form id="postForm">

        <div class="form-row">

            <div class="form-group">
                <label>Category (श्रेणी)</label>

                <select id="category">
                    <option value="latest">Latest Forms</option>
                    <option value="admit">Admit Cards</option>
                    <option value="result">Results</option>
                </select>
            </div>

            <div class="form-group">
                <label>Form Title (नाम)</label>

                <input type="text"
                       id="title"
                       placeholder="e.g. Railway RRB Constable Recruitment 2026"
                       required>
            </div>

        </div>

        <!-- DATES -->
        <div class="form-row">

            <div class="form-group">
                <label>Start Date</label>

                <input type="text"
                       id="startDate"
                       placeholder="e.g. 10/08/2026">
            </div>

            <div class="form-group">
                <label>Last Date</label>

                <input type="text"
                       id="lastDate"
                       placeholder="e.g. 31/08/2026">
            </div>

            <div class="form-group">
                <label>Exam Date</label>

                <input type="text"
                       id="examDate"
                       placeholder="e.g. Sept 2026">
            </div>

        </div>

        <!-- FEES -->
        <div class="form-row">

            <div class="form-group">
                <label>Fee (Gen/OBC)</label>

                <input type="text"
                       id="feeGen"
                       placeholder="e.g. ₹500">
            </div>

            <div class="form-group">
                <label>Fee (SC/ST/Female)</label>

                <input type="text"
                       id="feeSc"
                       placeholder="e.g. ₹250 / ₹0">
            </div>

            <div class="form-group">
                <label>Payment Mode</label>

                <input type="text"
                       id="payMode"
                       placeholder="Online (UPI/Debit Card)">
            </div>

        </div>

        <!-- AGE -->
        <div class="form-row">

            <div class="form-group">
                <label>Age Limit</label>

                <input type="text"
                       id="ageLimit"
                       placeholder="e.g. 18 - 25 Years">
            </div>

        </div>

        <div class="form-group">
            <label>Qualification Required</label>

            <textarea id="qualification"
                      rows="2"
                      placeholder="e.g. 10th Pass / 12th Pass from recognized board"></textarea>
        </div>

        <!-- LINKS -->
        <div class="form-group">
            <label>Apply Online Link</label>

            <input type="url"
                   id="applyLink"
                   placeholder="https://..."
                   required>
        </div>

        <div class="form-row">

            <div class="form-group">
                <label>Notification PDF Link (Optional)</label>

                <input type="url"
                       id="notifLink"
                       placeholder="https://...">
            </div>

            <div class="form-group">
                <label>Official Website Link (Optional)</label>

                <input type="url"
                       id="officialLink"
                       placeholder="https://...">
            </div>

        </div>

        <button type="submit" class="btn">
            Publish Full Post
        </button>

    </form>


    <!-- PUBLISHED POSTS -->
    <div class="posts-section">

        <h2>Published Forms</h2>

        <div id="postsList"></div>

    </div>


    <br>

    <p style="text-align: center;">
        <a href="index.html"
           style="color: #3182ce; font-weight: bold; text-decoration: none;">
            ← Go to Homepage
        </a>
    </p>

</div>


<script>

    const ADMIN_PASSWORD = "admin803";


    /* LOGIN */
    window.onload = function() {

        if (sessionStorage.getItem('isLoggedIn') === 'true') {
            showDashboard();
        }

    };


    document.getElementById('loginForm').addEventListener('submit', function(e) {

        e.preventDefault();

        if (document.getElementById('adminPass').value === ADMIN_PASSWORD) {

            sessionStorage.setItem('isLoggedIn', 'true');

            showDashboard();

        } else {

            document.getElementById('loginError').style.display = 'block';

        }

    });


    /* SHOW DASHBOARD */
    function showDashboard() {

        document.getElementById('loginBox').style.display = 'none';

        document.getElementById('dashboard').style.display = 'block';

        document.getElementById('logoutBtn').style.display = 'block';

        loadPosts();

    }


    /* LOGOUT */
    function logout() {

        sessionStorage.removeItem('isLoggedIn');

        location.reload();

    }


    /* SAVE FULL FORM DATA */
    document.getElementById('postForm').addEventListener('submit', function(e) {

        e.preventDefault();

        const newPost = {

            id: Date.now(),

            category: document.getElementById('category').value,

            title: document.getElementById('title').value,

            startDate: document.getElementById('startDate').value,

            lastDate: document.getElementById('lastDate').value,

            examDate: document.getElementById('examDate').value,

            feeGen: document.getElementById('feeGen').value,

            feeSc: document.getElementById('feeSc').value,

            payMode: document.getElementById('payMode').value,

            ageLimit: document.getElementById('ageLimit').value,

            qualification: document.getElementById('qualification').value,

            applyLink: document.getElementById('applyLink').value,

            notifLink: document.getElementById('notifLink').value,

            officialLink: document.getElementById('officialLink').value

        };


        let posts =
            JSON.parse(localStorage.getItem('dforms_posts')) || [];


        posts.push(newPost);


        localStorage.setItem(
            'dforms_posts',
            JSON.stringify(posts)
        );


        document.getElementById('successMsg').style.display = 'block';

        document.getElementById('postForm').reset();


        loadPosts();


        setTimeout(function() {

            document.getElementById('successMsg').style.display = 'none';

        }, 3000);

    });


    /* LOAD PUBLISHED POSTS */
    function loadPosts() {

        const postsList =
            document.getElementById('postsList');

        postsList.innerHTML = '';


        let posts =
            JSON.parse(localStorage.getItem('dforms_posts')) || [];


        if (posts.length === 0) {

            postsList.innerHTML =
                '<div class="empty-message">Abhi koi published form nahi hai.</div>';

            return;

        }


        /* Latest post first */
        posts.slice().reverse().forEach(function(post) {

            const item =
                document.createElement('div');

            item.className = 'post-item';


            const info =
                document.createElement('div');

            info.className = 'post-info';


            const title =
                document.createElement('div');

            title.className = 'post-title';

            title.textContent = post.title;


            const category =
                document.createElement('div');

            category.className = 'post-category';

            category.textContent =
                'Category: ' + getCategoryName(post.category);


            info.appendChild(title);

            info.appendChild(category);


            const removeButton =
                document.createElement('button');

            removeButton.className = 'remove-btn';

            removeButton.textContent = '🗑️ Remove';


            removeButton.onclick = function() {

                removePost(post.id);

            };


            item.appendChild(info);

            item.appendChild(removeButton);


            postsList.appendChild(item);

        });

    }


    /* CATEGORY NAME */
    function getCategoryName(category) {

        if (category === 'latest') {
            return 'Latest Forms';
        }

        if (category === 'admit') {
            return 'Admit Cards';
        }

        if (category === 'result') {
            return 'Results';
        }

        return category;

    }


    /* REMOVE POST */
    function removePost(postId) {

        const confirmDelete =
            confirm(
                'Kya aap is form ko permanently remove karna chahte hain?'
            );


        if (!confirmDelete) {
            return;
        }


        let posts =
            JSON.parse(localStorage.getItem('dforms_posts')) || [];


        posts =
            posts.filter(function(post) {

                return post.id !== postId;

            });


        localStorage.setItem(
            'dforms_posts',
            JSON.stringify(posts)
        );


        loadPosts();


        document.getElementById('removeMsg').style.display = 'block';


        setTimeout(function() {

            document.getElementById('removeMsg').style.display = 'none';

        }, 3000);

    }

</script>

</body>
</html>
```

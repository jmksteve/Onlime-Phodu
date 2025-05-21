<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Earning MULTIPLE TASKS</title>
    <style>
        :root {
            --primary-color: #FF6B6B; /* Adjusted to a reddish-orange */
            --primary-dark: #E05252;
            --secondary-color: #FFD166;
            --background-color: #FFF8F0; /* Light creamy background */
            --card-background: #FFFFFF;
            --text-color: #333333;
            --text-light: #777777;
            --border-radius: 15px;
            --box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
            --vip-color: gold; /* Color for VIP elements */
            --orange-color: #FFA500;
            --dark-orange-color: #FF8C00;

            /* WhatsApp-like chat colors */
            --my-message-bg: #DCF8C6;
            --my-message-text: #303030;
            --other-message-bg: #FFFFFF;
            --other-message-text: #303030;
            --chat-background: #E5DDD5; /* Optional: WhatsApp-like chat background */
        }

        /* Ensure html and body allow full screen behavior */
        html, body {
            margin: 0;
            padding: 0;
            height: 100%; /* Important for child elements using percentage height */
            /* overflow: hidden; /* Optional: to prevent scrollbars on body if app strictly manages scrolling */
        }

        body {
            font-family: 'Arial', sans-serif;
            /* margin: 0; */ /* Moved to html, body rule */
            background-color: var(--background-color);
            color: var(--text-color);
            /* display: flex; */ /* No longer needed to center a fixed-width app */
            /* justify-content: center; */
            /* align-items: flex-start; */
            /* min-height: 100vh; */ /* Replaced by height: 100% */
            /* padding-top: 20px; */ /* REMOVED */
            /* padding-bottom: 20px; */ /* REMOVED */
        }

        .app-container {
            width: 100vw; /* MODIFIED: Full viewport width */
            height: 100vh; /* MODIFIED: Full viewport height */
            /* max-width: 375px; */ /* REMOVED */
            /* min-height: 750px; */ /* REMOVED */
            background-color: var(--card-background);
            /* border-radius: var(--border-radius); */ /* REMOVED for full-screen look */
            /* box-shadow: var(--box-shadow); */ /* REMOVED for full-screen look */
            overflow: hidden; /* Screens inside will scroll */
            display: flex;
            flex-direction: column;
            position: relative;
        }

        .screen {
            display: none;
            flex-direction: column;
            height: 100%; /* Screens will take full height of app-container */
            overflow-y: auto; /* Allow individual screens to scroll */
            padding: 20px;
            box-sizing: border-box;
        }

        .screen.active {
            display: flex;
        }

        /* Common elements */
        .app-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: linear-gradient(135deg, var(--primary-color), var(--primary-dark));
            color: white;
            border-top-left-radius: var(--border-radius); /* Kept for header's own styling */
            border-top-right-radius: var(--border-radius); /* Kept for header's own styling */
            padding: 20px;
            margin: -20px -20px 20px -20px; /* Extend to edges of .screen's padding box */
        }
        .app-header.no-bg {
            background: none;
            color: var(--text-color);
            padding: 15px 0; 
            margin: 0 0 15px 0; 
            border-top-left-radius: 0; 
            border-top-right-radius: 0;
        }

        .app-header h1, .app-header h2 {
            margin: 0;
            font-size: 1.5em;
            flex-grow: 1;
            text-align: center;
        }
        .app-header .back-button {
            font-size: 1.5em;
            cursor: pointer;
            background: none;
            border: none;
            color: white;
            margin-right: 10px;
        }
         .app-header.no-bg .back-button {
            color: var(--text-color);
         }
         .app-header .header-action-placeholder {
            width: 24px;
            visibility: hidden;
         }


        .input-group {
            margin-bottom: 20px;
        }

        .input-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
            color: var(--text-light);
        }

        .input-group input, .input-group select {
            width: 100%;
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 8px;
            box-sizing: border-box;
            font-size: 1em;
        }
        
        .password-wrapper {
            position: relative;
            display: flex;
            align-items: center;
        }
        .password-wrapper input {
            padding-right: 40px;
        }
        .toggle-password {
            position: absolute;
            right: 10px;
            cursor: pointer;
            color: var(--text-light);
            user-select: none;
        }


        .btn {
            display: block;
            width: 100%;
            padding: 15px;
            background-color: var(--primary-color);
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 1.1em;
            font-weight: bold;
            text-align: center;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }
        .btn:disabled {
            background-color: #ccc;
            cursor: not-allowed;
        }

        .btn:hover:not(:disabled) {
            background-color: var(--primary-dark);
        }

        .link-text {
            text-align: center;
            margin-top: 20px;
        }

        .link-text a {
            color: var(--primary-color);
            text-decoration: none;
            font-weight: bold;
        }

        /* Specific Screen Styles */

        /* Home Screen */
        #homeScreen .user-greeting {
            display: flex;
            align-items: center;
            background: linear-gradient(135deg, var(--primary-color), var(--primary-dark));
            color: white;
            padding: 20px;
            border-radius: var(--border-radius); 
            margin: -20px -20px 20px -20px; 
        }

        #homeScreen .user-greeting div h2 { 
            margin: 0 0 5px 0;
            font-size: 1.2em;
        }
        #homeScreen .user-greeting div p {
            margin: 0;
            font-size: 0.9em;
            opacity: 0.9;
        }
        #homeScreen .balance-card {
            background-color: var(--primary-dark);
            color: white;
            padding: 20px;
            border-radius: var(--border-radius);
            text-align: center;
            margin-bottom: 25px;
            box-shadow: var(--box-shadow);
        }
        #homeScreen .balance-card p {
            margin: 0 0 5px 0;
            font-size: 0.9em;
        }
        #homeScreen .balance-card h3 {
            margin: 0 0 15px 0;
            font-size: 2em;
        }
        #homeScreen .balance-card .btn-wallet {
            background-color: var(--secondary-color);
            color: var(--text-color);
            padding: 10px 20px;
            font-size: 0.9em;
            width: auto;
            display: inline-block;
        }

        #homeScreen .quick-tasks {
            display: flex;
            justify-content: space-around;
            margin-bottom: 25px;
        }
        #homeScreen .quick-task-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            cursor: pointer;
            background-color: var(--card-background);
            padding: 15px;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
            width: 80px; 
            text-align: center;
        }
        #homeScreen .quick-task-item .icon {
            font-size: 2em;
            margin-bottom: 8px;
            color: var(--primary-color);
        }
        #homeScreen .quick-task-item span {
            font-size: 0.8em;
            color: var(--text-light);
        }

        #homeScreen .more-tasks-header {
            font-size: 1.2em;
            font-weight: bold;
            margin-bottom: 15px;
        }
        #homeScreen .task-card {
            display: flex;
            align-items: center;
            background-color: var(--card-background);
            padding: 15px;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
            margin-bottom: 15px;
        }
        #homeScreen .task-card .task-icon {
            font-size: 2em;
            margin-right: 15px;
            padding: 10px;
            border-radius: 10px;
            color: white;
            width: 40px; 
            height: 40px; 
            display: flex;
            align-items: center;
            justify-content: center;
            box-sizing: border-box;
        }

        #homeScreen .task-info {
            flex-grow: 1;
        }
        #homeScreen .task-info h4 { margin: 0 0 5px 0; }
        #homeScreen .task-info p { margin: 0; font-size: 0.9em; color: var(--text-light); }
        #homeScreen .task-card .btn-task {
            background-color: var(--primary-color);
            color: white;
            padding: 8px 15px;
            font-size: 0.8em;
            border-radius: 6px;
            text-decoration: none; 
        }

        /* Bottom Navigation */
        .bottom-nav {
            display: flex; 
            justify-content: space-around;
            padding: 10px 0;
            background-color: var(--card-background);
            border-top: 1px solid #eee;
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            /* border-bottom-left-radius: var(--border-radius); */ /* REMOVED for full-screen look */
            /* border-bottom-right-radius: var(--border-radius); */ /* REMOVED for full-screen look */
            box-shadow: 0 -2px 10px rgba(0,0,0,0.05);
        }
        .nav-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            cursor: pointer;
            color: var(--text-light);
            flex: 1;
        }
        .nav-item.active {
            color: var(--primary-color);
        }
        .nav-item .icon {
            font-size: 1.5em;
            margin-bottom: 3px;
        }
        .nav-item span {
            font-size: 0.75em;
        }
        .screen-with-nav {
            padding-bottom: 80px; /* Space for the bottom nav */
        }

        /* Invite & Earn Screen */
        #inviteScreen .invite-content {
            text-align: center;
        }
        #inviteScreen .invite-illustration {
            width: 180px;
            height: auto;
            margin: 20px auto;
            background-color: #e0e0e0;
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.2em;
            color: #777;
            padding: 30px 0;
        }
        #inviteScreen .referral-code-area {
            background-color: #f0f0f0;
            padding: 15px;
            border-radius: var(--border-radius);
            margin: 25px 0;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        #inviteScreen .referral-code {
            font-size: 1.5em;
            font-weight: bold;
            letter-spacing: 2px;
            color: var(--primary-dark);
        }
        #inviteScreen .copy-button {
            background-color: var(--primary-color);
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 6px;
            cursor: pointer;
        }
        #inviteScreen .share-buttons {
            display: flex;
            justify-content: center;
            gap: 15px; 
            margin-top: 20px;
        }
        #inviteScreen .share-button {
            background-color: var(--primary-color);
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 8px;
            font-size: 1em;
            cursor: pointer;
            flex: 1; 
            max-width: 150px;
        }


        /* Spin & Win Screen */
        #spinWinScreen .spin-wheel-container {
            display: flex;
            justify-content: center;
            align-items: center;
            margin: 30px 0;
            position: relative;
        }
        #spinWinScreen .wheel {
            width: 250px;
            height: 250px;
            border: 10px solid var(--vip-color);
            border-radius: 50%;
            position: relative;
            overflow: hidden;
            transition: transform 4s cubic-bezier(0.33, 1, 0.68, 1); 
            background-image: conic-gradient(
                var(--secondary-color) 0deg 30deg,
                var(--primary-color) 30deg 60deg,
                var(--orange-color) 60deg 90deg,
                var(--dark-orange-color) 90deg 120deg,
                var(--secondary-color) 120deg 150deg,
                var(--primary-color) 150deg 180deg,
                var(--orange-color) 180deg 210deg,
                var(--dark-orange-color) 210deg 240deg,
                var(--secondary-color) 240deg 270deg,
                var(--primary-color) 270deg 300deg,
                var(--orange-color) 300deg 330deg,
                var(--dark-orange-color) 330deg 360deg
            );
        }
        #spinWinScreen .wheel-hub {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 50px;
            height: 50px;
            background: var(--vip-color);
            border-radius: 50%;
            border: 4px solid #b8860b;
            box-shadow: 0 0 10px rgba(0,0,0,0.2);
            z-index: 5;
        }

        #spinWinScreen .wheel-segment-text {
            position: absolute;
            width: 50%; 
            height: 50%;
            top: 0;
            left: 50%;
            transform-origin: 0% 100%; 
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            font-size: 0.9em; 
            color: var(--text-color);
            pointer-events: none;
            z-index: 2;
        }

        #spinWinScreen .wheel-segment-text:nth-child(1) { transform: rotate(15deg); }
        #spinWinScreen .wheel-segment-text:nth-child(2) { transform: rotate(45deg); }
        #spinWinScreen .wheel-segment-text:nth-child(3) { transform: rotate(75deg); }
        #spinWinScreen .wheel-segment-text:nth-child(4) { transform: rotate(105deg); }
        #spinWinScreen .wheel-segment-text:nth-child(5) { transform: rotate(135deg); }
        #spinWinScreen .wheel-segment-text:nth-child(6) { transform: rotate(165deg); }
        #spinWinScreen .wheel-segment-text:nth-child(7) { transform: rotate(195deg); }
        #spinWinScreen .wheel-segment-text:nth-child(8) { transform: rotate(225deg); }
        #spinWinScreen .wheel-segment-text:nth-child(9) { transform: rotate(255deg); }
        #spinWinScreen .wheel-segment-text:nth-child(10) { transform: rotate(285deg); }
        #spinWinScreen .wheel-segment-text:nth-child(11) { transform: rotate(315deg); }
        #spinWinScreen .wheel-segment-text:nth-child(12) { transform: rotate(345deg); }

        #spinWinScreen .wheel-segment-text span {
            display: block; 
            text-align: center;
            padding: 2px 5px;
            background-color: rgba(255, 255, 255, 0.2);
            border-radius: 3px;
        }
        #spinWinScreen .wheel-segment-text:nth-child(1) span { transform: rotate(-15deg); }
        #spinWinScreen .wheel-segment-text:nth-child(2) span { transform: rotate(-45deg); }
        #spinWinScreen .wheel-segment-text:nth-child(3) span { transform: rotate(-75deg); }
        #spinWinScreen .wheel-segment-text:nth-child(4) span { transform: rotate(-105deg); }
        #spinWinScreen .wheel-segment-text:nth-child(5) span { transform: rotate(-135deg); }
        #spinWinScreen .wheel-segment-text:nth-child(6) span { transform: rotate(-165deg); }
        #spinWinScreen .wheel-segment-text:nth-child(7) span { transform: rotate(-195deg); }
        #spinWinScreen .wheel-segment-text:nth-child(8) span { transform: rotate(-225deg); }
        #spinWinScreen .wheel-segment-text:nth-child(9) span { transform: rotate(-255deg); }
        #spinWinScreen .wheel-segment-text:nth-child(10) span { transform: rotate(-285deg); }
        #spinWinScreen .wheel-segment-text:nth-child(11) span { transform: rotate(-315deg); }
        #spinWinScreen .wheel-segment-text:nth-child(12) span { transform: rotate(-345deg); }


        #spinWinScreen .pointer {
            width: 0;
            height: 0;
            border-left: 15px solid transparent;
            border-right: 15px solid transparent;
            border-top: 25px solid var(--primary-dark);
            position: absolute;
            top: -20px; 
            left: 50%;
            transform: translateX(-50%);
            z-index: 10;
        }
        #spinWinScreen .spin-button {
            margin-top: 30px;
        }
        #spinWinScreen .spin-info {
            text-align: center;
            margin-top: 15px;
            color: var(--text-light);
        }
        #spinWinScreen .spin-result {
            text-align: center;
            margin-top: 20px;
            font-size: 1.2em;
            font-weight: bold;
            color: var(--primary-color);
        }
        
        /* Wallet, Deposit, Withdraw, History Screens */
        .transaction-list-item {
            background-color: #f9f9f9;
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 10px;
            border: 1px solid #eee;
        }
        .transaction-list-item p {
            margin: 5px 0;
            font-size: 0.9em;
        }
        .transaction-list-item .status {
            font-weight: bold;
            text-transform: capitalize; 
        }
        .transaction-list-item .status.pending { color: orange; }
        .transaction-list-item .status.approved { color: green; } 
        .transaction-list-item .status.rejected { color: red; }


        /* Utility for error/success messages */
        .message-text { 
            font-size: 0.9em;
            text-align: center;
            margin-top: 10px;
            padding: 10px;
            border-radius: 5px;
        }
        .message-text.error { color: red; background-color: #ffebee; border: 1px solid red;}
        .message-text.success { color: green; background-color: #e8f5e9; border: 1px solid green;}

        /* Profile Screen Avatar Removal Adjustments */
        #profileScreen .profile-info-container { 
            text-align: center; 
            margin-bottom: 20px;
        }
        #profileScreen .profile-info-container h2 { margin-bottom: 5px; }
        #profileScreen .profile-info-container p { margin-bottom: 10px; }

        /* Update Screen Styles */
        #updateScreen .update-list-container {
            padding-top: 10px;
        }
        #updateScreen .update-item {
            background-color: var(--card-background);
            padding: 15px;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
            margin-bottom: 15px;
        }
        #updateScreen .update-item .update-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 8px;
        }
        #updateScreen .update-item .update-title {
            font-size: 1.1em;
            font-weight: bold;
            color: var(--primary-color);
        }
        #updateScreen .update-item .update-date {
            font-size: 0.8em;
            color: var(--text-light);
        }
        #updateScreen .update-item .update-description {
            font-size: 0.95em;
            line-height: 1.5;
            color: var(--text-color);
            white-space: pre-wrap;
        }
        #updateScreen .update-item .update-version {
            font-size: 0.8em;
            color: var(--text-light);
            background-color: #f0f0f0;
            padding: 2px 6px;
            border-radius: 4px;
            display: inline-block;
            margin-top: 8px;
        }

        /* Live Chat Screen Styles -- WHATSAPP STYLE */
        #liveChatScreen {
            /* background-color: var(--chat-background); */ /* Optional */
        }

        #chatMessagesContainer { 
            flex-grow: 1; /* Allows this to take available vertical space */
            overflow-y: auto; /* Enables scrolling for messages */
            padding: 10px;
            margin-bottom: 10px; /* Space above input area */
            display: flex;
            flex-direction: column; /* Stacks messages vertically */
            gap: 8px; /* Space between messages */
        }

        #liveChatScreen .chat-message {
            padding: 8px 12px;
            border-radius: 12px;
            max-width: 80%;
            word-wrap: break-word;
            box-shadow: 0 1px 2px rgba(0,0,0,0.1);
            position: relative;
        }

        #liveChatScreen .chat-message .sender-name {
            font-weight: bold;
            font-size: 0.85em;
            color: var(--primary-color);
            display: block;
            margin-bottom: 4px;
        }

        #liveChatScreen .chat-message .message-text-content { 
            font-size: 0.95em;
            line-height: 1.4;
            white-space: pre-wrap;
        }

        #liveChatScreen .chat-message .message-time {
            font-size: 0.7em;
            color: var(--text-light);
            display: block;
            margin-top: 5px;
            text-align: right;
        }

        #liveChatScreen .my-message {
            background-color: var(--my-message-bg);
            color: var(--my-message-text);
            align-self: flex-end; 
            border-top-right-radius: 5px;
        }
         #liveChatScreen .my-message .message-time {
            color: rgba(0,0,0,0.5);
        }

        #liveChatScreen .other-message {
            background-color: var(--other-message-bg);
            color: var(--other-message-text);
            align-self: flex-start; 
            border-top-left-radius: 5px;
        }
         #liveChatScreen .other-message .message-time {
            color: var(--text-light);
        }

        #liveChatScreen .chat-input-area {
            display: flex;
            gap: 10px;
            align-items: center;
            padding: 10px;
            background-color: #f0f0f0;
            border-top: 1px solid #ddd;
            flex-shrink: 0; /* Prevents this area from shrinking */
        }

        #liveChatScreen #chatMessageInput {
            flex-grow: 1;
            padding: 10px 15px;
            border: 1px solid #ccc;
            border-radius: 20px;
            font-size: 1em;
            background-color: white;
        }

        #liveChatScreen #sendChatMessageButton {
            width: auto;
            padding: 10px 15px;
            font-size: 1em; 
            border-radius: 20px;
            background-color: var(--primary-color);
            color: white;
        }
        #liveChatScreen #sendChatMessageButton:hover {
            background-color: var(--primary-dark);
        }

    </style>
</head>
<body>
    <div class="app-container">
        <!-- Sign Up Screen -->
        <div id="signUpScreen" class="screen active">
            <div class="app-header no-bg" style="justify-content: center;">
                <h1>Create Account</h1>
            </div>
            <div class="input-group">
                <label for="signUpName">Your Name</label>
                <input type="text" id="signUpName" placeholder="ZORAIB AK">
            </div>
            <div class="input-group">
                <label for="signUpEmail">Email Address</label>
                <input type="email" id="signUpEmail" placeholder="zoraib@gmail.com">
            </div>
            <div class="input-group">
                <label for="signUpPassword">Create a Password</label>
                <div class="password-wrapper">
                    <input type="password" id="signUpPassword" placeholder="••••••••">
                    <span class="toggle-password" onclick="togglePasswordVisibility('signUpPassword', this)">👁️</span>
                </div>
            </div>
            <div class="input-group">
                <label for="signUpReferralCode">Referral Code (Optional)</label>
                <input type="text" id="signUpReferralCode" placeholder="Enter referral code">
            </div>
            <button id="signUpButton" class="btn">Sign Up</button>
            <p id="signUpError" class="message-text error" style="display:none;"></p>
            <p class="link-text">Already have an account? <a href="#" id="navigateToLogin">Sign In</a></p>
        </div>

        <!-- Login Screen -->
        <div id="loginScreen" class="screen">
            <div class="app-header no-bg" style="justify-content: center;">
                <h1>Welcome Back!</h1>
            </div>
            <div class="input-group">
                <label for="loginEmail">Email Address</label>
                <input type="email" id="loginEmail" placeholder="zoraib@gmail.com">
            </div>
            <div class="input-group">
                <label for="loginPassword">Password</label>
                 <div class="password-wrapper">
                    <input type="password" id="loginPassword" placeholder="••••••••">
                    <span class="toggle-password" onclick="togglePasswordVisibility('loginPassword', this)">👁️</span>
                </div>
            </div>
            <button id="loginButton" class="btn">Login</button>
            <p id="loginError" class="message-text error" style="display:none;"></p>
            <p class="link-text">Don't have an account? <a href="#" id="navigateToSignUp">Sign Up</a></p>
        </div>

        <!-- Home Screen -->
        <div id="homeScreen" class="screen screen-with-nav">
            <div class="user-greeting"> 
                <div>
                    <h2 id="userNameHome">Hi, Guest!</h2>
                    <p>Welcome back, let's earn!</p>
                </div>
            </div>

            <div class="balance-card">
                <p>Current Balance</p>
                <h3 id="currentBalanceHome">🪙 0</h3>
                <button class="btn btn-wallet" onclick="showScreen('walletScreen')">My Wallet</button>
            </div>

            <div class="quick-tasks">
                <div class="quick-task-item" id="dailyCheckInButton">
                    <span class="icon">🎁</span>
                    <span>Daily Check-in</span>
                </div>
                <div class="quick-task-item" onclick="showScreen('spinWinScreen')">
                    <span class="icon">🎯</span>
                    <span>Spin & Win</span>
                </div>
                <div class="quick-task-item" onclick="showScreen('inviteScreen')">
                    <span class="icon">🧑‍🤝‍🧑</span>
                    <span>Invite & Earn</span>
                </div>
            </div>

            <h3 class="more-tasks-header">More Tasks</h3>
            <div class="task-card" id="whatsappContactCard">
                <span class="task-icon" style="background-color: #25D366;">📱</span>
                <div class="task-info">
                    <h4>Contact on WhatsApp</h4>
                    <p>For support: ZORAIB </p>
                </div>
                <a href="https://wa.me/9203185051357" target="_blank" class="btn btn-task">Chat Now</a>
            </div>
        </div>
        
        <!-- Update Screen -->
        <div id="updateScreen" class="screen screen-with-nav">
            <div class="app-header no-bg" style="justify-content: center;"> 
                <h1>App Updates</h1>
            </div>
            <div id="updateListContainer" class="update-list-container">
                <p style="text-align:center;">Loading updates...</p>
            </div>
        </div>

        <!-- Live Chat Screen -- WHATSAPP STYLE -->
        <div id="liveChatScreen" class="screen screen-with-nav"> 
            <div class="app-header no-bg" style="margin-bottom: 0;">
                <h1 style="flex-grow:1; text-align:center;">Live Chat</h1>
            </div>
            <div id="chatMessagesContainer">
                <p style="text-align:center; color: var(--text-light);">Loading chat...</p>
            </div>
            <div class="chat-input-area">
                <input type="text" id="chatMessageInput" placeholder="Type a message">
                <button id="sendChatMessageButton" class="btn">Send</button>
            </div>
        </div>


        <!-- Invite & Earn Screen -->
        <div id="inviteScreen" class="screen">
            <div class="app-header no-bg"> 
                <button class="back-button" onclick="goBackToPreviousScreenOrHome('homeScreen')">←</button>
                <h2>Invite & Earn</h2>
                <span class="header-action-placeholder"></span>
            </div>
            <div class="invite-content">
                <div class="invite-illustration">
                    Two People Waving
                </div>
                <p>Invite your friends and earn rewards when they sign up using your code!</p>
                
                <div class="referral-code-area">
                    <span class="referral-code" id="referralCodeDisplay">LOGIN</span>
                    <button class="copy-button" id="copyReferralCode">Copy</button>
                </div>

                <div class="share-buttons">
                    <button class="share-button">Share via WhatsApp</button>
                    <button class="share-button">More Options</button>
                </div>
            </div>
        </div>

        <!-- Spin & Win Screen -->
        <div id="spinWinScreen" class="screen">
            <div class="app-header no-bg"> 
                <button class="back-button" onclick="showScreen('homeScreen')">←</button>
                <h2>Spin & Win</h2>
                 <span class="header-action-placeholder"></span>
            </div>
            <p id="availableSpinsText" class="spin-info">Available Spins: 0</p>
            <div class="spin-wheel-container">
                <div class="pointer"></div>
                <div class="wheel" id="spinWheel">
                    <div class="wheel-segment-text"><span>25</span></div>
                    <div class="wheel-segment-text"><span>10</span></div>
                    <div class="wheel-segment-text"><span>15</span></div>
                    <div class="wheel-segment-text"><span>20</span></div>
                    <div class="wheel-segment-text"><span>5</span></div>
                    <div class="wheel-segment-text"><span>50</span></div>
                    <div class="wheel-segment-text"><span>100</span></div>
                    <div class="wheel-segment-text"><span>150</span></div>
                    <div class="wheel-segment-text"><span>75</span></div>
                    <div class="wheel-segment-text"><span>25</span></div>
                    <div class="wheel-segment-text"><span>10</span></div>
                    <div class="wheel-segment-text"><span>SE</span></div>
                    <div class="wheel-hub"></div>
                </div>
            </div>
            <button class="btn spin-button" id="spinButton" disabled>Spin Now!</button>
            <p class="spin-result" id="spinResultText"></p>
        </div>
        
        <!-- Profile Screen (Enhanced) -->
        <div id="profileScreen" class="screen screen-with-nav">
             <div class="app-header no-bg" style="justify-content: center;">
                <h1>My Profile</h1>
            </div>
            <div class="profile-info-container"> 
                <h2 id="profileUserName">User Name</h2>
                <p id="profileUserEmail" style="color: var(--text-light);">user@example.com</p>
                <span id="profileVipBadge" style="background-color: var(--vip-color); color: black; padding: 3px 8px; border-radius: 5px; font-size: 0.8em; display: none;">VIP</span>
            </div>

            <div class="input-group">
                <label for="profileEditName">Change Name</label>
                <input type="text" id="profileEditName" placeholder="Enter new name">
                <button id="updateNameButton" class="btn" style="margin-top:10px; font-size: 0.9em; padding: 10px;">Update Name</button>
            </div>
            
            <div class="input-group">
                <label for="profileEditEmail">Change Email</label>
                <input type="email" id="profileEditEmail" placeholder="Enter new email">
                <input type="password" id="profileCurrentPasswordForEmail" class="input-group input" placeholder="Current Password for verification" style="margin-top:5px;">
                <button id="updateEmailButton" class="btn" style="margin-top:10px; font-size: 0.9em; padding: 10px;">Update Email</button>
            </div>

            <div class="input-group">
                <label for="profileNewPassword">Change Password</label>
                <input type="password" id="profileCurrentPasswordForPassword" class="input-group input" placeholder="Current Password">
                <input type="password" id="profileNewPassword" placeholder="Enter new password" style="margin-top:5px;">
                <input type="password" id="profileConfirmNewPassword" placeholder="Confirm new password" style="margin-top:5px;">
                <button id="updatePasswordButton" class="btn" style="margin-top:10px; font-size: 0.9em; padding: 10px;">Update Password</button>
            </div>
            <p id="profileMessage" class="message-text" style="display:none;"></p>

            <button id="logoutButton" class="btn" style="background-color: #888; margin-top:20px;">Logout</button>
        </div>

        <!-- Wallet Screen -->
        <div id="walletScreen" class="screen screen-with-nav">
            <div class="app-header no-bg"> 
                <button class="back-button" onclick="showScreen('homeScreen')">←</button>
                <h2>My Wallet</h2>
                <span class="header-action-placeholder"></span>
            </div>
            <div class="balance-card" style="background-color: var(--primary-color); color: white; margin-top: 0; margin-bottom:25px;">
                <p>Current Balance</p>
                <h3 id="walletBalanceDisplay">🪙 0</h3>
            </div>
            <button class="btn" onclick="showScreen('depositScreen')" style="margin-bottom: 15px;">Deposit</button>
            <button class="btn" style="background-color: var(--secondary-color); color: var(--text-color); margin-bottom: 15px;" onclick="showScreen('withdrawScreen')">Withdraw</button>
            
            <h3 style="margin-top: 20px; margin-bottom: 15px; text-align:center;">Transaction History</h3>
            <button class="btn" style="background-color: #f0f0f0; color: var(--text-color); margin-bottom: 15px; font-size:1em; padding:12px;" onclick="showScreen('depositHistoryScreen')">View Deposit History</button>
            <button class="btn" style="background-color: #f0f0f0; color: var(--text-color); font-size:1em; padding:12px;" onclick="showScreen('withdrawalHistoryScreen')">View Withdrawal History</button>
        </div>

        <!-- Deposit Screen -->
        <div id="depositScreen" class="screen">
            <div class="app-header no-bg"> 
                <button class="back-button" onclick="showScreen('walletScreen')">←</button>
                <h2>Deposit Funds</h2>
                <span class="header-action-placeholder"></span>
            </div>
            <div style="padding: 10px; background-color: #f9f9f9; border-radius: 8px; margin-bottom: 20px;">
                <p style="margin-top:0;">To deposit, send funds to:</p>
                <p><strong>Account Name:</strong> SYED HUSSNAIN RAZIQ</p>
                <p><strong>Account Number (Sadapay):</strong> 03319234418</p>
            </div>
            <p>After sending, enter the amount (PKR) and Transaction ID (TID) below:</p>
            <div class="input-group">
                <label for="depositAmount">Amount Sent (PKR)</label>
                <input type="number" id="depositAmount" placeholder="e.g., 200">
            </div>
            <div class="input-group">
                <label for="depositTid">Transaction ID (TID)</label>
                <input type="text" id="depositTid" placeholder="Enter TID from payment receipt">
            </div>
            <button id="submitDepositButton" class="btn">Submit Deposit Request</button>
            <p id="depositMessage" class="message-text" style="display:none;"></p>
        </div>

        <!-- Withdraw Screen -->
        <div id="withdrawScreen" class="screen">
            <div class="app-header no-bg"> 
                <button class="back-button" onclick="showScreen('walletScreen')">←</button>
                <h2>Withdraw Funds</h2>
                <span class="header-action-placeholder"></span>
            </div>
            <div class="input-group">
                <label for="withdrawMethod">Withdrawal Method</label>
                <select id="withdrawMethod">
                    <option value="JazzCash">JazzCash</option>
                    <option value="Easypaisa">Easypaisa</option>
                </select>
            </div>
            <div class="input-group">
                <label for="withdrawAccountName">Account Name</label>
                <input type="text" id="withdrawAccountName" placeholder="Your full name on the account">
            </div>
            <div class="input-group">
                <label for="withdrawAccountNumber">Account Number</label>
                <input type="text" id="withdrawAccountNumber" placeholder="e.g., 03xxxxxxxxx">
            </div>
            <div class="input-group">
                <label for="withdrawAmount">Amount to Withdraw (🪙)</label>
                <input type="number" id="withdrawAmount" placeholder="Min 1000 coins">
            </div>
            <button id="submitWithdrawalButton" class="btn">Submit Withdrawal Request</button>
            <p id="withdrawalMessage" class="message-text" style="display:none;"></p>
        </div>

        <!-- Deposit History Screen -->
        <div id="depositHistoryScreen" class="screen screen-with-nav">
            <div class="app-header no-bg"> 
                <button class="back-button" onclick="showScreen('walletScreen')">←</button>
                <h2>Deposit History</h2>
                <span class="header-action-placeholder"></span>
            </div>
            <div id="depositHistoryList" style="padding-bottom: 10px;">
                <p style="text-align:center;">Loading history...</p>
            </div>
        </div>

        <!-- Withdrawal History Screen -->
        <div id="withdrawalHistoryScreen" class="screen screen-with-nav">
            <div class="app-header no-bg"> 
                <button class="back-button" onclick="showScreen('walletScreen')">←</button>
                <h2>Withdrawal History</h2>
                <span class="header-action-placeholder"></span>
            </div>
            <div id="withdrawalHistoryList" style="padding-bottom: 10px;">
                <p style="text-align:center;">Loading history...</p>
            </div>
        </div>


        <!-- Bottom Navigation Bar -->
        <div class="bottom-nav" id="bottomNav" style="display: none;">
            <div class="nav-item active" data-screen="homeScreen">
                <span class="icon">🏠</span>
                <span>Home</span>
            </div>
            <div class="nav-item" data-screen="updateScreen">
                <span class="icon">📢</span>
                <span>Updates</span>
            </div>
            <div class="nav-item" data-screen="liveChatScreen">
                <span class="icon">💬</span>
                <span>Chat</span>
            </div>
             <div class="nav-item" data-screen="inviteScreen" data-non-nav-parent="homeScreen">
                <span class="icon">🎁</span>
                <span>Invite</span>
            </div>
            <div class="nav-item" data-screen="profileScreen">
                <span class="icon">👤</span>
                <span>Profile</span>
            </div>
        </div>
    </div>

    <!-- Firebase SDKs -->
    <script src="https://www.gstatic.com/firebasejs/8.10.0/firebase-app.js"></script>
    <script src="https://www.gstatic.com/firebasejs/8.10.0/firebase-auth.js"></script>
    <script src="https://www.gstatic.com/firebasejs/8.10.0/firebase-database.js"></script>

    <script>
        const firebaseConfig = {
            apiKey: "AIzaSyC14VjV9H-sXGWpKF7zWcTvNaOfTpVs9mw", // Replace with your actual config
            authDomain: "bg-remover-1699f.firebaseapp.com",
            databaseURL: "https://bg-remover-1699f-default-rtdb.firebaseio.com",
            projectId: "bg-remover-1699f",
            storageBucket: "bg-remover-1699f.appspot.com",
            messagingSenderId: "562843649498",
            appId: "1:562843649498:web:435a7caddf8059ace2ace3",
            measurementId: "G-3PQ5FVBW3X"
        };

        try {
            firebase.initializeApp(firebaseConfig);
        } catch (e) {
            console.error("Firebase initialization error:", e);
            alert("Could not initialize Firebase. App functionality will be limited.");
        }
        
        const auth = firebase.auth();
        const database = firebase.database();
        const serverTimestamp = firebase.database.ServerValue.TIMESTAMP;

        // DOM Elements
        const screens = document.querySelectorAll('.screen');
        const bottomNav = document.getElementById('bottomNav');
        const bottomNavItems = document.querySelectorAll('.bottom-nav .nav-item');


        // Auth Elements
        const signUpNameInput = document.getElementById('signUpName');
        const signUpEmailInput = document.getElementById('signUpEmail');
        const signUpPasswordInput = document.getElementById('signUpPassword');
        const signUpReferralCodeInput = document.getElementById('signUpReferralCode'); 
        const signUpButton = document.getElementById('signUpButton');
        const navigateToLoginLink = document.getElementById('navigateToLogin');
        const signUpError = document.getElementById('signUpError');
        const loginEmailInput = document.getElementById('loginEmail');
        const loginPasswordInput = document.getElementById('loginPassword');
        const loginButton = document.getElementById('loginButton');
        const navigateToSignUpLink = document.getElementById('navigateToSignUp');
        const loginError = document.getElementById('loginError');

        // Home Screen Elements
        const userNameHome = document.getElementById('userNameHome');
        const currentBalanceHome = document.getElementById('currentBalanceHome');
        const dailyCheckInButton = document.getElementById('dailyCheckInButton');

        // Invite Screen Elements
        const referralCodeDisplay = document.getElementById('referralCodeDisplay');
        const copyReferralCodeButton = document.getElementById('copyReferralCode');

        // Spin Wheel Elements
        const spinWheel = document.getElementById('spinWheel');
        const spinButton = document.getElementById('spinButton');
        const spinResultText = document.getElementById('spinResultText');
        const availableSpinsText = document.getElementById('availableSpinsText');
        let isSpinning = false;
        const wheelSegments = [ 
            { value: 25, label: "25 Coins" }, { value: 10, label: "10 Coins" }, { value: 15, label: "15 Coins" },
            { value: 20, label: "20 Coins" }, { value: 5, label: "5 Coins" }, { value: 50, label: "50 Coins" },
            { value: 100, label: "100 Coins" }, { value: 150, label: "150 Coins" }, { value: 75, label: "75 Coins" },
            { value: 25, label: "25 Coins" }, { value: 10, label: "10 Coins" }, { value: 0, label: "Try Again" } 
        ];

        // Profile Screen Elements
        const logoutButton = document.getElementById('logoutButton');
        const profileUserName = document.getElementById('profileUserName');
        const profileUserEmail = document.getElementById('profileUserEmail');
        const profileVipBadge = document.getElementById('profileVipBadge');
        const profileEditNameInput = document.getElementById('profileEditName');
        const updateNameButton = document.getElementById('updateNameButton');
        const profileEditEmailInput = document.getElementById('profileEditEmail');
        const profileCurrentPasswordForEmailInput = document.getElementById('profileCurrentPasswordForEmail');
        const updateEmailButton = document.getElementById('updateEmailButton');
        const profileCurrentPasswordForPasswordInput = document.getElementById('profileCurrentPasswordForPassword');
        const profileNewPasswordInput = document.getElementById('profileNewPassword');
        const profileConfirmNewPasswordInput = document.getElementById('profileConfirmNewPassword');
        const updatePasswordButton = document.getElementById('updatePasswordButton');
        const profileMessage = document.getElementById('profileMessage');

        // Wallet Screen Elements
        const walletBalanceDisplay = document.getElementById('walletBalanceDisplay');

        // Deposit Screen Elements
        const depositAmountInput = document.getElementById('depositAmount');
        const depositTidInput = document.getElementById('depositTid');
        const submitDepositButton = document.getElementById('submitDepositButton');
        const depositMessage = document.getElementById('depositMessage');

        // Withdraw Screen Elements
        const withdrawMethodSelect = document.getElementById('withdrawMethod');
        const withdrawAccountNameInput = document.getElementById('withdrawAccountName');
        const withdrawAccountNumberInput = document.getElementById('withdrawAccountNumber');
        const withdrawAmountInput = document.getElementById('withdrawAmount');
        const submitWithdrawalButton = document.getElementById('submitWithdrawalButton');
        const withdrawalMessage = document.getElementById('withdrawalMessage');

        // History List Elements
        const depositHistoryList = document.getElementById('depositHistoryList');
        const withdrawalHistoryList = document.getElementById('withdrawalHistoryList');

        // Update Screen Elements
        const updateListContainer = document.getElementById('updateListContainer');

        // Live Chat Screen Elements
        const chatMessagesContainer = document.getElementById('chatMessagesContainer');
        const chatMessageInput = document.getElementById('chatMessageInput');
        const sendChatMessageButton = document.getElementById('sendChatMessageButton');
        let chatMessagesRef = null;
        let chatListenerAttached = false;


        let currentUserData = null; 
        let previousScreenId = 'homeScreen'; 

        // Screen Navigation Logic
        function showScreen(screenId, isBackAction = false) {
            const currentActiveScreen = document.querySelector('.screen.active');
            if (currentActiveScreen && !isBackAction) {
                previousScreenId = currentActiveScreen.id;
            }

            if (currentActiveScreen && currentActiveScreen.id === 'liveChatScreen' && screenId !== 'liveChatScreen') {
                detachChatListener();
            }

            screens.forEach(screen => screen.classList.remove('active'));
            const activeScreen = document.getElementById(screenId);
            if (activeScreen) activeScreen.classList.add('active');

            updateBottomNavActiveState(screenId);

            if (screenId === 'updateScreen') loadUpdatesData(); 
            if (screenId === 'profileScreen' && currentUserData) populateProfileScreen(currentUserData);
            if (screenId === 'walletScreen' && currentUserData) walletBalanceDisplay.textContent = `🪙 ${currentUserData.balance.toLocaleString()}`;
            if (screenId === 'depositHistoryScreen') loadDepositHistory();
            if (screenId === 'withdrawalHistoryScreen') loadWithdrawalHistory();
            if (screenId === 'spinWinScreen' && currentUserData) updateSpinUI();
            if (screenId === 'liveChatScreen') initChat(); 
        }

        function goBackToPreviousScreenOrHome(defaultScreen = 'homeScreen') {
            const targetScreen = document.getElementById(previousScreenId) ? previousScreenId : defaultScreen;
            showScreen(targetScreen, true);
        }


        function updateBottomNavActiveState(screenId) {
            let navTargetScreenId = screenId;
            
            const currentScreenNavItem = document.querySelector(`.nav-item[data-screen="${screenId}"]`);
            if (!currentScreenNavItem) { 
                 if (['walletScreen', 'depositScreen', 'withdrawScreen', 'depositHistoryScreen', 'withdrawalHistoryScreen', 'spinWinScreen'].includes(screenId)) {
                    navTargetScreenId = 'homeScreen'; 
                }
                 else if (screenId === 'inviteScreen'){ 
                    const inviteNavItem = document.querySelector(`.nav-item[data-screen="inviteScreen"]`);
                    if (inviteNavItem) navTargetScreenId = "inviteScreen";
                    else navTargetScreenId = 'homeScreen'; 
                 }
            }

            bottomNavItems.forEach(item => {
                item.classList.remove('active');
                if (item.dataset.screen === navTargetScreenId) {
                    item.classList.add('active');
                }
            });
        }


        function togglePasswordVisibility(inputId, toggleElement) {
            const passwordInput = document.getElementById(inputId);
            if (passwordInput.type === "password") {
                passwordInput.type = "text";
                toggleElement.textContent = "🙈";
            } else {
                passwordInput.type = "password";
                toggleElement.textContent = "👁️";
            }
        }

        bottomNavItems.forEach(item => {
            item.addEventListener('click', () => showScreen(item.dataset.screen));
        });

        navigateToLoginLink.addEventListener('click', (e) => { e.preventDefault(); showScreen('loginScreen'); });
        navigateToSignUpLink.addEventListener('click', (e) => { e.preventDefault(); showScreen('signUpScreen'); });

        auth.onAuthStateChanged(async (user) => {
            if (user) {
                console.log("User is currently logged in:", user.uid);
                await loadAndSetUserData(user.uid, user.email);
                
                const currentActive = document.querySelector('.screen.active');
                if (!currentActive || currentActive.id === 'signUpScreen' || currentActive.id === 'loginScreen') {
                     showScreen('homeScreen');
                } else {
                    updateUserInfoUI(currentUserData); 
                    if (currentActive.id === 'liveChatScreen') initChat(); 
                }
                bottomNav.style.display = 'flex'; 
            } else {
                console.log("No user logged in.");
                detachChatListener(); 
                currentUserData = null;
                clearUserInfoUI();
                showScreen('signUpScreen'); 
                bottomNav.style.display = 'none'; 
            }
        });

        async function loadAndSetUserData(userId, email) {
            try {
                const snapshot = await database.ref('users/' + userId).once('value');
                let userData = snapshot.val();

                if (!userData) { 
                    const name = email.split('@')[0];
                    userData = {
                        username: name,
                        email: email,
                        balance: 0, 
                        referralCode: generateReferralCode(userId.substring(0, 6).toUpperCase()),
                        lastDailyCheckIn: '1970-01-01',
                        lastFreeSpinDate: '1970-01-01',
                        availableSpins: 1,
                        vipStatus: false, 
                        referralsMade: 0, 
                    };
                    await database.ref('users/' + userId).set(userData);
                    console.log("New user data created on load (fallback):", userData);
                } else {
                    const defaultNewFields = {
                        lastDailyCheckIn: userData.lastDailyCheckIn || '1970-01-01',
                        lastFreeSpinDate: userData.lastFreeSpinDate || '1970-01-01',
                        availableSpins: userData.availableSpins === undefined ? 1 : userData.availableSpins,
                        vipStatus: userData.vipStatus || false,
                        referralsMade: userData.referralsMade === undefined ? 0 : userData.referralsMade,
                    };
                    let needsUpdate = false;
                    for (const key in defaultNewFields) {
                        if (!(key in userData)) {
                            userData[key] = defaultNewFields[key];
                            needsUpdate = true;
                        }
                    }
                    if(needsUpdate) await database.ref('users/' + userId).update(userData);
                }
                currentUserData = { ...userData, uid: userId };
                updateUserInfoUI(currentUserData);
            } catch (error) {
                console.error("Error loading/setting user data:", error);
                currentUserData = null; 
                clearUserInfoUI();
                showScreen('signUpScreen');
                bottomNav.style.display = 'none';
            }
        }
        
        function updateUserInfoUI(userData) {
            if (!userData) return;
            userNameHome.textContent = `Hi, ${userData.username}!`;
            currentBalanceHome.textContent = `🪙 ${userData.balance.toLocaleString()}`;
            
            if (referralCodeDisplay) referralCodeDisplay.textContent = userData.referralCode || "N/A";
            if (walletBalanceDisplay) walletBalanceDisplay.textContent = `🪙 ${userData.balance.toLocaleString()}`;
            
            if (document.getElementById('profileScreen').classList.contains('active')) { 
                populateProfileScreen(userData);
            }
            if (document.getElementById('spinWinScreen').classList.contains('active')) {
                updateSpinUI();
            }
        }
        
        function populateProfileScreen(userData) {
            if (!userData) return;
            profileUserName.textContent = userData.username;
            profileUserEmail.textContent = userData.email;
            profileEditNameInput.value = userData.username;
            profileEditEmailInput.value = userData.email;
            profileVipBadge.style.display = userData.vipStatus ? 'inline-block' : 'none';
            profileCurrentPasswordForEmailInput.value = '';
            profileCurrentPasswordForPasswordInput.value = '';
            profileNewPasswordInput.value = '';
            profileConfirmNewPasswordInput.value = '';
            profileMessage.style.display = 'none';
        }

        function clearUserInfoUI() {
            userNameHome.textContent = "Hi, Guest!";
            currentBalanceHome.textContent = "🪙 0";
            if (referralCodeDisplay) referralCodeDisplay.textContent = "LOGIN";
            if (walletBalanceDisplay) walletBalanceDisplay.textContent = "🪙 0";
            if (availableSpinsText) availableSpinsText.textContent = "Available Spins: 0";
            if (spinButton) spinButton.disabled = true;
            
            profileUserName.textContent = "User Name";
            profileUserEmail.textContent = "user@example.com";
            profileVipBadge.style.display = 'none';
        }


        if (signUpButton) {
            signUpButton.addEventListener('click', async () => {
                const name = signUpNameInput.value.trim();
                const email = signUpEmailInput.value.trim();
                const password = signUpPasswordInput.value;
                const enteredReferralCode = signUpReferralCodeInput.value.trim().toUpperCase(); 
                signUpError.style.display = 'none';

                if (!name || !email || !password) {
                    showUIMessage(signUpError, "Please fill in all fields (except optional referral code).", "error");
                    return;
                }
                if (password.length < 6) {
                    showUIMessage(signUpError, "Password should be at least 6 characters.", "error");
                    return;
                }

                try {
                    signUpButton.disabled = true;
                    signUpButton.textContent = "Signing Up...";

                    const userCredential = await auth.createUserWithEmailAndPassword(email, password);
                    const user = userCredential.user;
                    console.log("User signed up:", user.uid);

                    let initialBalance = 0;
                    let referredByUID = null;

                    if (enteredReferralCode) {
                        const referrerSnapshot = await database.ref('users')
                                                              .orderByChild('referralCode')
                                                              .equalTo(enteredReferralCode)
                                                              .once('value');
                        
                        if (referrerSnapshot.exists()) {
                            const referrerData = referrerSnapshot.val();
                            const referrerUID = Object.keys(referrerData)[0]; 
                            const referrer = referrerData[referrerUID];

                            if (referrerUID !== user.uid) { 
                                initialBalance = 30; 
                                referredByUID = referrerUID;
                                console.log(`User referred by ${referrer.username} (UID: ${referrerUID}). New user gets 30 coins.`);

                                const currentReferralsMade = referrer.referralsMade || 0;
                                await database.ref('users/' + referrerUID).update({
                                    referralsMade: currentReferralsMade + 1
                                });
                                console.log(`Referrer ${referrer.username} referralsMade updated to ${currentReferralsMade + 1}`);
                            } else {
                                console.log("Referral code belongs to the signing up user. No bonus.");
                            }
                        } else {
                            console.log("Invalid or non-existent referral code entered.");
                        }
                    }

                    const newUserSetup = {
                        username: name,
                        email: email,
                        balance: initialBalance,
                        referralCode: generateReferralCode(user.uid.substring(0, 6).toUpperCase()),
                        lastDailyCheckIn: '1970-01-01',
                        lastFreeSpinDate: '1970-01-01',
                        availableSpins: 1, 
                        vipStatus: false, 
                        referralsMade: 0, 
                        ...(referredByUID && { referredBy: referredByUID }) 
                    };
                    await database.ref('users/' + user.uid).set(newUserSetup);
                    console.log("New user data set in DB:", newUserSetup);
                } catch (error) {
                    showUIMessage(signUpError, error.message, "error");
                    console.error("Sign up error:", error);
                } finally {
                    signUpButton.disabled = false;
                    signUpButton.textContent = "Sign Up";
                }
            });
        }

        if (loginButton) {
            loginButton.addEventListener('click', async () => {
                const email = loginEmailInput.value.trim();
                const password = loginPasswordInput.value;
                loginError.style.display = 'none';

                if (!email || !password) {
                    showUIMessage(loginError, "Please fill in all fields.", "error");
                    return;
                }
                try {
                    loginButton.disabled = true;
                    loginButton.textContent = "Logging In...";
                    await auth.signInWithEmailAndPassword(email, password);
                } catch (error) {
                    showUIMessage(loginError, error.message, "error");
                    console.error("Login error:", error);
                } finally {
                    loginButton.disabled = false;
                    loginButton.textContent = "Login";
                }
            });
        }
        
        if (logoutButton) {
            logoutButton.addEventListener('click', () => {
                detachChatListener(); 
                auth.signOut().catch((error) => console.error("Logout error:", error));
            });
        }
        
        function generateReferralCode(base = '') {
            const chars = 'ABCDEFGHJKLMNPQRSTUVWXYZ23456789'; 
            let code = base;
            const length = 8 - base.length;
            for (let i = 0; i < length; i++) {
                code += chars.charAt(Math.floor(Math.random() * chars.length));
            }
            return code.toUpperCase();
        }

        function showUIMessage(element, message, type = "error") {
            element.textContent = message;
            element.className = `message-text ${type}`; 
            element.style.display = 'block';
            setTimeout(() => { element.style.display = 'none'; }, 5000);
        }

        if(dailyCheckInButton) {
            dailyCheckInButton.addEventListener('click', async () => {
                if (!currentUserData) { alert("Please login first."); return; }
                const today = new Date().toISOString().split('T')[0]; 
                if (currentUserData.lastDailyCheckIn === today) {
                    alert("You have already checked in today!");
                    return;
                }
                const rewardAmount = 50;
                const newBalance = (currentUserData.balance || 0) + rewardAmount;
                try {
                    await database.ref('users/' + currentUserData.uid).update({
                        balance: newBalance,
                        lastDailyCheckIn: today
                    });
                    currentUserData.balance = newBalance;
                    currentUserData.lastDailyCheckIn = today;
                    updateUserInfoUI(currentUserData);
                    alert(`Daily Check-in! You received ${rewardAmount} coins.`);
                } catch (error) {
                    console.error("Daily check-in error:", error);
                    alert("Could not process check-in. Please try again.");
                }
            });
        }

        function updateSpinUI() {
            if (!currentUserData || !availableSpinsText || !spinButton) return;
            availableSpinsText.textContent = `Available Spins: ${currentUserData.availableSpins || 0}`;
            spinButton.disabled = (currentUserData.availableSpins || 0) <= 0 || isSpinning;
        }

        if (spinButton) {
            spinButton.addEventListener('click', async () => {
                if (isSpinning || !currentUserData) return;
                const today = new Date().toISOString().split('T')[0];
                let canSpinFree = currentUserData.lastFreeSpinDate !== today;
                let spinsToUse = currentUserData.availableSpins || 0;

                if (spinsToUse <= 0 && !canSpinFree) {
                     alert("No spins available. Deposit to get more or wait for your daily free spin tomorrow!");
                     return;
                }
                
                isSpinning = true;
                spinResultText.textContent = "";
                spinButton.disabled = true;
                spinButton.style.backgroundColor = '#ccc'; 

                let newAvailableSpins = spinsToUse;
                let newLastFreeSpinDate = currentUserData.lastFreeSpinDate;

                if (canSpinFree) { 
                    newLastFreeSpinDate = today;
                } else if (spinsToUse > 0) { 
                    newAvailableSpins--;
                } else { 
                    isSpinning = false;
                    spinButton.disabled = false;
                    spinButton.style.backgroundColor = 'var(--primary-color)';
                    updateSpinUI();
                    return;
                }

                const totalRotations = 3; 
                const randomIndex = Math.floor(Math.random() * wheelSegments.length);
                const segmentAngle = 360 / wheelSegments.length;
                const targetBaseAngle = (randomIndex * segmentAngle); 
                const pointerStopAngle = targetBaseAngle + (segmentAngle / 2); 
                const finalRotation = (totalRotations * 360) - pointerStopAngle + (segmentAngle * 0.05); 

                spinWheel.style.transform = `rotate(${finalRotation}deg)`;

                setTimeout(async () => {
                    isSpinning = false;
                    spinButton.style.backgroundColor = 'var(--primary-color)';
                    const winningSegment = wheelSegments[randomIndex];
                    spinResultText.textContent = `You won: ${winningSegment.label}!`;
                    
                    let updates = {
                        availableSpins: newAvailableSpins,
                        lastFreeSpinDate: newLastFreeSpinDate
                    };
                    if (winningSegment.value > 0) {
                        const newBalance = (currentUserData.balance || 0) + winningSegment.value;
                        updates.balance = newBalance;
                        currentUserData.balance = newBalance; 
                    }

                    try {
                        await database.ref('users/' + currentUserData.uid).update(updates);
                        currentUserData.availableSpins = newAvailableSpins; 
                        currentUserData.lastFreeSpinDate = newLastFreeSpinDate; 
                        updateUserInfoUI(currentUserData); 
                        updateSpinUI(); 
                    } catch (error) {
                        console.error("Spin update error:", error);
                        alert("Error saving spin result. Please check your connection.");
                    }
                }, 4100); 
            });
        }

        if (copyReferralCodeButton) {
            copyReferralCodeButton.addEventListener('click', () => {
                const codeToCopy = referralCodeDisplay.textContent;
                if (codeToCopy === "LOGIN" || codeToCopy === "N/A") {
                    alert("Login to get your referral code.");
                    return;
                }
                navigator.clipboard.writeText(codeToCopy).then(() => {
                    alert('Referral code copied!');
                }).catch(err => {
                    console.error('Failed to copy: ', err);
                    alert('Failed to copy code.');
                });
            });
        }
        
        if (updateNameButton) {
            updateNameButton.addEventListener('click', async () => {
                if (!currentUserData) return;
                const newName = profileEditNameInput.value.trim();
                if (!newName) {
                    showUIMessage(profileMessage, "Name cannot be empty.", "error");
                    return;
                }
                if (newName === currentUserData.username) {
                    showUIMessage(profileMessage, "Name is already set to this.", "success");
                    return;
                }
                try {
                    await database.ref('users/' + currentUserData.uid).update({ username: newName });
                    currentUserData.username = newName;
                    updateUserInfoUI(currentUserData); 
                    showUIMessage(profileMessage, "Name updated successfully!", "success");
                } catch (error) {
                    console.error("Update name error:", error);
                    showUIMessage(profileMessage, "Error updating name.", "error");
                }
            });
        }

        if (updateEmailButton) {
            updateEmailButton.addEventListener('click', async () => {
                if (!currentUserData) return;
                const newEmail = profileEditEmailInput.value.trim();
                const currentPassword = profileCurrentPasswordForEmailInput.value;

                if (!newEmail || !currentPassword) {
                    showUIMessage(profileMessage, "New email and current password are required.", "error");
                    return;
                }
                if (newEmail === currentUserData.email) {
                     showUIMessage(profileMessage, "This is already your current email.", "success");
                    return;
                }

                const user = auth.currentUser;
                if (!user) return;

                const credential = firebase.auth.EmailAuthProvider.credential(user.email, currentPassword);
                try {
                    await user.reauthenticateWithCredential(credential);
                    await user.updateEmail(newEmail);
                    await database.ref('users/' + user.uid).update({ email: newEmail });
                    currentUserData.email = newEmail;
                    updateUserInfoUI(currentUserData);
                    profileCurrentPasswordForEmailInput.value = ''; 
                    showUIMessage(profileMessage, "Email updated successfully! You might need to re-login elsewhere.", "success");
                } catch (error) {
                    console.error("Update email error:", error);
                    showUIMessage(profileMessage, `Error updating email: ${error.message}`, "error");
                }
            });
        }

        if (updatePasswordButton) {
            updatePasswordButton.addEventListener('click', async () => {
                if (!currentUserData) return;
                const currentPassword = profileCurrentPasswordForPasswordInput.value;
                const newPassword = profileNewPasswordInput.value;
                const confirmNewPassword = profileConfirmNewPasswordInput.value;

                if (!currentPassword || !newPassword || !confirmNewPassword) {
                    showUIMessage(profileMessage, "All password fields are required.", "error");
                    return;
                }
                if (newPassword.length < 6) {
                    showUIMessage(profileMessage, "New password must be at least 6 characters.", "error");
                    return;
                }
                if (newPassword !== confirmNewPassword) {
                    showUIMessage(profileMessage, "New passwords do not match.", "error");
                    return;
                }

                const user = auth.currentUser;
                if (!user) return;

                const credential = firebase.auth.EmailAuthProvider.credential(user.email, currentPassword);
                try {
                    await user.reauthenticateWithCredential(credential);
                    await user.updatePassword(newPassword);
                    profileCurrentPasswordForPasswordInput.value = '';
                    profileNewPasswordInput.value = '';
                    profileConfirmNewPasswordInput.value = '';
                    showUIMessage(profileMessage, "Password updated successfully!", "success");
                } catch (error) {
                    console.error("Update password error:", error);
                    showUIMessage(profileMessage, `Error updating password: ${error.message}`, "error");
                }
            });
        }

        if (submitDepositButton) {
            submitDepositButton.addEventListener('click', async () => {
                if (!currentUserData) return;
                const amount = parseFloat(depositAmountInput.value);
                const tid = depositTidInput.value.trim();

                if (isNaN(amount) || amount <= 0 || !tid) {
                    showUIMessage(depositMessage, "Please enter a valid amount and TID.", "error");
                    return;
                }
                const depositData = {
                    userId: currentUserData.uid,
                    username: currentUserData.username, 
                    amount: amount,
                    tid: tid,
                    timestamp: serverTimestamp,
                    status: "pending" 
                };
                try {
                    const newDepositRef = database.ref('depositRequests/' + currentUserData.uid).push();
                    await newDepositRef.set(depositData);
                    await database.ref('allDepositRequests').child(newDepositRef.key).set({...depositData, userSpecificPath: `depositRequests/${currentUserData.uid}/${newDepositRef.key}` });

                    let bonusSpins = 0;
                    if (amount >= 1000) bonusSpins = 11;
                    else if (amount >= 500) bonusSpins = 5;
                    else if (amount >= 200) bonusSpins = 2;

                    if (bonusSpins > 0) {
                        const newAvailableSpins = (currentUserData.availableSpins || 0) + bonusSpins;
                        await database.ref('users/' + currentUserData.uid).update({ availableSpins: newAvailableSpins });
                        currentUserData.availableSpins = newAvailableSpins; 
                        if (document.getElementById('spinWinScreen').classList.contains('active')) {
                             updateSpinUI(); 
                        }
                        alert(`${bonusSpins} bonus spins added! Your deposit is under review.`);
                    } else {
                         alert("Your deposit is under review.");
                    }
                    showUIMessage(depositMessage, "Deposit request submitted! It will be reviewed.", "success");
                    depositAmountInput.value = '';
                    depositTidInput.value = '';
                } catch (error) {
                    console.error("Deposit submission error:", error);
                    showUIMessage(depositMessage, "Error submitting deposit request.", "error");
                }
            });
        }

        if (submitWithdrawalButton) {
            submitWithdrawalButton.addEventListener('click', async () => {
                if (!currentUserData) return;
                const method = withdrawMethodSelect.value;
                const accountName = withdrawAccountNameInput.value.trim();
                const accountNumber = withdrawAccountNumberInput.value.trim();
                const amount = parseInt(withdrawAmountInput.value);

                if (!accountName || !accountNumber || isNaN(amount) || amount <= 0) {
                    showUIMessage(withdrawalMessage, "Please fill all fields with valid data.", "error");
                    return;
                }
                if (amount < 1000) { 
                    showUIMessage(withdrawalMessage, "Minimum withdrawal amount is 1000 coins.", "error");
                    return;
                }
                if (amount > currentUserData.balance) {
                    showUIMessage(withdrawalMessage, "Insufficient balance for this withdrawal.", "error");
                    return;
                }
                const withdrawalData = {
                    userId: currentUserData.uid,
                    username: currentUserData.username, 
                    method: method,
                    accountName: accountName,
                    accountNumber: accountNumber,
                    amount: amount,
                    timestamp: serverTimestamp,
                    status: "pending" 
                };
                try {
                    const newWithdrawalRef = database.ref('withdrawalRequests/' + currentUserData.uid).push();
                    await newWithdrawalRef.set(withdrawalData);
                    await database.ref('allWithdrawalRequests').child(newWithdrawalRef.key).set({...withdrawalData, userSpecificPath: `withdrawalRequests/${currentUserData.uid}/${newWithdrawalRef.key}`});

                    showUIMessage(withdrawalMessage, "Withdrawal request submitted! It will be processed.", "success");
                    withdrawAccountNameInput.value = '';
                    withdrawAccountNumberInput.value = '';
                    withdrawAmountInput.value = '';
                } catch (error) {
                    console.error("Withdrawal submission error:", error);
                    showUIMessage(withdrawalMessage, "Error submitting withdrawal request.", "error");
                }
            });
        }

        async function loadDepositHistory() {
            if (!currentUserData || !depositHistoryList) {
                if (depositHistoryList) depositHistoryList.innerHTML = "<p>Please login to see history.</p>";
                return;
            }
            depositHistoryList.innerHTML = "<p style='text-align:center;'>Loading history...</p>";
            try {
                const snapshot = await database.ref('depositRequests/' + currentUserData.uid)
                                           .orderByChild('timestamp')
                                           .limitToLast(20) 
                                           .once('value');
                if (snapshot.exists()) {
                    let html = '';
                    const requests = [];
                    snapshot.forEach(childSnapshot => { 
                        requests.push({ id: childSnapshot.key, ...childSnapshot.val() });
                    });
                    requests.reverse().forEach(req => { 
                        html += `
                            <div class="transaction-list-item">
                                <p><strong>Amount:</strong> ${req.amount} PKR</p>
                                <p><strong>TID:</strong> ${req.tid}</p>
                                <p><strong>Date:</strong> ${new Date(req.timestamp).toLocaleDateString()}</p>
                                <p><strong>Status:</strong> <span class="status ${req.status ? req.status.toLowerCase() : 'pending'}">${req.status || 'pending'}</span></p>
                            </div>
                        `;
                    });
                    depositHistoryList.innerHTML = html;
                } else {
                    depositHistoryList.innerHTML = "<p style='text-align:center;'>No deposit history found.</p>";
                }
            } catch (error) {
                console.error("Error loading deposit history:", error);
                depositHistoryList.innerHTML = "<p style='text-align:center;'>Error loading history.</p>";
            }
        }
        
        async function loadWithdrawalHistory() {
            if (!currentUserData || !withdrawalHistoryList) {
                if (withdrawalHistoryList) withdrawalHistoryList.innerHTML = "<p>Please login to see history.</p>";
                return;
            }
            withdrawalHistoryList.innerHTML = "<p style='text-align:center;'>Loading history...</p>";
            try {
                const snapshot = await database.ref('withdrawalRequests/' + currentUserData.uid)
                                           .orderByChild('timestamp')
                                           .limitToLast(20)
                                           .once('value');
                if (snapshot.exists()) {
                    let html = '';
                    const requests = [];
                    snapshot.forEach(childSnapshot => {
                         requests.push({ id: childSnapshot.key, ...childSnapshot.val() });
                    });
                    requests.reverse().forEach(req => {
                        html += `
                            <div class="transaction-list-item">
                                <p><strong>Amount:</strong> 🪙 ${req.amount.toLocaleString()}</p>
                                <p><strong>Method:</strong> ${req.method}</p>
                                <p><strong>Account:</strong> ${req.accountName} (${req.accountNumber})</p>
                                <p><strong>Date:</strong> ${new Date(req.timestamp).toLocaleDateString()}</p>
                                <p><strong>Status:</strong> <span class="status ${req.status ? req.status.toLowerCase() : 'pending'}">${req.status || 'pending'}</span></p>
                            </div>
                        `;
                    });
                    withdrawalHistoryList.innerHTML = html;
                } else {
                    withdrawalHistoryList.innerHTML = "<p style='text-align:center;'>No withdrawal history found.</p>";
                }
            } catch (error) {
                console.error("Error loading withdrawal history:", error);
                withdrawalHistoryList.innerHTML = "<p style='text-align:center;'>Error loading history.</p>";
            }
        }

        async function loadUpdatesData() {
            if (!updateListContainer) return;
            updateListContainer.innerHTML = "<p style='text-align:center;'>Loading updates...</p>";

            try {
                const updatesSnapshot = await database.ref('updates')
                                                  .orderByChild('timestamp') 
                                                  .limitToLast(20) 
                                                  .once('value');
                if (!updatesSnapshot.exists()) {
                    updateListContainer.innerHTML = "<p style='text-align:center;'>No updates available at the moment.</p>";
                    return;
                }

                const updates = [];
                updatesSnapshot.forEach(childSnapshot => {
                    updates.push({ id: childSnapshot.key, ...childSnapshot.val() });
                });
                updates.sort((a, b) => b.timestamp - a.timestamp); 

                let updatesHtml = '';
                updates.forEach(update => {
                    updatesHtml += `
                        <div class="update-item">
                            <div class="update-header">
                                <span class="update-title">${update.title || 'Update'}</span>
                                <span class="update-date">${new Date(update.timestamp).toLocaleDateString()}</span>
                            </div>
                            <p class="update-description">${(update.description || '').replace(/\n/g, '<br>')}</p>
                            ${update.version ? `<span class="update-version">Version: ${update.version}</span>` : ''}
                        </div>
                    `;
                });
                updateListContainer.innerHTML = updatesHtml || "<p style='text-align:center;'>No updates found.</p>";

            } catch (error) {
                console.error("Error loading updates:", error);
                updateListContainer.innerHTML = "<p style='text-align:center;'>Error loading updates. Please try again later.</p>";
            }
        }

        function initChat() {
            if (!currentUserData) {
                chatMessagesContainer.innerHTML = "<p style='text-align:center; color: var(--text-light);'>Please login to use chat.</p>";
                if(chatMessageInput) chatMessageInput.disabled = true;
                if(sendChatMessageButton) sendChatMessageButton.disabled = true;
                return;
            }
            if(chatMessageInput) chatMessageInput.disabled = false;
            if(sendChatMessageButton) sendChatMessageButton.disabled = false;
[[[]]]
            const placeholder = chatMessagesContainer.querySelector('p[style*="text-align:center"]');
             if (!chatListenerAttached || (placeholder && chatMessagesContainer.children.length === 1)) { // Only show "Loading..." if not already listening or if only placeholder is there
                 chatMessagesContainer.innerHTML = '<p style="text-align:center; color: var(--text-light);">Loading messages...</p>';
             }
            
            chatMessagesRef = database.ref('liveChatMessages');

            if (!chatListenerAttached) {
                chatMessagesRef.orderByChild('timestamp').limitToLast(50).on('child_added', (snapshot) => {
                    const messageData = snapshot.val();
                    if (messageData) {
                        const loadingPlaceholder = chatMessagesContainer.querySelector('p[style*="text-align:center"]');
                        if (loadingPlaceholder) { // Remove placeholder once first message arrives
                           loadingPlaceholder.remove();
                        }
                        displayChatMessage(messageData);
                    }
                }, (error) => {
                    console.error("Error attaching chat listener: ", error);
                    chatMessagesContainer.innerHTML = "<p style='text-align:center; color:red;'>Error loading chat.</p>";
                });
                chatListenerAttached = true;
                // Check if there are no messages initially after attaching listener
                chatMessagesRef.orderByChild('timestamp').limitToLast(1).once('value', snapshot => {
                    if (!snapshot.exists() && chatMessagesContainer.querySelector('p[style*="text-align:center"]')) { // If still showing loading/placeholder and no msgs
                         chatMessagesContainer.innerHTML = "<p style='text-align:center; color: var(--text-light);'>No messages yet. Be the first!</p>";
                    }
                });
            }
        }

        function detachChatListener() {
            if (chatMessagesRef && chatListenerAttached) {
                chatMessagesRef.off(); 
                chatListenerAttached = false;
                console.log("Chat listener detached.");
            }
        }

        function displayChatMessage(message) {
            if (!chatMessagesContainer || !currentUserData) return;

            const messageElement = document.createElement('div');
            messageElement.classList.add('chat-message');

            const textElement = document.createElement('p');
            textElement.classList.add('message-text-content');
            textElement.textContent = message.text; 
            
            const timeElement = document.createElement('span');
            timeElement.classList.add('message-time');
            timeElement.textContent = message.timestamp ? new Date(message.timestamp).toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' }) : '';


            if (message.userId === currentUserData.uid) {
                messageElement.classList.add('my-message');
            } else {
                messageElement.classList.add('other-message');
                const senderNameElement = document.createElement('span');
                senderNameElement.classList.add('sender-name');
                senderNameElement.textContent = message.username || "Anonymous";
                messageElement.appendChild(senderNameElement); 
            }
            
            messageElement.appendChild(textElement);
            messageElement.appendChild(timeElement);
            
            chatMessagesContainer.appendChild(messageElement);
            chatMessagesContainer.scrollTop = chatMessagesContainer.scrollHeight; // This ensures scroll to bottom
        }

        if (sendChatMessageButton) {
            sendChatMessageButton.addEventListener('click', sendChatMessage);
        }
        if (chatMessageInput) {
            chatMessageInput.addEventListener('keypress', (e) => {
                if (e.key === 'Enter' && !e.shiftKey) {
                    e.preventDefault(); 
                    sendChatMessage();
                }
            });
        }

        async function sendChatMessage() {
            if (!currentUserData || !chatMessageInput || !chatMessagesRef) {
                alert("You must be logged in to send messages.");
                return;
            }
            const messageText = chatMessageInput.value.trim();
            if (messageText === "") return;

            const messageData = {
                userId: currentUserData.uid,
                username: currentUserData.username,
                text: messageText,
                timestamp: serverTimestamp 
            };

            try {
                await chatMessagesRef.push(messageData);
                chatMessageInput.value = ""; 
            } catch (error) {
                console.error("Error sending chat message:", error);
                alert("Could not send message. Please try again.");
            }
        }

        document.addEventListener('DOMContentLoaded', () => {
            // Auth state change handles initial screen
        });

    </script>
</body>
</html> 

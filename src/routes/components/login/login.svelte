<script>
    let username = "";
    let password = "";
    let incorrectPassword = false; // Flag to track incorrect password
    let incorrectUsername = false;

    function handleKeyPress(event) {
        if (event.key === "Enter") {
            // Focus on the password input field
            if (event.target.id === "password") {
                handleSubmit();
            }
            document.getElementById("password").focus();
        }
    }

    function handleSubmit() {
        incorrectPassword = false;
        incorrectUsername = false;
        if (username.trim() === "" || password.trim() === "") {
            alert("Please fill in all fields.");
            return;
        }

        //todo add secure user authentication and session management
        if(username === "admin" && password === "admin") {
            updateProgress(0);
            setTimeout(() => {
                window.location.href = "./../dashboard";
            }, 500);
        } else if (username !== "1") {
            incorrectUsername = true; // Set flag to true if password is incorrect
        } else {
            incorrectPassword = true; // Set flag to true if password is incorrect
        }
    }

    let progressBarWidth = 0; // Initialize progress bar width

    // Function to update the progress bar
    function updateProgress(percent) {
        progressBarWidth = percent;

        if (percent < 100) {
            setTimeout(() => {
                updateProgress(percent + 1);
            }, 1);
        }
    }
</script>

<style>
    #progress-bar {
        position: fixed;
        top: 0;
        left: 0;
        height: 2px;
        z-index: 9999; /* moves the progressbar to the top of everything */
        background-color: #057AE2;
        box-shadow: 0 0 17px rgb(5, 122, 226);
    }
    .login-container {
        width: 350px;
        max-width: 500px;
        margin: 0 auto;
        padding: 20px;
        background-color: #333;
        color: #fff;
        border-radius: 8px;
        box-shadow: 0 0 10px rgba(47, 56, 70, 0.8);
    }

    .input-field {
        margin-bottom: 10px;
    }

    .input-field input {
        font-size: 16px;
        height: 40px;
        width: calc(100%);
        padding: 8px;
        border-radius: 5px;
        border: 2px solid transparent; /* Transparent border by default */
        background-color: #555;
        color: #fff;
    }

    .input-field input.incorrect {
        border-color: red; /* Red border when password is incorrect */
    }

    .submit-button {
        font-size: 16px;
        height: 40px;
        width: 100%;
        padding: 10px;
        border-radius: 5px;
        border: none;
        background-color: #007bff;
        color: #fff;
        cursor: pointer;
        transition: background-color 0.3s ease;
        box-shadow: 0 0 7px rgb(0, 123, 255);
    }

    .submit-button:hover {
        background-color: #0056b3;
        transition: background-color 0.3s ease;
    }
    .create-account {
        margin-top: 10px;
        font-size: 14px;
        text-align: center;
    }

    .create-account a {
        color: #007bff;
        text-decoration: none;
    }

    .create-account a:hover {
        text-decoration: underline;
    }

    .error-message {
        color: red;
        margin-top: 5px;
        font-size: 14px;
    }
</style>

<div id="progress-bar" style="width: {progressBarWidth}%"></div>
<div class="login-container">
    <div class="input-field">
        <!-- todo add secure user authentication and session management -->
        <input type="text" placeholder="Username" id="username" bind:value={username} class:incorrect={incorrectUsername} on:keydown={handleKeyPress}>
        {#if incorrectUsername}
            <div class="error-message">Incorrect Username</div>
        {/if}
    </div>
    <div class="input-field">
        <input type="password" id="password" placeholder="Password" bind:value={password} class:incorrect={incorrectPassword} on:keydown={handleKeyPress}>
        {#if incorrectPassword}
            <div class="error-message">Incorrect Password</div>
        {/if}
    </div>
    <button class="submit-button" id="submit" on:click={handleSubmit}>Login</button>
    <div class="create-account">
        <span><a href="https://placeholder/">Forgot Password?</a></span>
    </div>
</div>
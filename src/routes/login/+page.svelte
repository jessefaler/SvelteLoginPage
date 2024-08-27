<script>
    import Login from "./../components/login/login.svelte";
    import logo from "./../content/logo.svg";
    import logo_text from "./../content/logo_text.webp";
    import Logo_SVG from "./../content/logoSVG.svelte";
    import Logo_Text_SVG from "./../content/logoTextSVG.svelte";
</script>

<style>
    body {
        background-color: #1a1a1a; /* Dark background color */
        color: #fff; /* Text color */
        font-family: Arial, sans-serif;
        margin: 0;
        padding: 0;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        position: relative; /* Ensure relative positioning for z-index */
    }

    .container {
        width: 390px;
        position: relative; /* Ensure relative positioning for z-index */
        z-index: 1; /* Increase z-index */
        background-color: #232323; /* White background color for container */
        padding: 20px;
        border-radius: 10px;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); /* Box shadow for container */
        text-align: center;
    }

    .logo-container {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .logo {
        width: 100px;
        height: auto;
        padding: 0;
    }

    .logo-text {
        width: 200px; /* Adjust width as needed */
        height: auto;
        padding: 0;
    }

    .text {
        padding: 8px;
        font-size: 14px;
        font-weight: bold;
    }

    .footer {
        position: fixed;
        left: 0;
        bottom: 0;
        width: 100%;
        text-align: center;
        padding: 10px;
        color: gray;
        font-size: 11px;
        font-weight: bold;
    }
</style>

<head>
    <title>Login</title>
    <link rel="preload" href="./../components/login/login.svelte" as="script">
    <link rel="preload" href="./../content/logo.svg" as="image">
    <link rel="preload" href="./../jh/logo_text.webp" as="image">
</head>
<body>
<div class="container">
    <div class="logo-container">
        <Logo_SVG/>
        <Logo_Text_SVG/>
    </div>
    <p class="text">ADMIN LOGIN</p>
    <Login/>
</div>
<div class="footer">
    SLIMELABS.NET © 2024 | VERSION: 1.0.0 | DEVELOPED BY: PROTOXON
</div>
</body>
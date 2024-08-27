<script>
    import "../../app.css";
    import Logo_SVG from "./../content/logoSVG.svelte";

    function redirectToLogin() {
        window.location.href = '/login'; // Replace 'login.html' with your login page URL
    }

    function redirectToWitherpanel() {
        window.location.href = '/dashboard/witherpanel'; // Replace 'login.html' with your login page URL
    }
</script>

<style>
    .sidebar {
        position: fixed; /* Add this line */
        top: 0; /* Add this line */
        left: 0; /* Add this line */
        width: 200px;
        height: 100vh;
        background-color: #232323;
        padding: 10px;
        box-shadow: 0 4px 8px rgb(35, 35, 35); /* Box shadow for container */
    }

    .sidebar-item {
        padding: 10px;
        cursor: pointer;
    }
    .divider {
        border: 0;
        height: 1px;
        background: #8a8585;
        margin: 20px 0;
        box-shadow: 0 4px 8px rgb(166, 159, 159, 0.7);
    }
    .sidebar-item:hover {
        background-color: rgb(45, 45, 45);
    }
</style>

<body>
<div>
    <slot />
</div>
<div class="sidebar">
    <div>
        <Logo_SVG width="50px"/>
    </div>
    <hr class="divider" />
    <div class="sidebar-item">Dashboard</div>
    <div class="sidebar-item">Users</div>
    <div class="sidebar-item">Settings</div>
    <button class="sidebar-item" style="width: 165px; text-align: left;" on:click={redirectToWitherpanel}>Witherpanel</button>
    <button class="sidebar-item" style="bottom: 20px; cursor: pointer; width: 165px; text-align: left;" on:click={redirectToLogin}>Logout</button>
</div>
</body>
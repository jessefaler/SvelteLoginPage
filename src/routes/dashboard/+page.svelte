<script>
    import PlayerInfo from "./../components/table/playerInfo.svelte";
    import logo from "../content/logo.webp";
    import logo_text from "../content/logo_text.webp";
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
    <title>Dashboard</title>
</head>
<body>
<div>
    <div class="player-info-container">
        <PlayerInfo />
    </div>
</div>
<div class="footer">
    SLIMELABS.NET © 2024 | VERSION: 1.0.0 | DEVELOPED BY: PROTOXON
</div>
</body>
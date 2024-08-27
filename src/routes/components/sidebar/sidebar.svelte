<script>
</script>

<style>
    .container {
        display: flex;
    }

    .sidebar {
        display: flex;
        flex-direction: column;
        width: 200px;
    }

    .flex-item {
        margin: 20px;
        background-color: black;
    }

    .hello {
        background-color: black;
    }
</style>

<body>
<div class="container">
    <div class="sidebar">
        <div class="flex-item">Home</div>
        <div class="flex-item">About</div>
        <div class="flex-item">Contact</div>
    </div>
    <div>
        <h1 class="hello">hello</h1>
    </div>
</div>
</body>
<template>
    <div id="AppHeader">
        <div class="logo">
            <img src="../assets/logo.png" alt="Logo">
        </div>
        <div class="title">
            Abituriyent yordamchisi
        </div>
        <div class="menu">
            <div class="menu_title"><a href="">Hisoblash</a></div>
            <div class="menu_title"><a href="">Natijalar</a></div>
            <div class="menu_title"><a href="">About</a></div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Header'
    }
</script>

<style scoped>
    #AppHeader {
        display: flex;
        flex-direction: row;
        align-items: center;
        background: #B8FFBE;
        border-bottom: 4px solid rgba(29, 161, 235, 0.8);
        box-shadow: 0 4px 4px rgba(0, 0, 0, 0.25);
        transform: rotate(-0.12deg);
        width: 100%;
    }

    .logo {
        width: 33%;
    }

    .logo img {
        height: 108px;
        margin-left: 120px;
    }

    div.title {
        width: 33%;
        font-size: 30px;
        font-weight: bold;
        color: #000000;
        margin-left: 80px;
    }

    div.menu {
        display: flex;
        justify-content: space-around;
        width: 33%;
        padding-right: 50px;
        text-transform: uppercase;
    }

    .menu a {
        color: #777777;
        text-decoration: none;
        font-weight: bold;
    }
</style>

<template>
    <div id="app">
        <Header />
        <div id="nav">
            <router-link to="/">Home</router-link> |
            <router-link to="/about">About</router-link>
        </div>
        <router-view />
        <footer class="footer">
            <Footer footnote="This is a trial ToDo app" year="© 2020" />
        </footer>

    </div>
</template>

<script>
    import Header from "./components/layout/Header";
    import Footer from './components/layout/Footer';

    export default {
        name: "App",
        components: {
            Header: Header,
            Footer: Footer,
        }
    }
</script>

<style>
    html, body, #app {
        height: 100%;
    }
    
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        display: flex;
        flex-direction: column;
    }

    #nav {
        padding: 30px;
    }

    #nav a {
        font-weight: bold;
        color: #2c3e50;
    }

    #nav a.router-link-exact-active {
        color: #42b983;
    }
    .footer {
        flex-shrink: 0;  
    }
</style>

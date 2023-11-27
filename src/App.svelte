<style lang="scss" global>
@import "./styles/globals.scss";
</style>

<script>
import Router from "svelte-spa-router"
import Projects from "./routes/Projects.svelte"
import Home from "./routes/Home.svelte"
import NotFound from "./routes/NotFound.svelte"
import NavBar from "./components/NavBar.svelte"
import Footer from "./components/Footer.svelte"
import Contact from "./routes/Contact.svelte"

let routes = {
    "/": Home,
    "/projects": Projects,
    "/contact": Contact,

    "*": NotFound,
}
</script>

<main>
    <Router routes="{routes}" />
    <Footer />
</main>

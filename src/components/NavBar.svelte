<style lang="scss" global>
@import "../styles/style.scss";
@import "../styles/globals.scss";
@import "../styles/NavBar.scss";

.active {
    text-decoration: underline;
    color: aqua;
}
</style>

<script>
import {Link} from "svelte-navigator"
import Button from "../components/Theme.svelte"

import gsap from "gsap"

import {onMount} from "svelte"

onMount(() => {
    const tl = gsap.timeline()

    gsap.from(".nav", {
        delay: 0.7,
        y: -16,
        opacity: 0,
        duration: 1,
        ease: "power3.inOut",
    })
})
function scrollToTop() {
    window.scrollTo({
        top: 0,
        left: 1000,
        behavior: "smooth",
    })
}
</script>

<nav class="nav container">
    <div class="nav__logo">
        <Link to="/" on:click="{scrollToTop}">
            <span class="nav__logo--menu">GHOFRANE.</span>
        </Link>
    </div>
    <div class="nav__list  ">
        <ul class="nav__list--ul  ">
            <!-- <Link to='/' on:click={scrollToTop} >
         <li  >
            <a >About</a>
          
          </li>
        </Link> -->

            <!-- <Link to="/projects" on:click="{scrollToTop}">
                <li>
                    <a>Projects</a>
                </li>
            </Link> -->
        </ul>
    </div>
    <div class="nav__theme ">
        <Button />
    </div>
    <div class="menu hide-for-desktop hide-for-mobile">
        <span></span>
        <span></span>
    </div>
</nav>

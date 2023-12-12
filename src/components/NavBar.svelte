<style lang="scss" global>
@import "../styles/globals.scss";
@import "../styles/NavBar.scss";

:global(body) .menu span {
    background-color: rgb(255, 255, 255);
}

:global(body.dark-mode) .menu span {
    background-color: rgb(0, 0, 0);
}
:global(body) .blacklogo {
    display: none;
}
:global(body.dark-mode) .blacklogo {
    display: block;
}
:global(body) .whitelogo {
    display: block;
}
:global(body.dark-mode) .whitelogo {
    display: none;
}
.active {
    text-decoration: underline;
    color: aqua;
}
a {
    overflow: hidden;
}
</style>

<script>
import Button from "../components/Theme.svelte"
import gsap from "gsap"

import {onMount} from "svelte"
import SplitText from "./SplitText.svelte"
import SocialMediaAccounts from "./SocialMediaAccounts.svelte"

onMount(() => {
    const tl = gsap.timeline()

    tl.from([".nav ", ".slideUp"], {
        delay: 0.5,
        y: -16,
        opacity: 0,
        duration: 1,
        ease: "power3.inOut",
    })
})
let isMenuOpen = false

function toggleMenu() {
    isMenuOpen = !isMenuOpen
    window.scrollTo({
        top: 0,
        left: 1000,
        behavior: "smooth",
    })
}
function scrollTop() {
    window.scrollTo({
        top: 0,
        left: 1000,
        behavior: "smooth",
    })
}
</script>

<div class="nav__bg">
    <nav class="nav container">
        <div class="nav__logo">
            <a href="/#/" on:click="{scrollTop}">
                <img src="/assets/SVG/logoarbw.svg" alt="logo white" class="whitelogo" />
                <img src="/assets/SVG/logoarbb.svg" alt="logo black" class="blacklogo" />

            </a>
        </div>

        <div class="nav__theme ">
            <Button />
        </div>
        <div
            class="{`menu hide-for-desktop hide-for-mobile ${isMenuOpen ? 'isopen ' : ''} `}"
            on:click="{toggleMenu}"
        >
            <span></span>
            <span></span>
        </div>
    </nav>
</div>
<div class="{`list ${isMenuOpen ? 'isopen ' : ''} `}">
    <div class=" ">
        <ul class="list__ul">
            <li class="{` ${isMenuOpen ? 'isopen slideUp' : ''} `}">
                <a class="alink" href="/#/" on:click="{toggleMenu}">Home</a>
            </li>
            <li class="{` ${isMenuOpen ? 'isopen slideUp' : ''} `}">
                <a class="alink" href="/#/projects" on:click="{toggleMenu}">My Work </a>
            </li>
            <li class="{` ${isMenuOpen ? 'isopen slideUp' : ''} `}">
                <a class="alink" href="/#/contact" on:click="{toggleMenu}"> Contact </a>
            </li>
            <li class="{` ${isMenuOpen ? 'isopen slideUp' : ''} `}">
                <SocialMediaAccounts/></li>
           
        </ul>
    </div>
</div>

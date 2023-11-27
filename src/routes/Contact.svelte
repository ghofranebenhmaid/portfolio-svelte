<style lang="scss" global>
@import "../styles/globals.scss";
@import "../styles/Home.scss";

.container-900 {
    height: 100vh;
    flex-direction: column;
}

:global(body) svg {
    fill: rgb(255, 255, 255);
}
:global(body.dark-mode) svg {
    fill: rgb(0, 0, 0);
}

:global(body) h2 {
    color: rgb(255, 255, 255);
}
:global(body.dark-mode) h2 {
    color: rgb(0, 0, 0);
}
h2 {
    font-size: var(--step-3);
    margin-bottom: var(--space-3xs);
}
p {
    font-size: var(--step-0);
    line-height: var(--space-m);
}
img {
    width: 450px;
    /* max-width: 100%; */
    height: 600px;
    @media (max-width: 799px) {
        width: 100%;
        display: none;
    }
}
.container {
    min-height: calc(100vh - 267.09px);
}
.flexi {
    display: flex;
    flex-direction: row;
    align-items: center;
    gap: 3.5rem;
    @media (max-width: 799px) {
        flex-wrap: wrap;
    }
}
</style>

<script>
let ImageProfile = "../assets/image/bg-profile.jpg"
import gsap from "gsap"

import {onMount} from "svelte"
import NavBar from "../components/NavBar.svelte"

onMount(() => {
    gsap.from(".contact-bg", {
        duration: 1,
        scale: 1.1,
        width: 0,
        skewX: 2,
        ease: "power3.inOut",
        stagger: {
            amount: 0.3,
        },
    })
    gsap.from(".content", {
        delay: 1,
        y: 40,
        duration: 0.4,
        opacity: 0,
        ease: "power3.out",
    })
})
</script>

<NavBar />

<article class="container flexi  ">
    <figure>
        <img class="contact-bg" src="{ImageProfile} " alt="banner bg" />
    </figure>
    <section class="content ">
        <h2>Get in touch</h2>
        <p class="">
            Thank you for taking the time to explore my portfolio. If you have any questions, need
            further information, or would like to discuss potential projects or job opportunities,
            please don't hesitate to get in touch.<br /> I am always open to new challenges and
            opportunities. You can reach me via email at
            <a href="mailto:me@ghofranebenhmaid.com" target="_blank">
                <samp class="samp"> me@ghofranebenhmaid.com</samp>
            </a>. <br /> I look forward to hearing from you and will respond as soon as possible.
        </p>
    </section>
</article>

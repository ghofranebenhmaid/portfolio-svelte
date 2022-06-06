<style lang="scss" global>
@import "../styles/Home.scss";
@import "../styles/globals.scss";
</style>

<script>
import {Link} from "svelte-navigator"
import NavBar from "../components/NavBar.svelte"
import SocialMediaAccounts from "../components/SocialMediaAccounts.svelte"
import Footer from "../components/Footer.svelte"
import Accordion from "../components/AccordionList.svelte"
import Projects from "./projects.svelte"

let ImageProfile = "../../assets/image/bg-profile.jpg"

import gsap from "gsap"

import {onMount} from "svelte"
onMount(() => {
    const tl = gsap.timeline()

    gsap.from([".banner-addition-bg", ".banner-bg", ".banner-bg2"], {
        duration: 1,
        width: 0,
        skewX: 2,
        ease: "power3.inOut",
        stagger: {
            amount: 0.2,
        },
    })
    gsap.from(".hero__social", {
        delay: 2.3,
        x: 10,
        duration: 0.5,
        opacity: 0,
        ease: "power3.out",
    })
    gsap.from([p, h1], {
        opacity: 0,
        y: 40,
        duration: 0.6,
        ease: "powe3.out",
        stagger: {
            amount: 0.2,
        },
    })
    gsap.from(p, {
        delay: -0.4,
        opacity: 0,
        y: 40,
        duration: 0.6,
        ease: "power3.out",
        stagger: {
            amount: 0.4,
        },
    })
})
</script>

<NavBar />
<div class="hero" id="hero">
    <div class="hero__image">
        <div id="bannerBgAddition" class="banner-addition-bg"></div>
        <div id="bannerBg" class="banner-bg"></div>

        <img id="bannerBg2" class="banner-bg2" src="{ImageProfile} " />
        <div class="hero__social">
            <SocialMediaAccounts />
        </div>
    </div>
</div>
<div class="container">
    <h1 class="title">Hello!</h1>
    <p>
        I’m a skilled and diligent frontend developer with a passion for React and a flair for user
        interface design. I have experience with different programming languages and technologies,
        including HTML, CSS, JavaScript, Node.js, Express.js, React, MySQL, Knex.js and
        Git/Bitbucket (Version control) as well as WordPress. I’m also very skilled in using Adobe
        design programs, such as Photoshop, Illustrator, InDesign, Lightroom, Premiere Pro, After
        Effects and 3Ds max.
    </p>

    <p>
        I’m educated in IT & Multimedia, and have completed the HackYourFuture web-development
        education program, and have achieved a lot of learning-by-doing through the years.
    </p>

    <p>
        I have a broad skillset beside web-development including graphic design, user interface
        design, typography, photo and video editing. In my spare time I also enjoy photography and
        exploring the city and the nature.
    </p>

    <h1 class="title">Skills!</h1>
    <Accordion />
    <h1 class="title">Projects!</h1>
    <Projects />
    <p>
        Currently I am working at
        <a href=" https://kglakademi.dk/" target="_blank">
            <samp class="samp"> The Royal Danish Academy (KADK)</samp>
        </a>
    </p>

    <p>
        If you have a project that you'd like to work together on, please don't hesitate to get in
        touch
        <a href="mailto:me@ghofranebenhmaid.com" target="_blank">
            <samp class="samp"> me@ghofranebenhmaid.com</samp>
        </a>
    </p>
</div>

<Footer />

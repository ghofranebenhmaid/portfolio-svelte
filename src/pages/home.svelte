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
import Slider from "./slider.svelte"

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
    gsap.fromTo(
        ".svg",
        {
            opacity: 1,
            scale: 0,

            transformOrigin: "50%",
        },

        {
            opacity: 1,
            scale: 1,
            duration: 1,

            // ease: "power2.out",
        },
    )
    gsap.fromTo(
        ".svg",
        {
            rotation: 0,
        },
        {
            rotation: -360,
            duration: 15,
            repeat: -1,

            // ease: "elastic.out",
            ease: "linear",

            // ease: "power1.out",
            // ease: "Power2.easeOut",
        },
    )

    // gsap.fromTo(".svg", {timeScale: 1.5}, {timeScale: 1.4, duration: 2.4})
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

        <a href="#0" onclick="window.open('../../assets/CV_GhofraneBenHmaid.pdf');">
            <svg class="svg" viewBox="0 0 100 100" width="100" height="100">
                <defs>
                    <path
                        id="circle"
                        d="
                    M 50, 50
                    m -37, 0
                    a 37,37 0 1,1 74,0
                    a 37,37 0 1,1 -74,0"></path>
                </defs>
                <text class="svg" font-size="12">
                    <textPath class="svg" xlink:href="#circle">
                        click here to see my resume ..
                    </textPath>
                </text>
            </svg>
        </a>
    </div>
</div>
<div class="container">
    <h1 class="title">Hello!</h1>
    <p>
        I’m a skilled and diligent frontend developer with a passion for React and a flair for user
        interface design. I have experience with different programming languages and technologies,
        including HTML5, CSS3, Bootstrap, SASS, JavaScript, Git, React/Nextjs, Node.js, Express.js,
        MySQL and Git (Version control) as well as WordPress. I’m also very skilled in using Adobe
        design programs, such as Photoshop, Illustrator, InDesign, Lightroom, Premiere Pro, After
        Effects and 3Ds max.
    </p>

    <p>
        I’m educated in computer science and multimedia, and have completed a full-stack web
        development Bootcamp in Hack Your Future education program, and have achieved a lot of
        learning-by-doing through the years.
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
    <!-- <Slider /> -->

    <p>
        I've been working at
        <a href=" https://kglakademi.dk/" target="_blank">
            <samp class="samp"> The Royal Danish Academy (KADK)</samp>
        </a>
        as a Frontend developer using Reactjs, NodeJS, AWS, animatione Lottie, Git and Docker on a project
        called Facegarden, which is a browser game controlled with facial expressions. It is built for
        people who suffer from facial paralysis and would benefit from exercise of their facial muscles.
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

<style lang="scss" global>
@import "../styles/globals.scss";
@import "../styles/Home.scss";

:global(body) h2,
h3,
h1 {
    color: rgb(255, 255, 255);
}

:global(body.dark-mode) h2,
h3,
h1 {
    color: rgb(0, 0, 0);
}
:global(body) h3 {
    color: rgb(255, 255, 255);
}

.paragraph {
    z-index: -2;
}

h2 {
    font-size: var(--step-1);
    margin-bottom: var(--space-m);
    overflow: hidden;
}
h3 {
    font-size: var(--step-1);
    margin-bottom: var(--space-xs);
    overflow: hidden;
}
p {
    font-size: var(--step-0);
    line-height: var(--space-m);
    margin-bottom: var(--space-m);
}

:global(body.dark-mode) .technologi p {
    border: 1px solid rgb(0, 0, 0);
}
:global(body.dark-mode) .card__content {
    background-color: #000;
}
:global(body.dark-mode) .card {
    &__title,
    &__subtitle {
        color: #fff;
    }
    &__email {
        background-color: #fff;
        color: #000;
        padding: 1rem 2rem;
        border-radius: 50px;
    }
}
:global(body) .card__content {
    background-color: #fff;
}
:global(body) .card {
    &__title,
    &__subtitle {
        color: #000;
    }
    &__email {
        background-color: #000;
        color: #fff;
        padding: 1rem 2rem;
        border-radius: 50px;
        &:hover {
            transform: scale(1.1);
        }
    }
}
.primary-button {
    margin-top: var(--space-xl);
}
</style>

<script>
import Accordion from "../components/AccordionList.svelte"

let ImageProfile = "../assets/image/bg-profile.jpg"

import {GsapHomeAnimation} from "../components/GsapHomeAnimation.svelte"
import {GsapAnimation} from "../components/GsapAnimations.svelte"
import {onMount} from "svelte"

import {fade, scale} from "svelte/transition"
import {tweened} from "svelte/motion"
import {cubicOut} from "svelte/easing"
import Header from "../components/header/Header.svelte"
import SplitText from "../components/SplitText.svelte"

const carouselPhotos = [
    "/assets/web/a6.jpg",
    "/assets/web/a5.jpg",
    "/assets/web/a4.jpg",
    "/assets/web/a3.png",
    "/assets/web/a2.png",
]
const carouselPhotos1 = [
    "/assets/web/b1.png",
    "/assets/web/b2.png",
    "/assets/web/b3.png",
    "/assets/web/b4.png",
    "/assets/web/b5.png",
]
let index = 0
const duration = 1300
const opacity = tweened(1, {duration, easing: cubicOut})

const next = () => {
    index = (index + 1) % carouselPhotos.length
    opacity.set(0).then(() => {
        opacity.set(1)
    })
}

setInterval(next, duration)

onMount(() => {
    GsapHomeAnimation()
    GsapAnimation()
})
</script>

<!-- <svelte:window bind:scrollY="{y}" /> -->

<div class="gradient"></div>
<Header />
<!-- <div class="hero container" id="hero">
    <div class="hero__image ">
        <div id="bannerBgAddition" class="banner-addition-bg"></div>
        <div id="bannerBg" class="banner-bg"></div>

        <img id="bannerBg2" class="banner-bg2 " src="{ImageProfile} " alt="banner bg" />
    </div>
</div> -->

<article class="container-900 ">
    <SplitText><h2 class="">About me</h2></SplitText>
    <p class="wrap">
        I’m a skilled and diligent frontend developer with a passion for React and a flair for user
        interface design. I have experience with different programming languages and technologies,
        including HTML5, CSS3, Bootstrap, SASS, JavaScript, Git, React/Nextjs, Node.js, Express.js,
        MySQL and Git (Version control) as well as WordPress. I’m also very skilled in using Adobe
        design programs, such as Photoshop, Illustrator, InDesign, Lightroom, Premiere Pro, After
        Effects and 3Ds max.
    </p>

    <p class="wrap">
        I’m educated in computer science and multimedia, and have completed a full-stack web
        development Bootcamp in Hack Your Future education program, and have achieved a lot of
        learning-by-doing through the years.
    </p>

    <p class="wrap">
        I have a broad skillset beside web-development including graphic design, user interface
        design, typography, photo and video editing. In my spare time I also enjoy photography and
        exploring the city and the nature.
    </p>
</article>
<article class="container-900 m-top">
    <SplitText><h2 class="">Tech Stack</h2></SplitText>

    <Accordion />
</article>

<article class="container m-top fadein">
    <section class="project">
        <div class="project__content">
            <div class="project__content--description fadein ">
                <SplitText><h3>Face Garden</h3></SplitText>
                <p>
                    Face Garden combines machine learning and motion graphics to create three games
                    that react to facial expressions. Face Garden demonstrates novel interactions
                    between facial expressions and visual stimuli. The project is a proof of concept
                    for types of digital interactions that can be used to stimulate muscular
                    movements.
                    <a href="https://facegarden.dk/" target="_blank"
                        ><samp class="samp">facegarden.dk</samp></a
                    >
                </p>
                <div class="technologi">
                    <p>Reactjs/Sveltejs</p>
                    <p>UI/UX Design</p>
                    <p>AWS</p>
                    <p>LottieFiles</p>
                </div>
            </div>
            <div class="project1__content--image fadein">
                <div class="project1__content--image-relative slider fadein ">
                    {#each [carouselPhotos1[index]] as src (index)}
                        <img
                            src="{src}"
                            alt="Treasure Hunt game"
                            in:fade="{{duration: duration / 2}}"
                            out:fade="{{duration: duration / 2}}"
                        />
                    {/each}
                </div>
            </div>
        </div>
    </section>
</article>

<article class="container m-top fadein">
    <section class="project">
        <div class="project__content">
            <div class="project__content--description fadein">
                <SplitText><h3 class="">Treasure Hunt game</h3></SplitText>
                <p class="">
                    Treasure hunt game for kids parties, where an adult (host) can create a game for
                    the kids, with a theme. The host can create posts, and questions. The kids have
                    to find the posts and answer the questions.
                </p>
                <div class="technologi">
                    <p>Reactjs</p>
                    <p>UI/UX Design</p>
                    <p>Figma</p>
                    <p>Mongodb</p>
                </div>
            </div>
            <div class="project__content--image fadein">
                <div class="project__content--image-relative slider fadein ">
                    {#each [carouselPhotos[index]] as src (index)}
                        <img
                            src="{src}"
                            alt="Treasure Hunt game"
                            in:fade="{{duration: duration / 2}}"
                            out:fade="{{duration: duration / 2}}"
                        />
                    {/each}
                </div>
            </div>
        </div>
    </section>

    <div class=" flex flex-jc-c flex-ai-c ">
        <a data-sveltekit-reload href="/#/projects">
            <button class="primary-button"> See More</button>
        </a>
    </div>
</article>

<article class=" container-900 m-top">
    <p class="wrap">
        I've been working at
        <a href=" https://kglakademi.dk/" target="_blank">
            <samp class="samp"> The Royal Danish Academy (KADK)</samp>
        </a>
        as a Frontend developer using Reactjs, NodeJS, AWS, animatione Lottie, Git and Docker on a project
        called Facegarden, which is a browser game controlled with facial expressions. It is built for
        people who suffer from facial paralysis and would benefit from exercise of their facial muscles.
    </p>

    <!-- <p class="wrap">
        If you have a project that you'd like to work together on, please don't hesitate to get in
        touch
        <a href="mailto:me@ghofranebenhmaid.com" target="_blank">
            <samp class="samp"> me@ghofranebenhmaid.com</samp>
        </a>
    </p> -->
</article>

<article class="card container m-top fadein">
    <div class="card__content ">
        <h2 class="card__title">Let's build your idea.</h2>
        <p class="card__subtitle">
            If you have a project that you'd like to work together on, don't hesitate to get in
            touch.
        </p>
        <a href="mailto:me@ghofranebenhmaid.com" target="_blank">
            <samp class="samp card__email"> me@ghofranebenhmaid.com</samp>
        </a>
    </div>
</article>

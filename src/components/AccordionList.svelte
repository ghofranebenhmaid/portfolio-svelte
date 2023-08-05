<style lang="scss" global>
@import "../styles/globals.scss";
@import "../styles/Accordion.scss";

:global(body) h3 {
    color: rgb(255, 255, 255);
}
:global(body.dark-mode) h3 {
    color: rgb(0, 0, 0);
}

:global(body) svg {
    fill: rgb(255, 255, 255);
}
:global(body.dark-mode) svg {
    fill: rgb(0, 0, 0);
}
.isActive {
    transform: rotate(90deg);
    transition: all 0.7s cubic-bezier(0.645, 0.045, 0, 1);
}
p {
    font-size: var(--step-0);
    line-height: var(--space-m);
}
</style>

<script>
import {slide} from "svelte/transition"
import Accordion from "./Accordion.svelte"

let sections = [
    {
        id: 1,
        title: "HTML5",
        discreption: ["Semantic HTML5", "Forms", "Markdown", "HTML Attributes"],
        active: false,
    },
    {
        id: 2,
        title: "CSS3",
        discreption: [
            "BEM",
            "SASS",
            "styled-components",
            "Sass Module System",
            "Responsive Web Design",
            "Flex and Grid",
            "Animations, variables",
        ],
        active: false,
    },
    {
        id: 3,
        title: "JavaScript",
        discreption: [
            "JavaScript ES6 + features",
            "JS: Local storage",
            "Loops, functions, class",
            "Fetch API",
            "Arrays, objects",
        ],
        active: false,
    },
    {
        id: 4,
        title: "React.js / Next.js / Svelte.js",
        discreption: [
            "React Hooks",
            "React router",
            "REST API",
            "Styling components",
            "Component life cycle (hooks)",
            "Formik",
            "Building the interface",
            "Design tools and form handling",
            "Solving the most common problems with React",
        ],
        active: false,
    },
    // {
    //     id: 5,
    //     title: "Next.js",
    //     discreption: ["SSR"],
    //     active: false,
    // },
    {
        id: 6,
        title: "Animation",
        discreption: [
            "GSAP",
            "Lottie (JSON)",
            "@keyframes ",
            "Css transitions",
            "Adobe After Effects (Lottie)",
        ],
        active: false,
    },
    {
        id: 7,
        title: "Software",
        discreption: [
            "VS Code",
            "Figma",
            "Adobe After Effects",
            "Adobe Illustrator",
            "Adobe Photochop",
            "Adobe XD",
            "Adobe InDesign",
            "Maya Software",
            "3Ds Max",
            "Unity",
        ],
        active: false,
    },
    {
        id: 8,

        title: "Version Control",
        discreption: ["Git"],
        active: false,
    },
    {
        id: 9,
        title: "Design",
        discreption: ["Logos", "Typography", "Web Design", "Graphic Design"],
        active: false,
    },
    {
        id: 10,
        title: "UPCOMING",
        discreption: ["Typescript", "Vue.js"],
        active: false,
    },
]
let isOpen = true

import {onMount} from "svelte"
import {GsapAnimation} from "./GsapAnimations.svelte"

onMount(() => {
    GsapAnimation()
})
</script>

<div class=" wrapper">
    <div class="disc">
        <p class="paragraf fadein">
            Passionate about creating visually stunning and user-friendly web experiences.
            Proficient in frontend technologies. Strong problem-solving skills and attention to
            detail.
        </p>
    </div>
    <div>
        {#each sections as section}
            <div class="accordion">
                <Accordion>
                    <div class="wrap" slot="header" let:toggle on:click="{toggle}">
                        <p>{section.title}</p>
                        <p class="{!isOpen ? ' ' : ' isActive'}">
                            <svg
                                xmlns="http://www.w3.org/2000/svg"
                                width="20"
                                height="20"
                                viewBox="0 0 30 30"
                                fill="currentColor"
                                stroke="currentColor"
                                ><path
                                    d="M1 15C0.447716 15 0 15.4477 0 16C0 16.5523 0.447716 17 1 17H24.254C22.9563 17.7179 21.7537 18.6189 20.6863 19.6863C17.9222 22.4504 16.2738 26.1218 16.0312 30.0005C15.9967 30.5517 16.4477 31 17 31C17.5523 31 17.9963 30.5517 18.0357 30.0008C18.2751 26.653 19.7115 23.4895 22.1005 21.1005C24.4895 18.7115 27.653 17.2751 31.0008 17.0357C31.5517 16.9963 32 16.5523 32 16C32 15.4477 31.5517 15.0037 31.0008 14.9643C27.653 14.7249 24.4895 13.2885 22.1005 10.8995C19.7115 8.51051 18.2751 5.34703 18.0357 1.99921C17.9963 1.44834 17.5523 1 17 1C16.4477 1 15.9967 1.44827 16.0312 1.99948C16.2738 5.8782 17.9222 9.54957 20.6863 12.3137C21.7537 13.3811 22.9563 14.2821 24.254 15H1Z"
                                    fill="fadein"></path></svg
                            >
                        </p>
                    </div>

                    <div class="slider" transition:slide>
                        <ul class="dropdown">
                            {#each section.discreption as item}
                                <li>
                                    <svg
                                        xmlns="http://www.w3.org/2000/svg"
                                        width="1em"
                                        height="1em"
                                        viewBox="0 0 256 256"
                                        ><g fill="currentColor"
                                            ><path
                                                d="M176 128a48 48 0 1 1-48-48a48 48 0 0 1 48 48Z"
                                                opacity=".2"></path><path
                                                d="M140 128a12 12 0 1 1-12-12a12 12 0 0 1 12 12Z"
                                            ></path></g
                                        ></svg
                                    >
                                    <p>{item}</p>
                                </li>
                            {/each}
                        </ul>
                    </div>
                </Accordion>
            </div>
        {/each}
    </div>
</div>

<style lang="scss" global>
@import "../styles/globals.scss";
@import "../styles/Accordion.scss";

:global(body) h3 {
    color: rgb(255, 255, 255);
}
:global(body) svg {
    stroke: rgb(255, 255, 255);
}
:global(body.dark-mode) svg {
    stroke: rgb(0, 0, 0);
}
:global(body.dark-mode) h3 {
    color: rgb(0, 0, 0);
}
.isActive {
    transform: rotate(90deg);
    transition: all 0.7s cubic-bezier(0.645, 0.045, 0, 1);
}
</style>

<script>
import {slide} from "svelte/transition"
import Accordion from "./Accordion.svelte"

let sections = [
    {
        id: 1,
        title: "HTML",
        discreption: ["Semantic HTML5", "Forms", "Markdown", "HTML Attributes"],
        active: false,
    },
    {
        id: 2,
        title: "CSS",
        discreption: [
            "BEM",
            "SASS",
            "Sass Module System",
            "Responsive Web Design",
            "flex and grid",
            "Animations, variables",
            "styled-components",
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
            "Arrays, objects, prototypes",
        ],
        active: false,
    },
    {
        id: 4,
        title: "React",
        discreption: [
            "React Hooks",
            "React router",
            "Communication with REST API",
            "Styling components",
            "Component life cycle (class and hooks)",
            "Formik",
            "Building the interface",
            "Design tools and form handling",
            "Solving the most common problems with React",
        ],
        active: false,
    },
    {
        id: 5,
        title: "Next js",
        discreption: [],
        active: false,
    },
    {
        id: 6,
        title: "Animation",
        discreption: [
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
]
let isOpen = true
console.log(!isOpen)
</script>

<div class="wrapper">
    {#each sections as section}
        <div class="accordion">
            <Accordion>
                <div class="wrap" slot="header" let:toggle on:click="{toggle}">
                    <h3>{section.title}</h3>
                    <h5 class="{!isOpen ? ' ' : ' isActive'}">
                        <svg
                            xmlns="http://www.w3.org/2000/svg"
                            width="24"
                            height="24"
                            viewBox="0 0 24 24"
                            fill="none"
                            stroke="currentColor"
                            stroke-width="1"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            class="feather feather-arrow-up-right"
                            ><line x1="7" y1="17" x2="17" y2="7"></line><polyline
                                points="7 7 17 7 17 17"></polyline>
                        </svg>
                    </h5>
                </div>

                <div class="slider" transition:slide>
                    <ul class="dropdown">
                        {#each section.discreption as item}
                            <li>
                                <svg
                                    xmlns="http://www.w3.org/2000/svg"
                                    width="32"
                                    height="32"
                                    viewBox="0 0 24 24"
                                    fill="none"
                                    stroke="currentColor"
                                    stroke-width="1"
                                    stroke-linecap="round"
                                    stroke-linejoin="round"
                                    class="feather feather-check"
                                    ><polyline points="20 6 9 17 4 12"></polyline>
                                </svg>
                                <p>{item}</p>
                            </li>
                        {/each}
                    </ul>
                </div>
            </Accordion>
        </div>
    {/each}
</div>

<style lang="scss" global>
@import "../styles/globals.scss";
@import "../styles/Projects.scss";

:global(body.dark-mode) .logoImage {
    filter: brightness(1) invert(0);
}
:global(body.dark-mode) .calygraphyImage {
    filter: brightness(1) invert(0);
}
:global(body) .logoImage,
.calygraphyImage {
    filter: brightness(0) invert(1);
    transition: all 300ms ease-in-out;
}
:global(body) .logoImage:hover {
    filter: brightness(1) invert(0);
}
:global(body) svg {
    stroke: rgb(255, 255, 255);
    margin: 0;
}
:global(body.dark-mode) svg {
    stroke: rgb(0, 0, 0);
    margin: 0;
}
:global(body) li {
    border: 1px solid rgb(0, 0, 0);
}
:global(body.dark-mode) li {
    border: 1px solid rgb(0, 0, 0);
}
</style>

<script>
import {onMount} from "svelte"

const apiURL = "/assets/db.json"
// const apiURL = "http://localhost:3001/posts"

let data = []

onMount(async function () {
    const response = await fetch(apiURL)
    data = await response.json()

    console.log("data", data)
    console.log("data1", data)
})

let tabItems = ["🖥️ Web", "🖍️ Calygraphy", "🪄 Logos"]
let activeItem = "🖥️ Web"

const triggerTabChange = event => {
    activeItem = event.detail
}
import Tabs from "../components/Tabs.svelte"

import {GsapProjectsAnimation} from "../components/GsapProjectsAnimation.svelte"
import NavBar from "../components/NavBar.svelte"

onMount(() => {
    GsapProjectsAnimation()
})
</script>

<NavBar />

<section class="hero__cases container">
    <h1>Cases</h1>
    <p>See some of the projects I have worked on.</p>
</section>

{#await data}
    <h2>Loading...</h2>
{:then data}
    <main class="container">
        <Tabs tabItems="{tabItems}" activeItem="{activeItem}" on:tabChange="{triggerTabChange}" />
        {#if activeItem === "🪄 Logos"}
            <div class="projects" id="projects">
                {#each data as item}
                    {#if item.type === "logo"}
                        <div class="content ">
                            <div class="image ">
                                <a href="{item.link}" target="_blank" rel="noreferrer">
                                    <img
                                        class="logoImage"
                                        src="{item.imageUrl}"
                                        alt="{item.title}"
                                    />
                                </a>
                            </div>
                        </div>
                    {/if}
                {/each}
            </div>
        {:else if activeItem === "🖍️ Calygraphy"}
            <div class="projects">
                {#each data as item}
                    {#if item.type === "calygraphy"}
                        <div class="content ">
                            <div class="image ">
                                <a href="{item.link}" target="_blank" rel="noreferrer">
                                    <img
                                        class="calygraphyImage"
                                        src="{item.imageUrl}"
                                        alt="{item.title}"
                                    />
                                </a>
                            </div>
                        </div>
                    {/if}
                {/each}
            </div>
        {:else}
            <div class="projects web__projects ">
                {#each data as item}
                    {#if item.type === "web"}
                        <div class="content ">
                            <div class="web__image ">
                                <a href="{item.link}" target="_blank" rel="noreferrer">
                                    <img src="{item.imageUrl}" alt="{item.title}" />
                                </a>
                            </div>
                            <div class="web__description  ">
                                <div class="flex  flex-ai-c">
                                    <h3>{item.title}</h3>

                                    <a href="{item.link}" target="blank" rel="noopener noreferrer">
                                        <button class="web__btn">
                                            <svg
                                                xmlns="http://www.w3.org/2000/svg"
                                                width="34"
                                                height="34"
                                                viewBox="0 0 24 24"
                                                fill="none"
                                                stroke="currentColor"
                                                stroke-width="1"
                                                stroke-linecap="round"
                                                stroke-linejoin="round"
                                                class="feather feather-arrow-up-right"
                                                ><line x1="7" y1="17" x2="17" y2="7"
                                                ></line><polyline points="7 7 17 7 17 17"
                                                ></polyline></svg
                                            >
                                        </button>
                                    </a>
                                </div>

                                <ul class="web__description--ul">
                                    {#each item.technologies as items}
                                        <li>{items}</li>
                                    {/each}
                                </ul>
                            </div>
                        </div>
                    {/if}
                {/each}
            </div>
        {/if}
    </main>
{/await}

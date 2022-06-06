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
</style>

<script>
// import NavBar from "../components/NavBar.svelte"
import SocialMediaAccounts from "../components/SocialMediaAccounts.svelte"
// import Footer from "../components/Footer.svelte"

import {onMount} from "svelte"

const apiURL = "/assets/db.json"

let data = []

onMount(async function () {
    const response = await fetch(apiURL)
    data = await response.json()
    console.log(data)
})

import Tabs from "../components/Tabs.svelte"

let tabItems = ["Logos", "Calygraphy", "Web"]
let activeItem = "Logos"

const triggerTabChange = event => {
    activeItem = event.detail
}
</script>

<!-- <NavBar /> -->

<main class="container">
    <Tabs tabItems="{tabItems}" activeItem="{activeItem}" on:tabChange="{triggerTabChange}" />
    {#if activeItem === "Logos"}
        <div class="projects">
            {#each data as item}
                {#if item.type === "logo"}
                    <div class="centent">
                        <div class="image">
                            <a href="{item.link}" target="_blank" rel="noreferrer">
                                <img class="logoImage" src="{item.imageUrl}" alt="{item.title}" />
                            </a>
                        </div>
                    </div>
                {/if}
            {/each}
        </div>
    {:else if activeItem === "Calygraphy"}
        <div class="projects">
            {#each data as item}
                {#if item.type === "calygraphy"}
                    <div class="centent">
                        <div class="image">
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
        <div class="projects web__projects">
            {#each data as item}
                {#if item.type === "web"}
                    <div class="centent  ">
                        <div class="web__image">
                            <a href="{item.link}" target="_blank" rel="noreferrer">
                                <img class="" src="{item.imageUrl}" alt="{item.title}" />
                            </a>

                            <span class="web__bg">
                                <a href="{item.link}" target="blank" rel="noopener noreferrer">
                                    <button class="web__btn">
                                        <p>View Case Study</p>
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
                                            ><line x1="7" y1="17" x2="17" y2="7"></line><polyline
                                                points="7 7 17 7 17 17"></polyline></svg
                                        >
                                    </button>
                                </a>
                            </span>
                            <div class="web__description">
                                <h4>{item.title}</h4>
                                <ul class="web__description--ul">
                                    {#each item.technologies as items}
                                        <li>{items}</li>
                                    {/each}
                                </ul>
                            </div>
                        </div>
                    </div>
                {/if}
            {/each}
        </div>
    {/if}
</main>

<!-- <Footer /> -->

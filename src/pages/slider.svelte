<style lang="scss" global>
@import "../styles/globals.scss";
@import "../styles/Slider.scss";

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
import {onMount} from "svelte"

const apiURL = "/assets/logodb.json"

let data = []

onMount(async function () {
    const response = await fetch(apiURL)
    data = await response.json()
    console.log(data)
})

import Tabs from "../components/Tabs.svelte"
</script>

<!-- <NavBar /> -->

<main class="container">
    <div class="slider" id="projects">
        <div class="centent animate ">
            {#each data as item}
            <div class="image animate">
                    <a href="{item.link}" target="_blank" rel="noreferrer">
                        <img class="logoImage" src="{item.imageUrl}" alt="{item.title}" />
                    </a>
                </div>
                {/each}
            </div>
        </div>
</main>

<!-- <Footer /> -->

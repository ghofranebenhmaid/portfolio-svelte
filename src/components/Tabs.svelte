<style>
:global(body) span {
    color: rgb(255, 255, 255);
}
:global(body.dark-mode) span {
    color: rgb(0, 0, 0);
}
.tabs {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-bottom: 40px;
    position: sticky;
    /* padding: 1.2rem; */
    height: 4rem;
    top: 4.8rem;
    z-index: 1;
    backdrop-filter: blur(45px);
}
ul {
    display: flex;
    justify-content: center;
    padding: 0;
    list-style-type: none;
}
li {
    margin: 0 16px;
    font-size: 1rem;
    font-weight: 600;

    cursor: pointer;
    text-transform: uppercase;
    letter-spacing: 1.5px;
    color: var(--color-title);
}
.active {
    color: #5f77e0;
    border-bottom: 2px solid #5f77e0;
    padding-bottom: 2px;
    text-decoration: none;
}
</style>

<script>
import {createEventDispatcher} from "svelte"
const dispatch = createEventDispatcher()

export let tabItems
export let activeItem

function scrollToTop() {
    window.scrollTo({
        top: 250,
        left: 1000,
        behavior: "smooth",
    })
}
</script>

<div class="tabs">
    <ul>
        {#each tabItems as item}
            <li on:click="{() => dispatch('tabChange', item)}">
                <div class:active="{item === activeItem}">
                    <span on:click="{scrollToTop}">{item}</span>
                </div>
            </li>
        {/each}
    </ul>
</div>

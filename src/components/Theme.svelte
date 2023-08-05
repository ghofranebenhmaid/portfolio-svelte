<style>
button {
    width: 35px;
    height: 35px;
    border: none;
    border-radius: 5px;
    /* padding: 0.5rem; */
    cursor: pointer;
    display: flex;
    justify-content: center;
    align-items: center;
    
    
}
:global(body.dark-mode) button {
    background-color:  #000;
}
:global(body.dark-mode) button svg {
    /* transform: translateX(12px); */

    stroke: #fff;
    transition: all 0.5s cubic-bezier(0.645, 0.045, 0.355, 1);
}
:global(body.dark-mode) button svg:hover {
    transform: rotate(-20deg);
    transition: all 0.5s cubic-bezier(0.645, 0.045, 0.355, 1);
}

:global(body) button {
    background-color: #fff;
}
:global(body) button svg {
    /* transform: translateX(-12px); */

    transition: all 0.5s cubic-bezier(0.645, 0.045, 0.355, 1);
    stroke: #000;
}
:global(body) button svg:hover {
    transform: rotate(-40deg);
    transition: all 0.5s cubic-bezier(0.645, 0.045, 0.355, 1);
}
</style>

<script>
import {onMount} from "svelte"

let _Theme = localStorage.getItem("_Theme") // null or 'true'

let darkMode = false
let body

onMount(() => {
    body = document.querySelector("body")
    if (_Theme) body.classList.add("dark-mode")
})
function toggleTheme() {
    darkMode = !darkMode
    if (_Theme) {
        _Theme = null
        localStorage.removeItem("_Theme")
        body.classList.remove("dark-mode")
    } else {
        _Theme = "true"
        localStorage.setItem("_Theme", "true")
        body.classList.add("dark-mode")
    }
}
</script>

<button on:click="{toggleTheme}" class="sunmoon">
    <!-- <slot/> -->
    {#if darkMode}
        <svg
            xmlns="http://www.w3.org/2000/svg"
            width="25"
            height="25"
            viewBox="0 0 24 24"
            fill="none"
            stroke="#fff"
            strokeWidth="2"
            strokeLinecap="round"
            strokeLinejoin="round"
            class="feather feather-moon"
        >
            <path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"></path>
        </svg>
    {:else}
        <svg
            xmlns="http://www.w3.org/2000/svg"
            width="25"
            height="25"
            viewBox="0 0 24 24"
            fill="none"
            stroke="#000"
            strokeWidth="2"
            strokeLinecap="round"
            strokeLinejoin="round"
            class="feather feather-sun"
        >
            <circle cx="12" cy="12" r="5"></circle>
            <line x1="12" y1="1" x2="12" y2="3"></line>
            <line x1="12" y1="21" x2="12" y2="23"></line>
            <line x1="4.22" y1="4.22" x2="5.64" y2="5.64"></line>
            <line x1="18.36" y1="18.36" x2="19.78" y2="19.78"></line>
            <line x1="1" y1="12" x2="3" y2="12"></line>
            <line x1="21" y1="12" x2="23" y2="12"></line>
            <line x1="4.22" y1="19.78" x2="5.64" y2="18.36"></line>
            <line x1="18.36" y1="5.64" x2="19.78" y2="4.22"></line>
        </svg>
    {/if}
</button>

<style>
.cursor {
    width: 40px;
    height: 40px;
    background-color: #000;
    border-radius: 50%;
    pointer-events: none;
    z-index: 9999;
    /* mix-blend-mode: difference; */
    cursor: pointer;
}

.cursor__image {
    position: fixed;
    width: 100px;
    height: 100px;
    pointer-events: none;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    opacity: 0;
    z-index: 9998;
}
</style>

<script>
import {onMount, onDestroy} from "svelte"
import {gsap} from "gsap"

let cursor
let cursorImage
let isHovering = false

onMount(() => {
    cursor = document.querySelector(".cursor")
    cursorImage = document.querySelector(".cursor__image")
    gsap.set(cursor, {xPercent: -50, yPercent: -50})
})

function handleMouseEnter() {
    isHovering = true
    gsap.to(cursorImage, {opacity: 1, duration: 0.3})
}

function handleMouseLeave() {
    isHovering = false
    gsap.to(cursorImage, {opacity: 0, duration: 0.3})
}

function handleMouseMove(event) {
    if (!isHovering) return
    gsap.to(cursor, {x: event.clientX, y: event.clientY, duration: 0.2})
}

onDestroy(() => {
    cursor = null
    cursorImage = null
})
</script>

<div
    class="cursor"
    on:mouseenter="{handleMouseEnter}"
    on:mouseleave="{handleMouseLeave}"
    on:mousemove="{handleMouseMove}"
></div>

{#if isHovering}
    <img
        class="cursor__image"
        src="https://images.unsplash.com/photo-1646303746488-3927e8bf81a7?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80"
        alt="Custom Cursor"
    />
{/if}

<!-- <div class="cursor">
    <img
        src="https://images.unsplash.com/photo-1646303746488-3927e8bf81a7?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80"
        class="cursor__media"
    />

    <img
        src="https://images.unsplash.com/photo-1609314491503-a864b0abf611?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1470&q=80"
        class="cursor__media"
    />

    <img
        src="https://images.unsplash.com/photo-1643125978288-7c7c8babc5fe?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=735&q=80"
        class="cursor__media"
    />
</div>
<div class="nav__link">Link 1</div>
<div class="nav__link">Link 2</div> -->
<!-- <nav class="nav">
    <a href="#" class="nav__link">Studio</a>
    <a href="#" class="nav__link">Showcase</a>
    <a href="#" class="nav__link">Contact</a>
</nav> -->

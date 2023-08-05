<style>
.back-to-top {
    opacity: 1;
    transition: opacity 0.5s, visibility 0.5s;
    position: fixed;
    z-index: 99;
    right: 20px;
    user-select: none;
    bottom: 20px;
    color: white;
    background-color: black;
    border-radius: 50%;
    aspect-ratio: 1 / 1;
    width: 35px;
    height: 35px;
}

.back-to-top.hidden {
    opacity: 0;
    visibility: hidden;
}
</style>

<script>
export let showOnPx = 150
let hidden = true

function goTop() {
    document.body.scrollIntoView()
}

function scrollContainer() {
    return document.documentElement || document.body
}

function handleOnScroll() {
    if (!scrollContainer()) {
        return
    }

    if (scrollContainer().scrollTop > showOnPx) {
        hidden = false
    } else {
        hidden = true
    }
}
</script>

<svelte:window on:scroll="{handleOnScroll}" />

<div class="back-to-top flex flex-jc-c flex-ai-c" on:click="{goTop}" class:hidden>
    <svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24"
        ><path fill="currentColor" d="M11 20V7.825l-5.6 5.6L4 12l8-8l8 8l-1.4 1.425l-5.6-5.6V20h-2Z"
        ></path></svg
    >
</div>

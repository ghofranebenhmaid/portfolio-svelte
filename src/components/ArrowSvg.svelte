<style lang="scss" global>
:global(body) svg {
    fill: rgb(255, 255, 255);
}
:global(body.dark-mode) svg {
    fill: rgb(0, 0, 0);
}

svg {
    -webkit-transform: rotate(-45deg);
    -moz-transform: rotate(-45deg);
    -ms-transform: rotate(-45deg);
    -o-transform: rotate(-45deg);
    transform: rotate(-45deg);

    width: clamp(3rem, 1rem + 10vw, 8rem);
    height: clamp(3rem, 1rem + 10vw, 8rem);
}
</style>

<script>
import {onMount} from "svelte"
import {TweenLite} from "gsap"

let arrow
let arrowCenterX = 0
let arrowCenterY = 0

// Function to update the arrow's rotation based on mouse cursor position
function updateArrowRotation(event) {
    const mouseX = event.clientX - arrowCenterX
    const mouseY = event.clientY - arrowCenterY
    const rotation = Math.atan2(mouseY, mouseX) * (360 / Math.PI) // Convert radians to degrees

    TweenLite.to(arrow, 0.05, {
        rotation,
        ease: "power2.out",
    })
}

onMount(() => {
    arrow = document.querySelector(".arrow")
    const {left, top, width, height} = arrow.getBoundingClientRect()
    arrowCenterX = left + width / 1
    arrowCenterY = top + height / 180
    window.addEventListener("mousemove", updateArrowRotation)
})

// Clean up the event listener when the component is unmounted
function onDestroy() {
    window.removeEventListener("mousemove", updateArrowRotation)
}
</script>

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 30 30" fill="" stroke="none" class="arrow"
    ><path
        d="M1 15C0.447716 15 0 15.4477 0 16C0 16.5523 0.447716 17 1 17H24.254C22.9563 17.7179 21.7537 18.6189 20.6863 19.6863C17.9222 22.4504 16.2738 26.1218 16.0312 30.0005C15.9967 30.5517 16.4477 31 17 31C17.5523 31 17.9963 30.5517 18.0357 30.0008C18.2751 26.653 19.7115 23.4895 22.1005 21.1005C24.4895 18.7115 27.653 17.2751 31.0008 17.0357C31.5517 16.9963 32 16.5523 32 16C32 15.4477 31.5517 15.0037 31.0008 14.9643C27.653 14.7249 24.4895 13.2885 22.1005 10.8995C19.7115 8.51051 18.2751 5.34703 18.0357 1.99921C17.9963 1.44834 17.5523 1 17 1C16.4477 1 15.9967 1.44827 16.0312 1.99948C16.2738 5.8782 17.9222 9.54957 20.6863 12.3137C21.7537 13.3811 22.9563 14.2821 24.254 15H1Z"
        fill=""></path></svg
>

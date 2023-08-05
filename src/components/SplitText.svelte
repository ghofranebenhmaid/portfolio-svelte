<style>
.word-line {
    overflow: hidden;
}
.skew-up {
    opacity: 0;
}
</style>

<script>
import {onMount, onDestroy} from "svelte"
import SplitType from "split-type"
import gsap from "gsap"
import ScrollTrigger from "gsap/ScrollTrigger"

let skewUpElements = []

function addAnimation() {
    skewUpElements.forEach(textInstance => {
        const text = new SplitType(textInstance, {
            types: "lines, words",
            lineClass: "word-line",
        })

        let line = textInstance.querySelector(".word-line")
        let word = line.querySelectorAll(".word")

        let tl = gsap.timeline({
            scrollTrigger: {
                trigger: textInstance,
                start: "top 95%",
                end: "top 95%",
                onComplete: function () {
                    textInstance.classList.remove("skew-up")
                },
            },
        })

        tl.set(textInstance, {opacity: 1}).from(word, {
            y: "100%",
            skewX: "-10",
            duration: 2,
            stagger: 0.07,
            ease: "expo.out",
        })
    })
}

onMount(() => {
    // Initialize ScrollTrigger
    gsap.registerPlugin(ScrollTrigger)

    skewUpElements = document.querySelectorAll(".skew-up")

    addAnimation()

    // Add event listener for window resize
    window.addEventListener("resize", handleResize)
})

onDestroy(() => {
    // Remove the event listener on component unmount
    window.removeEventListener("resize", handleResize)
})

function handleResize() {
    if (window.innerWidth >= 992) {
        addAnimation()
    }
}
</script>

<div class="skew-up"><slot /></div>

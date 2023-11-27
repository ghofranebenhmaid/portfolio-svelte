<script context="module">
import {gsap} from "gsap"

export function GsapProjectsAnimation() {
    gsap.set(".zoomin", {transformOrigin: "center center"}),
        gsap.to([".zoomin"], {
            scale: 3.5,

            ease: "linear",
            scrollTrigger: {
                trigger: ".zoomin",
                // start: "100% 55%",
                // end: "100% 0%",

                // markers: true,
                scrub: true,
                smooth: 1,
            },
        })
    gsap.to(".projects", {
        // scale: 30,
        yPercent: -100,

        ease: "linear",
        scrollTrigger: {
            trigger: ".projects",
            start: "100% 55%",
            // end: "100% 0%",
            // markers: true,
            scrub: true,
            smooth: 1,
        },
    })
}
</script>

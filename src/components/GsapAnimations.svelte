<script context="module">
import {gsap} from "gsap"

import {ScrollTrigger} from "gsap/ScrollTrigger"

gsap.registerPlugin(ScrollTrigger)

export function GsapAnimation() {
    gsap.defaults({ease: "power4"})

    gsap.set(".wrap ", {duration: 1, y: 40})
    ScrollTrigger.batch(".wrap", {
        onEnter: batch =>
            gsap.to(batch, {opacity: 1, y: 0, stagger: 0.02, duration: 0.5, overwrite: true}),
    })

    gsap.set(".fadein", {duration: 2.5, opacity: 0, y: -40})
    ScrollTrigger.batch(".fadein", {
        onEnter: batch =>
            gsap.to(batch, {
                opacity: 1,
                y: 0,
                duration: 1,
                stagger: 0.05,
                overwrite: true,
            }),
        start: "20% 90%",
    })
}
</script>

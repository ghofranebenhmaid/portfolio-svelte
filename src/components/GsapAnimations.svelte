<script context="module">
import {gsap} from "gsap"

import {ScrollTrigger} from "gsap/ScrollTrigger"

gsap.registerPlugin(ScrollTrigger)

export function GsapAnimation() {
    gsap.defaults({ease: "slow"})

    gsap.set(".wrap ", {duration: 1, skewY: -4, y: 50})
    ScrollTrigger.batch(".wrap", {
        onEnter: batch =>
            gsap.to(batch, {
                opacity: 1,
                y: 0,
                skewY: 0,
                duration: 0.5,
                overwrite: true,
                stagger: 0.25,
                scrollTrigger: {
                    start: "100% 80%",
                    end: "0% 70%",
                    markers: false,

                    scrub: false,
                },
                // stagger: {
                //     amount: 2.3,
                // },
            }),
    })

    gsap.set(".fadein", {duration: 2.5, opacity: 0, y: -40})
    ScrollTrigger.batch(".fadein", {
        onEnter: batch =>
            gsap.to(batch, {
                opacity: 1,
                y: 0,
                duration: 0.5,
                stagger: 0.15,
                overwrite: true,
            }),
        start: "20% 90%",
    })
}
</script>

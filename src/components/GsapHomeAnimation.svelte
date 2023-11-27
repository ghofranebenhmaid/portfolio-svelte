<script context="module">
import {gsap} from "gsap"

export function GsapHomeAnimation() {
    gsap.from([".banner-addition-bg", ".banner-bg", ".banner-bg2"], {
        duration: 1.1,
        width: 0,
        // skewX: 1,
        ease: "power3.inOut",
        // once: true,
        stagger: {
            amount: 0.3,
        },
    })
    gsap.to([".banner-addition-bg", ".banner-bg", ".banner-bg2"], {
        duration: 1.1,
        width: "100%",
        // skewX: 1,
        ease: "power3.inOut",
        // once: true,
        stagger: {
            amount: 0.3,
        },
    })

    // gsap.from(".header__title", {
    //     delay: 0.7,
    //     x: 20,
    //     duration: 0.8,
    //     opacity: 0,
    //     stagger: 0.05,
    //     ease: "back.out",
    //     scrollTrigger: {
    //         trigger: ".header__title",
    //     },
    // })
    gsap.set(".svg2", {transformOrigin: "center center"}),
        gsap.to(".svg2", {
            rotation: -180,
            ease: "linear",
            scrollTrigger: {
                trigger: ".svg2",
                // start: "100% 75%",
                // end: "100% 0%",
                // markers: true,

                scrub: true,
            },
        })

    gsap.fromTo(
        ".svg2",
        {
            opacity: 2,
            scale: 0.8,
            ease: "linear",
            transformOrigin: "50%",
            rotation: 0,
        },
        {
            delay: 2,
            opacity: 1,
            scale: 0.8,
            duration: 3,
            rotation: "-=30",
            // repeat: 3,
            // repeatDelay: 5.2,
        },
    )
    gsap.fromTo(
        ".svg2",
        {
            opacity: 2,
            scale: 0.8,
            ease: "linear",
            transformOrigin: "50%",
            rotation: 0,
        },
        {
            delay: 5,
            opacity: 1,
            scale: 0.7,
            duration: 3,
            rotation: "+=80",
        },
    )
}
</script>

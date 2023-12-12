<style lang="scss">
@import "../../styles/globals.scss";
:global(body) {
    h1,
    p {
        color: rgb(255, 255, 255);
        overflow: hidden;
    }
}

:global(body.dark-mode) h1,
p {
    color: rgb(0, 0, 0);
    overflow: hidden;
}

.head {
    width: 100vw;
    height: 85vh;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    gap: var(--space-xl);
    @media (min-width: 315px) and (max-width: 1400px) and (orientation: landscape) {
        height: 115vh;
    }

    h1 {
        font-size: clamp(2.5rem, 1rem + 10vw, 7.5rem);
        // font-family: "Segoe UI";
        line-height: clamp(2.5rem, 1rem + 10vw, 10rem);
        font-family: "Black Han Sans", sans-serif;
        /* font-family: "Roboto Slab", serif; */
        /* font-family: "Merriweather", serif; */
        text-align: center;
        /* font-weight: 200; */
        @media (min-width: 315px) and (max-width: 1400px) and (orientation: landscape) {
            font-size: clamp(1.5rem, 1rem + 10vw, 3.5rem);
            line-height: var(--step-5);
        }
    }
    .arrow {
        // scale: 2.5;
        cursor: pointer;
        opacity: 0;
        // border: 8px solid #5f77e0;
        // border-radius: 50%;
        // padding: 40px;
        &:hover {
            // scale: 1.03;
        }
    }
}
</style>

<script>
import {onMount} from "svelte"
import SplitText from "../SplitText.svelte"

import {GsapHomeAnimation} from "../GsapHomeAnimation.svelte"
import {GsapAnimation} from "../GsapAnimations.svelte"
import NavBar from "../NavBar.svelte"
import ArrowSvg from "../ArrowSvg.svelte"

onMount(() => {
    GsapHomeAnimation()
    GsapAnimation()
})
</script>

<header>
    <NavBar />

    <div class="head container">
        <SplitText>
            <h1 class="head__text ">Frontend Developer & User experience</h1>
        </SplitText>
        <span class="arrow fadein" title="CV">
            <a href="#0" onclick="window.open('../../assets/CV_Ghofrane_BenHmaid.pdf');">
                <ArrowSvg />
            </a>
        </span>
    </div>
</header>

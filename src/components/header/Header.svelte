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
.blacklogo,
.whitelogo {
    width: max(5vw, 55px);
    margin-left: 3rem;
}

:global(body) .blacklogo {
    display: none;
}
:global(body.dark-mode) .blacklogo {
    display: block;
}
:global(body) .whitelogo {
    display: block;
}
:global(body.dark-mode) .whitelogo {
    display: none;
}
/* :global(body) .svg-circle {
    background-color: rgb(255, 255, 255);
}
:global(body.dark-mode) .svg-circle {
    background-color: rgb(0, 0, 0);
} */

.header {
    display: grid;
    grid-template-columns: 1fr 1fr;
    justify-items: stretch;
    align-items: center;

    /* width: 100%; */

    margin-trim: block;

    height: 90vh;
    height: 90svh;
    /* position: relative; */
    text-wrap: balance;

    @media (max-width: 599px) {
        grid-template-columns: 1fr;
    }
    @media (min-width: 315px) and (max-width: 1400px) and (orientation: landscape) {
        grid-template-columns: 1fr;
    }

    h1 {
        /* font-size: var(--step-4); */
        font-size: clamp(2rem, 1.2727rem + 3.6364vw, 4rem);

        font-weight: 600;
        font-family: "IBM Plex Sans", sans-serif;
        text-wrap: balance;
    }
    p {
        margin-top: var(--space-m);
        font-size: var(--step-0);
        line-height: var(--space-m);
        text-wrap: balance;
    }
}

.svg-circle {
    position: relative;
    /* outline: 1px solid tan; */
    @media (min-width: 315px) and (max-width: 1400px) and (orientation: landscape) {
        display: none;
    }
    .arrow {
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        position: absolute;
        transform-box: fill-box;
        transform-origin: center center;
    }
    right: 0;
    bottom: 0;
    overflow: hidden;

    @media (max-width: 599px) {
        display: none;
    }
}
/* .head {

    width: 100vw;
    height: 75vh;
    display: flex;
    align-items: end;


    h1 {

        font-size: clamp(5rem, 3.7273rem + 6.3636vw, 8.5rem);
    }
} */
.header-bg {
    /* background-color: rgba(223, 199, 18, 0.919); */
    overflow: hidden;
}
</style>

<script>
import ArrowSvg from "../ArrowSvg.svelte"
import CircularTextSvg from "../CircularTextSvg.svelte"
import NavBar from "../NavBar.svelte"
import SplitText from "../SplitText.svelte"
</script>

<!-- <div class="head container">
    <SplitText>
        <h1 class="head__text ">Frontend Developer & UI/UX Designer</h1>
    </SplitText>
</div> -->
<header class="header-bg ">
    <NavBar />

    <div class="header container ">
        <div class="description  ">
            <div class="flex  flex-ai-c-end"></div>
            <SplitText>
                <h1 class="header__subtitle ">Frontend Developer & UI/UX Designer</h1>
            </SplitText>

            <SplitText>
                <p class="header__subtitle ">
                    I Build a fast, flexible, mobile first website that clearly communicates with
                    visitors.
                </p>
            </SplitText>
            <a href="#0" onclick="window.open('../../assets/CV_Ghofrane_BenHmaid.pdf');">
                <button class="primary-button "> Resume </button>
            </a>
        </div>
        <div class="svg-circle ±±+?">
            <div class="arrow">
                <ArrowSvg />
            </div>
            <a href="#0" onclick="window.open('../../assets/CV_Ghofrane_BenHmaid.pdf');">
                <CircularTextSvg />
            </a>
        </div>
    </div>
</header>

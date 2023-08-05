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

.header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-trim: block;

    height: 95vh;
    height: 95svh;
    position: relative;
    text-wrap: balance;

    @media (min-width: 768px) and (max-width: 1024px) and (orientation: landscape) {
        margin: var(--space-xl) 0;
    }

    h1 {
        font-size: var(--step-4);
        font-weight: 900;
        line-height: var(--step-5);
        @media (min-width: 768px) and (max-width: 1024px) and (orientation: landscape) {
            font-size: var(--step-2);
            line-height: var(--step-3);
        }
    }
    p {
        font-size: var(--step-0);
        line-height: var(--space-m);
    }
}

.svg-circle {
    position: relative;
    /* outline: 1px solid tan; */

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
    width: 45vw;
    height: 45hw;
    max-width: 45vw;
    max-height: 45hw;
    overflow: hidden;

    @media (max-width: 599px) {
        display: none;
    }
}
</style>

<script>
import ArrowSvg from "../ArrowSvg.svelte"
import CircularTextSvg from "../CircularTextSvg.svelte"
import SplitText from "../SplitText.svelte"
</script>

<header class="header-bg ">
    <div class="header container">
        <div class="description wrap ">
            <SplitText>
                <p class=" wrap">Hi there 👋🏽, I'm</p>
            </SplitText>

            <div class="flex  flex-ai-c-end">
                <SplitText>
                    <h1 class="header__subtitle ">Ghofrane Ben Hmaid</h1>
                    <!-- <img src="/assets/SVG/logoarbw.svg" alt="logo white" class="whitelogo " />
                        <img src="/assets/SVG/logoarbb.svg" alt="logo black" class="blacklogo " /> -->
                </SplitText>
            </div>
            <SplitText>
                <h1 class="header__subtitle ">Frontend Developer & UI/UX Designer</h1>
            </SplitText>

            <SplitText>
                <p class=" ">
                    I Build a fast, flexible, mobile first website that clearly communicates with
                    visitors.
                </p>
            </SplitText>
            <a href="#0" onclick="window.open('../../assets/CV_Ghofrane_BenHmaid.pdf');">
                <button class="primary-button "> Resume </button>
            </a>
        </div>
        <div class="svg-circle wrap">
            <div class="arrow">
                <ArrowSvg />
            </div>
            <a href="#0" onclick="window.open('../../assets/CV_Ghofrane_BenHmaid.pdf');">
                <CircularTextSvg />
            </a>
        </div>
    </div>
</header>

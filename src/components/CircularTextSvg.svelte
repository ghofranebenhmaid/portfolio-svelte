<style lang="scss" global>
:global(body) svg {
    fill: rgb(255, 255, 255);
}
:global(body.dark-mode) svg {
    fill: rgb(0, 0, 0);
}
svg:hover {
    fill: rgb(111, 76, 238);
    transform: scale(1.3);
}
circle {
    stroke: rgb(111, 76, 238);
    stroke-width: 3px;
    fill: none;
}
</style>

<svg
    xmlns="http://www.w3.org/2000/svg"
    xml:lang="en"
    xmlns:xlink="http://www.w3.org/1999/xlink"
    viewBox="0 0 500 500"
    class="svg2 svg1"
>
    <title>Circular Text Path</title>
    <style>
    text {
        font-size: 60px;
        /* font-family: Copperplate, Copperplate Gothic, serif; */
        /* font-weight: bold; */
        /* font-weight: 900; */
        font-variant: small-caps;
        font-variant-ligatures: none;
        /* stroke-width: 1.5px; */
        /* fill: #5f77e0; */
        /* fill: var(--color-text); */
    }
    </style>
    <defs>
        <path
            id="textcircle"
            d="M250,400
 a150,150 0 0,1 0,-300a150,150 0 0,1 0,300Z"
            transform="rotate(22,250 250)"></path>
    </defs>
    <!-- <circle cx="50%" cy="50%" r="260px"></circle> -->
    <!-- <circle cx="50%" cy="50%" r="100px"></circle> -->

    <text dy="-60">
        <textPath
            xlink:href="#textcircle"
            aria-label="All for One &amp; One for All"
            textLength="890"
        >
            •click here to see my resume•
        </textPath>
    </text>
</svg>

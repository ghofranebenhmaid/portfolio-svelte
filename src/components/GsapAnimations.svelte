<script context="module">
import gsap from 'gsap';
 import { onMount } from 'svelte';

	onMount(() => {
		// const tl = gsap.timeline();

   let anim1 =  gsap.from('.hero__social', {
          delay: 1.8,
    x: 10,
    duration: 0.5,
    opacity: 0,
    ease: 'power3.out',
    
})

    })

</script>
<script>
export let isOpen = false

const toggle = () => (isOpen = !isOpen)
</script>



<slot name="header" toggle="{toggle}" />

{#if isOpen}
    <slot />
{/if}

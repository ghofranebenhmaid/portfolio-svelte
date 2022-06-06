<script>
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();

    export let tabItems;
    export let activeItem;

</script>

<div class="tabs">
    <ul>
        {#each tabItems as item}
            <li on:click={() => dispatch('tabChange', item)}>
                <div class:active={item===activeItem}>{item}</div>
            </li>
        {/each}
    </ul>
</div>

<style>
    .tabs {
        margin-bottom: 40px
    }
    ul {
        display: flex;
        justify-content: center;
        padding: 0;
        list-style-type: none;
    }
    li {
        margin: 0 16px;
        font-size: 18px;
        color: #555;
        cursor: pointer;
    }
    .active {
        color: #5f77e0;
        border-bottom: 2px solid #5f77e0;
        padding-bottom: 8px;
    }

</style>
<main>
    <h1>ADDICTION. IT'S A REAL THING.</h1>
    {#if showContent}
    <div transition:fade={{ duration: 5000 }}>
        <!-- New content goes here -->
        <p>New content displayed after buttons disappear.</p>
    </div>
    {/if}
    <button on:click={handleClick} class:fade-out={showContent}>Learn More</button>
    <br>
    <br>
    <button on:click={handleClick} class:fade-out={showContent}>Find Resources</button>
</main>
<script>
    import { fade } from 'svelte/transition';

    let showContent = false;

    function handleClick() {
        showContent = true;
    }
</script>

<style>
    .hidden {
        display: none;
    }
    .fade-out {
        animation: fadeOut 1.5s forwards;
    }
    @keyframes fadeOut {
        to {
            transform: translateY(-100%);
            opacity: 0;
        }
    }
</style>
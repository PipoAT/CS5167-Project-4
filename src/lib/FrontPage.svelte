<main>
    <div class="maincontainer">
        <h1>GAMBLING ADDICTION.</h1>
        <h1>IT'S A REAL THING.</h1>
        {#if showContent && !showResources}
        <div transition:fade={{ duration: 5000 }}>
            <!-- New content goes here -->
            <p>New content displayed after buttons disappear.</p>
        </div>
        {/if}
        {#if showResources}
        <div transition:fade={{ duration: 5000 }} class="map-container">
            <img src="https://maps.googleapis.com/maps/api/staticmap?center=-33.8569,151.2153&zoom=15&size=600x300&maptype=roadmap&markers=color:red%7Clabel:S%7C-33.8569,151.2153&key=AIzaSyD_ePMwjv6DT2ObpPTxsv7jil1XTUYfCuc">
        </div>
        {/if}
        {#if !showResources}
        <button on:click={handleClick} class:fade-out={showContent || showResources}>Learn More</button>
        {/if}
        <br>
        <br>
        <button on:click={handleClickResources} class:fade-out={showResources}>Find Resources</button>
    </div>
</main>
<script>
    import { fade } from 'svelte/transition';

    let showContent = false;
    let showResources = false;

    function handleClick() {
        showContent = true;
    }

    function handleClickResources() {
        showResources = true;
    }
</script>

<style>

    p {
        color: black;
    }

    .maincontainer {
        background-color: white;
        padding: 75px;
        border-radius: 100px;
        border-color: crimson;
    }

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
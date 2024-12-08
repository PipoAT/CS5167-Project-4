<main>
    <div class="maincontainer">
        <h1>GAMBLING ADDICTION.</h1>
        <h1>IT'S A REAL THING.</h1>
        {#if showContent && !showResources}
        <div transition:fade={{ duration: 2000 }}>
            <p>Gambling addiction, also known as compulsive gambling, is a type of impulse-control disorder. It can have devastating consequences for individuals and their families. People with a gambling addiction often feel an uncontrollable urge to gamble, even when it has negative effects on their lives.</p>
            <p>Signs of gambling addiction include:</p>
            <ul>
                <li>Preoccupation with gambling</li>
                <li>Needing to gamble with increasing amounts of money to achieve the desired excitement</li>
                <li>Repeated unsuccessful attempts to control, cut back, or stop gambling</li>
                <li>Restlessness or irritability when trying to cut down or stop gambling</li>
                <li>Gambling to escape problems or relieve feelings of helplessness, guilt, anxiety, or depression</li>
                <li>Chasing losses (trying to get back lost money by gambling more)</li>
                <li>Lying to family members or others to hide the extent of gambling</li>
                <li>Jeopardizing or losing significant relationships, jobs, or educational/career opportunities because of gambling</li>
                <li>Relying on others to provide money to relieve desperate financial situations caused by gambling</li>
            </ul>
            <p>If you or someone you know is struggling with gambling addiction, it's important to seek help. There are many resources available, including counseling, support groups, and treatment programs.</p>
        </div>
        {/if}
        {#if showResources}
        <div transition:fade={{ duration: 2000 }} class="map-container move-up">
            <img src={mapUrl} alt="Map showing current location">
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

    import { onMount } from 'svelte';

    let latitude;
    let longitude;
    let mapUrl;

    onMount(() => {
        if (navigator.geolocation) {
            navigator.geolocation.getCurrentPosition(position => {
                latitude = position.coords.latitude;
                longitude = position.coords.longitude;
                mapUrl = `https://maps.googleapis.com/maps/api/staticmap?center=${latitude},${longitude}&zoom=15&size=600x300&maptype=roadmap&markers=color:red%7Clabel:S%7C${latitude},${longitude}&key=AIzaSyD_ePMwjv6DT2ObpPTxsv7jil1XTUYfCuc`;
            });
        } else {
            console.error("Geolocation is not supported by this browser.");
        }
    });

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

    ul {
        color: black;
    }

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
        animation: fadeOut 1s forwards;
    }
    @keyframes fadeOut {
        to {
            transform: translateY(-100%);
            opacity: 0;
        }
    }
</style>
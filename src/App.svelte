<script lang="ts">
    /*
     * NODE
     * this is only a schoolproject
     * don't take this serious
     * */
    import Download from "./lib/Download.svelte";
    import Support from "./lib/Support.svelte";
    import Home from "./lib/Home.svelte";
    import Faq from "./lib/Faq.svelte";
    let items = ["Home", "Download", "Support", "FAQ"];
    let current_component = items[0];
    const nav = (location: string) => {
        current_component = location;
    };
</script>

<div class="content">
    {#if current_component == items[0]}
        <Home />
    {:else if current_component == items[1]}
        <Download />
    {:else if current_component == items[2]}
        <Support />
    {:else if current_component == items[3]}
        <Faq />
    {:else}
        <p>Something went wrong</p>
    {/if}
</div>
<div class="nav">
    {#each items as item}
        <li>
            <button
                on:click={() => {
                    nav(item);
                }}>{item}</button
            >
        </li>
    {/each}
    <div id="lang">
        <p>En</p>
        <img
            src={"https://upload.wikimedia.org/wikipedia/commons/thumb/a/a5/Flag_of_the_United_Kingdom_%281-2%29.svg/1200px-Flag_of_the_United_Kingdom_%281-2%29.svg.png"}
        />
    </div>
</div>

<style>
    :global(body) {
        background: #2e313b;
    }
    :global(h1:hover) {
        text-decoration: underline;
    }
    li {
        list-style-type: none;
    }
    #lang {
        position: absolute;
        bottom: 3.5vh;
        left: 3vh;
    }
    #lang img {
        position: absolute;
        bottom: 1.5vh;
        left: 6vh;
        width: 300%;
    }
    .content {
        background: #2e313b;
        position: absolute;
        width: 86%;
        left: 10%;
        padding: 2%;
    }
    .nav {
        background: #1d202b;
        position: absolute;
        left: 0;
        top: 0;
        height: 100%;
        width: 10%;
    }
    .nav button {
        margin-top: 2vw;
        background: #65a1ac;
        border: none;
        border-radius: 12px;
        padding: 1vh;
        margin-left: 2vw;
    }
</style>

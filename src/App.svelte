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
    import MediaQuery from "./lib/MediaQuery.svelte";
    import logo from "./assets/logo.png";
    let items = ["Home", "Download", "Support", "FAQ"];
    let current_component = 0;
    const nav = (location: number) => {
        current_component = location;
    };
    const handle = (dir: String) => {
        if (dir == "n") {
            if (current_component == 3) {
                current_component = 0;
            }
            current_component += 1;
        } else {
            if (current_component == 0) {
                current_component = 3;
            }
            current_component -= 1;
        }
    };
</script>

<!--div class="nav">
    <div id="lang">
        <p>En</p>
        <img
            alt="english"
            src={"https://upload.wikimedia.org/wikipedia/commons/thumb/a/a5/Flag_of_the_United_Kingdom_%281-2%29.svg/1200px-Flag_of_the_United_Kingdom_%281-2%29.svg.png"}
        />
    </div>
</div-->
<header class="header">
    <MediaQuery query="(max-width: 650px)" let:matches>
        {#if !matches}
            <img src={logo} class="logo" />
            <ul class="nav">
                {#each items as item, i}
                    <li>
                        <button
                            on:click={() => {
                                nav(i);
                            }}>{item}</button
                        >
                    </li>
                {/each}
            </ul>
            <!-- else content here -->
        {:else}
            <button on:click={() => handle("p")}> Previous</button>
            <img src={logo} class="logo" />
            <button on:click={() => handle("n")}> Next </button>
        {/if}
    </MediaQuery>
    <MediaQuery query="(max-width: 650px)" let:matches>
        {#if matches}
            <div class="nav-buttons">
                <!-- else content here -->
            </div>
        {/if}
    </MediaQuery>
</header>
<div class="content">
    {#if current_component == 0}
        <Home />
    {:else if current_component == 1}
        <Download />
    {:else if current_component == 2}
        <Support />
    {:else if current_component == 3}
        <Faq />
    {:else}
        <p>Something went wrong</p>
    {/if}
</div>

<style>
    header {
        background: #1d202b;
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        padding: 30px 100px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        z-index: 10000;
    }

    header .logo {
        width: calc(8vh - 15%);
        text-decoration: none;
        font-size: 2em;
        text-transform: uppercase;
    }

    header ul {
        display: flex;
        justify-content: center;
        align-items: center;
    }

    header ul li {
        list-style: none;
        margin-left: 20px;
    }

    button {
        text-decoration: none;
        padding: 6px 15px;
        color: #fff;
        border-radius: 20px;
        transition: 0.5s;
        border: 0;
    }

    button:hover {
        background-color: #fff;
        color: #2b1055;
    }
    * {
        box-sizing: border-box;
        font-family: "Poppins", sans-serif;
        margin: 0;
        padding: 0;
        scroll-behavior: smooth;
    }
    :global(body) {
        background: #2e313b;
    }
    :global(h1:hover) {
        text-decoration: underline;
        transition: 0.5s;
    }
    li {
        list-style-type: none;
    }
    .content {
        background: #2e313b;
        position: absolute;
        width: 96%;
        padding: 2%;
    }

    @media screen and (max-width: 650px) {
        .header {
            justify-content: center;
        }
    }
</style>

<script lang="ts">
    import { fade } from "svelte/transition";
    // modules
    import Welcome from "./modules/Welcome.svelte";
    import Nerdfetch from "./modules/Nerdfetch.svelte";
    import Blog from "./modules/Blog.svelte";
    import Links from "./modules/Links.svelte";
    import Authors from "./modules/Authors.svelte";
    import Projects from "./modules/Projects.svelte";
    import About from "./modules/About.svelte";
    import Dd from "./modules/Dd.svelte";
    const modules = [
        Welcome,
        Nerdfetch,
        About,
        Links,
        Projects,
        Blog,
        Authors,
        Dd
    ];
    let sex: boolean = true;
    let scrollbox: any;
    let displayModules: any[] = [Welcome, Nerdfetch];
    let i: number = 2;
    const s = setInterval(() => {
        if (displayModules.length == modules.length) {
            clearInterval(s);
            sex = false;
        }
        
        scrollbox.scrollTop = scrollbox.scrollHeight;
        
        displayModules = [...displayModules, modules.at(i)];
        i++;
    }, 1500);
</script>

<article>
    <div bind:this={scrollbox} class="scrollbox">
        {#each displayModules as mod}
            <div>
                <svelte:component this={mod}></svelte:component>
            </div>
        {/each}
        {#if sex}
        <span style="height: {document.documentElement.scrollHeight * 0.75}px;" class="filler"></span>
        {/if}
    </div>
</article>

<style lang="scss">
    .filler{
        display: inline-block;
    }
    .scrollbox{
        overflow: scroll;
        overflow-x: hidden;
        position: absolute;
        left: 0px;
        right: 0px;
        bottom: 0px;
        top: 0px;
        padding: 1rem;
        padding-left: 0;
    }

    article {
        border-width: 3px;
        border-style: solid;
        border-color: var(--foreground);
        border-radius: 15px;
        align-items: left;
        position: absolute;
        top: 8px;
        bottom: 8px;
        left: 8px;
        right: 8px;
        overflow: hidden;
    }

    /* width */
    ::-webkit-scrollbar {
        width: 6px;
        display: hidden;
    }

    /* Track */
    ::-webkit-scrollbar-track {
        background: none;
        border-radius: 25px;
    }

    /* Handle */
    ::-webkit-scrollbar-thumb {
        background: var(--foreground);
        border-radius: 40px;
    }

    /* Handle on hover */
    ::-webkit-scrollbar-thumb:hover {
        display: show;
        background: var(--secondary);
    }
</style>

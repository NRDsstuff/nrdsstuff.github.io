<script lang="ts">
    
    import Cursor from "./lib/Cursor.svelte";
    import Prompt from "./lib/Prompt.svelte";
    
    // modules
    import Welcome from "./modules/Welcome.svelte";
    import Nerdfetch from "./modules/Nerdfetch.svelte";
    import Blog from "./modules/Blog.svelte";
    import Links from "./modules/Links.svelte";
    import Authors from "./modules/Authors.svelte";
    import Projects from "./modules/Projects.svelte";
    import About from "./modules/About.svelte";
</script>

<article>
    <Welcome></Welcome>
    <Nerdfetch></Nerdfetch>
    <About></About>
    <Links></Links>
    <Projects></Projects>
    <Authors></Authors>
    <Blog />
    <Prompt>
        <div>dd</div>
        <div>if=/dev/zero</div>
        <div>of=/dev/sda1</div>
        <Cursor />
    </Prompt>
</article>

<style lang="scss">

    .egg {
        text-decoration: none;
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
        padding: 1rem;
        padding-left: 0;
        overflow: scroll;
        overflow-x: hidden;
    }

    /* width */
    ::-webkit-scrollbar {
        width: 6px;
        display: hidden;
    }

    /* Track */
    ::-webkit-scrollbar-track {
        background: var(--foreground);
        border-radius: 25px;
    }

    /* Handle */
    ::-webkit-scrollbar-thumb {
        background: #888;
        border-radius: 40px;
    }

    /* Handle on hover */
    ::-webkit-scrollbar-thumb:hover {
        display: show;
        background: var(--secondary);
    }
</style>

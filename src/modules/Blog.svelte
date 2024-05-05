<script lang="ts">
    import SvelteMarkdown from "svelte-markdown";
    import CommandBody from "../lib/CommandBody.svelte";
    export let scrollbox: any;

    let noAnimation: boolean = false;

    async function loadMarkdownFile(
        index: number,
    ): Promise<{ content: string; date: string | undefined }> {
        const md = (await import(`../../blog/${index}.md?raw`)) as {
            default: string;
        };
        const content: string = md.default;

        const lines = content.split("\n");
        const date = lines.shift();
        return { content: lines.join("\n"), date };
    }

    var blogFiles = [];
    let index: number = 0;
    const markdownModules = import.meta.glob("../../blog/*.md");
    for (const modulePath in markdownModules) {
        blogFiles.push(modulePath.substring(11, modulePath.length - 3));
        index++;
    }
    blogFiles.sort((a, b) => +a - +b);
    console.log(blogFiles);

    let currentMdFile = blogFiles.length - 1;
    const prevBlog = () => {
        if (currentMdFile == 0) return;
        currentMdFile--;
        noAnimation = true;
    };

    const nextBlog = () => {
        if (currentMdFile == blogFiles.length - 1) return;
        currentMdFile++;
        noAnimation = true;
    };
</script>

{#await loadMarkdownFile(currentMdFile)}
    <CommandBody command="glow ???.md">loading blog...</CommandBody>
{:then md}
    <CommandBody {noAnimation} {scrollbox} command={`glow ${md.date}.md`}>
        <button on:click={prevBlog}>◀</button>
        {currentMdFile + 1} out of {blogFiles.length}
        <button on:click={nextBlog}>▶</button>
        <hr />
        <SvelteMarkdown source={md.content}></SvelteMarkdown>
    </CommandBody>
{:catch}
    <CommandBody command="glow ???.md">unable to load the blog...</CommandBody>
{/await}

<style lang="scss">
    button {
        background-color: var(--background);
        color: var(--foreground);
        border: none;
        cursor: pointer;
    }
</style>

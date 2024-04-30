<script lang="ts">
    import SvelteMarkdown from "svelte-markdown";
    import CommandBody from "../lib/CommandBody.svelte";

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
    blogFiles.sort((a, b) => +a - +b)
    console.log(blogFiles)

    let currentMdFile = blogFiles.length - 1;
    const prevBlog = () => {
        if (currentMdFile == 0) return;
        currentMdFile--;
    };

    const nextBlog = () => {
        if (currentMdFile == blogFiles.length - 1) return;
        currentMdFile++;
    };
</script>

{#await loadMarkdownFile(currentMdFile)}
    <CommandBody>
        <span slot="command">glow ???.md</span>
        <div slot="output" class="output">loading blog...</div>
    </CommandBody>
{:then md}
    <CommandBody>
        <span slot="command">
            glow
            {md.date}.md
        </span>
        <div slot="output" class="output">
            <button on:click={prevBlog}>◀</button>
            {currentMdFile + 1} out of {blogFiles.length}
            <button on:click={nextBlog}>▶</button>
            <hr />
            <SvelteMarkdown source={md.content}></SvelteMarkdown>
        </div>
    </CommandBody>
{:catch}
    <CommandBody>
        <span slot="command">glow ???.md</span>
        <div slot="output" class="output">unable to load the blog...</div>
    </CommandBody>
{/await}

<style lang="scss">
    button {
        background-color: var(--background);
        color: var(--foreground);
        border: none;
        cursor: pointer;
    }
</style>

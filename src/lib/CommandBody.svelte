<script lang="ts">
    import Prompt from "./Prompt.svelte";
    import Cursor from "./Cursor.svelte";
    import { fade } from "svelte/transition";

    export let command: string;
    export let ready: boolean = false;
    export let noAnimation: boolean = false;
    export let scrollbox: any = undefined;

    if (noAnimation) {
        ready = true;
    }

    let displayCommand: string = "";
    let i: number = 0;
    const stop = setInterval(() => {
        if (displayCommand.length === command.length) {
            ready = true;
            clearInterval(stop);
            // if (scrollbox != undefined) {
            //     scrollbox.scrollTop = scrollbox.scrollHeight;
            // }
        }
        displayCommand += command.charAt(i);
        i++;
    }, 50);
</script>

<div class="prompt">
    {#if ready}
        <Prompt>{command}</Prompt>
    {:else}
        <Prompt
            >{displayCommand}
            {#if !ready}
                <Cursor noBlinking={true}></Cursor>
            {/if}
        </Prompt>
    {/if}
</div>

{#if ready}
    <div class="output" in:fade={{ duration: 250 }}>
        <slot></slot>
    </div>
{/if}

<style lang="scss">
    .output {
        margin-bottom: 1rem;
        padding-left: 1rem;
    }
</style>

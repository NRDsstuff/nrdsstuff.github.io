<script lang="ts">
    import CommandBody from "../lib/CommandBody.svelte";
    export let scrollbox: any;
</script>

<CommandBody command="cat projects.txt" {scrollbox}>
    i made some weird stuff in the past, take a look
    <div class="links" style="padding-top: 1rem;">
        <a href="https://github.com/negative-zero-inft/ixni-docs"> 󰗊 ixni</a>
        <a
            href="https://www.figma.com/file/u7L9UTfSclI4EQpXwZhjsj/NUDL-6.0?type=design&t=o2y4LSfvZrUIQdJU-6"
        >
            󰏘 NUDL</a
        >
        <a href="https://github.com/NRDsstuff/nrdsstuff.github.io">
            󰇧 this website</a
        >
        <a href="https://github.com/raluvy95/raluvy95.github.io">
            󰇧 my girlfriend's website</a
        >
        <a href="https://github.com/negative-zero-inft/plugbot-neu">
             plugbot</a
        >
        <a href="https://github.com/negative-zero-inft/minusshell">
            󱆃 minusshell</a
        >
        <a href="https://github.com/negative-zero-inft/freeglo"> 󰏘 free glo</a>
        <a href="https://github.com/loqaCommunities"> 󰭹 loqa</a>
    </div>
</CommandBody>

<style lang="scss">
    .links {
        display: flex;
        flex-direction: column;
        gap: 0.5rem;
        a {
            width: fit-content;
        }
    }
</style>

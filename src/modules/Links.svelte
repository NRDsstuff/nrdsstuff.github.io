<script lang="ts">
    import CommandBody from "../lib/CommandBody.svelte";
    export let scrollbox: any;
</script>

<CommandBody command="cat links.txt" {scrollbox}>
    <div class="links">
        <a href="https://t.me/nrdeez"> Telegram</a>
        <a href="https://youtube.com/@nrdfoss"> YouTube</a>
        <a href="https://github.com/NRDsstuff"> Github</a>
        <a href="https://techhub.social/@nrd">󰫑 Mastodon</a>
        <a href="https://discord.gg/XuwCS8ydya">󰙯 Discord</a>
        <a href="https://buymeacoffee.com/nrdeez/">󰅶 Buy me a coffee</a>
        <a href="https://www.figma.com/@nrd"> Figma</a>
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

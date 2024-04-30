<script lang="ts">
    import CommandBody from "../lib/CommandBody.svelte";
</script>

<CommandBody>
    <span slot="command">cat authors.txt</span>
    <div slot="output">
        made with love by <a href="https://github.com/raluvy95"
            >CatNowblue</a
        >
        and <a href="https://github.com/NRDsstuff">NRD</a>
    </div>
</CommandBody>
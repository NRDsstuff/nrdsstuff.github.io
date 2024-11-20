<script lang="ts">
    import CommandBody from "../lib/CommandBody.svelte";
    export let scrollbox: any;
</script>

<CommandBody command="cat authors.txt" {scrollbox}>
    made with love by <a href="https://github.com/raluvy95">CatNowblue</a>
    and <a href="https://github.com/NRDsstuff">NRD</a>
</CommandBody>

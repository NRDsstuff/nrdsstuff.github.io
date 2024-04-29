<script>
    import { onMount } from "svelte";
    import Body from "./Body.svelte";

    onMount(() => {
        const root = document.querySelector(":root");
        if (!root) {
            throw new Error(
                "Your browser doesn't handle :root css. Your browser sucks.",
            );
        }
    });
</script>

<Body />

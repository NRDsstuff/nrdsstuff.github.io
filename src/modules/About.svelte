<script lang="ts">
    import CommandBody from "../lib/CommandBody.svelte";
    export let scrollbox: any;
</script>

<CommandBody command="cat about.txt" {scrollbox}>
    hey! i'm just some random guy from warsaw, poland who likes to do stuff.<br
    />
    namely, i like to design user interfaces, program, hack my devices, nerd out
    about spoken languages and (very rarely) draw.<br />
    i'm a strong believer in open source and linux.<br /> hell, all of my x86
    devices run a linux distribution, nixos.<br />
    i can fluently speak polish (native), english (main mental language), ixni and
    toki pona<br />
    i have a bunch of random smartphones, none of them made by ap*le...<br />
    and most of them are running a custom ROM<br />
    i'm a huge fan of XR (AR/VR) and i own a meta quest 2. (aldo i want a quest 3)<br
    />
    gonk 🤑<br />
</CommandBody>

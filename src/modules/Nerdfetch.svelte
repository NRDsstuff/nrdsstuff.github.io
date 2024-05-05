<script lang="ts">
    import { cats } from "../catascii";
    import { yearsOld, timeFormat } from "../time";
    import CommandBody from "../lib/CommandBody.svelte";

    let seconds: number = 0;

    const myAge = yearsOld(Date.now(), Date.parse("15 Aug 2008 00:00:00 GMT"));
    let randomCat = cats[Math.floor(Math.random() * cats.length)];
    setInterval(() => {
        seconds++;
    }, 1000);

    function changeCat() {
        randomCat = cats[Math.floor(Math.random() * cats.length)];
    }
    export let scrollbox: any;
</script>

<CommandBody command="nerdfetch --balls" {scrollbox}>
    <div class="neofetch">
        <div class="kitty">
            <!-- svelte-ignore a11y-click-events-have-key-events -->
            <!-- svelte-ignore a11y-no-noninteractive-element-interactions -->
            <pre on:click={changeCat}>{randomCat}</pre>
        </div>
        <div class="info">
            󰄛 Alex, NRD<br />
            󰊝 he/him<br />
             Europe, Poland<br />
             {myAge}<br />
            <hr />
            󰇄 Negative Zero Shitbox PRO<br />
             i5-10400f (8) @ 4.3GHz<br />
            󰍛 16 GB RAM<br />
            󰍛 NVIDIA GeForce RTX 3060<br />
            <hr />
            󰓶 Microsoft Surface Pro 3<br />
             i5-4300U (4) @ 2.9GHz<br />
            󰍛 8 GB RAM<br />
            <hr />
             Google Pixel 7 (panther) (main)<br />
             Redmi note 11 (spesn)<br />
             Samsung A52 (broken)<br />
             Redmi note 10S (rosemary)<br />
             Redmi note 9 (merlinnfc) (broken)<br />
             Redmi note 8 (ginkgo)<br />
             Huawei P Smart 2018 (fig-lx1)<br />
            <hr />
             NixOS<br />
             6.1<br />
             zsh<br />
             GNOME<br />
            <hr />
             you wasted {timeFormat(seconds)}<br />
            <a class="egg" href="egg.png" target="_blank">󰪯 egg</a>
        </div>
    </div>
</CommandBody>

<style lang="scss">
    .neofetch {
        display: flex;
        flex-direction: row;
        gap: 2rem;
    }

    .kitty {
        font-family: "Fira Code";
        font-size: 2.5rem;
        height: 17rem;
        width: 17rem;
        margin: 1rem;
        margin-right: 0;
        display: flex;
        justify-content: center;
        align-items: center;
        user-select: none;
    }

    @media only screen and (max-width: 650px) {
        // mobile check lol
        .neofetch {
            align-items: center;
            flex-direction: column;
        }
        .kitty {
            margin-right: 1rem;
        }
    }
</style>

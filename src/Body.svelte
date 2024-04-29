<script lang="ts">
    import { yearsOld, timeFormat } from "./time";
    import { cats } from "./catascii";
    import Cursor from "./lib/Cursor.svelte";
    import Prompt from "./lib/Prompt.svelte";
    import CommandBody from "./lib/CommandBody.svelte";
    import Blog from "./lib/Blog.svelte";

    let seconds: number = 0;

    const myAge = yearsOld(Date.now(), Date.parse("15 Aug 2008 00:00:00 GMT"));
    let randomCat = cats[Math.floor(Math.random() * cats.length)];
    setInterval(() => {
        seconds++;
    }, 1000);

    function changeCat() {
        randomCat = cats[Math.floor(Math.random() * cats.length)];
    }
</script>

<article>
    <div class="welcomeMessage">
        Welcome to nrdsstuff.github.io!<br />
        This is NRD's personal website.<br />
        By the way, this page is
        <a
            href="https://github.com/nrdsstuff/nrdsstuff.github.io"
            target="_blank">open source</a
        >!
    </div>
    <CommandBody>
        <div slot="command">
            nerdfetch <a class="egg" href="kys.png" target="_blank">
                --balls
            </a>
        </div>
        <div slot="output">
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
                     you wasted {timeFormat(seconds)}<br />
                    <hr />
                    󰓶 Microsoft Surface Pro 3<br />
                     i5-4300U (4) @ 2.9GHz<br />
                    󰍛 8 GB RAM<br />
                    <hr />
                     NixOS<br />
                     6.1<br />
                     zsh<br />
                     GNOME<br />
                    <hr />
                     Google Pixel 7 (panther) (main)<br />
                     Redmi note 11 (spesn)<br />
                     Redmi note 10S (rosemary)<br />
                     Redmi note 9 (merlinnfc) (broken)<br />
                     Redmi note 8 (ginkgo)<br />
                     Huawei P Smart 2018 (fig-lx1)<br />
                    <hr />
                    <!-- meow did you finally fix the deployment issue? xd ajjta <3 nope but im gonna rice the website -->
                    <a class="egg" href="egg.png" target="_blank">󰪯 egg</a>
                </div>
            </div>
        </div>
    </CommandBody>
    <CommandBody>
        <div slot="command">cat links.txt</div>
        <div slot="output">
            <div class="links">
                <a href="https://t.me/nrdeez"> Telegram</a>
                <a href="https://youtube.com/@nrdfoss"> YouTube</a>
                <a href="https://github.com/NRDsstuff"> Github</a>
                <a href="https://techhub.social/@nrd">󰫑 Mastodon</a>
                <a href="https://discord.gg/XuwCS8ydya">󰙯 Discord</a>
                <a href="https://buymeacoffee.com/nrdeez/">󰅶 Buy me a coffee</a>
            </div>
        </div>
    </CommandBody>
    <CommandBody>
        <span slot="command">cat authors.txt</span>
        <div slot="output">
            made with love by <a href="https://github.com/raluvy95"
                >CatNowblue</a
            >
            and <a href="https://github.com/NRDsstuff">NRD</a>
        </div>
    </CommandBody>
    <CommandBody>
        <span slot="command">cat about.txt</span>
        <div slot="output">
            hey! i'm just some random guy from warsaw, poland who likes to do
            stuff.<br />
            namely, i like to design user interfaces, program, hack my devices, nerd
            out about spoken languages and (very rarely) draw.<br />
            i'm a strong believer in open source and linux.<br /> hell, all of
            my x86 devices run a linux distribution, nixos.<br />
            i can fluently speak polish (native), english (main mental language),
            ixni and toki pona<br />
            i have a bunch of random smartphones, none of them made by ap*le...<br
            />
            and most of them are running a custom ROM<br />
            i'm a huge fan of XR (AR/VR) and i own a meta quest 2. (aldo i want a
            quest 3)<br />
            gonk 🤑<br /> jer jab tura anax aleks - CNB
        </div>
    </CommandBody>
    <CommandBody>
        <span slot="command">cat projects.txt</span>
        <div slot="output">
            i made some weird stuff in the past, take a look
            <div class="links" style="padding-top: 1rem;">
                <a href="https://github.com/negative-zero-inft/ixni-docs"
                    >󰗊 ixni</a
                >
                <a
                    href="https://www.figma.com/file/u7L9UTfSclI4EQpXwZhjsj/NUDL-6.0?type=design&t=o2y4LSfvZrUIQdJU-6"
                    >󰏘 NUDL</a
                >
                <a href="https://github.com/NRDsstuff/nrdsstuff.github.io"
                    >󰇧 this website</a
                >
                <a href="https://github.com/raluvy95/raluvy95.github.io"
                    >󰇧 my girlfriend's website</a
                >
                <a href="https://github.com/negative-zero-inft/plugbot-neu"
                    > plugbot</a
                >
                <a href="https://github.com/negative-zero-inft/minusshell"
                    >󱆃 minusshell</a
                >
                <a href="https://github.com/negative-zero-inft/freeglo"
                    >󰏘 free glo</a
                >
                <a href="https://github.com/loqaCommunities">󰭹 loqa</a>
            </div>
        </div>
    </CommandBody>
    <Blog />
    <Prompt>
        <div>dd</div>
        <div>if=/dev/zero</div>
        <div>of=/dev/sda1</div>
        <Cursor />
    </Prompt>
</article>

<style lang="scss">
    .welcomeMessage {
        margin-left: 1rem;
        margin-bottom: 1rem;
    }

    .egg {
        text-decoration: none;
    }

    article {
        border-width: 3px;
        border-style: solid;
        border-color: var(--foreground);
        border-radius: 15px;
        align-items: left;
        position: absolute;
        top: 8px;
        bottom: 8px;
        left: 8px;
        right: 8px;
        padding: 1rem;
        padding-left: 0;
        overflow: scroll;
        overflow-x: hidden;
    }

    /* width */
    ::-webkit-scrollbar {
        width: 6px;
        display: hidden;
    }

    /* Track */
    ::-webkit-scrollbar-track {
        background: var(--foreground);
        border-radius: 25px;
    }

    /* Handle */
    ::-webkit-scrollbar-thumb {
        background: #888;
        border-radius: 40px;
    }

    /* Handle on hover */
    ::-webkit-scrollbar-thumb:hover {
        display: show;
        background: var(--secondary);
    }

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

    .links {
        display: flex;
        flex-direction: column;
        gap: 0.5rem;
        a {
            width: fit-content;
        }
    }

    hr {
        color: var(--foreground);
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

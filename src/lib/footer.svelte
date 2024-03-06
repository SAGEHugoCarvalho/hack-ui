<script>
    import { getContext } from 'svelte';
    const { SubmitMessage } = getContext('messageCtx');

    export let textMessage = "";

    function handleSubmit(e) {
        if (e.key == "Enter") {
            SendMessage();
        }
    }

    function SendMessage() {
        if (textMessage.length != 0) {
            SubmitMessage(textMessage);
            setTimeout(() => {
                textMessage = "";
            }, 10);
        }
    }
</script>

<section class="footer">
    <textarea bind:value={textMessage} name="prompt" id="prompt" placeholder="Say something like 'Give me a list of all available suppliers'" on:keydown={handleSubmit}></textarea>
    <div class="icon-cabinet">
        <div style="height: 20px;">
            <button on:click={() => {}} style="margin-right: 10px;">
                <img class="icon" src="attachment.png" alt="attachment">
            </button>
            <button on:click={() => {}}>
                <img class="icon" src="voice.png" alt="voice">
            </button>
        </div>
        <button on:click={() => { SendMessage() }}>
            <img class="icon" src="send.png" alt="send">
        </button>
    </div>
</section>

<style>
    .footer{
        padding: 10px;
    }

    button {
        background-color: transparent;
        border: none;
        color: inherit;
        font: inherit;
        cursor: pointer;
        padding: 0;
        margin: 0;
    }

    textarea {
        width: 100%;
        height: 4em;
        border: none;
        outline: none;
        resize: none;
    }

    .icon-cabinet {
        display: flex;
        justify-content: space-between;
    }

    .icon {
        height: 20px;
    }
</style>
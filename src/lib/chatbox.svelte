<script>
    let messages = [];

    export function AddMessage(NewMessage) {
        messages.push(NewMessage);
        messages = messages;
        setTimeout(() => {
            AutoScroll();
        }, 10);
    }

    function AutoScroll() {
        var scrollableElement = document.getElementById("scrollable");
        scrollableElement.scrollTop = scrollableElement.scrollHeight;
    }
</script>

<section class="chatbox-section" id="scrollable">
    {#each messages as message, i}
        {#if i % 2 == 0}
            <div class="chat-bubble chat-bubble-user">
                <pre class="sub-bubble">{message}</pre>
            </div>
        {:else}
            <div class="chat-bubble chat-bubble-copilot">
                <pre class="sub-bubble">{@html message}</pre>
            </div>
        {/if}
    {/each}
</section>

<style>
    .chatbox-section{
        flex-grow: 1;
        max-height: 772px;
        padding: 20px 20px 0 20px;
        overflow: auto;
    }

    .chat-bubble {
        margin-bottom: 20px;
        display: flex;
    }

    .chat-bubble-user {
        justify-content: flex-end;
    }

    .chat-bubble-user pre {
        background-color: #a9d3f2;
    }

    .chat-bubble-copilot {
        justify-content: flex-start;
    }

    .sub-bubble {
        max-width: 70%;
        padding: 10px;
        border-radius: 10px;
        box-shadow: 0 0 10px rgb(200, 200, 200);
        white-space: pre-wrap;
    }
</style>
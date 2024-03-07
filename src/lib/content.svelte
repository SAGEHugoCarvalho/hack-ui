<script>
    export let messages = [
        //"Give me a list of all available suppliers. Give me a list of all available suppliers. Give me a list of all available suppliers. Give me a list of all available suppliers.",
        //"List of suppliers:* 1* 2* 3* 4* 5"
    ];

    export function AddMessage(NewMessage) {
        messages.push(NewMessage);
        messages = messages;
    }
</script>

<section class="content">
    {#each messages as message, i}
        {#if i % 2 == 0}
            <div class="bubble bubble-user">
                <div class="sub-bubble sub-bubble-user">{message}</div>
            </div>
        {:else}
            <div class="bubble bubble-copilot">
                <div class="sub-bubble">{message}</div>
            </div>
        {/if}
    {/each}
</section>

<style>
    .content{
        margin-bottom: -15px;
        min-height: 570px;
        padding: 20px 20px 0 20px;
    }

    .bubble {
        margin-bottom: 20px;
        display: flex;
    }

    .bubble-user {
        justify-content: flex-end;
    }

    .bubble-copilot {
        justify-content: flex-start;
    }

    .sub-bubble {
        max-width: 70%;
        padding: 10px;
        border-radius: 10px;
        box-shadow: 0 0 10px rgb(200, 200, 200);
    }

    .sub-bubble-user {
        background-color: #a9d3f2;
    }
</style>
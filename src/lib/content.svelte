<section class="content">
    <div class="bubble bubble-user">
        <div class="sub-bubble sub-bubble-user">
            Give me a list of all available suppliers. Give me a list of all available suppliers. Give me a list of all available suppliers. Give me a list of all available suppliers.
        </div>
    </div>
    <div class="bubble bubble-copilot">
        <div class="sub-bubble">
            List of suppliers:
            * 1
            * 2
            * 3
            * 4
            * 5
        </div>
    </div>
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
        width: 70%;
        padding: 10px;
        border-radius: 10px;
        box-shadow: 0 0 10px rgb(200, 200, 200);
    }

    .sub-bubble-user {
        background-color: #a9d3f2;
    }
</style>
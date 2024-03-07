<script>
    import "$lib/global.css";
    import { marked } from "marked";
    import { setContext } from 'svelte';
    import Header from "$lib/header.svelte"
    import Chatbox from "$lib/chatbox.svelte"
    import Input from "$lib/input.svelte"
	
	setContext('messageCtx', { SubmitMessage });
	
    let child;

	function SubmitMessage(message) {
        child.AddMessage(message);
        BackendCall(message);
	}

    function BackendCall(prompt) {

        const url = 'http://127.0.0.1:8000/ask/';
        const options = {
            method: 'POST',
            headers: { 'Content-Type': 'application/json'},
            body: JSON.stringify({ question: prompt })
        };

        fetch(url, options)
            .then(response => {
                if (!response.ok) {
                    throw new Error('Network response was not ok');
                }

                return response.json();
            })
            .then(data => {
                child.AddMessage(marked(data.output));
            })
            .catch(() => {
                child.AddMessage('An unexpected problem occured. Please try again.');
            });
    }
</script>

<div class="page">
    <Header></Header>
    <img class="gradient" src="gradient.png" alt="gradient">
    <Chatbox bind:this={child}></Chatbox>
    <img class="gradient" src="solid.png" alt="gradient">
    <Input></Input>
</div>

<style>
    .page {
        display: flex;
        flex-direction: column;
        height: 100vh;
    }

    .gradient {
        width: 100%;
        height: 5px;
    }
</style>
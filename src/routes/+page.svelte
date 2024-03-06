<script>
    import "$lib/global.css";
    import { setContext } from 'svelte';
    import Header from "$lib/header.svelte"
    import Content from "$lib/content.svelte"
    import Footer from "$lib/footer.svelte"
	
	setContext('messageCtx', { SubmitMessage });
	
    let child;

	async function SubmitMessage(message) {
        child.AddMessage(message);
        BackendCall(message);
	}

    function BackendCall(prompt) {

        const url = 'http://127.0.0.1:8000/ask';

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
                child.AddMessage(data.output);
            })
            .catch(error => {
                child.AddMessage('An unexpected problem occured. Please try again.');
            });
    }
</script>

<div>
    <Header></Header>
    <img class="gradient" src="gradient.png" alt="gradient">
    <Content bind:this={child}></Content>
    <img class="gradient" src="solid.png" alt="gradient">
    <Footer></Footer>
</div>

<style>
    .gradient {
        width: 100%;
        height: 5px;
        margin: -5px 0;
    }
</style>
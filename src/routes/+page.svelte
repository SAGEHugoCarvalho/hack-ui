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
        //const res = await BackendCall(message);
        //child.AddMessage(res.Content);

        setTimeout(() => {
            child.AddMessage("Reply from the backed...");
        }, 2000);
	}

    async function BackendCall(prompt) {

        const url = 'http://127.0.0.1/8000';

        const options = {
            method: 'POST',
            headers: { 'Content-Type': 'application/json'},
            body: JSON.stringify(prompt)
        };

        fetch(url, options)
            .then(response => {
                if (!response.ok) {
                    throw new Error('Network response was not ok');
                }

                return response.json();
            })
            .then(data => {
                console.log('Response:', data);
            })
            .catch(error => {
                console.error('There was a problem with the request:', error);
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
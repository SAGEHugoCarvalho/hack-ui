<script>
    import "$lib/global.css";
    import Header from "$lib/header.svelte"
    import Content from "$lib/content.svelte"
    import Footer from "$lib/footer.svelte"
</script>

<div>
    <Header></Header>
    <img class="gradient" src="gradient.png" alt="gradient">
    <Content></Content>
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
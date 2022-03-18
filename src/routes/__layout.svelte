<script>
	import Title from '$lib/Title.svelte';
	import '../styles/global.css';
</script>

<header>
	<Title title="S4mLab Gaming Guide" />
</header>

<main>
	<slot />
</main>

<footer>
	<p>Copyright 2022 S4mLab Gaming Guide</p>
</footer>

<style>
	header {
		display: flex;
		justify-content: center;
	}
	main {
		max-width: 960px;
		margin: 20px auto;
	}
	footer {
		text-align: center;
	}
</style>

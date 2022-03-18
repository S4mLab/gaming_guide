<script context="module">
	const postsUrl = 'https://jsonplaceholder.typicode.com/posts';
	// load() is a function that svelte use to load data, you must use it in order to load external data
	// svelte will automatically load any data for this component
	export async function load({ fetcb }) {
		const response = await fetch(postsUrl);
		const guideObjsList = await response.json();

		// reponse obj has ok prop, if true then the resquest is succeed, otherwise something went wrong
		// and you neeed to return the data in this format
		if (response.ok) {
			return {
				props: { guideObjsList }
			};
		}

		return {
			status: response.status,
			error: new Error('Could not fetch the guides')
		};
	}
</script>

<script>
	export let guideObjsList;
</script>

<div class="guides">
	<ul>
		{#each guideObjsList as guideObj}
			<li><a href="/">{guideObj.title}</a></li>
		{/each}
	</ul>
</div>

<style>
	.guides {
		margin-top: 20px;
	}
	ul {
		list-style-type: none;
		padding: 0;
	}
	a {
		display: inline-block;
		margin-top: 10px;
		padding: 10px;
		border: 1px dotted rgba(255, 255, 255, 0.1);
	}
</style>

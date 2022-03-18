<script context="module">
	export async function load({ fetch, params }) {
		const guideId = params.id;
		const guideUrl = `https://jsonplaceholder.typicode.com/posts/${guideId}`;
		try {
			const response = await fetch(guideUrl);
			const guideObj = await response.json();
			return {
				props: {
					guideObj
				}
			};
		} catch (err) {
			return {
				error: err
			};
		}
	}
</script>

<script>
	export let guideObj;
</script>

<div class="guide">
	<h2>{guideObj.title}</h2>
	<p>{guideObj.body}</p>
</div>

<style>
	.guide {
		margin-top: 40px;
		padding: 10px;
		border: 1px dotted rgba(255, 255, 255, 0.2);
	}
</style>

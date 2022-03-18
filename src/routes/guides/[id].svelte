<script context="module">
	export async function load({ fetch, params }) {
		const guideId = params.id;
		const guideUrl = `https://jsonplaceholder.typicode.com/posts/${guideId}`;
		const response = await fetch(guideUrl);
		const guideObj = await response.json();

		if (response.ok) {
			return {
				props: {
					guideObj
				}
			};
		}

		return {
			status: 301,
			redirect: '/guides'
		};
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

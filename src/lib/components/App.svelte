<script>
	import { Canvas } from '@threlte/core';
	import Scene from './Scene.svelte';
</script>

<div>
	<div style="position: fixed; pointer-events:none">
		<div class="callout">
			<p>Hover Around and</p>
			<p>Click the logo!</p>
		</div>
	</div>
	<Canvas>
		<Scene />
	</Canvas>
</div>

<style>
	div {
		width: 100%;
		height: 100%;
	}
	p {
		padding: 0;
		margin: 0;
	}
	.callout {
		pointer-events: none;
		font-size: 1.25rem; /* 20px */
		line-height: 1.75rem; /* 28px */
		background-color: rgb(255 255 255 / 0.8);
		width: fit-content;
		height: fit-content;
		text-align: center;
		border-radius: 1rem;
		padding: 0.5rem;
		margin: 1rem;
	}
</style>

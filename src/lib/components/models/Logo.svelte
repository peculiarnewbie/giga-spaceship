<!--
Auto-generated by: https://github.com/threlte/threlte/tree/main/packages/gltf
Command: npx @threlte/gltf@2.0.3 Giga Logo.glb --transform
-->

<script>
	import { AddEquation, CustomBlending, Group, LessEqualDepth, OneFactor } from 'three';
	import { T, forwardEventHandlers } from '@threlte/core';
	import { useGltf } from '@threlte/extras';
	import { useTexture } from '@threlte/extras';
	export const ref = new Group();
	const gltf = useGltf('/Giga Logo-transformed.glb', { useDraco: true });
	gltf.then((model) => {
		function alphaFix(material) {
			material.transparent = true;
			material.alphaToCoverage = true;
			material.depthFunc = LessEqualDepth;
			material.depthTest = true;
			material.depthWrite = true;
		}
		alphaFix(model.materials.spaceship_racer);
		alphaFix(model.materials.cockpit);
	});
	const component = forwardEventHandlers();

	import { interactivity } from '@threlte/extras';
	import { spring } from 'svelte/motion';
	interactivity();
	const scale = spring(0.6);
</script>

<T is={ref} dispose={false} {...$$restProps} bind:this={$component}>
	{#await gltf}
		<slot name="fallback" />
	{:then gltf}
		<T.Group
			scale={$scale}
			on:pointerenter={() => scale.set(0.9)}
			on:pointerleave={() => scale.set(0.6)}
			rotation={[0, -Math.PI * 0.5, 0]}
			position={[1.95, -1, -1.735]}
			on:click={() =>
				(window.location.href =
					'https://docs.google.com/forms/d/e/1FAIpQLSc1rVF4HuMQ07XOTBa9e1VX71u261NNhFck5QQ0E7szzw9hWg/viewform')}
		>
			<T.Mesh geometry={gltf.nodes.Cube002.geometry} material={gltf.materials['Material.001']} />
			<T.Mesh geometry={gltf.nodes.Cube002_1.geometry} material={gltf.materials['Material.002']} />
			<T.Mesh geometry={gltf.nodes.Cube002_2.geometry} material={gltf.materials['Material.003']} />
			<T.Mesh geometry={gltf.nodes.Cube002_3.geometry} material={gltf.materials['Material.004']} />
		</T.Group>
	{:catch error}
		<slot name="error" {error} />
	{/await}
	<slot {ref} />
</T>

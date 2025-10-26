<script lang="ts">
	import { SvelteFlow, Controls, Background, MiniMap, type Node, type Edge } from '@xyflow/svelte';

	import '@xyflow/svelte/dist/style.css';

	let nodes = $state.raw<Node[]>([
		{
			id: '1',
			data: { label: 'Hello' },
			position: { x: 0, y: 0 }
		},
		{
			id: '2',
			data: { label: 'World' },
			position: { x: 100, y: 150 }
		}
	]);

	let edges = $state.raw<Edge[]>([
		{
			id: '1-2',
			source: '1',
			target: '2'
		}
	]);
</script>

<div style:height="100vh" class="test">
	<SvelteFlow proOptions={{ hideAttribution: true }} bind:nodes bind:edges>
		<Controls />
		<Background />
		<MiniMap />
	</SvelteFlow>
</div>

<style>
	:global(.svelte-flow) {
		--xy-node-background-color-default: #dda;
		--xy-node-border-default: 15px solid #1a192b;
		--xy-edge-stroke-width-default: 10px;
		--xy-node-color-default: #dda;
	}

	:global(.svelte-flow__handle) {
		opacity: 0;
	}

	:global(.svelte-flow__node-default) {
		padding: 20px;
	}
</style>

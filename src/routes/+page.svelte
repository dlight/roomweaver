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
	<SvelteFlow proOptions={{ hideAttribution: true }} bind:nodes bind:edges fitView>
		<Controls />
		<Background />
		<MiniMap />
	</SvelteFlow>
</div>

<style>
	:global(.svelte-flow) {
		--xy-node-color-default: #000;
		--xy-node-background-color-default: #f0f0c4;
	}

	:global(.svelte-flow__node) {
		min-width: 10px;
		width: auto;
	}
</style>

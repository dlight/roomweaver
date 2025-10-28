<script lang="ts">
	import {
		SvelteFlow,
		Controls,
		Background,
		MiniMap,
		type Node,
		type Edge,
		type NodeTypes
	} from '@xyflow/svelte';
	import '@xyflow/svelte/dist/style.css';

	import AbilityNode from '$lib/components/AbilityNode.svelte';

	const nodeTypes: NodeTypes = {
		ability: AbilityNode
	};

	let nodes = $state.raw<Node[]>([
		{
			id: '1',
			type: 'ability',
			data: { name: 'Dash', type: 'move' },
			position: { x: 0, y: 0 }
		},
		{
			id: '2',
			type: 'ability',
			data: { name: 'Ice Gun', type: 'weapon' },

			position: { x: 60, y: 30 }
		},
		{
			id: '3',
			type: 'ability',
			data: { name: 'Vanish', type: 'spell' },
			position: { x: 140, y: 30 }
		}
	]);

	let edges = $state.raw<Edge[]>([
		{
			id: '1-2',
			source: '1',
			target: '2'
		},
		{
			id: '2-3',
			source: '2',
			target: '3'
		}
	]);
</script>

<div style:height="100vh" class="test">
	<SvelteFlow proOptions={{ hideAttribution: true }} {nodeTypes} bind:nodes bind:edges fitView>
		<Controls />
		<Background />
		<MiniMap />
	</SvelteFlow>
</div>

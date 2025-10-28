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

	import Ability from '$lib/components/Ability.svelte';

	const nodeTypes: NodeTypes = {
		ability: Ability
	};

	let nodes = $state.raw<Node[]>([
		{
			id: '1',
			type: 'ability',
			data: { label: 'Hello' },
			position: { x: 0, y: 0 }
		},
		{
			id: '2',
			type: 'ability',
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
	<SvelteFlow proOptions={{ hideAttribution: true }} {nodeTypes} bind:nodes bind:edges fitView>
		<Controls />
		<Background />
		<MiniMap />
	</SvelteFlow>
</div>

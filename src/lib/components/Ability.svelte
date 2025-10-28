<script lang="ts">
	import { Handle, Position, type NodeProps } from '@xyflow/svelte';

	let { data }: NodeProps = $props();
</script>

<div class="ability-node">
	<div class="ability-content">
		{data.label}
	</div>
	<Handle type="target" position={Position.Top} />
	<Handle type="source" position={Position.Bottom} />
</div>

<style>
	.ability-node {
		padding: 10px;
		border-radius: 5px;
		background: #f0f0c4;
		border: 1px solid #000;
		min-width: 10px;
		width: auto;
	}

	.ability-content {
		text-align: center;
	}
</style>

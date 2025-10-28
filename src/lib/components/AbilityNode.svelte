<script lang="ts">
	import typia from 'typia';
	import { match } from 'ts-pattern';

	import { Handle, Position, type NodeProps } from '@xyflow/svelte';

	type AbilityType = 'move' | 'weapon' | 'spell';

	function getAbilityColor(type: AbilityType): string {
		return match(type)
			.with('move', () => '#a8d5e2')
			.with('weapon', () => '#ff6b6b')
			.with('spell', () => '#9ae6b4')
			.exhaustive();
	}

	type Ability = {
		name: string;
		type: AbilityType;
	};

	let { data }: NodeProps = $props();

	let ability = $state<Ability>(typia.assert<Ability>(data));
</script>

<div class="ability-node" style="background: {getAbilityColor(ability.type)}">
	<div class="ability-content">
		{ability.name}
	</div>
	<Handle type="target" position={Position.Left} />
	<Handle type="source" position={Position.Right} />
</div>

<style>
	.ability-node {
		padding: 0.6em;
		border-radius: 5px;
		border: 1px solid #000;

		font-size: 12px;
		line-height: 20%;
	}

	.ability-node:hover {
		filter: brightness(110%);
	}
</style>

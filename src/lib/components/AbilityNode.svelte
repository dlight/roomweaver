<script lang="ts">
	import { Handle, Position, type NodeProps } from '@xyflow/svelte';
	import typia from 'typia';

	type AbilityType = 'move' | 'attack';

	const moveColor = '#a8d5e2';
	const attackColor = '#ff6b6b';

	type Ability = {
		label: string;
		type: AbilityType;
	};

	const isAbility = typia.createIs<Ability>();

	let { data }: NodeProps = $props();

	if (!isAbility(data)) {
		throw new Error(
			`Invalid ability data: expected 'move' or 'attack', got ${JSON.stringify(data)}`
		);
	}

	let ability = $state<Ability>(data);

	const backgroundColor = $derived(ability.type === 'move' ? moveColor : attackColor);

	function toggleType() {
		ability.type = ability.type === 'move' ? 'attack' : 'move';
	}
</script>

<div class="ability-node" style="background: {backgroundColor}">
	<div class="ability-content">
		{ability.label}
	</div>
	<button class="toggle-btn" onclick={toggleType}>
		Toggle ({ability.type})
	</button>
	<Handle type="target" position={Position.Left} />
	<Handle type="source" position={Position.Right} />
</div>

<style>
	.ability-node {
		padding: 8px;
		border-radius: 5px;
		border: 1px solid #000;
		min-width: 10px;
		width: auto;
	}

	.ability-content {
		text-align: center;
	}

	.toggle-btn {
		margin-top: 8px;
		padding: 2px 4px;
		font-size: 10px;
		border-radius: 3px;
		border: 1px solid rgba(0, 0, 0, 0.2);
		background: rgba(255, 255, 255, 0.8);
		cursor: pointer;
		width: 100%;
	}

	.toggle-btn:hover {
		background: rgba(255, 255, 255, 1);
	}
</style>

<script lang="ts">
	import { Transition } from '@animotion/core'

	let items = $state([1, 2, 3, 4])
	let layout = $state('flex gap-4')
</script>

<Transition>
	<p class="text-6xl font-bold drop-shadow-sm">🪄 Layout Animations</p>
</Transition>

<Transition
	do={() => {
		items = [1, 2, 3, 4]
		layout = 'flex gap-4'
	}}
	class="mt-16"
>
	<div class={layout}>
		{#each items as item, i (item)}
			<Transition
				class="grid h-[180px] w-[180px] place-content-center rounded-2xl border-t-2 border-white bg-gray-200 text-6xl font-semibold text-black shadow-2xl"
				entry="rotate"
				duration={2}
				delay={i * 0.1}
				visible
			>
				{item}
			</Transition>
		{/each}
	</div>
</Transition>

<Transition
	transitions={[
		() => {
			layout = 'grid grid-cols-2 grid-rows-2 gap-4'
			items = [4, 3, 2, 1]
		},
		() => {
			layout = 'grid grid-cols-2 grid-rows-2 gap-4'
			items = [2, 1, 4, 3]
		},
		() => {
			layout = 'grid grid-cols-2 grid-rows-2 gap-4'
			items = [4, 3, 2, 1]
		},
		() => {
			layout = 'grid grid-cols-2 grid-rows-2 gap-4'
			items = [1, 2, 3, 4]
		},
		() => (layout = 'flex gap-4'),
	]}
/>

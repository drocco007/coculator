<script>
	export let pack_cost;
	export let pack_size;
	export let unit_ounces;

	export let bogo_buy;
	export let bogo_get;

	$: bogo_quantity_cost = +bogo_buy * +pack_cost;
	$: bogo_total_units = (+bogo_buy + +bogo_get) * +pack_size;
	$: bogo_total_ounces = bogo_total_units * +unit_ounces;

	$: _dollars_per_ounce = bogo_total_units
		? bogo_quantity_cost / bogo_total_ounces
		: +pack_cost / (+pack_size * +unit_ounces);
	$: _can_equivalent = _dollars_per_ounce * 12;

	$: cents_per_ounce = _dollars_per_ounce && (_dollars_per_ounce * 100).toFixed(1);
	$: can_equivalent = _can_equivalent && _can_equivalent.toFixed(2);
</script>

<div class="flex flex-wrap mb-6 pb-6 max-w-screen-lg place-content-center">
	<div class="basis-2/3 flex-none lg:ml-0 ml-4">
		<div class="grid grid-cols-6 gap-x-1 gap-y-2">
			<label class="block">
				<!-- $ -->
				<input
					type="text"
					class="mt-0 block w-full bg-transparent px-0.5 py-0.5 border-0 border-b-2 border-primary-800 focus:ring-0 focus:border-primary-500"
					placeholder="Pack cost"
					bind:value={pack_cost}
				/>
			</label>
			<span class="block text-center">for a</span>
			<label class="block">
				<input
					type="text"
					class="mt-0 block w-full bg-transparent px-0.5 py-0.5 border-0 border-b-2 border-primary-800 focus:ring-0 focus:border-primary-500"
					placeholder="Pack size"
					bind:value={pack_size}
				/>
			</label>
			<span class="block text-center">pack of</span>
			<label class="block">
				<input
					type="text"
					class="mt-0 block w-full bg-transparent px-0.5 py-0.5 border-0 border-b-2 border-primary-800 focus:ring-0 focus:border-primary-500"
					placeholder="Unit ounces"
					bind:value={unit_ounces}
				/>
			</label>
			<span class="block text-ellipsis overflow-hidden">oz. cans/bottles</span>

			<!-- second row -->
			<span class="block"></span>

			<div class="block text-center">buy</div>

			<input
				class="mt-0 block w-full bg-transparent px-0.5 py-0.5 border-0 border-b-2 border-primary-800 focus:ring-0 focus:border-primary-500"
				type="text"
				placeholder="Amount"
				bind:value={bogo_buy}
			/>

			<div class="block text-center">get</div>

			<input
				class="mt-0 block w-full bg-transparent px-0.5 py-0.5 border-0 border-b-2 border-primary-800 focus:ring-0 focus:border-primary-500"
				type="text"
				placeholder="Amount"
				bind:value={bogo_get}
			/>

			<div class="block">free</div>
		</div>
	</div>
	<div class="flex-none ml-4 sm:mt-0 my-5">
		{#if cents_per_ounce}
			<h1><span class="sm:text-5xl text-3xl">{cents_per_ounce}<em>¢</em></span> / oz.</h1>
		{/if}

		{#if can_equivalent}
			<h1><span class="sm:text-5xl text-3xl">${can_equivalent}</span> / 12&nbsp;oz.&nbsp;can</h1>
		{/if}
	</div>
</div>

<script>
	let _date = new Date();
	$: src = `http://www.patriarchia.ru/bu/${date.date}/print.html`;

	let date = {
		get date() {
			return _date.toISOString().slice(0, 10);
		},
		set date(value) {
			_date = new Date(value);
		}
	};
</script>

<div class="d-flex align-items-center p-3 bg-light shadow-sm">
	<h2 class="flex-grow-1 mb-0">
		Богослужебные указания на {new Date(date.date).toLocaleDateString()}
	</h2>
	<div class=" btn-group">
		<button class="btn btn-dark text-light">Назад</button>
		<input class="btn btn-light bg-white" type="date" bind:value={date.date} />
		<button
			class="btn btn-dark text-light"
			on:click={() =>
				(date.date = new Date(new Date().getTime() + 24 * 60 * 60 * 1000)
					.toISOString()
					.slice(0, 10))}>Вперёд</button
		>
		<button
			class="btn btn-dark text-light"
			on:click={() => (date.date = new Date().toISOString().slice(0, 10))}>Сегодня</button
		>
	</div>
</div>
<iframe
	id="frame"
	class="bg-dark text-light w-100"
	style="min-height:90vh;"
	{src}
	title=""
	frameborder="0"
/>

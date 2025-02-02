<script>
	let ida = '';
	let pes = '';
	let alt = '';
	let gen = 'male';
	let mb = null;
	let nivAtiv = [
		{ v: 1.2, l: 'Sedentário' },
		{ v: 1.375, l: 'Levemente ativo' },
		{ v: 1.55, l: 'Moderadamente ativo' },
		{ v: 1.725, l: 'Muito ativo' }
	];
	let selAtiv = nivAtiv[0].v;
	let gasto = null;

	function calcMB() {
		let i = parseFloat(ida);
		let p = parseFloat(pes);
		let a = parseFloat(alt);
		if (isNaN(i) || isNaN(p) || isNaN(a) || i < 0 || p < 0 || a < 0) {
			mb = null;
			gasto = null;
			return;
		}
		if (gen === 'male') {
			mb = 66 + 13.7 * p + 5 * a - 6.8 * i;
		} else {
			mb = 655 + 9.6 * p + 1.8 * a - 4.7 * i;
		}
		calcGasto();
	}

	function calcGasto() {
		if (mb !== null) {
			gasto = mb * parseFloat(selAtiv);
		} else {
			gasto = null;
		}
	}

	$: corGasto =
		parseFloat(selAtiv) === 1.2
			? '#00BFFF'
			: parseFloat(selAtiv) === 1.375
				? '#1E90FF'
				: parseFloat(selAtiv) === 1.55
					? '#FFA500'
					: '#FF4500';
</script>

<svelte:head>
	<meta charset="UTF-8" />
	<meta name="viewport" content="width=device-width, initial-scale=1" />
	<title>Calc. Metabólico</title>
	<link
		href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css"
		rel="stylesheet"
	/>
	<style>
		body {
			background-image: url('https://images2.alphacoders.com/132/thumb-1920-1325726.png');
			background-size: cover;
			background-position: center;
			background-attachment: fixed;
			background-color: transparent;
		}
	</style>
</svelte:head>

<div class="pagina">
	<div class="container mt-5">
		<h1 class="text-center">Cálculo do Metabolismo Basal</h1>
		<form on:submit|preventDefault={calcMB}>
			<div class="mb-3">
				<b><br />Feito utilizando a Fórmula de Harris-Benedict!<br /></b>
				<label for="ida" class="form-label">Idade (anos):</label>
				<input type="number" id="ida" class="form-control" bind:value={ida} required />
			</div>
			<div class="mb-3">
				<label for="pes" class="form-label">Peso (kg):</label>
				<input type="number" id="pes" class="form-control" bind:value={pes} required />
			</div>
			<div class="mb-3">
				<label for="alt" class="form-label">Altura (cm):</label>
				<input type="number" id="alt" class="form-control" bind:value={alt} required />
			</div>
			<div class="mb-3">
				<label for="gen" class="form-label">Gênero:</label>
				<select id="gen" class="form-select" bind:value={gen}>
					<option value="male">Masculino</option>
					<option value="female">Feminino</option>
				</select>
			</div>
			<button type="submit" class="btn btn-primary">Calcular MB</button>
		</form>
		{#if mb !== null}
			<div class="alert alert-info mt-3">
				MB: <strong>{mb.toFixed(2)}</strong> cal/dia.
			</div>
		{/if}
	</div>

	<div class="container mt-5">
		<h1 class="text-center">Cálculo do Gasto Energético Total</h1>
		<div class="mb-3">
			<label for="ativ" class="form-label">Nível de atividade:</label>
			<select id="ativ" class="form-select" bind:value={selAtiv} on:change={calcGasto}>
				{#each nivAtiv as n}
					<option value={n.v}>{n.l}</option>
				{/each}
			</select>
		</div>
		{#if gasto !== null}
			<div class="alert mt-3" style="background-color: {corGasto};">
				Gasto: <strong>{gasto.toFixed(2)}</strong> cal/dia.
			</div>
		{/if}
		<b>O cálculo do Gasto Diário Total é feito da seguinte forma:</b><br>
		Sedentário: (MB * 1.2)<br>
		Levemente Ativo: (MB * 1.375)<br>
		Moderadamente Ativo: (MB * 1.55)<br>
		Muito Ativo: (MB * 1.725)<br><br>
    Para formular a quantidade de calorias da sua dieta: <a class="nav-link" href="/Dieta">Clique aqui!</a >
</div></div>
<style>
	.pagina {
		background-image: url('https://images2.alphacoders.com/132/thumb-1920-1325726.png');
		background-size: cover;
		background-position: center;
		background-attachment: fixed;
		min-height: 100vh;
		color: white;
	}
</style>

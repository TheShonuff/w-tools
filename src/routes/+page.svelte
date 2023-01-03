<script>
	let value = '';
	const re = new RegExp(/#/g);
	function format() {
		console.log(value);
		value = value.replaceAll(re, '\n# ');
		navigator.clipboard.writeText(value).then(() => copied());
	}
	function copied() {
		let x = document.querySelector('.copied');
		let legend = document.querySelector('legend');
		legend.innerHTML = 'COPIED';
		x.innerHTML = "LOOK AT THAT!!! It's been copied to your clipboard";
	}
	function clear() {
		value = '';
	}
</script>

<h1>W-Tools</h1>
<form>
	<fieldset>
		<legend>Format</legend>
		<textarea name="textarea" rows="50" cols="100" bind:value placeholder="Format Log Here" />
		<p>
			<button class="format-btn" on:click={format}>Format</button><button
				class="clear-btn"
				on:click={clear}>Clear</button
			>
		</p>
		<p class="copied" />
	</fieldset>
</form>

<style>
	.copied {
		font-weight: bold;
	}

	.format-btn {
		margin-right: 10px;
	}
</style>

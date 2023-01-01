<script>
	let value = '';
	const re = new RegExp(/#/g);
	function format() {
		console.log(value);
		value = value.replaceAll(re, '\n# ');
	}
</script>

<h1>W-Tools</h1>
<form>
	<fieldset>
		<legend>Format</legend>
		<textarea name="textarea" rows="50" cols="100" bind:value placeholder="Format Log Here" />
		<p><button on:click={format}>Format</button></p>
	</fieldset>
</form>

<script>
	let value = '';
	let num = '';
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

	function hexify() {
		let str = num;
		str = str.replaceAll(/\s+/g, '');
		let r = [];
		for (let i = 0; i < str.length - 1; i += 2) {
			r.push(String.fromCharCode(parseInt(str.charAt(i) + str.charAt(i + 1), 16)));
		}
		//oreturn r.join('');
		console.log(num);
		num = r.join('');
	}
</script>

<main>
	<h1>W-Tools</h1>
	<div class="container">
		<form>
			<fieldset>
				<legend>Format Your Log</legend>
				<textarea
					name="textarea"
					rows="25"
					cols="75"
					bind:value
					placeholder="Paste the log to be formatted here..."
				/>
				<p>
					<button class="btn format-btn" on:click={format}>Format</button><button
						class=" btn clear-btn"
						on:click={clear}>Clear</button
					>
				</p>
				<p class="copied" />
			</fieldset>
		</form>
		<form>
			<fieldset>
				<legend>Hex to ASCII String</legend>
				<textarea
					name="hex-conversion"
					rows="5"
					cols="50"
					bind:value={num}
					placeholder="Paste Hexdecimal to be converted"
				/>
				<p><button class="btn format-btn" on:click={hexify}>Convert</button></p>
			</fieldset>
		</form>
	</div>
</main>

<style>
	/* https://coolors.co/palette/8ecae6-219ebc-023047-ffb703-fb8500 */
	@import url('https://fonts.googleapis.com/css2?family=Oswald:wght@200;300;400;500;600;700&display=swap');
	.copied {
		font-weight: bold;
	}

	h1 {
		font-family: 'Oswald', sans-serif;
	}
	:global(body) {
		background-color: #e7ecef;
	}
	.container {
		display: flex;
		flex-direction: row;
		justify-content: space-evenly;
		margin: 0 auto;
	}
	.btn {
		font-family: 'Oswald', sans-serif;
		margin-right: 10px;
		background-color: #023047;
		color: white;
		height: 35px;
		width: 65px;
		border-radius: 5px;
		border-style: none;
	}
	.btn:hover {
		background-color: white;
		color: black;
		cursor: pointer;
	}
	fieldset {
		font-family: 'Oswald', sans-serif;
		font-size: 20px;
		font-weight: bold;
		background-color: #219ebc;
		border-radius: 10px;
		border-style: none;
	}
	textarea {
		border-radius: 10px;
		padding-left: 10px;
		padding-top: 5px;
		border: 2px solid #023047;
	}
	textarea:focus {
		outline: none !important;
		border: 2px solid #fb8500;
	}
</style>

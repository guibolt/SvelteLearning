<script>
	 let firstName = 'John'
	 let lastName = 'Lennon'
	let color = 'black'
	const handleClick = () =>{
		name =' novo nome'
	}
	const handleInput = (event) => {
		name = event.target.value

	}

	$: fullName = `${firstName} ${lastName}`
	$: {
		console.log(color)
		console.log(fullName)
	}
</script>

<main>
	<p style="color: {color}">name: {fullName} -{color} cor</p>
	
	<input type="text" bind:value={color}>
	<input type="text" bind:value={lastName}>
	<input type="text" bind:value={firstName}>

</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
<script>

	let people = [
		{ name: 'john', beltColor: 'black', age: 25, id: 1 },
		{ name: 'mario', beltColor: 'orange', age: 45, id: 2 },
		{ name: 'lones', beltColor: 'blue', age: 39, id: 3 }
	]

	const deletePerson = (id) =>{
		people = people.filter((person) => person.id != id)
	}
</script>

<main>
	{#each people as person (person.id)}
	<div>
		<h4>
			{person.name}
		</h4>
		<p>{person.age} years old, {person.beltColor} belt.</p>
		<button on:click="{() => deletePerson(person.id)}"> Delete</button>
	</div>
	{:else}
	<p>No data to show</p>
	{/each}
</main>

<style>
	

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
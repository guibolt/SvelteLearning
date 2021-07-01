<script>
import Modal from './components/Modal.svelte';
import AddPersonForm from './components/AddPersonForm.svelte';

	let people = [
		{ name: 'john', beltColor: 'black', age: 25, id: 1 },
		{ name: 'mario', beltColor: 'orange', age: 45, id: 2 },
		{ name: 'lones', beltColor: 'blue', age: 39, id: 3 }
	]

	const deletePerson = id => people = people.filter(person => person.id != id)
	const exibitModal = () => showModal = !showModal
	const addPerson = (event) => {
		const person = event.detail
		people = [person, ...people]
		showModal = false
	}
	let showModal = false


</script>


<Modal {showModal} on:click={exibitModal}>,
<AddPersonForm on:addPerson={addPerson}/>
</Modal>


<main>
	
	<button on:click="{exibitModal}">
		show modal
	 </button>
	{#each people as person (person.id)}
	<div>
		<h4>
			{person.name}
		</h4>
		<p>{person.age} years old, {person.beltColor} belt.</p>
		{#if person.beltColor === 'blue'}
			<p>Ill give blue</p>
			{:else }
			<p>Notting</p>
		{/if}

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
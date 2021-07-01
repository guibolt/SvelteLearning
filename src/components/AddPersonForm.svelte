<script>
    import { createEventDispatcher} from 'svelte'
    let dispatch = createEventDispatcher();

    let name,age,beltColor = ''
    // let fighting,sneaking,running;
    let skills = []
    let options = [
        { color : 'select the color'},
        { color : 'black'},
        { color : 'orange'},
        { color : 'brown'},
        { color : 'white'},
        { color : 'purple'},
    ]

    const handleSubmit = () => {
       const person = {
           name,
           beltColor,
           age,
           skills,
           id: (Math.random() + 1)  * 3
       }
       dispatch('addPerson', person)
    }

</script>

<h3> Form</h3>
    <form on:submit|preventDefault="{handleSubmit}">
        <input type="text" placeholder="name" bind:value="{name}">
        <input type="number" placeholder="age"  bind:value="{age}">
        <label for="">Skills</label>

        <!-- <input type="checkbox" bind:checked={fighting} > fighting<br>
        <input type="checkbox" bind:checked={sneaking} > sneaking<br>
        <input type="checkbox" bind:checked={running} > running<br>
    -->

           <input type="checkbox" bind:group={skills} value="fighting"> fighting<br>
        <input type="checkbox" bind:group={skills}  value="sneaking"> sneaking<br>
        <input type="checkbox" bind:group={skills} value="running" > running<br>

        <select bind:value="{beltColor}">
            {#each options  as opt }
               <option value="{opt.color}">{opt.color}</option> 
            {/each}
        </select>
        <button>Add person</button>
    </form>

    <style>

    </style>
<script>
	import ContactCard from './ContactCard.svelte';


	let name = 'Ravi';
	let age = 12;

	let job = '';
	let description = '';
	let image = '';

	$: uppercaseName = name.toUpperCase();

	$: if (name === 'Isis'){
		age = 31;
	}

	function incrementAge(){
		age += 1;
	}

	function changeName(){
		name = 'Isis';
	}

	function nameInput(event){
		const enteredValue = event.target.value;
		name = enteredValue;
		
	}


</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello! My name is {uppercaseName}, and my age is {age}!</h1>
<button on:click="{incrementAge}">Change Age</button>
<!-- <button on:click="{changeName}">Change Name</button> -->
<!-- <input type="text" value="{name}" on:input="{nameInput}"> -->
<input type="text" bind:value="{name}"> 
<input type="text" bind:value="{job}"> 
<input type="text" bind:value="{image}"> 
<textarea rows="3" bind:value="{description}"></textarea>


<ContactCard 
	userName="{name}" 
	jobTitle="{job}" 
	{description}
	userImage="{image}"/>

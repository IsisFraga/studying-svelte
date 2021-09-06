<script>
	let password = '';
	let pwdStatus = '';
	let pwdList = [];

	function validatePassword() {
		if (password.trim().length <= 5) {
			pwdStatus = 'tooShort';
			return;
		}  else if (password.trim().length >= 10){
			pwdStatus = 'tooLong';
			return;
		} else if (password.trim().length < 10 && password.trim().length > 5){
			pwdStatus = 'pwdOk'
			pwdList = [
				...pwdList,
				{
					id:Math.random(),
					password: password,
				}
			];
		}
	}

	function changeValue(){
		if (password.trim().length <= 5 || password.trim().length >= 10) {
			pwdStatus = 'typing'
		}
	}

	function deletePwd(id) {
		pwdList = pwdList.filter(passw => passw.id != id)
	}


</script>

<input type="password" bind:value="{password}" id="password" on:input="{changeValue}"/>
<button on:click="{validatePassword}">Submit</button>

{#if pwdStatus === 'empty'}
		<p>Please insert password.</p>
	{:else if pwdStatus === 'tooShort'}
		<p>Please provide a password longer than 5 characters.</p>
	{:else if pwdStatus === 'tooLong'}
		<p>Please provide a password shorter than 10 characters.</p>
	{:else if pwdStatus === 'pwdOk'}
		<p>{password}</p>
	{:else if pwdStatus === 'typing'}
		<p></p>
{/if}
{#each pwdList as pwd, i(pwd.id)}
	<h2># {i + 1}</h2>
	<li on:click="{deletePwd(pwd.id)}">{pwd.password}</li>
{/each}

<!-- <h1>Assignment</h1>

<p>Solve these tasks.</p>

<ol>
	<li>Add a password input field and save the user input in a variable.</li>
	<li>Output "Too short" if the password is shorter than 5 characters and "Too long" if it's longer than 10.</li>
	<li>Output the password in a paragraph tag if it's between these boundaries.</li>
	<li>Add a button and let the user add the passwords to an array.</li>
	<li>Output the array values (= passwords) in a unordered list (ul tag).</li>
	<li>Bonus: If a password is clicked, remove it from the list.</li>
</ol> -->

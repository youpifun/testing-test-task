<script>
	import Preloader from "./Preload.svelte"
	const form_template = [
    {
        id: "check1",
		type: "input",
		name: "login", 
        labelFor: "check1",
        labelText: "Your login", 
        placeholder: "login"
}, 
    {
        id: "check2",
		type: "input", 
		name: "password",
        labelFor: "check2",
        labelText: "Your password", 
        placeholder: "password"
},
	{
		id: "applyBtn",
		type: "submit",
		value: "Submit"
},
	{
		id: "check3",
        type: "input",
		value: "some value"
	}
];
</script>

<style>
	#wrapper {
		width: 100%;
		height: 100%;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	#content {
		display: flex;
		justify-content: center;
		width: 40%;
		max-height: 100%;
		min-height: 10%;
		box-shadow: 0px 0px 15px 5px;
		background-color: rgba(255, 127, 80, 0.281);
	}

	@media (max-width: 480px) {
    #content {
       width: 250px;
    }
}

	form {
		padding: 10px;
	}

	input {
        display: block;
    }

	label {
		padding: 5px;
	}

	img {
		width: 200px;
		height: 200px;
		position: absolute;
		z-index: -1;
	}

</style>

<Preloader></Preloader>
<img src="build/image.png" alt="">
<div id="wrapper">
	<div id="content">
		<form method="POST">
			{#each form_template as {id, type, name, labelFor, labelText, placeholder, value}}
				{#if (labelFor!=undefined)||(labelText!=undefined)}
					<label for={labelFor}>{labelText}</label>
				{/if}

				{#if (value!=undefined)}
					<input {id} {name} {type} {value}/>
				{:else}
					<input {id} {name} {type} {placeholder}/>
				{/if}

				{:else}
					<p>Nothing here!</p>
			{/each}
		</form>
	</div>
</div>
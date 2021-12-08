<button on:click>
	<slot />
</button>

<style>

	button {
		font:inherit;
		padding: 0.15rem 0.5rem;
		background-color: #D10057;
		border: 1px solid #D10057;
		color: white;
		cursor: pointer;
	}
	button:hover, 
	button:active {
		box-shadow: 1px 1px 6px rgba(0, 0, 0, 0.26);
	}
</style>
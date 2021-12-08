<script>
	import Product from "./Product.svelte";
	import Button from "./Button.svelte";
	import Cart from "./Cart.svelte";

	let title = "";
	let price = 0;
	let description = "";
	let products = [];
	let cardItems = [];

	function setTitle(event) {
		title = event.target.value;
	}

	function createProduct() {
		const newProduct = {
			title,
			price,
			description,
		};
		// products = [...products, newProduct];
		products = products.concat(newProduct);
	}

	function addToCart(event){
		const selectedTitle = event.detail;
		// console.log('selectedTitle', selectedTitle);
		cardItems = cardItems.concat({...products.find(prod => prod.title === selectedTitle)});
		console.log(cardItems);
	}
</script>

<section>
	<Cart items={cardItems} />
</section>
<hr>

<section>
	<div>
		<label for="title">Title</label>
		<input type="text" id="title" value={title} on:input={setTitle} />
	</div>
	<div>
		<label for="price">Price</label>
		<input type="number" id="price" bind:value={price} />
	</div>
	<div>
		<label for="description" />
		<textarea rows="3" id="description" bind:value={description} />
	</div>
	<Button on:click={createProduct}>Create Product</Button>
</section>

<section>
	{#if products.length === 0}
		<p>No products were added yet!</p>
	{:else}
		{#each products as product}
			<Product
				productTitle={product.title}
				productPrice={product.price}
				productDescription={product.description}
				on:addtocart={addToCart}
			/>
		{/each}
	{/if}
</section>

<style>
	section {
		width: 30rem;
		margin: auto;
	}
	label,
	input,
	textarea {
		width: 100%;
	}
</style>

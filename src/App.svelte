<script>

	let products =[
		{
		id: 1,
		name:'hp laptop',
		description: 'laptop de hp',
		category: 'laptop'
		},
		{
		id: 2,
		name:'mac laptop',
		description: 'laptop de apple',
		category: 'laptop'
		}
];
	let product = {id:0, name: '', description:'', category: '',imageURL: ''};

	const cleanProduct =()=>{
		product ={
			id: '',
			name: '',
			description: '',
			category: '',
			imageURL:''
		}
	}

	const onSubmitHandle = e=>{
		e.preventDefault();
		const newProduct = {
			id: products.length +1,
			name: product.name,
			description: product.description,
			category: product.category,
			imageURL: product.imageURL
		}
		products = products.concat(newProduct);
		cleanProduct();
		console.log(products);
	};

	const deleteProduct= (id)=>{
		console.log(id);
	}
</script>

<main>
	<div class="container p-4">
		<div class="row">
			<div class="col-md-6">
				{#each products as product}

					<div class="card">
						<div class="row">
							<div class="col-md-4">
								{#if !product.imageURL}
									<img src="./images/favicon.png" alt="imagen" class="img-fluid p-2"  />
								{:else}
									<img src="{product.imageURL}" alt="imagen" class="img-fluid p-2"  />

								{/if}
							</div>
							<div class="col-md-8 ">
								<h5>
									<strong>{product.name}</strong>
									<span><small>{product.category}</small></span>
								</h5>
								<p > {product.description}</p>
								<button class="btn btn-danger" on:click={deleteProduct(product.id)}>borrar</button>
								<button class="btn btn-secondary">editar</button>
							</div>
						</div>
					</div>

				{/each}
			</div>
			<div class="col-md-6">
				<div class="card">
					<div class="card-body">

						<form on:submit={onSubmitHandle}>

							<div class="form-group">
								<input bind:value={product.name} 
								class="form-control"
								type="text" 
								placeholder="Product name" 
								id="product-name"/>
					
							</div>
							
							<div class="form-group">
								<textarea bind:value={product.description}  
								class="form-control"
								id="producto-description" 
								rows="3" 
								placeholder="descripcion del producto"></textarea>
					
							</div>

							<div class="form-group">
								<input bind:value={product.imageURL}
									type="url"
									id="product-image-url" 
									placeholder="google.com"
									class="form-control">
							</div>
							
							<div class="form-group">
								<select bind:value={product.category} id="category">
									<option value="laptops">Laptos</option>
									<option value="perifericos">Perifericos</option>
									<option value="monitor">Monitor</option>
								</select>
							</div>
					
							<button class="btn btn-primary" >guardar</button>
						</form>

					</div>
				</div>
			</div>
		</div>
	</div>
</main>

<style>
</style>
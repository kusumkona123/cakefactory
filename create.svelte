<script>
	import {firestore} from '../db';
	let cakename,typeofcake,url, price ,quantity;
	const addcakename =async()=> {
		await firestore.collection('cakename').add({
		    cakename,
			typeofcake,
			url,
			price,
			quantity,
		});
		alert('cakename added')
	}
</script>


<div>
	<p class="title">Create cake</p>
	<div class="container">
		<input bind:value ={cakename} type="text" placeholder="enter cake name"/>
		<input bind:value={typeofcake} type="text" placeholder=" enter type of cake"/>
		<input bind:value={url} type="text" placeholder=" enter the url"/>
		<input bind:value={price} type="number" placeholder=" enter price"/>
		<input bind:value={quantity} type="number" placeholder=" enter quantity"/>
		<button on:click={addcakename}>create</button>
	</div>
</div>
<style>
	.title{
		text-align: center;
		font-size: 30px;
		background-color: crimson;
	}
	.container{
		display: flex;
		flex-direction: column;
		gap:20px;
	}
	input{
		padding:15px;
		width:20%;
		margin:6px;
		border-radius: 10px;
		border:1px solid #ccc;
	    background-color:lemonchiffon;
		text-align: center;
        margin:0 auto;
		border:none;
	}
	button{
		border-radius: 8px;
		padding:12px 28px;
		font-size: 12px;
		background-color: lightgreen;
		width:20%;
		margin:0 auto;
		display:block;
		outline:none;
		text-decoration: none;
		cursor: pointer;
	}
</style>
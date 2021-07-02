

<script>
    import {onMount} from 'svelte';
   import {firestore} from '../db';
   let cakes =[];
   let search='';
   $:new_cakes=cakes.filter((i)=>i.cakename.includes(search));
   onMount(()=>{
       getcakename();
   });

   async function filters(){
    const l6 = await firestore
			.collection('cakename')
			.where('price', '>=', 100)
			.where('price', '<=', 300)
			.get();
   }
   async function getcakename(){
       let t=[];
       const l= await firestore.collection('cakename').get();
       l.forEach((doc)=>t.push(doc.data()));
       cakes=t;
           
       }

</script>
<div>
   <a href ="/title">Create cake</a>
   <input type="text" placeholder="search..." bind:value={search} />
   <div class="container">
   {#each new_cakes as i}
   <div class="card">
       <img src={i.url} alt="" width="200" height="200" />
       <p>{i.cakename}</p>
       <p>{i.price}</p>
   </div>
   {/each}
</div>
</div>

<style>
   
   a {
       padding: 10px 20px;
       border: none;
       background-color: yellow;
       margin: 0 auto;
       font-size: 18px;
       border: 1px solid #ccc;
       border-radius: 40px;
       text-decoration: none;
       display: block;
       width: 200px;
   }
   .card {
       margin: 20px;
       border: 1px solid #ccc;
       width: 200px;
   }
   p {
       margin-left: 10px;
   }
   .container {
       display: grid;
       grid-template-columns: auto auto auto auto;
       width: 80%;
       margin: 20px auto;
       border: 1px solid #ccc;
   }
   input {
		padding: 14px;
		width: 60%;
		margin: 10px auto;
		border-radius: 40px;
		border: 1px solid #ccc;
		display: block;
	}
</style>

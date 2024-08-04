<script>
  import productjson from "../DB/ProductsList.json";
  export let AddToCart;

</script>

<div class="product__list">
  {#each productjson as product}
    <div class="product__card">
      <img class="product__img" src={product.image} alt={product.name} />
      <p class="product__name">{product.name}</p>
      <p>{product.description}</p>
      <p class="product__price">S/{product.price.toFixed(2)}</p>
      <button class="product__btn-add" on:click={()=>AddToCart(product)}>Add To Cart</button>
    </div>
  {/each}
</div>

<style>
  *{
    box-sizing: border-box;
  }
  .product__list {
    padding: 1em;
    display: flex;
    flex-wrap: wrap;
    gap: 1em;
    justify-content: center;
    text-align: center;
  }
  .product__card{
    width: 310px;
    border: 1px solid #fafafafa;
    border: 1px solid #ccc;
    padding-bottom: 1em;
  }
  .product__img {
    height: 250px;
    width: 100%;
    object-fit: cover;
  }
  .product__price{
    font-weight: bold;
    text-align: start;
    padding:0 1em;
    font-weight: 1.2em;
  }
  .product__btn-add{
    padding: .5em 1em;
    border-radius: 5px;
    background-color: #21618C;
  }
</style>

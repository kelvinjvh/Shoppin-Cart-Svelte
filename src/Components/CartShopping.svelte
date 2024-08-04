<script>
  export let products;
  export let DeleteProduct;
  export let IncreaseAmountProduct;
  export let DecreaseAmountProduct;
  export let totalsale;
  export let numberunits;
  export let ShowComponent;

</script>

<div class="shopping__cart">
  {#each products as items}
    <div class="shopping__cart-item">
      <img src={items.image} alt="" />
      <p class="shopping__cart-name">{items.name}</p>
      <div class="shopping__cart-buttons">
        <button
          class="btn btn-increase"
          on:click={() => IncreaseAmountProduct(items)}>+</button
        >
        <p>{items.amount}</p>
        <button
          class="btn btn-decrease"
          on:click={() => DecreaseAmountProduct(items)}>-</button
        >
      </div>
      <div class="price">
        <p>S/{items.price}</p>
        <p class="btn-remove" on:click={() => DeleteProduct(items)}>Remover</p>
      </div>
    </div>
  {/each}
</div>
<div class="container__detail">
  <div class="sale__detail">
    <p>Total De Productos :{products.length}</p>
    <p>Total De Unidades : {numberunits}</p>
    <p>Total Sale :S/{totalsale}</p>
  </div>
  <button on:click={()=>ShowComponent()} class="btn__close">Close </button>
</div>

<style>
  .shopping__cart {
    margin-bottom: 2em;
    height: 400px;
    overflow-y: scroll;

  }
  .shopping__cart-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    width: 200px;
    margin-bottom: 1em;
    width: 60%;
    margin: 2em auto 1em;
    border: 1px solid #ccc;
  }
  img {
    height: 100px;
    width: 100px;
    object-fit: cover;
  }
  .shopping__cart-name {
    text-align: start;
    font-size: 1.1em;
    width: 200px;
  }
  .shopping__cart-buttons {
    display: flex;
    font-size: 1.3em;
    justify-content: space-between;
    align-items: center;
    width: 100px;
  }
  .btn {
    border-radius: 50%;
    height: 40px;
    width: 40px;
    background-color: #074e7e;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .price {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding-right: 1em;
  }
  p {
    margin: 0;
  }
  .btn-remove {
    cursor: pointer;
    color: #cb4335;
    font-weight: bold;
  }
  .container__detail{
    width: 60%;
    margin: 0 auto;
  }
  .sale__detail {
    display: flex;
    justify-content: space-between;
    margin-bottom: 1em;
    font-weight: bold;
  }
  .btn__close{
    border-radius: 5px;
    background-color: #cb4335;
    color: #fff;
    padding: .5em 2em;
    font-weight: normal;
  }
  @media (max-width:768px){
    .shopping__cart-item{
      width: 90%;
      padding-right: 1em;
      margin-bottom: 1em;
    }
    .container__detail{
      width: 90%;
    }
    .shopping__cart-name{
      text-align: center;
    }
  }

  @media (max-width:412px){
    .shopping__cart-name{
      width: 100px;
      text-align: center;
    }
  }
</style>

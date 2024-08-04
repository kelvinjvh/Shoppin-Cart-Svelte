<script>
  export let ShowComponent;
  export let products;
</script>

<header>
  <img
    class="header__logo"
    src="image/shopping-cart.png"
    alt=""
    on:click={() => ShowComponent()}
  />
  <div class="icon__shopping-cart">
    <img src="/image/cart.png" alt="cart" on:click={() => ShowComponent()} />
    <span>{products.length}</span>
  </div>
</header>

<style>
  header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #222;
    padding: 0.5em 3em;
    color: #fff;
    position: static;
  }
  .header__logo {
    width: 70px;
    height: 70px;
  }
  .icon__shopping-cart {
    height: 100%;
    width: 50px;
    position: relative;
  }
  img {
    height: 100%;
    width: 100%;
    cursor: pointer;
  }
  span {
    position: absolute;
    top: 0;
    left: 90%;
    display: block;
    height: 30px;
    width: 30px;
    border-radius: 50%;
    background-color: #cb4335;
    display: grid;
    place-items: center;
    font-weight: bold;
  }
</style>

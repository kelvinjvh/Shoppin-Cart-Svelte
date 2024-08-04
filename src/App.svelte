<script>
  import CartShopping from "./Components/CartShopping.svelte";
  import Header from "./Components/Header.svelte";
  import ProductsList from "./Components/ProductsList.svelte";

  let ShowHideComponent = false;
  let numberunits = 0;
  let amountproducts = 0;
  let totalsale = 0;
  let products = JSON.parse(localStorage.getItem("products")) || [];
  $: localStorage.setItem("products", JSON.stringify(products));

  const AddToCart = (product) => {
    let searchproduct = products.find((item) => item.id === product.id);
    if (!searchproduct) {
      products = [...products, { ...product, amount: 1 }];
    }
    NumberUnits();
    amountproducts = products.length;
    TotalSale();
  };

  const DeleteProduct = (product) => {
    products = products.filter((item) => item.id !== product.id);
    NumberUnits();
    amountproducts = products.length;
    TotalSale();
  };

  const IncreaseAmountProduct = (product) => {
    products = products.map((item) =>
      item.id === product.id ? { ...product, amount: item.amount + 1 } : item
    );
    NumberUnits();
    TotalSale();
  };

  const DecreaseAmountProduct = (product) => {
    let searchproduct = products.find((item) => item.id === product.id);
    if (searchproduct.amount !== 1) {
      products = products.map((item) =>
        item.id === product.id ? { ...product, amount: item.amount - 1 } : item
      );
      NumberUnits();
      TotalSale();
      return;
    }
    DeleteProduct(product);
  };
  const ShowComponent = () => {
    ShowHideComponent = !ShowHideComponent;
  };

  const NumberUnits = () => {
    numberunits = products.reduce((acum, total) => acum + total.amount, 0);
    console.log(numberunits);
  };
  
  const TotalSale = () => {
    totalsale = products.reduce(
      (acumulador, product) => (acumulador + product.price) * product.amount,
      0
    );
  };

  TotalSale();
  NumberUnits();


</script>

<Header {ShowComponent} {products} />

{#if ShowHideComponent}
  <CartShopping
    {products}
    {DeleteProduct}
    {IncreaseAmountProduct}
    {DecreaseAmountProduct}
    {totalsale}
    {numberunits}
    {ShowComponent}
  />
{:else}
  <ProductsList {AddToCart} />
{/if}



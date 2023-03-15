<script>
  import Navbar from "./components/Navbar.svelte";
  import { cart } from "./store/cart.store";
  //   $cart = [
  //     {
  //         "itemID": 2,
  //         "name": "Concealer 1",
  //         "price": 1000,
  //         "description": "A concealer",
  //         "img": "https://www.esteelauder.in/media/export/cms/products/558x768/el_sku_PCCE09_558x768_0.jpg"
  //     }
  // ]
</script>

<section class="flex flex-col min-h-screen h-full p-10">
  <Navbar />

  <div
    class="flex flex-col justify-center items-center h-full    flex-1
  "
  >
    <div class="newfont text-5xl">Your Cart</div>

    <div class="flex gap-7 flex-col my-10 max-w-xl  divide-y-2 ">
      {#each $cart as item}
        <div class="flex gap-9 py-7 items-center">
          <div class="w-[700px] h-[200px]">
            <img
              class="w-full h-full  rounded-xl object-cover"
              src={item.img}
              alt=""
            />
          </div>

          <div>
            <div class="text-3xl font-bold">{item.name}</div>
            <div class="line-clamp-2">
              {item.description} Lorem ipsum dolor sit amet consectetur adipisicing
              elit. Laudantium cupiditate aliquam natus ducimus perferendis tenetur
              harum quam! Cupiditate, odit. Quam saepe corporis aperiam blanditiis
              quos ut quas nisi qui facere.
            </div>
          </div>
          <div class="text-xl col-span-2 justify-self-end font-bold">
            ${item.price}
          </div>
        </div>
      {/each}
    </div>
    <div class="border" />
    <div class="flex justify-between items-center w-full max-w-xl">
      <div>
        <div class="">Grand Total</div>
        <div class="text-xl font-bold ">$3000</div>
      </div>
      <button class="btn">Pay and Check out > </button>
    </div>
  </div>
</section>

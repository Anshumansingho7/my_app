<script>
  let firstname = 'John';
  let lastname = 'Doe';

  // Reactive declaration for fullname
  $: fullname = `${firstname} ${lastname}`;

  let items = [
      { id: 1, title: 'Item 1', price: 10 },
      { id: 2, title: 'Item 2', price: 20 },
      { id: 3, title: 'Item 3', price: 30 },
  ];

  // Reactive declaration for total price
  $: totalPrice = items.reduce((sum, item) => sum + item.price, 0);

  // Reactive statement to add a new item and update the total price
  function addItem() {
      const newItem = { id: items.length + 1, title: `Item ${items.length + 1}`, price: 15 };
      items = [...items, newItem];
  }
</script>

<style>
  .container {
      max-width: 400px;
      margin: 20px auto;
      padding: 20px;
      border: 1px solid #ccc;
      border-radius: 8px;
      box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  input {
      display: block;
      width: 100%;
      margin-bottom: 10px;
      padding: 8px;
      font-size: 16px;
      border: 1px solid #ccc;
      border-radius: 4px;
  }

  p {
      font-size: 18px;
      margin-bottom: 10px;
  }

  .fullname {
      font-weight: bold;
      color: #007BFF;
  }

  .item-list {
      margin-top: 20px;
  }

  .item {
      margin-bottom: 10px;
      padding: 8px;
      border-bottom: 1px solid #ccc;
  }

  .total-price {
      font-weight: bold;
      color: green;
  }

  button {
      padding: 8px 12px;
      background-color: #007BFF;
      color: white;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      font-size: 16px;
  }

  button:hover {
      background-color: #0056b3;
  }
</style>

<div class="container">
  <p>First Name: {firstname}</p>
  <p>Last Name: {lastname}</p>
  <p class="fullname">Full Name: {fullname}</p>

  <input bind:value={firstname} placeholder="First Name">
  <input bind:value={lastname} placeholder="Last Name">

  <div class="item-list">
      <h3>Items:</h3>
      {#each items as item}
          <div class="item">
              <p>Title: {item.title}</p>
              <p>Price: ${item.price}</p>
          </div>
      {/each}
      <p class="total-price">Total Price: ${totalPrice}</p>
      <button on:click={addItem}>Add New Item</button>
  </div>
</div>

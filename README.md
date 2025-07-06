<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>WearTheLuxury Store</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(to bottom, #f0f3ff, #ffffff);
      color: #222;
    }
    header {
      background: linear-gradient(to right, #2b2d42, #8d99ae);
      color: white;
      padding: 30px 20px;
      text-align: center;
      letter-spacing: 1px;
    }
    nav {
      background: #2b2d42;
      padding: 12px;
      text-align: center;
    }
    nav a {
      color: white;
      margin: 0 18px;
      text-decoration: none;
      font-weight: bold;
      font-size: 15px;
    }
    .products {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      padding: 40px 20px;
      gap: 30px;
    }
    .product {
      background: white;
      border-radius: 14px;
      box-shadow: 0 4px 20px rgba(0,0,0,0.1);
      width: 280px;
      padding: 20px;
      text-align: center;
      transition: transform 0.3s ease;
    }
    .product:hover {
      transform: translateY(-5px);
    }
    .product img {
      width: 100%;
      border-radius: 10px;
    }
    .product h3 {
      margin: 15px 0 5px;
      font-size: 18px;
    }
    .product p {
      font-size: 14px;
      color: #555;
    }
    .product button {
      margin-top: 12px;
      padding: 10px 15px;
      background: #2b2d42;
      color: white;
      border: none;
      border-radius: 6px;
      cursor: pointer;
      transition: background 0.3s;
    }
    .product button:hover {
      background: #1d1f30;
    }
    #cart {
      padding: 30px;
      background: #fff;
      max-width: 600px;
      margin: 40px auto;
      border-radius: 12px;
      box-shadow: 0 2px 20px rgba(0,0,0,0.1);
    }
    #cart h2 {
      text-align: center;
      font-size: 24px;
    }
    #cart ul {
      list-style: none;
      padding: 0;
    }
    #cart ul li {
      margin: 12px 0;
      padding: 10px;
      background: #f9f9f9;
      border-radius: 6px;
      display: flex;
      justify-content: space-between;
    }
    .remove-btn {
      background: #dc3545;
      color: white;
      border: none;
      border-radius: 4px;
      padding: 5px 10px;
      cursor: pointer;
    }
    .buy-btn {
      display: block;
      margin: 20px auto 0;
      padding: 12px 25px;
      background: #28a745;
      color: white;
      border: none;
      border-radius: 6px;
      font-weight: bold;
      cursor: pointer;
    }
    #admin-access {
      text-align: center;
      margin: 40px auto;
    }
    #admin-panel {
      display: none;
      max-width: 600px;
      margin: 20px auto;
      background: #fefefe;
      border: 1px solid #ccc;
      padding: 20px;
      border-radius: 12px;
      box-shadow: 0 4px 20px rgba(0,0,0,0.05);
    }
    #admin-panel input {
      margin-bottom: 10px;
      width: calc(100% - 20px);
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 6px;
    }
    #admin-panel button {
      padding: 10px 20px;
      background: #2b2d42;
      color: white;
      border: none;
      border-radius: 6px;
      cursor: pointer;
    }
    footer {
      text-align: center;
      background: #2b2d42;
      color: white;
      padding: 18px;
      margin-top: 30px;
    }
  </style>
</head>
<body>
  <header>
    <h1>WearTheLuxury</h1>
    <p>Style. Comfort. Confidence.</p>
  </header>

  <nav>
    <a href="#">Home</a>
    <a href="#products">Products</a>
    <a href="#cart">Cart</a>
    <a href="#admin-access">Admin</a>
    <a href="#contact">Contact</a>
  </nav>

  <div class="products" id="products"></div>

  <div id="cart">
    <h2>Your Cart</h2>
    <ul id="cart-items"></ul>
    <button class="buy-btn" onclick="buyNow()">Buy Now</button>
  </div>

  <div id="admin-access">
    <h3>Admin Access</h3>
    <input type="password" id="admin-password" placeholder="Enter Admin Password">
    <button onclick="verifyAdmin()">Enter</button>
  </div>

  <div id="admin-panel">
    <h2>Add Product</h2>
    <input type="text" id="product-name" placeholder="Product Name">
    <input type="text" id="product-price" placeholder="Price (₹)">
    <input type="text" id="product-description" placeholder="Short Description">
    <input type="text" id="product-image" placeholder="Image URL">
    <button onclick="addProductFromAdmin()">Add Product</button>
  </div>

  <footer id="contact">
    <p>Contact us at: <a style="color:white;" href="mailto:support@weartheluxury.com">support@weartheluxury.com</a></p>
    <p>&copy; 2025 WearTheLuxury | Built for Gen Z and Mid Adults 💙💜</p>
  </footer>

  <script>
    const cartItems = [];
    const cartList = document.getElementById('cart-items');
    const productsDiv = document.getElementById('products');
    const adminPanel = document.getElementById('admin-panel');

    function addToCart(item, index) {
      cartItems.push({ name: item, index });
      renderCart();
    }

    function renderCart() {
      cartList.innerHTML = '';
      cartItems.forEach((item, i) => {
        const li = document.createElement('li');
        li.textContent = item.name;

        const removeBtn = document.createElement('button');
        removeBtn.textContent = 'Remove';
        removeBtn.className = 'remove-btn';
        removeBtn.onclick = () => {
          cartItems.splice(i, 1);
          renderCart();
        };

        li.appendChild(removeBtn);
        cartList.appendChild(li);
      });
    }

    function buyNow() {
      if (cartItems.length === 0) {
        alert("Your cart is empty!");
      } else {
        const items = cartItems.map(item => item.name).join('\n');
        window.location.href = `https://wa.me/918860538136?text=I want to buy:\n${encodeURIComponent(items)}`;
      }
    }

    function addProductFromAdmin() {
      const name = document.getElementById('product-name').value;
      const price = document.getElementById('product-price').value;
      const desc = document.getElementById('product-description').value;
      const img = document.getElementById('product-image').value;

      if (!name || !price || !desc || !img) return alert('Fill all fields');

      const productBox = document.createElement('div');
      productBox.className = 'product';
      productBox.innerHTML = `
        <img src="${img}" alt="${name}">
        <h3>${name}</h3>
        <p>₹${price} - ${desc}</p>
        <button onclick="addToCart('${name} - ₹${price}')">Add to Cart</button>
      `;

      productsDiv.appendChild(productBox);

      document.getElementById('product-name').value = '';
      document.getElementById('product-price').value = '';
      document.getElementById('product-description').value = '';
      document.getElementById('product-image').value = '';
    }

    function verifyAdmin() {
      const password = document.getElementById('admin-password').value;
      if (password === 'goat123') {
        adminPanel.style.display = 'block';
        document.getElementById('admin-access').style.display = 'none';
      } else {
        alert('Incorrect password.');
      }
    }

    const sampleProducts = [
      {
        name: 'Runner One',
        price: '999',
        desc: 'Lightweight sneakers for daily hustle',
        img: 'https://images.unsplash.com/photo-1584467735871-bfb5b1c5223d?auto=format&fit=crop&w=800&q=80'
      },
      {
        name: 'Flex Hoodie',
        price: '1199',
        desc: 'Premium streetwear hoodie',
        img: 'https://images.unsplash.com/photo-1584466991124-74f944c52d80?auto=format&fit=crop&w=800&q=80'
      }
    ];

    sampleProducts.forEach(p => {
      const box = document.createElement('div');
      box.className = 'product';
      box.innerHTML = `
        <img src="${p.img}" alt="${p.name}">
        <h3>${p.name}</h3>
        <p>₹${p.price} - ${p.desc}</p>
        <button onclick="addToCart('${p.name} - ₹${p.price}')">Add to Cart</button>
      `;
      productsDiv.appendChild(box);
    });
  </script>
</body>
</html>
ding wear_the_luxury_store (4).html…]()

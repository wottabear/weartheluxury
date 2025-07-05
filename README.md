<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>WearTheLuxury Store</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: #f0f3ff;
      color: #222;
    }
    header {
      background: linear-gradient(to right, #3f2b96, #a8c0ff);
      color: white;
      padding: 20px;
      text-align: center;
    }
    nav {
      background: #3f2b96;
      padding: 10px;
      text-align: center;
    }
    nav a {
      color: white;
      margin: 0 15px;
      text-decoration: none;
      font-weight: bold;
    }
    .products {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      padding: 20px;
      gap: 20px;
    }
    .product {
      background: white;
      border-radius: 10px;
      box-shadow: 0 2px 10px rgba(0,0,0,0.1);
      width: 250px;
      padding: 15px;
      text-align: center;
    }
    .product img {
      width: 100%;
      border-radius: 8px;
    }
    .product h3 {
      margin: 10px 0 5px;
    }
    .product p {
      font-size: 14px;
      color: #555;
    }
    .product button {
      margin-top: 10px;
      padding: 10px;
      background: #3f2b96;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    #cart {
      padding: 20px;
      background: #fff;
      max-width: 600px;
      margin: 30px auto;
      border-radius: 10px;
      box-shadow: 0 2px 10px rgba(0,0,0,0.1);
    }
    #cart h2 {
      text-align: center;
    }
    #cart ul {
      list-style: none;
      padding: 0;
    }
    #cart ul li {
      margin: 10px 0;
      padding: 8px;
      background: #f4f4f4;
      border-radius: 5px;
    }
    footer {
      text-align: center;
      background: #3f2b96;
      color: white;
      padding: 15px;
      margin-top: 30px;
    }
    .buy-btn {
      display: block;
      margin: 20px auto 0;
      padding: 10px 20px;
      background: #28a745;
      color: white;
      border: none;
      border-radius: 5px;
      font-weight: bold;
      cursor: pointer;
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
    <a href="#contact">Contact</a>
  </nav>

  <div class="products" id="products">
    <div class="product">
      <img src="https://images.unsplash.com/photo-1584467735871-bfb5b1c5223d?auto=format&fit=crop&w=800&q=80" alt="Sneakers">
      <h3>Runner One</h3>
      <p>₹999 - Lightweight sneakers for daily hustle</p>
      <button onclick="addToCart('Runner One - ₹999')">Add to Cart</button>
    </div>
    <div class="product">
      <img src="https://images.unsplash.com/photo-1584466991124-74f944c52d80?auto=format&fit=crop&w=800&q=80" alt="Hoodie">
      <h3>Flex Hoodie</h3>
      <p>₹1199 - Premium streetwear hoodie</p>
      <button onclick="addToCart('Flex Hoodie - ₹1199')">Add to Cart</button>
    </div>
  </div>

  <div id="cart">
    <h2>Your Cart</h2>
    <ul id="cart-items"></ul>
    <button class="buy-btn" onclick="buyNow()">Buy Now</button>
  </div>

  <footer id="contact">
    <p>Contact us at: <a style="color:white;" href="mailto:support@weartheluxury.com">support@weartheluxury.com</a></p>
    <p>&copy; 2025 WearTheLuxury | Built with 💙 + 💜</p>
  </footer>

  <script>
    const cartItems = [];
    const cartList = document.getElementById('cart-items');

    function addToCart(item) {
      cartItems.push(item);
      renderCart();
    }

    function renderCart() {
      cartList.innerHTML = '';
      cartItems.forEach((item, index) => {
        const li = document.createElement('li');
        li.textContent = item;
        cartList.appendChild(li);
      });
    }

    function buyNow() {
      if (cartItems.length === 0) {
        alert("Your cart is empty!");
      } else {
        const items = cartItems.join('\n');
        window.location.href = `https://wa.me/918860538136?text=I want to buy:\n${encodeURIComponent(items)}`;
      }
    }
  </script>
</body>
</html>

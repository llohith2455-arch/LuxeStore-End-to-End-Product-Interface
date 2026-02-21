<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Premium Store | Nike Air Max</title>
    <style>
        :root {
            --primary: #000000;
            --accent: #ff4757;
            --text-dark: #1a1a1a;
            --text-light: #707072;
            --bg-gray: #f5f5f5;
            --border: #e5e5e5;
            --success: #2ed573;
        }

        * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Segoe UI', sans-serif; }

        body { background-color: #fff; }

        /* Navigation Bar */
        nav {
            display: flex; justify-content: space-between; align-items: center;
            padding: 15px 5%; border-bottom: 1px solid var(--border);
            background: white; position: sticky; top: 0; z-index: 100;
        }
        .logo { font-weight: 800; font-size: 1.5rem; letter-spacing: -1px; }
        .bag-container { position: relative; cursor: pointer; padding: 10px; }
        #bag-count {
            position: absolute; top: 0; right: 0; background: var(--accent);
            color: white; font-size: 11px; font-weight: bold; width: 18px;
            height: 18px; border-radius: 50%; display: none; justify-content: center; align-items: center;
        }

        /* Main Product Section */
        .container {
            max-width: 1100px; margin: 40px auto;
            display: grid; grid-template-columns: 1.2fr 1fr; gap: 50px; padding: 20px;
        }
        .gallery img { width: 100%; border-radius: 8px; background: var(--bg-gray); }
        .thumbnails { display: flex; gap: 10px; margin-top: 15px; }
        .thumb { width: 70px; height: 70px; cursor: pointer; object-fit: cover; border: 2px solid transparent; border-radius: 4px; }
        .thumb.active { border-color: var(--primary); }

        .info-section h1 { font-size: 2.2rem; margin-bottom: 10px; }
        .price { font-size: 1.6rem; font-weight: 600; margin: 15px 0; }
        .old-price { color: var(--text-light); text-decoration: line-through; font-size: 1.1rem; margin-left: 10px; }
        
        /* Action Buttons */
        .action-row { display: flex; gap: 15px; margin-top: 25px; align-items: stretch; }
        .qty-box { display: flex; align-items: center; border: 1px solid var(--border); border-radius: 8px; background: white; }
        .qty-box button { background: none; border: none; width: 40px; height: 50px; cursor: pointer; font-size: 1.2rem; }
        .qty-box input { width: 30px; text-align: center; border: none; font-weight: bold; outline: none; }
        
        .btn-group { display: flex; gap: 10px; flex: 1; }
        .add-btn { background: var(--primary); color: white; border: none; flex: 1; border-radius: 8px; font-weight: 600; cursor: pointer; transition: 0.2s; }
        .buy-btn { background: var(--accent); color: white; border: none; flex: 1; border-radius: 8px; font-weight: 600; cursor: pointer; transition: 0.2s; }
        .add-btn:hover, .buy-btn:hover { opacity: 0.85; transform: translateY(-1px); }

        /* Related Products */
        .related-section { max-width: 1100px; margin: 60px auto; padding: 20px; border-top: 1px solid var(--border); }
        .related-section h2 { margin-bottom: 30px; font-size: 1.5rem; }
        .related-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 25px; }
        .related-card { cursor: pointer; transition: 0.3s; }
        .related-card:hover { transform: translateY(-5px); }
        .related-card img { width: 100%; border-radius: 8px; background: var(--bg-gray); margin-bottom: 10px; }

        /* Shopping Bag Sidebar */
        .cart-overlay {
            position: fixed; top: 0; right: -400px; width: 380px; height: 100%;
            background: white; box-shadow: -5px 0 20px rgba(0,0,0,0.1);
            z-index: 1001; transition: 0.4s cubic-bezier(0.16, 1, 0.3, 1);
            display: flex; flex-direction: column;
        }
        .cart-overlay.active { right: 0; }
        .cart-header { padding: 25px; display: flex; justify-content: space-between; align-items: center; border-bottom: 1px solid var(--border); }
        .cart-items { flex: 1; overflow-y: auto; padding: 20px; }
        .cart-item { display: flex; gap: 15px; margin-bottom: 20px; align-items: center; }
        .cart-item img { width: 60px; height: 60px; object-fit: cover; border-radius: 4px; }
        .remove-item { font-size: 12px; color: var(--accent); cursor: pointer; text-decoration: underline; margin-top: 5px; display: block; }
        .cart-footer { padding: 25px; border-top: 1px solid var(--border); }
        .checkout-btn { width: 100%; padding: 15px; background: var(--primary); color: white; border: none; border-radius: 8px; font-weight: bold; cursor: pointer; }

        @media (max-width: 768px) { 
            .container { grid-template-columns: 1fr; } 
            .cart-overlay { width: 100%; }
            .action-row { flex-direction: column; }
            .qty-box { justify-content: center; }
        }
    </style>
</head>
<body>

    <nav>
        <div class="logo">LUXE STORE</div>
        <div class="bag-container" onclick="toggleCart()">
            <span style="font-size: 24px;">👜</span>
            <span id="bag-count">0</span>
        </div>
    </nav>

    <div class="container">
        <div class="gallery">
            <img src="https://images.unsplash.com/photo-1542291026-7eec264c27ff?q=80&w=1000" id="main-view">
            <div class="thumbnails">
                <img src="https://images.unsplash.com/photo-1542291026-7eec264c27ff?q=80&w=1000" class="thumb active">
                <img src="https://images.unsplash.com/photo-1606107557195-0e29a4b5b4aa?q=80&w=1000" class="thumb">
            </div>
        </div>
        <div class="info-section">
            <p style="color: var(--accent); font-weight: bold; font-size: 0.9rem;">NIKE EXCLUSIVE</p>
            <h1>Nike Air Max 270</h1>
            <p class="price">₹12,995.00 <span class="old-price">₹15,000.00</span></p>
            <p style="color: #666; line-height: 1.6; margin-bottom: 20px;">The Nike Air Max 270 delivers visible cushioning under every step. Updated for modern comfort, it nods to the original 1991 Air Max 180.</p>
            
            <div class="action-row">
                <div class="qty-box">
                    <button onclick="updateQty(-1)">-</button>
                    <input type="text" id="qty" value="1" readonly>
                    <button onclick="updateQty(1)">+</button>
                </div>
                <div class="btn-group">
                    <button class="add-btn" onclick="addToBag()">Add to Bag</button>
                    <button class="buy-btn" onclick="buyNow()">Buy Now</button>
                </div>
            </div>
        </div>
    </div>

    <div class="related-section">
        <h2>You Might Also Like</h2>
        <div class="related-grid">
            <div class="related-card" onclick="alert('Viewing Product...')">
                <img src="https://images.unsplash.com/photo-1549298916-b41d501d3772?q=80&w=600">
                <h3>Nike Court Vision</h3>
                <p>₹5,995</p>
            </div>
            <div class="related-card" onclick="alert('Viewing Product...')">
                <img src="https://images.unsplash.com/photo-1595950653106-6c9ebd614d3a?q=80&w=600">
                <h3>Nike Air Jordan High</h3>
                <p>₹16,495</p>
            </div>
            <div class="related-card" onclick="alert('Viewing Product...')">
                <img src="https://images.unsplash.com/photo-1525966222134-fcfa99b8ae77?q=80&w=600">
                <h3>Vans Old Skool</h3>
                <p>₹4,500</p>
            </div>
            <div class="related-card" onclick="alert('Viewing Product...')">
                <img src="https://images.unsplash.com/photo-1584735175315-9d5df23860e6?q=80&w=600">
                <h3>Adidas Ultraboost</h3>
                <p>₹14,999</p>
            </div>
        </div>
    </div>

    <div class="cart-overlay" id="cart-drawer">
        <div class="cart-header">
            <h3>Shopping Bag</h3>
            <span style="cursor:pointer; font-size: 24px;" onclick="toggleCart()">×</span>
        </div>
        <div class="cart-items" id="cart-items-list"></div>
        <div class="cart-footer">
            <div style="display:flex; justify-content:space-between; font-weight:bold; margin-bottom:15px;">
                <span>Total</span>
                <span id="cart-total">₹0.00</span>
            </div>
            <button class="checkout-btn" onclick="processCheckout()">Checkout Now</button>
        </div>
    </div>

    <script>
        const product = { name: "Nike Air Max 270", price: 12995, img: "https://images.unsplash.com/photo-1542291026-7eec264c27ff?q=80&w=1000" };
        let cart = [];

        function updateQty(val) {
            const input = document.getElementById('qty');
            let current = parseInt(input.value);
            if (current + val >= 1) input.value = current + val;
        }

        function addToBag() {
            const quantity = parseInt(document.getElementById('qty').value);
            const existingItem = cart.find(item => item.name === product.name);
            if (existingItem) existingItem.qty += quantity;
            else cart.push({ ...product, qty: quantity });
            
            updateUI();
            toggleCart(true);
        }

        function buyNow() {
            // Adds to cart and immediately triggers checkout
            addToBag();
            processCheckout();
        }

        function processCheckout() {
            if (cart.length === 0) {
                alert("Your bag is empty!");
                return;
            }
            const total = cart.reduce((sum, item) => sum + (item.price * item.qty), 0);
            alert(`Proceeding to Secure Payment...\nOrder Total: ₹${total.toLocaleString('en-IN')}`);
            // window.location.href = 'checkout.html'; // Example redirect
        }

        function removeItem(index) {
            cart.splice(index, 1);
            updateUI();
        }

        function updateUI() {
            const badge = document.getElementById('bag-count');
            const totalQty = cart.reduce((sum, item) => sum + item.qty, 0);
            badge.style.display = totalQty > 0 ? "flex" : "none";
            badge.innerText = totalQty;

            const list = document.getElementById('cart-items-list');
            const totalEl = document.getElementById('cart-total');
            list.innerHTML = cart.length === 0 ? '<p style="text-align:center; color:#999; margin-top:50px;">Bag is empty</p>' : "";
            
            let total = 0;
            cart.forEach((item, index) => {
                total += (item.price * item.qty);
                list.innerHTML += `
                    <div class="cart-item">
                        <img src="${item.img}">
                        <div style="flex:1">
                            <div style="font-weight:600">${item.name}</div>
                            <div style="font-size:0.8rem; color:#666">Qty: ${item.qty}</div>
                            <span class="remove-item" onclick="removeItem(${index})">Remove</span>
                        </div>
                        <div style="font-weight:600">₹${(item.price * item.qty).toLocaleString('en-IN')}</div>
                    </div>`;
            });
            totalEl.innerText = `₹${total.toLocaleString('en-IN')}`;
        }

        function toggleCart(open = false) {
            const drawer = document.getElementById('cart-drawer');
            if (open) drawer.classList.add('active');
            else drawer.classList.toggle('active');
        }

        // Gallery Switcher
        document.querySelectorAll('.thumb').forEach(t => {
            t.addEventListener('click', function() {
                document.getElementById('main-view').src = this.src;
                document.querySelectorAll('.thumb').forEach(thumb => thumb.classList.remove('active'));
                this.classList.add('active');
            });
        });
    </script>
</body>
</html>

How the Code Works
This project uses State Management. The "State" is your cart array. When you click buttons, JavaScript updates that array, and the updateUI() function automatically "re-renders" the cart and total price on the screen. It uses CSS Flexbox and Grid to keep the layout clean and professional.

4 Quick Steps to Upload
Prepare: Ensure your file is named exactly index.html.

Create: Go to GitHub, click New Repository, and name it (e.g., nike-store).

Upload: Drag and drop your index.html file into the repository and click Commit changes.

Go Live: Go to Settings > Pages, set the Branch to main, and click Save. GitHub will give you a link to your live store!

Why this code is "GitHub Ready"
Unlike your previous project, this one uses External Image URLs (from Unsplash). This means you don't need to upload any image files; the code will automatically pull the pictures from the internet as soon as the page loads.

Would you like me to show you how to add a "Remove All" button to clear the entire cart at once?


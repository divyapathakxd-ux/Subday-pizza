# Subday-pizza
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Subday Pizza - Fresh Soft Base Pizza</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #fff8f0 0%, #ffe5d9 100%);
            min-height: 100vh;
            padding-bottom: 100px;
        }

        header {
            background: linear-gradient(135deg, #e63946 0%, #d62828 100%);
            color: white;
            padding: 30px 20px;
            text-align: center;
            box-shadow: 0 4px 12px rgba(230, 57, 70, 0.3);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
        }

        header p {
            font-size: 1em;
            margin: 5px 0;
            opacity: 0.95;
        }

        .contact-info {
            margin-top: 15px;
            font-weight: 600;
        }

        .menu-header {
            text-align: center;
            padding: 30px 20px;
            background: white;
            margin: 20px;
            border-radius: 10px;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
        }

        .menu-header h2 {
            color: #e63946;
            margin-bottom: 10px;
        }

        .filters {
            display: flex;
            justify-content: center;
            gap: 10px;
            flex-wrap: wrap;
            margin-bottom: 20px;
        }

        .filter-btn {
            padding: 8px 16px;
            border: 2px solid #ffb703;
            background: white;
            color: #333;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: 500;
        }

        .filter-btn.active {
            background: #ffb703;
            color: white;
        }

        .filter-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(255, 183, 3, 0.3);
        }

        .menu {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 20px;
            padding: 20px;
            max-width: 1200px;
            margin: 0 auto;
        }

        .card {
            background: white;
            padding: 20px;
            border-radius: 12px;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
            display: flex;
            flex-direction: column;
            height: 100%;
        }

        .card:hover {
            transform: translateY(-8px);
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.15);
        }

        .card h3 {
            color: #333;
            margin-bottom: 10px;
            font-size: 1.3em;
        }

        .card p {
            color: #666;
            margin-bottom: 15px;
            flex-grow: 1;
            font-size: 0.95em;
        }

        .price {
            color: #e63946;
            font-size: 1.5em;
            font-weight: bold;
            margin-bottom: 15px;
        }

        .card-footer {
            display: flex;
            gap: 10px;
            margin-top: auto;
        }

        button {
            background: #ffb703;
            border: none;
            padding: 12px 20px;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
            color: #333;
            flex: 1;
        }

        button:hover {
            background: #fb9500;
            transform: scale(1.05);
        }

        button:active {
            transform: scale(0.98);
        }

        .quantity-input {
            width: 60px;
            padding: 10px;
            border: 2px solid #ffb703;
            border-radius: 8px;
            text-align: center;
            font-weight: 600;
        }

        .cart-section {
            position: fixed;
            bottom: 20px;
            right: 20px;
            z-index: 200;
        }

        .cart-btn {
            background: linear-gradient(135deg, #25D366 0%, #1da752 100%);
            color: white;
            padding: 15px 25px;
            border-radius: 50px;
            border: none;
            cursor: pointer;
            font-weight: 600;
            font-size: 1em;
            box-shadow: 0 4px 12px rgba(37, 211, 102, 0.4);
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 10px;
            position: relative;
        }

        .cart-btn:hover {
            transform: scale(1.1);
            box-shadow: 0 6px 16px rgba(37, 211, 102, 0.6);
        }

        .cart-count {
            background: #e63946;
            color: white;
            border-radius: 50%;
            width: 24px;
            height: 24px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.85em;
            font-weight: bold;
        }

        .modal {
            display: none;
            position: fixed;
            z-index: 300;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            animation: fadeIn 0.3s ease;
        }

        .modal.show {
            display: flex;
            align-items: center;
            justify-content: center;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .modal-content {
            background: white;
            padding: 30px;
            border-radius: 15px;
            width: 90%;
            max-width: 500px;
            max-height: 80vh;
            overflow-y: auto;
            animation: slideUp 0.3s ease;
        }

        @keyframes slideUp {
            from { transform: translateY(30px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            border-bottom: 2px solid #eee;
            padding-bottom: 15px;
        }

        .modal-header h2 {
            color: #e63946;
        }

        .close-btn {
            background: none;
            border: none;
            font-size: 1.5em;
            cursor: pointer;
            color: #666;
            width: auto;
            padding: 0;
        }

        .cart-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 12px 0;
            border-bottom: 1px solid #eee;
        }

        .cart-item-info {
            flex-grow: 1;
        }

        .cart-item-name {
            font-weight: 600;
            color: #333;
        }

        .cart-item-price {
            color: #e63946;
            font-weight: bold;
        }

        .remove-btn {
            background: #ff6b6b;
            color: white;
            padding: 8px 12px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-size: 0.85em;
            font-weight: 600;
        }

        .remove-btn:hover {
            background: #ff5252;
        }

        .cart-summary {
            margin-top: 20px;
            padding-top: 20px;
            border-top: 2px solid #eee;
        }

        .summary-row {
            display: flex;
            justify-content: space-between;
            padding: 10px 0;
            font-size: 1.05em;
        }

        .total-row {
            font-weight: bold;
            color: #e63946;
            font-size: 1.3em;
        }

        .order-btn {
            width: 100%;
            margin-top: 20px;
            background: linear-gradient(135deg, #25D366 0%, #1da752 100%);
            color: white;
            padding: 15px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            font-size: 1.05em;
        }

        .order-btn:hover:not(:disabled) {
            transform: scale(1.02);
            box-shadow: 0 4px 12px rgba(37, 211, 102, 0.4);
        }

        .order-btn:disabled {
            background: #ccc;
            cursor: not-allowed;
            opacity: 0.6;
        }

        .empty-cart {
            text-align: center;
            padding: 40px 20px;
            color: #999;
        }

        .empty-cart-icon {
            font-size: 3em;
            margin-bottom: 15px;
        }

        @media (max-width: 768px) {
            header h1 {
                font-size: 1.8em;
            }

            .menu {
                grid-template-columns: 1fr;
                padding: 15px;
            }

            .cart-btn {
                padding: 12px 20px;
                font-size: 0.9em;
            }

            .modal-content {
                width: 95%;
                padding: 20px;
            }
        }

        .success-message {
            display: none;
            position: fixed;
            top: 20px;
            right: 20px;
            background: #25D366;
            color: white;
            padding: 15px 20px;
            border-radius: 8px;
            box-shadow: 0 4px 12px rgba(37, 211, 102, 0.4);
            z-index: 400;
            animation: slideIn 0.3s ease;
        }

        .success-message.show {
            display: block;
        }

        @keyframes slideIn {
            from { transform: translateX(400px); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }
    </style>
</head>

<body>
    <header>
        <h1>🍕 Subday Pizza</h1>
        <p>Fresh Soft Base Pizza</p>
        <div class="contact-info">
            📞 <a href="tel:09773717429" style="color: white; text-decoration: none;">09773717429</a>
        </div>
    </header>

    <div class="menu-header">
        <h2>Our Delicious Menu</h2>
        <p>Choose your favorite pizza and sides</p>
        <div class="filters">
            <button class="filter-btn active" onclick="filterMenu('all')">All Items</button>
            <button class="filter-btn" onclick="filterMenu('pizza')">🍕 Pizzas</button>
            <button class="filter-btn" onclick="filterMenu('burger')">🍔 Burgers</button>
            <button class="filter-btn" onclick="filterMenu('dessert')">🍰 Desserts</button>
        </div>
    </div>

    <div class="menu" id="menuContainer">
        <!-- Menu items will be inserted here by JavaScript -->
    </div>

    <div class="cart-section">
        <button class="cart-btn" onclick="openCart()">
            🛒 Cart
            <span class="cart-count" id="cartCount">0</span>
        </button>
    </div>

    <!-- Cart Modal -->
    <div class="modal" id="cartModal">
        <div class="modal-content">
            <div class="modal-header">
                <h2>Your Order</h2>
                <button class="close-btn" onclick="closeCart()">✕</button>
            </div>
            <div id="cartItems"></div>
            <div class="cart-summary" id="cartSummary"></div>
            <button class="order-btn" id="orderBtn" onclick="sendOrder()">Order on WhatsApp</button>
        </div>
    </div>

    <div class="success-message" id="successMessage">✓ Item added to cart!</div>

    <script>
        const menuData = [
            { id: 1, name: "Cheese Corn Pizza", price: 105, category: "pizza", description: "Fresh corn with melted cheese" },
            { id: 2, name: "Paneer Pizza", price: 150, category: "pizza", description: "Creamy paneer with special sauce" },
            { id: 3, name: "Farm House Pizza", price: 140, category: "pizza", description: "Mix of vegetables and paneer" },
            { id: 4, name: "Tandoori Paneer Pizza", price: 195, category: "pizza", description: "Tandoori flavored paneer pizza" },
            { id: 5, name: "Aloo Tikki Burger", price: 59, category: "burger", description: "Crispy aloo tikki with fresh toppings" },
            { id: 6, name: "Choco Lava Cake", price: 120, category: "dessert", description: "Warm chocolate cake with lava center" }
        ];

        let cart = [];
        let currentFilter = 'all';

        function renderMenu() {
            const container = document.getElementById('menuContainer');
            container.innerHTML = '';

            const filteredMenu = currentFilter === 'all' 
                ? menuData 
                : menuData.filter(item => item.category === currentFilter);

            filteredMenu.forEach(item => {
                const card = document.createElement('div');
                card.className = 'card';
                card.innerHTML = `
                    <h3>${item.name}</h3>
                    <p>${item.description}</p>
                    <div class="price">₹${item.price}</div>
                    <div class="card-footer">
                        <input type="number" class="quantity-input" id="qty-${item.id}" value="1" min="1">
                        <button onclick="addItem(${item.id}, '${item.name}', ${item.price})">Add</button>
                    </div>
                `;
                container.appendChild(card);
            });
        }

        function addItem(id, name, price) {
            const quantity = parseInt(document.getElementById(`qty-${id}`).value) || 1;
            
            for (let i = 0; i < quantity; i++) {
                cart.push({ name, price, id });
            }

            updateCart();
            showSuccessMessage();
            document.getElementById(`qty-${id}`).value = 1;
        }

        function updateCart() {
            document.getElementById('cartCount').textContent = cart.length;
            renderCartItems();
        }

        function renderCartItems() {
            const cartItemsDiv = document.getElementById('cartItems');
            
            if (cart.length === 0) {
                cartItemsDiv.innerHTML = '<div class="empty-cart"><div class="empty-cart-icon">🛒</div><p>Your cart is empty</p></div>';
                document.getElementById('cartSummary').innerHTML = '';
                document.getElementById('orderBtn').disabled = true;
                return;
            }

            let itemsHTML = '';
            const itemGroups = {};

            cart.forEach((item, index) => {
                const key = `${item.name}-${item.price}`;
                if (!itemGroups[key]) {
                    itemGroups[key] = { item, count: 0, indices: [] };
                }
                itemGroups[key].count++;
                itemGroups[key].indices.push(index);
            });

            Object.entries(itemGroups).forEach(([key, group]) => {
                itemsHTML += `
                    <div class="cart-item">
                        <div class="cart-item-info">
                            <div class="cart-item-name">${group.item.name} x ${group.count}</div>
                            <div class="cart-item-price">₹${group.item.price * group.count}</div>
                        </div>
                        <button class="remove-btn" onclick="removeItem('${key}')">Remove</button>
                    </div>
                `;
            });

            cartItemsDiv.innerHTML = itemsHTML;

            const total = cart.reduce((sum, item) => sum + item.price, 0);
            document.getElementById('cartSummary').innerHTML = `
                <div class="summary-row">
                    <span>Subtotal:</span>
                    <span>₹${total}</span>
                </div>
                <div class="summary-row">
                    <span>Delivery:</span>
                    <span>Free</span>
                </div>
                <div class="summary-row total-row">
                    <span>Total:</span>
                    <span>₹${total}</span>
                </div>
            `;

            document.getElementById('orderBtn').disabled = false;
        }

        function removeItem(key) {
            const [name, price] = key.split('-');
            const index = cart.findIndex(item => item.name === name && item.price === parseInt(price));
            if (index > -1) {
                cart.splice(index, 1);
                updateCart();
            }
        }

        function filterMenu(category) {
            currentFilter = category;
            document.querySelectorAll('.filter-btn').forEach(btn => btn.classList.remove('active'));
            event.target.classList.add('active');
            renderMenu();
        }

        function openCart() {
            document.getElementById('cartModal').classList.add('show');
        }

        function closeCart() {
            document.getElementById('cartModal').classList.remove('show');
        }

        function sendOrder() {
            if (cart.length === 0) {
                alert('Please add items to your cart');
                return;
            }

            let text = "Hello Subday Pizza! 🍕%0AI would like to order:%0A%0A";
            const itemGroups = {};

            cart.forEach(item => {
                const key = `${item.name}-${item.price}`;
                if (!itemGroups[key]) {
                    itemGroups[key] = { item, count: 0 };
                }
                itemGroups[key].count++;
            });

            Object.values(itemGroups).forEach(group => {
                text += `• ${group.item.name} x ${group.count} = ₹${group.item.price * group.count}%0A`;
            });

            const total = cart.reduce((sum, item) => sum + item.price, 0);
            text += `%0ATotal: ₹${total}%0A%0AThank you!`;

            window.open(`https://wa.me/919773717429?text=${text}`);
            cart = [];
            updateCart();
            closeCart();
        }

        function showSuccessMessage() {
            const msg = document.getElementById('successMessage');
            msg.classList.add('show');
            setTimeout(() => msg.classList.remove('show'), 2000);
        }

        // Close modal when clicking outside
        document.getElementById('cartModal').addEventListener('click', function(event) {
            if (event.target === this) {
                closeCart();
            }
        });

        // Initialize
        renderMenu();
    </script>
</body>
</html>

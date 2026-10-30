<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ultra Milk Store - Susu Segar Berkualitas</title>
<style>
    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    body {
        background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 50%, #90caf9 100%);
        min-height: 100vh;
        color: #333;
    }

    header {
        background: linear-gradient(135deg, #1565c0 0%, #0d47a1 100%);
        color: white;
        padding: 20px 5%;
        display: flex;
        justify-content: space-between;
        align-items: center;
        box-shadow: 0 4px 20px rgba(0,0,0,0.2);
        position: sticky;
        top: 0;
        z-index: 100;
    }

    .logo {
        display: flex;
        align-items: center;
        gap: 12px;
        font-size: 24px;
        font-weight: bold;
    }

    .logo-icon {
        width: 45px;
        height: 45px;
        background: white;
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 26px;
    }

    .cart-btn {
        background: #ffc107;
        color: #0d47a1;
        border: none;
        padding: 12px 22px;
        border-radius: 30px;
        font-weight: bold;
        cursor: pointer;
        font-size: 15px;
        transition: 0.3s;
        box-shadow: 0 4px 12px rgba(255,193,7,0.4);
    }

    .cart-btn:hover {
        transform: translateY(-2px);
        box-shadow: 0 6px 18px rgba(255,193,7,0.6);
    }

    .hero {
        text-align: center;
        padding: 50px 20px 30px;
    }

    .hero h1 {
        font-size: 42px;
        color: #0d47a1;
        margin-bottom: 12px;
        text-shadow: 2px 2px 4px rgba(255,255,255,0.8);
    }

    .hero p {
        font-size: 18px;
        color: #1565c0;
        margin-bottom: 10px;
    }

    .badge {
        display: inline-block;
        background: #ffc107;
        color: #0d47a1;
        padding: 8px 20px;
        border-radius: 20px;
        font-weight: bold;
        margin-top: 10px;
        animation: pulse 2s infinite;
    }

    @keyframes pulse {
        0%, 100% { transform: scale(1); }
        50% { transform: scale(1.05); }
    }

    .container {
        max-width: 1200px;
        margin: 0 auto;
        padding: 20px;
    }

    .section-title {
        text-align: center;
        color: #0d47a1;
        font-size: 28px;
        margin-bottom: 30px;
        position: relative;
        padding-bottom: 12px;
    }

    .section-title::after {
        content: '';
        position: absolute;
        bottom: 0;
        left: 50%;
        transform: translateX(-50%);
        width: 80px;
        height: 4px;
        background: linear-gradient(90deg, #1565c0, #ffc107);
        border-radius: 2px;
    }

    .products {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
        gap: 25px;
        margin-bottom: 50px;
    }

    .product-card {
        background: white;
        border-radius: 20px;
        overflow: hidden;
        box-shadow: 0 6px 20px rgba(21,101,192,0.15);
        transition: 0.3s;
        display: flex;
        flex-direction: column;
    }

    .product-card:hover {
        transform: translateY(-8px);
        box-shadow: 0 12px 30px rgba(21,101,192,0.3);
    }

    .product-img {
        height: 180px;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 80px;
        position: relative;
        overflow: hidden;
    }

    .product-img.original { background: linear-gradient(135deg, #e3f2fd, #90caf9); }
    .product-img.strawberry { background: linear-gradient(135deg, #ffcdd2, #f8bbd0); }
    .product-img.chocolate { background: linear-gradient(135deg, #d7ccc8, #bcaaa4); }
    .product-img.mocha { background: linear-gradient(135deg, #f5e6d3, #d7bda1); }
    .product-img.vanilla { background: linear-gradient(135deg, #fff9c4, #fff59d); }
    .product-img.lowfat { background: linear-gradient(135deg, #c8e6c9, #a5d6a7); }

    .product-info {
        padding: 18px;
        display: flex;
        flex-direction: column;
        flex-grow: 1;
    }

    .product-info h3 {
        color: #0d47a1;
        font-size: 18px;
        margin-bottom: 6px;
    }

    .product-info .desc {
        font-size: 13px;
        color: #666;
        margin-bottom: 12px;
        flex-grow: 1;
    }

    .price {
        font-size: 22px;
        font-weight: bold;
        color: #e91e63;
        margin-bottom: 12px;
    }

    .add-btn {
        background: linear-gradient(135deg, #1565c0, #0d47a1);
        color: white;
        border: none;
        padding: 12px;
        border-radius: 12px;
        font-weight: bold;
        cursor: pointer;
        transition: 0.3s;
        font-size: 14px;
    }

    .add-btn:hover {
        background: linear-gradient(135deg, #1976d2, #1565c0);
        transform: scale(1.02);
    }

    .modal-overlay {
        display: none;
        position: fixed;
        top: 0; left: 0;
        width: 100%; height: 100%;
        background: rgba(0,0,0,0.6);
        z-index: 999;
        backdrop-filter: blur(4px);
    }

    .modal-overlay.active { display: flex; align-items: center; justify-content: center; padding: 20px; }

    .modal {
        background: white;
        border-radius: 20px;
        max-width: 500px;
        width: 100%;
        max-height: 90vh;
        overflow-y: auto;
        padding: 25px;
        animation: slideUp 0.4s ease;
    }

    @keyframes slideUp {
        from { transform: translateY(50px); opacity: 0; }
        to { transform: translateY(0); opacity: 1; }
    }

    .modal-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
        padding-bottom: 15px;
        border-bottom: 2px solid #e3f2fd;
    }

    .modal-header h2 { color: #0d47a1; }

    .close-btn {
        background: #ff5252;
        color: white;
        border: none;
        width: 35px; height: 35px;
        border-radius: 50%;
        cursor: pointer;
        font-size: 18px;
        font-weight: bold;
    }

    .cart-item {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 12px;
        background: #f5f9ff;
        border-radius: 12px;
        margin-bottom: 10px;
    }

    .cart-item-info { flex: 1; }
    .cart-item-info strong { color: #0d47a1; font-size: 14px; }
    .cart-item-info small { color: #666; display: block; }

    .qty-controls {
        display: flex;
        align-items: center;
        gap: 8px;
    }

    .qty-btn {
        background: #1565c0;
        color: white;
        border: none;
        width: 28px; height: 28px;
        border-radius: 50%;
        cursor: pointer;
        font-weight: bold;
    }

    .qty-btn:hover { background: #0d47a1; }

    .qty-num {
        min-width: 25px;
        text-align: center;
        font-weight: bold;
        color: #0d47a1;
    }

    .empty-cart {
        text-align: center;
        color: #999;
        padding: 30px 0;
    }

    .cart-total {
        display: flex;
        justify-content: space-between;
        padding: 15px 0;
        border-top: 2px solid #e3f2fd;
        font-size: 18px;
        font-weight: bold;
        color: #0d47a1;
        margin-top: 10px;
    }

    .form-group {
        margin-bottom: 15px;
    }

    .form-group label {
        display: block;
        margin-bottom: 6px;
        font-weight: 600;
        color: #0d47a1;
        font-size: 14px;
    }

    .form-group input,
    .form-group textarea {
        width: 100%;
        padding: 12px;
        border: 2px solid #e3f2fd;
        border-radius: 10px;
        font-size: 14px;
        font-family: inherit;
        transition: 0.3s;
    }

    .form-group input:focus,
    .form-group textarea:focus {
        outline: none;
        border-color: #1565c0;
    }

    .checkout-btn {
        width: 100%;
        background: linear-gradient(135deg, #25d366, #128c7e);
        color: white;
        border: none;
        padding: 15px;
        border-radius: 12px;
        font-size: 16px;
        font-weight: bold;
        cursor: pointer;
        margin-top: 15px;
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 10px;
        transition: 0.3s;
        box-shadow: 0 4px 15px rgba(37,211,102,0.4);
    }

    .checkout-btn:hover {
        transform: translateY(-2px);
        box-shadow: 0 6px 20px rgba(37,211,102,0.6);
    }

    .toast {
        position: fixed;
        bottom: 30px;
        left: 50%;
        transform: translateX(-50%) translateY(100px);
        background: #0d47a1;
        color: white;
        padding: 14px 25px;
        border-radius: 30px;
        box-shadow: 0 6px 20px rgba(0,0,0,0.3);
        opacity: 0;
        transition: 0.4s;
        z-index: 2000;
        font-weight: 600;
    }

    .toast.show {
        transform: translateX(-50%) translateY(0);
        opacity: 1;
    }

    footer {
        background: #0d47a1;
        color: white;
        text-align: center;
        padding: 25px;
        margin-top: 40px;
    }

    footer p { font-size: 14px; opacity: 0.9; }

    @media (max-width: 600px) {
        .hero h1 { font-size: 28px; }
        .logo { font-size: 18px; }
        .cart-btn { padding: 10px 16px; font-size: 13px; }
    }
</style>
</head>
<body>

<header>
    <div class="logo">
        <div class="logo-icon">🥛</div>
        <span>Ultra Milk Store</span>
    </div>
    <button class="cart-btn" onclick="openCart()">
        🛒 Keranjang (<span id="cartCount">0</span>)
    </button>
</header>

<section class="hero">
    <h1>🥛 Ultra Milk Segar</h1>
    <p>Susu berkualitas tinggi untuk keluarga Indonesia</p>
    <div class="badge">✨ Gratis Ongkir Min. 5 Pcs ✨</div>
</section>

<div class="container">
    <h2 class="section-title">Pilihan Varian Ultra Milk</h2>
    <div class="products" id="productList"></div>
</div>

<div class="modal-overlay" id="cartModal">
    <div class="modal">
        <div class="modal-header">
            <h2>🛒 Keranjang Belanja</h2>
            <button class="close-btn" onclick="closeCart()">✕</button>
        </div>
        <div id="cartItems"></div>
        <div id="cartTotal"></div>

        <div id="orderForm" style="display:none; margin-top:20px;">
            <div class="form-group">
                <label>Nama Lengkap *</label>
                <input type="text" id="customerName" placeholder="Masukkan nama Anda">
            </div>
            <div class="form-group">
                <label>No. WhatsApp *</label>
                <input type="tel" id="customerPhone" placeholder="Contoh: 08123456789">
            </div>
            <div class="form-group">
                <label>Alamat Pengiriman *</label>
                <textarea id="customerAddress" rows="3" placeholder="Alamat lengkap pengiriman"></textarea>
            </div>
            <div class="form-group">
                <label>Catatan (opsional)</label>
                <textarea id="customerNote" rows="2" placeholder="Contoh: Kirim pagi hari"></textarea>
            </div>
            <button class="checkout-btn" onclick="checkoutWA()">
                📱 Pesan via WhatsApp
            </button>
        </div>
    </div>
</div>

<div class="toast" id="toast">Produk ditambahkan ke keranjang!</div>

<footer>
    <p>© 2024 Ultra Milk Store - Susu Segar Berkualitas</p>
    <p style="margin-top:8px;font-size:12px;">Pesan langsung melalui WhatsApp untuk proses cepat</p>
</footer>

<script>
// ================= KONFIGURASI =================
const WHATSAPP_NUMBER = "6285772590983"; // Nomor WA penjual

// ================= DATA PRODUK =================
const products = [
    { id: 1, name: "Ultra Milk Original", desc: "Susu murni segar 250ml", price: 6000, img: "🥛", class: "original" },
    { id: 2, name: "Ultra Milk Strawberry", desc: "Rasa stroberi manis 250ml", price: 6500, img: "🍓", class: "strawberry" },
    { id: 3, name: "Ultra Milk Chocolate", desc: "Cokelat lezat 250ml", price: 6500, img: "🍫", class: "chocolate" },
    { id: 4, name: "Ultra Milk Mocha", desc: "Kopi mocha creamy 250ml", price: 7000, img: "☕", class: "mocha" },
    { id: 5, name: "Ultra Milk Vanilla", desc: "Vanila lembut 250ml", price: 6500, img: "🍦", class: "vanilla" },
    { id: 6, name: "Ultra Milk Low Fat", desc: "Rendah lemak 250ml", price: 7000, img: "🥛", class: "lowfat" },
    { id: 7, name: "Ultra Milk Full Cream 1L", desc: "Kemasan besar 1 liter", price: 18000, img: "🥛", class: "original" },
    { id: 8, name: "Ultra Milk Chocolate 1L", desc: "Cokelat kemasan 1 liter", price: 20000, img: "🍫", class: "chocolate" },
];

let cart = JSON.parse(localStorage.getItem('ultraCart')) || [];

function renderProducts() {
    const list = document.getElementById('productList');
    list.innerHTML = products.map(p => `
        <div class="product-card">
            <div class="product-img ${p.class}">${p.img}</div>
            <div class="product-info">
                <h3>${p.name}</h3>
                <p class="desc">${p.desc}</p>
                <div class="price">Rp ${p.price.toLocaleString('id-ID')}</div>
                <button class="add-btn" onclick="addToCart(${p.id})">+ Tambah</button>
            </div>
        </div>
    `).join('');
}

function addToCart(id) {
    const product = products.find(p => p.id === id);
    const existing = cart.find(item => item.id === id);

    if (existing) {
        existing.qty += 1;
    } else {
        cart.push({ ...product, qty: 1 });
    }

    saveCart();
    updateCartCount();
    showToast(`${product.name} ditambahkan!`);
}

function saveCart() {
    localStorage.setItem('ultraCart', JSON.stringify(cart));
}

function updateCartCount() {
    const count = cart.reduce((sum, item) => sum + item.qty, 0);
    document.getElementById('cartCount').textContent = count;
}

function renderCart() {
    const cartItems = document.getElementById('cartItems');
    const cartTotal = document.getElementById('cartTotal');
    const orderForm = document.getElementById('orderForm');

    if (cart.length === 0) {
        cartItems.innerHTML = '<div class="empty-cart">🛒 Keranjang masih kosong<br><small>Yuk pilih susu favoritmu!</small></div>';
        cartTotal.innerHTML = '';
        orderForm.style.display = 'none';
        return;
    }

    cartItems.innerHTML = cart.map(item => `
        <div class="cart-item">
            <div class="cart-item-info">
                <strong>${item.name}</strong>
                <small>Rp ${item.price.toLocaleString('id-ID')} × ${item.qty}</small>
            </div>
            <div class="qty-controls">
                <button class="qty-btn" onclick="changeQty(${item.id}, -1)">−</button>
                <span class="qty-num">${item.qty}</span>
                <button class="qty-btn" onclick="changeQty(${item.id}, 1)">+</button>
            </div>
        </div>
    `).join('');

    const total = cart.reduce((sum, item) => sum + item.price * item.qty, 0);
    cartTotal.innerHTML = `
        <div class="cart-total">
            <span>Total:</span>
            <span>Rp ${total.toLocaleString('id-ID')}</span>
        </div>
    `;
    orderForm.style.display = 'block';
}

function changeQty(id, delta) {
    const item = cart.find(i => i.id === id);
    if (!item) return;

    item.qty += delta;
    if (item.qty <= 0) {
        cart = cart.filter(i => i.id !== id);
    }
    saveCart();
    updateCartCount();
    renderCart();
}

function openCart() {
    document.getElementById('cartModal').classList.add('active');
    renderCart();
}

function closeCart() {
    document.getElementById('cartModal').classList.remove('active');
}

document.getElementById('cartModal').addEventListener('click', (e) => {
    if (e.target.id === 'cartModal') closeCart();
});

function checkoutWA() {
    if (cart.length === 0) {
        showToast('Keranjang masih kosong!');
        return;
    }

    const name = document.getElementById('customerName').value.trim();
    const phone = document.getElementById('customerPhone').value.trim();
    const address = document.getElementById('customerAddress').value.trim();
    const note = document.getElementById('customerNote').value.trim();

    if (!name || !phone || !address) {
        showToast('⚠️ Lengkapi nama, no. WA, dan alamat!');
        return;
    }

    const total = cart.reduce((sum, item) => sum + item.price * item.qty, 0);
    const orderId = 'UM-' + Date.now().toString().slice(-6);

    let message = `*🛒 PESANAN BARU - ULTRA MILK STORE*%0A`;
    message += `━━━━━━━━━━━━━━━━━━%0A`;
    message += `*Order ID:* ${orderId}%0A`;
    message += `*Nama:* ${name}%0A`;
    message += `*No. WA:* ${phone}%0A`;
    message += `*Alamat:* ${address}%0A`;
    if (note) message += `*Catatan:* ${note}%0A`;
    message += `━━━━━━━━━━━━━━━━━━%0A`;
    message += `*📦 DETAIL PESANAN:*%0A`;

    cart.forEach((item, i) => {
        message += `${i + 1}. ${item.name}%0A`;
        message += `   ${item.qty} × Rp ${item.price.toLocaleString('id-ID')} = Rp ${(item.price * item.qty).toLocaleString('id-ID')}%0A`;
    });

    message += `━━━━━━━━━━━━━━━━━━%0A`;
    message += `*💰 TOTAL: Rp ${total.toLocaleString('id-ID')}*%0A`;
    message += `━━━━━━━━━━━━━━━━━━%0A`;
    message += `Mohon segera diproses ya kak 🙏`;

    const waUrl = `https://wa.me/${WHATSAPP_NUMBER}?text=${message}`;
    window.open(waUrl, '_blank');

    showToast('✅ Pesanan dikirim ke WhatsApp!');

    setTimeout(() => {
        cart = [];
        saveCart();
        updateCartCount();
        renderCart();
        closeCart();
        document.getElementById('customerName').value = '';
        document.getElementById('customerPhone').value = '';
        document.getElementById('customerAddress').value = '';
        document.getElementById('customerNote').value = '';
    }, 1500);
}

let toastTimeout;
function showToast(msg) {
    const toast = document.getElementById('toast');
    toast.textContent = msg;
    toast.classList.add('show');
    clearTimeout(toastTimeout);
    toastTimeout = setTimeout(() => toast.classList.remove('show'), 2500);
}

renderProducts();
updateCartCount();
</script>

</body>
</html>

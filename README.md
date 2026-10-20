<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ANIME ZERO - บริการรับฟาร์มเกมออนไลน์</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;500;600;700&display=swap');
        * { font-family: 'Kanit', sans-serif; }
        body { background-color: #080f1e; color: #e2f1f8; }
        .ice-glow { box-shadow: 0 0 20px rgba(56, 189, 248, 0.35); }
        .ice-border { border: 1px solid rgba(56, 189, 248, 0.3); }
        .bg-glass { background: rgba(15, 23, 42, 0.85); backdrop-filter: blur(12px); }
        .mascot-img { filter: drop-shadow(0 0 12px rgba(56, 189, 248, 0.5)); }
        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-track { background: #080f1e; }
        ::-webkit-scrollbar-thumb { background: #0284c7; border-radius: 10px; }
    </style>
</head>
<body class="min-h-screen flex flex-col justify-between selection:bg-cyan-500 selection:text-slate-900"<!-- NAVBAR -->
    <nav class="bg-slate-900/90 border-b border-cyan-500/30 sticky top-0 z-40 px-4 py-3 backdrop-blur-md shadow-lg">
        <div class="max-w-7xl mx-auto flex justify-between items-center">
            <div class="flex items-center space-x-3">
                <div class="w-11 h-11 rounded-full bg-cyan-900/40 border-2 border-cyan-400 overflow-hidden flex items-center justify-center ice-glow">
                    <span class="text-2xl">❄️</span>
                </div>
                <div>
                    <span class="text-2xl font-black tracking-wider text-transparent bg-clip-text bg-gradient-to-r from-cyan-300 via-sky-200 to-blue-400">ANIME ZERO</span>
                    <p class="text-[10px] text-cyan-400 tracking-widest uppercase font-semibold">Game Farming Service</p>
                </div>
            </div>
            
<div class="flex items-center space-x-3"<!-- เหรียญ Fong -->
                <div class="bg-slate-800/80 border border-cyan-500/40 px-3.5 py-1.5 rounded-full flex items-center space-x-2 ice-glow">
                    <i class="fas fa-coins text-amber-400 text-sm"></i>
                    <span class="text-xs text-cyan-300 font-medium">Fong:</span>
                    <span id="fongBalance" class="font-bold text-white text-sm">100</span<!ปุ่มเปลี่ยนโหมด แอดมิน/ลูกค้า -->
                <button id="adminLoginBtn" onclick="openAdminAuth()" class="bg-cyan-500/10 hover:bg-cyan-500/25 border border-cyan-400/50 text-cyan-300 px-3.5 py-1.5 rounded-xl text-xs font-semibold flex items-center gap-1.5 transition ice-glow">
                    <i class="fas fa-user-shield"></i>
                    <span id="adminBtnText">เข้าสู่ระบบผู้ดูแล</span>
                </button>
            </div>
        </div>
    </nav>
!-- BANNER HERO SECTION -->
    <header class="max-w-7xl mx-auto px-4 mt-6 w-full">
        <div class="bg-glass ice-border rounded-3xl p-6 md:p-8 flex flex-col md:flex-row items-center justify-between relative overflow-hidden ice-glow gap-6">
            <div class="z-10 text-center md:text-left max-w-xl">
                <span class="bg-cyan-500/20 text-cyan-300 text-xs px-3 py-1 rounded-full border border-cyan-400/40 font-semibold uppercase tracking-wider inline-block mb-3">
                    ✨ ร้านบริการฟาร์มเกมอนิเมะอันดับ 1
                </span>
                <h1 class="text-3xl md:text-5xl font-extrabold text-white leading-tight mb-3">
                    ยกระดับการเล่นเกมด้วย <span class="text-transparent bg-clip-text bg-gradient-to-r from-cyan-300 to-blue-400">ANIME ZERO</span>
                </h1>
                <p class="text-slate-300 text-sm md:text-base font-light mb-6">
                    ยินดีต้อนรับสู่บริการฟาร์มเกม ปลอดภัย 100% ทำงานรวดเร็ว พร้อมระบบติดตามคำสั่งซื้อเรียลไทม์!
                </p>
                <div class="flex flex-wrap gap-3 justify-center md:justify-start">
                    <a href="#productsSection" class="bg-gradient-to-r from-cyan-500 to-blue-600 hover:from-cyan-400 hover:to-blue-500 text-slate-950 font-bold px-6 py-2.5 rounded-xl text-sm shadow-lg transition transform hover:-translate-y-0.5">
                        <i class="fas fa-shopping-cart mr-1"></i> เลือกซื้อบริการ
                    </a>
                    <button onclick="toggleOrdersModal()" class="bg-slate-800/80 hover:bg-slate-700 text-cyan-300 border border-cyan-500/30 font-semibold px-5 py-2.5 rounded-xl text-sm transition">
                        <i class="fas fa-receipt mr-1"></i> ตรวจสอบคำสั่งซื้อ
                    </button>
                </div>
            </div>
!-- มาสคอตตัวละคร -->
            <div class="z-10 flex-shrink-0 relative">
                <div class="w-48 h-48 md:w-56 md:h-56 rounded-full bg-cyan-500/10 border-2 border-cyan-400/40 flex items-center justify-center overflow-hidden ice-glow p-2">
                    <img src="https://images2.imgbox.com/f0/73/pWcE8q48_o.jpg" alt="ANIME ZERO Mascot" class="w-full h-full object-cover rounded-full mascot-img">
                </div>
            </div>
        </div>
    </header>
!-- ADMIN PANEL (แสดงเมื่อเข้าแอดมินสำเร็จ) -->
    <section id="adminDashboard" class="hidden max-w-7xl mx-auto px-4 mt-8 w-full">
        <div class="bg-slate-900/95 border-2 border-cyan-400 rounded-3xl p-6 ice-glow">
            <div class="flex flex-col md:flex-row justify-between items-start md:items-center border-b border-slate-700/80 pb-4 mb-6 gap-4">
                <div>
                    <h2 class="text-2xl font-bold text-cyan-300 flex items-center gap-2">
                        <i class="fas fa-tools text-cyan-400"></i> แผงควบคุมผู้ดูแลระบบ (Admin Dashboard)
                    </h2>
                    <p class="text-xs text-slate-400">จัดการข้อมูลบริการ เติมเหรียญ และติดตามออเดอร์ของลูกค้าได้ที่นี่</p>
                </div>
                <button onclick="logoutAdmin()" class="bg-red-500/20 hover:bg-red-500/30 text-red-400 border border-red-500/40 px-4 py-2 rounded-xl text-xs font-bold transition">
                    <i class="fas fa-sign-out-alt mr-1"></i> ออกจากระบบแอดมิน
                </button>
            </div>
<div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-6">
                <button onclick="addNewProductModal()" class="bg-gradient-to-r from-cyan-600 to-blue-600 hover:from-cyan-500 hover:to-blue-500 text-white p-4 rounded-2xl font-bold text-sm shadow flex items-center justify-center gap-2 transition">
                    <i class="fas fa-plus-circle text-lg"></i> เพิ่มรายการบริการใหม่
                </button>
                <button onclick="addFongCoinsModal()" class="bg-slate-800 hover:bg-slate-700 text-cyan-300 border border-cyan-500/40 p-4 rounded-2xl font-bold text-sm shadow flex items-center justify-center gap-2 transition">
                    <i class="fas fa-coins text-amber-400 text-lg"></i> เติมเหรียญ Fong ให้บัญชี
                </button>
                <button onclick="toggleOrdersModal()" class="bg-slate-800 hover:bg-slate-700 text-sky-300 border border-sky-500/40 p-4 rounded-2xl font-bold text-sm shadow flex items-center justify-center gap-2 transition">
                    <i class="fas fa-tasks text-lg"></i> จัดการรายการคำสั่งซื้อทั้งหมด
                </button>
            </div>
        </div>
    </section>!-- MAIN CONTENT / PRODUCTS -->
    <main id="productsSection" class="max-w-7xl mx-auto px-4 py-8 w-full">
        <div class="flex justify-between items-center mb-6">
            <h2 class="text-2xl font-bold text-cyan-300 flex items-center gap-2">
                <i class="fas fa-fire text-amber-400"></i> บริการฟาร์มเกมทั้งหมด
            </h2>
            <span id="productCountBadge" class="text-xs bg-slate-800 border border-cyan-500/30 text-cyan-300 px-3 py-1 rounded-full">
                พร้อมให้บริการ
            </span>
        </div>

!-- PRODUCT GRID -->
        <div id="productGrid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
        !-- สินค้าจะโหลดด้วย JS -->
        </div>
    </main>!-- FLOATING CHAT BUTTON & MODAL -->
    <div class="fixed bottom-6 right-6 z-50">
        <button onclick="toggleChatModal()" class="w-14 h-14 bg-gradient-to-r from-cyan-400 to-blue-500 hover:from-cyan-300 hover:to-blue-400 text-slate-950 rounded-full flex items-center justify-center text-2xl shadow-2xl transition transform hover:scale-110 ice-glow">
            <i class="fas fa-comments"></i>
        </button>
    </div><-- CHAT BOX MODAL -->
    <div id="chatModal" class="hidden fixed bottom-24 right-6 w-80 sm:w-96 bg-slate-900 border border-cyan-400 rounded-3xl shadow-2xl z-50 overflow-hidden ice-glow">
        <div class="bg-slate-800 px-4 py-3 border-b border-slate-700 flex justify-between items-center">
            <div class="flex items-center space-x-2">
                <div class="w-3 h-3 rounded-full bg-emerald-400 animate-pulse"></div>
                <span class="font-bold text-sm text-cyan-300">แชตสอบถามแอดมิน ANIME ZERO</span>
            </div>
            <button onclick="toggleChatModal()" class="text-slate-400 hover:text-white"><i class="fas fa-times"></i></button>
        </div>
        <div id="chatMessages" class="p-4 h-64 overflow-y-auto space-y-3 text-xs">
            <div class="bg-slate-800 p-3 rounded-2xl max-w-[85%] border border-cyan-500/20">
                <p class="text-cyan-300 font-bold mb-1">🤖 แอดมิน ANIME ZERO</p>
                <p class="text-slate-200">สวัสดีครับ! สอบถามรายละเอียดบริการฟาร์มเกม หรือแจ้งปัญหาได้เลยครับ</p>
            </div>
        </div>
        <div class="p-3 bg-slate-950 border-t border-slate-800 flex gap-2">
            <input id="chatInput" type="text" placeholder="พิมพ์ข้อความที่นี่..." class="w-full bg-slate-800 border border-slate-700 rounded-xl px-3 py-2 text-xs text-white focus:outline-none focus:border-cyan-400">
            <button onclick="sendMessage()" class="bg-cyan-500 hover:bg-cyan-400 text-slate-950 px-3 py-2 rounded-xl text-xs font-bold transition">
                <i class="fas fa-paper-plane"></i>
            </button>
        </div>
    </div>

-- ORDERS LIST MODAL -->
    <div id="ordersModal" class="hidden fixed inset-0 bg-slate-950/80 backdrop-blur-sm z-50 flex items-center justify-center p-4">
        <div class="bg-slate-900 border border-cyan-400 rounded-3xl w-full max-w-2xl max-h-[85vh] flex flex-col overflow-hidden ice-glow">
            <div class="p-5 border-b border-slate-800 flex justify-between items-center">
                <h3 class="text-lg font-bold text-cyan-300 flex items-center gap-2">
                    <i class="fas fa-clipboard-list"></i> รายการคำสั่งซื้อทั้งหมด
                </h3>
                <button onclick="toggleOrdersModal()" class="text-slate-400 hover:text-white"><i class="fas fa-times text-lg"></i></button>
            </div>
            <div id="ordersList" class="p-5 overflow-y-auto space-y-3 flex-1 text-xs">
                !-- คำสั่งซื้อจะมาแสดงที่นี่ -->
            </div>
        </div>
    </div>

!-- FOOTER -->
    <footer class="bg-slate-950 border-t border-slate-800/80 text-center py-6 text-xs text-slate-500">
        <p class="mb-1">© 2026 ANIME ZERO Shop. All Rights Reserved.</p>
        <p class="text-[10px] text-slate-600">รหัสผ่านแอดมินสำหรับเจ้าของร้าน: <span class="text-cyan-400">ฟง888.</span></p>
    </footer>

-- JAVASCRIPT SYSTEM LOGIC -->
    <script>
        const ADMIN_CODE = "ฟง888.";
        let isAdmin = false;
        let fongCoins = 100;

let products = [
            { id: 1, name: "ฟาร์มเลเวล Roblox Blox Fruits", price: 50, detail: "ฟาร์มเลเวล 1 - Max การันตีรวดเร็ว ไม่ใช้โปรโมชั่นสุ่มเสี่ยง" },
            { id: 2, name: "เหมาดันเจี้ยน / หาวัตถุดิบหายาก", price: 80, detail: "การันตีไอเทมระดับตามสั่ง ทีมงานกดเอง 100%" },
            { id: 3, name: "จัดเซ็ตตัวละคร Neverness to Everness", price: 120, detail: "ปรับแต่งสเตตัส และปั้นตัวละครพร้อมลุยคอนเทนต์" }
        ];

let orders = [
            { id: "AZ-1001", item: "ฟาร์มเลเวล Roblox Blox Fruits", price: 50, status: "กำลังฟาร์ม ⏳", user: "Customer01" }
        ];

// Render Products
        function renderProducts() {
            const grid = document.getElementById('productGrid');
            grid.innerHTML = '';
document.getElementById('productCountBadge').innerText {products.length} รายการ
 products.forEach(p => {
                grid.innerHTML += div class="bg-glass ice-border rounded-2xl p-5 hover:border-cyan-400/80 transition duration-300 flex flex-col justify-between group ice-glow">
                        <div>
                            <div class="w-full h-36 bg-slate-800/80 rounded-xl overflow-hidden mb-4 border border-cyan-500/20 flex items-center justify-center relative">
                                <img src="https://images2.imgbox.com/f0/73/pWcE8q48_o.jpg" class="w-full h-full object-cover group-hover:scale-110 transition duration-500">
                                <span class="absolute top-2 right-2 bg-slate-900/80 backdrop-blur-md text-cyan-300 text-[10px] px-2 py-1 rounded-md font-bold border border-cyan-400/30">
                                    ANIME ZERO
                                </span>
                            </div>
                            <h3 class="font-bold text-base text-white mb-2 group-hover:text-cyan-300 transition">${p.name}</h3>
                            <p class="text-xs text-slate-300 mb-4 line-clamp-2">${p.detail}</p>
                        </div>
                        <div class="pt-4 border-t border-slate-700/60 flex items-center justify-between">
                            <div>
                                <span class="text-xs text-slate-400">ราคาบริการ</span>
                                <div class="text-cyan-300 font-extrabold text-lg">${p.price} <small class="text-xs font-normal">Fong</small></div>
                            </div>
                            <div class="flex gap-1.5">
                                ${isAdmin ? <button onclick="deleteProduct(${p.id})" class="bg-red-500/20 hover:bg-red-500/40 text-red-400 p-2 rounded-xl text-xs transition"><i class="fas fa-trash"></i></button> : ''}
                                <button onclick="buyProduct('${p.name}', ${p.price})" class="bg-gradient-to-r from-cyan-500 to-blue-500 hover:from-cyan-400 hover:to-blue-400 text-slate-950 font-bold px-4 py-2 rounded-xl text-xs transition shadow-md">
                                    สั่งซื้อเลย
                                </button>
                            </div>
                        </div>
                    </div>
                `;
            });
        }

// Admin Auth
        function openAdminAuth() {
            if (isAdmin) {
                document.getElementById('adminDashboard').scrollIntoView({ behavior: 'smooth' });
                return;
            }
 Swal.fire({
                title: '🔑 ยืนยันสิทธิ์ผู้ดูแลระบบ',
                text: 'กรุณากรอกรหัสเชิญแอดมินเพื่อเข้าสู่หน้าจัดการหลังบ้าน',
                input: 'password',
                inputPlaceholder: 'กรอกรหัสแอดมิน...',
                showCancelButton: true,
                confirmButtonText: 'เข้าสู่ระบบ',
                cancelButtonText: 'ยกเลิก',
                confirmButtonColor: '#0284c7',
                background: '#0f172a',
                color: '#fff'
            }).then((res) => {
                if (res.isConfirmed) {
                    if (res.value === ADMIN_CODE) {
                        isAdmin = true;
                        document.getElementById('adminDashboard').classList.remove('hidden');
                        document.getElementById('adminBtnText').innerText = "โหมดผู้ดูแลระบบ Active";
                        renderProducts();
                        Swal.fire({ icon: 'success', title: 'ยินดีต้อนรับแอดมิน!', text: 'เปิดใช้งานเมนูหลังบ้านเรียบร้อย', background: '#0f172a', color: '#fff', confirmButtonColor: '#0284c7' });
                    } else {
                        Swal.fire({ icon: 'error', title: 'รหัสไม่ถูกต้อง', text: 'กรุณาตรวจสอบรหัสเชิญใหม่อีกครั้ง', background: '#0f172a', color: '#fff', confirmButtonColor: '#ef4444' });
                    }
                }
            });
        }

function logoutAdmin() {
            isAdmin = false;
            document.getElementById('adminDashboard').classList.add('hidden');
            document.getElementById('adminBtnText').innerText = "เข้าสู่ระบบผู้ดูแล";
            renderProducts();
            Swal.fire({ icon: 'info', title: 'ออกจากระบบแล้ว', timer: 1200, showConfirmButton: false, background: '#0f172a', color: '#fff' });
        }

// Buy Product
        function buyProduct(name, price) {
            if (fongCoins < price) {
                Swal.fire({ icon: 'warning', title: 'เหรียญ Fong ไม่พอ!', text: 'กรุณาเติมเหรียญก่อนทำรายการสั่งซื้อ', background: '#0f172a', color: '#fff', confirmButtonColor: '#0284c7' });
                return;
            }

Swal.fire({
                title: 'ยืนยันการสั่งซื้อ',
                text: `คุณต้องการซื้อ ${name} ในราคา ${price} Fong หรือไม่?`,
                icon: 'question',
                showCancelButton: true,
                confirmButtonText: 'ยืนยันสั่งซื้อ',
                cancelButtonText: 'ยกเลิก',
                confirmButtonColor: '#0284c7',
                background: '#0f172a',
                color: '#fff'
            }).then((res) => {
                if (res.isConfirmed) {
                    fongCoins -= price;
                    document.getElementById('fongBalance').innerText = fongCoins;
                    const orderId = "AZ-" + Math.floor(1000 + Math.random() * 9000);
                    orders.push({ id: orderId, item: name, price: price, status: "กำลังฟาร์ม ⏳", user: "คุณลูกค้า" });
                    Swal.fire({ icon: 'success', title: 'สั่งซื้อสำเร็จ!', text: รหัสคำสั่งซื้อของคุณคือ ${orderId}`, background: '#0f172a', color: '#fff', confirmButtonColor: '#0284c7' });
                }
            });
        }

// Add Product Modal
        function addNewProductModal() {
            Swal.fire({
                title: 'เพิ่มรายการบริการใหม่',
                html: 
                    <input id="pName" class="swal2-input bg-slate-800 text-white text-xs border-slate-700" placeholder="ชื่อบริการ/สินค้า">
                    <input id="pPrice" type="number" class="swal2-input bg-slate-800 text-white text-xs border-slate-700" placeholder="ราคา (เหรียญ Fong)">
                    <textarea id="pDetail" class="swal2-textarea bg-slate-800 text-white text-xs border-slate-700" placeholder="รายละเอียดบริการ"></textarea>
                `,
                showCancelButton: true,
                confirmButtonText: 'บันทึกบริการ',
                confirmButtonColor: '#0284c7',
                background: '#0f172a',
                color: '#fff',
                preConfirm: () => {
                    return {
                        name: document.getElementById('pName').value,
                        price: parseInt(document.getElementById('pPrice').value),
                        detail: document.getElementById('pDetail').value
                    }
                }
            }).then((res) => {
                if (res.value && res.value.name && res.value.price) {
                    products.push({ id: Date.now(), name: res.value.name, price: res.value.price, detail: res.value.detail || '-' });
                    renderProducts();
                    Swal.fire({ icon: 'success', title: 'เพิ่มบริการสำเร็จ!', background: '#0f172a', color: '#fff', confirmButtonColor: '#0284c7' });
                }
            });
        }

function deleteProduct(id) {
            products = products.filter(p => p.id !== id);
            renderProducts();
        }

        
// Add Coins Modal
        function addFongCoinsModal() {
            Swal.fire({
                title: 'เติมเหรียญ Fong (ทดสอบ)',
                input: 'number',
                inputPlaceholder: 'ระบุจำนวนเหรียญ...',
                showCancelButton: true,
                confirmButtonText: 'เติมเหรียญ',
                confirmButtonColor: '#0284c7',
                background: '#0f172a',
                color: '#fff'
            }).then((res) => {
                if (res.isConfirmed && res.value) {
                    fongCoins += parseInt(res.value);
                    document.getElementById('fongBalance').innerText = fongCoins;
                    Swal.fire({ icon: 'success', title: 'เติมเหรียญสำเร็จ!', text: ยอดเหรียญปัจจุบัน: ${fongCoins} Fong`, background: '#0f172a', color: '#fff', confirmButtonColor: '#0284c7' });
                }
            });
        }

// Orders Modal
        function toggleOrdersModal() {
            const modal = document.getElementById('ordersModal');
            modal.classList.toggle('hidden');
            if (!modal.classList.contains('hidden')) {
                const list = document.getElementById('ordersList');
                list.innerHTML = '';
                if (orders.length === 0) {
                    list.innerHTML = <p class="text-center text-slate-500 py-8">ยังไม่มีรายการคำสั่งซื้อในขณะนี้</p>;
                    return;
                }
                orders.forEach((o, index) => {
                    list.innerHTML += 
                        <div class="bg-slate-800/80 p-4 rounded-2xl border border-slate-700 flex justify-between items-center gap-4">
                            <div>
                                <span class="text-cyan-400 font-bold">${o.id}</span>
                                <h4 class="text-white font-semibold text-sm">${o.item}</h4>
                                <p class="text-slate-400 text-[11px]">ราคา: ${o.price} Fong | ผู้ซื้อ: ${o.user}</p>
                            </div>
                            <div class="text-right">
                                <span class="inline-block bg-cyan-500/20 text-cyan-300 border border-cyan-500/40 px-3 py-1 rounded-full font-bold mb-2">${o.status}</span>
                                ${isAdmin ? 
                                    <div>
                                        <button onclick="changeOrderStatus(${index})" class="text-[10px] bg-slate-700 hover:bg-slate-600 text-slate-200 px-2.5 py-1 rounded-lg border border-slate-600">
                                            เปลี่ยนสถานะ
                                        </button>
                                    </div>
                                 : ''}
                            </div>
                        </div>
                    `;
                });
            }
        }

function changeOrderStatus(index) {
            const statuses = ["กำลังฟาร์ม ⏳", "ฟาร์มเสร็จสิ้น ✅", "ยกเลิกคำสั่งซื้อ ❌"];
            Swal.fire({
                title: 'เปลี่ยนสถานะคำสั่งซื้อ',
                input: 'select',
                inputOptions: {
                    "กำลังฟาร์ม ⏳": "กำลังฟาร์ม ⏳",
                    "ฟาร์มเสร็จสิ้น ✅": "ฟาร์มเสร็จสิ้น ✅",
                    "ยกเลิกคำสั่งซื้อ ❌": "ยกเลิกคำสั่งซื้อ ❌"
                },
                showCancelButton: true,
                confirmButtonText: 'บันทึก',
                confirmButtonColor: '#0284c7',
                background: '#0f172a',
                color: '#fff'
            }).then((res) => {
                if (res.isConfirmed && res.value) {
                    orders[index].status = res.value;
                    toggleOrdersModal();
                    toggleOrdersModal();
                }
            });
        }
   // Chat System
        function toggleChatModal() {
            document.getElementById('chatModal').classList.toggle('hidden');
        }

 function sendMessage() {
            const input = document.getElementById('chatInput');
            const msg = input.value.trim();
            if (!msg) return;

const chatMessages = document.getElementById('chatMessages');
            chatMessages.innerHTML += 
                <div class="bg-cyan-600/30 border border-cyan-400/30 p-3 rounded-2xl max-w-[85%] ml-auto text-right">
                    <p class="text-cyan-300 font-bold mb-1">คุณ</p>
                    <p class="text-white">${msg}</p>
                </div>
            `;
            input.value = '';
            chatMessages.scrollTop = chatMessages.scrollHeight;

 setTimeout(() => {
                chatMessages.innerHTML += 
                    <div class="bg-slate-800 p-3 rounded-2xl max-w-[85%] border border-cyan-500/20">
                        <p class="text-cyan-300 font-bold mb-1">🤖 แอดมิน ANIME ZERO</p>
                        <p class="text-slate-200">รับทราบครับ! เจ้าหน้าที่กำลังตรวจสอบข้อความของคุณครับ</p>
                    </div>
                `;
                chatMessages.scrollTop = chatMessages.scrollHeight;
            }, 1000);
        }

// Init App
        renderProducts();
    </script>
</body>
</html>

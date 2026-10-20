<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ANIME ZERO - บริการฟาร์มเกมออนไลน์</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;600;700&display=swap');
        body { font-family: 'Kanit', sans-serif; background-color: #0b132b; color: #e0f7fa; }
        .ice-glow { box-shadow: 0 0 15px rgba(0, 229, 255, 0.4); }
        .ice-border { border: 1px solid rgba(0, 229, 255, 0.3); }
        .bg-ice-card { background: rgba(28, 37, 65, 0.85); backdrop-filter: blur(10px); }
    </style>
</head>
<body class="min-h-screen flex flex-col justify-between">

    <!-- NAVBAR -->
    <nav class="bg-slate-900/90 border-b border-cyan-500/30 sticky top-0 z-50 px-4 py-3 shadow-lg">
        <div class="max-w-6xl mx-auto flex justify-between items-center">
            <div class="flex items-center space-x-3">
                <div class="w-10 h-10 rounded-full bg-cyan-500/20 border border-cyan-400 flex items-center justify-center text-cyan-300 font-bold text-xl ice-glow">
                    ❄️
                </div>
                <span class="text-2xl font-bold tracking-wider text-transparent bg-clip-text bg-gradient-to-r from-cyan-300 to-blue-500">ANIME ZERO</span>
            </div>
            
            <div class="flex items-center space-x-4">
                <div class="bg-slate-800 border border-cyan-500/40 px-3 py-1.5 rounded-full text-sm flex items-center space-x-2">
                    <span class="text-cyan-400 font-semibold">🪙 Fong:</span>
                    <span id="userFong" class="font-bold text-white">0</span>
                </div>
                <!-- ปุ่มสวิตช์แอดมิน / ปุ่มใส่รหัส -->
                <button onclick="openAdminModal()" class="p-2 bg-cyan-500/10 hover:bg-cyan-500/30 border border-cyan-400/50 rounded-lg text-cyan-300 transition" title="เข้าสู่ระบบผู้ดูแล">
                    <i class="fas fa-user-shield"></i>
                </button>
            </div>
        </div>
    </nav>

    <!-- MAIN CONTENT -->
    <main class="max-w-6xl mx-auto p-4 w-full my-6">
        
        <!-- BANNER -->
        <div class="bg-ice-card ice-border rounded-2xl p-6 mb-8 text-center relative overflow-hidden ice-glow">
            <h1 class="text-3xl md:text-4xl font-bold text-cyan-300 mb-2">ยินดีต้อนรับสู่ ANIME ZERO ❄️</h1>
            <p class="text-slate-300 text-sm md:text-base">บริการรับฟาร์มเกมราคาประหยัด ปลอดภัย รวดเร็ว โดยทีมงานมืออาชีพ</p>
        </div>

        <!-- SECTION: PRODUCTS -->
        <div class="flex justify-between items-center mb-6">
            <h2 class="text-xl font-semibold text-cyan-400 flex items-center gap-2">
                <i class="fas fa-gamepad"></i> บริการยอดนิยม
            </h2>
            <span id="adminBadge" class="hidden bg-red-500/20 text-red-400 text-xs px-3 py-1 rounded-full border border-red-500/40 font-bold">
                👑 โหมดผู้ดูแลระบบ (Admin Active)
            </span>
        </div>

        <!-- PRODUCT GRID -->
        <div id="productGrid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
            <!-- สินค้าจะถูกโหลดตรงนี้ -->
        </div>

        <!-- ADMIN CONTROLS (แสดงเฉพาะเมื่อเข้าแอดมิน) -->
        <div id="adminPanel" class="hidden mt-10 p-6 bg-slate-900/90 border border-cyan-400 rounded-2xl ice-glow">
            <h3 class="text-xl font-bold text-cyan-300 mb-4 flex items-center gap-2">
                <i class="fas fa-tools"></i> เมนูผู้ดูแลระบบ (Admin)
            </h3>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <button onclick="addNewProduct()" class="bg-cyan-600 hover:bg-cyan-500 text-white py-3 rounded-xl font-semibold shadow transition">
                    ➕ เพิ่มบริการ/สินค้าใหม่
                </button>
                <button onclick="addFongCoins()" class="bg-blue-600 hover:bg-blue-500 text-white py-3 rounded-xl font-semibold shadow transition">
                    🪙 เติมเหรียญ Fong (จำลอง)
                </button>
            </div>
        </div>
    </main>

    <!-- FOOTER -->
    <footer class="bg-slate-900 border-t border-slate-800 text-center py-4 text-xs text-slate-400">
        © 2026 ANIME ZERO Shop. All Rights Reserved.
    </footer>

    <!-- JAVASCRIPT LOGIC -->
    <script>
        // รหัสแอดมินตั้งต้น
        const ADMIN_CODE = "ฟง888.";
        let isAdmin = false;
        let userFongBalance = 100;

        // สินค้าเริ่มต้น
        let products = [
            { id: 1, name: "ฟาร์มเวล Roblox Blox Fruits", price: 50, detail: "ฟาร์มเวล 1-Max สดๆ ไม่ใช้โปร" },
            { id: 2, name: "เหมาดันเจี้ยน/หาของ", price: 80, detail: "การันตีไอเทมตามสั่ง" }
        ];

        document.getElementById('userFong').innerText = userFongBalance;

        function renderProducts() {
            const grid = document.getElementById('productGrid');
            grid.innerHTML = '';

            products.forEach(p => {
                grid.innerHTML += `
                    <div class="bg-ice-card ice-border rounded-xl p-5 hover:scale-[1.02] transition flex flex-col justify-between">
                        <div>
                            <div class="w-full h-32 bg-slate-800 rounded-lg flex items-center justify-center text-4xl mb-4 border border-cyan-500/20">
                                ❄️
                            </div>
                            <h3 class="font-bold text-lg text-white mb-1">${p.name}</h3>
                            <p class="text-xs text-slate-300 mb-4">${p.detail}</p>
                        </div>
                        <div class="flex justify-between items-center pt-3 border-t border-slate-700/50">
                            <span class="text-cyan-300 font-bold text-lg">${p.price} <small class="text-xs">Fong</small></span>
                            <button onclick="buyProduct('${p.name}', ${p.price})" class="bg-cyan-500 hover:bg-cyan-400 text-slate-950 font-bold px-4 py-2 rounded-lg text-sm shadow transition">
                                สั่งซื้อ
                            </button>
                        </div>
                    </div>
                `;
            });
        }

        // เปิดป็อปอัพใส่รหัสแอดมิน
        function openAdminModal() {
            if (isAdmin) {
                Swal.fire({
                    icon: 'info',
                    title: 'โหมดผู้ดูแลระบบ',
                    text: 'คุณเข้าสู่ระบบแอดมินอยู่นานแล้ว!',
                    confirmButtonColor: '#06b6d4'
                });
                return;
            }

            Swal.fire({
                title: '🔑 ยืนยันสิทธิ์แอดมิน',
                input: 'password',
                inputPlaceholder: 'กรอกรหัสเชิญแอดมิน...',
                showCancelButton: true,
                confirmButtonText: 'เข้าสู่ระบบ',
                cancelButtonText: 'ยกเลิก',
                confirmButtonColor: '#06b6d4',
                customClass: { popup: 'bg-slate-900 text-white' }
            }).then((result) => {
                if (result.isConfirmed) {
                    if (result.value === ADMIN_CODE) {
                        isAdmin = true;
                        document.getElementById('adminPanel').classList.remove('hidden');
                        document.getElementById('adminBadge').classList.remove('hidden');
                        Swal.fire({
                            icon: 'success',
                            title: 'สำเร็จ!',
                            text: 'เข้าสู่ระบบแอดมินเรียบร้อยแล้ว!',
                            timer: 1500,
                            showConfirmButton: false
                        });
                    } else {
                        Swal.fire({
                            icon: 'error',
                            title: 'รหัสไม่ถูกต้อง!',
                            text: 'รหัสเชิญแอดมินไม่ถูกต้อง กรุณาลองใหม่',
                            confirmButtonColor: '#ef4444'
                        });
                    }
                }
            });
        }

        function buyProduct(name, price) {
            if (userFongBalance < price) {
                Swal.fire('เหรียญไม่พอ!', 'คุณมีเหรียญ Fong ไม่พอสำหรับการสั่งซื้อนี้', 'warning');
                return;
            }
            userFongBalance -= price;
            document.getElementById('userFong').innerText = userFongBalance;
            Swal.fire('สั่งซื้อสำเร็จ!', `คุณได้ทำการสั่งซื้อ ${name} เรียบร้อยแล้ว`, 'success');
        }

        function addNewProduct() {
            Swal.fire({
                title: 'เพิ่มสินค้าใหม่',
                html: '<input id="swal-input1" class="swal2-input" placeholder="ชื่อสินค้า">' +
                      '<input id="swal-input2" class="swal2-input" placeholder="ราคา (Fong)" type="number">' +
                      '<input id="swal-input3" class="swal2-input" placeholder="รายละเอียด">',
                focusConfirm: false,
                preConfirm: () => {
                    return [
                        document.getElementById('swal-input1').value,
                        document.getElementById('swal-input2').value,
                        document.getElementById('swal-input3').value
                    ]
                }
            }).then((res) => {
                if (res.value && res.value[0] && res.value[1]) {
                    products.push({
                        id: products.length + 1,
                        name: res.value[0],
                        price: parseInt(res.value[1]),
                        detail: res.value[2] || '-'
                    });
                    renderProducts();
                    Swal.fire('สำเร็จ', 'เพิ่มสินค้าเรียบร้อยแล้ว!', 'success');
                }
            });
        }

        function addFongCoins() {
            userFongBalance += 500;
            document.getElementById('userFong').innerText = userFongBalance;
            Swal.fire('เพิ่มเหรียญสำเร็จ!', 'เพิ่ม 500 Fong เรียบร้อย', 'success');
        }

        renderProducts();
    </script>
</body>
</html>

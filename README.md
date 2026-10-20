<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ANIME ZERO - ร้านรับฟาร์มเกมออนไลน์</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;600;700&display=swap');
        body { font-family: 'Kanit', sans-serif; background-color: #050b14; color: #e0f7fa; }
        .ice-glow { box-shadow: 0 0 20px rgba(0, 229, 255, 0.4); }
        .ice-card { background: rgba(15, 23, 42, 0.9); border: 1px solid rgba(0, 229, 255, 0.3); }
    </style>
</head>
<body class="min-h-screen flex flex-col justify-between">

    <!-- NAVBAR -->
    <nav class="bg-slate-900 border-b border-cyan-500/30 px-4 py-3 sticky top-0 z-50 flex justify-between items-center shadow-lg">
        <div class="flex items-center space-x-3">
            <div class="w-10 h-10 rounded-full bg-cyan-500/20 border border-cyan-400 flex items-center justify-center text-cyan-300 font-bold text-xl ice-glow">❄️</div>
            <span class="text-xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-cyan-300 to-blue-400">ANIME ZERO</span>
        </div>
        <div class="flex items-center space-x-3">
            <div class="bg-slate-800 border border-cyan-500/40 px-3 py-1 rounded-full text-xs flex items-center space-x-2">
                <span class="text-cyan-400">🪙 Fong:</span>
                <span id="fongDisplay" class="font-bold text-white">100</span>
            </div>
            <!-- ปุ่มแอดมิน -->
            <button onclick="openAdmin()" class="bg-cyan-500/20 hover:bg-cyan-500/40 border border-cyan-400 text-cyan-300 px-3 py-1.5 rounded-xl text-xs font-bold transition ice-glow">
                <i class="fas fa-shield-alt"></i> แอดมิน
            </button>
        </div>
    </nav>

    <!-- HEADER / BANNER -->
    <header class="max-w-4xl mx-auto px-4 mt-6 w-full">
        <div class="ice-card rounded-3xl p-6 md:p-8 text-center relative overflow-hidden ice-glow">
            <div class="w-32 h-32 mx-auto rounded-full border-2 border-cyan-400 overflow-hidden mb-4 ice-glow">
                <img src="https://images2.imgbox.com/f0/73/pWcE8q48_o.jpg" alt="Mascot" class="w-full h-full object-cover">
            </div>
            <h1 class="text-2xl md:text-3xl font-extrabold text-cyan-300 mb-2">ANIME ZERO SHOP ❄️</h1>
            <p class="text-slate-300 text-xs md:text-sm mb-4">บริการฟาร์มเกมอนิเมะปลอดภัย รวดเร็ว ตลอด 24 ชั่วโมง</p>
            <button onclick="openOrders()" class="bg-gradient-to-r from-cyan-500 to-blue-600 text-slate-950 font-bold px-5 py-2 rounded-xl text-xs shadow transition">
                <i class="fas fa-receipt"></i> ดูสถานะคำสั่งซื้อ
            </button>
        </div>
    </header>

    <!-- PRODUCTS -->
    <main class="max-w-4xl mx-auto px-4 py-6 w-full flex-1">
        <h2 class="text-lg font-bold text-cyan-300 mb-4 flex items-center gap-2">
            <i class="fas fa-gamepad"></i> รายการบริการฟาร์ม
        </h2>
        <div id="productList" class="grid grid-cols-1 sm:grid-cols-2 gap-4">
            <!-- โหลดด้วย JS -->
        </div>

        <!-- ADMIN PANEL -->
        <div id="adminPanel" class="hidden mt-8 ice-card p-5 rounded-2xl border-cyan-400">
            <h3 class="text-cyan-300 font-bold text-sm mb-3 flex items-center gap-2">
                <i class="fas fa-tools"></i> แผงควบคุมผู้ดูแลระบบ (Admin Panel)
            </h3>
            <div class="flex flex-wrap gap-3">
                <button onclick="addCoin()" class="bg-blue-600 hover:bg-blue-500 text-white px-4 py-2 rounded-xl text-xs font-bold">
                    🪙 เติมเหรียญ Fong (+500)
                </button>
                <button onclick="alert('ระบบหลังบ้านพร้อมใช้งาน!')" class="bg-cyan-600 hover:bg-cyan-500 text-white px-4 py-2 rounded-xl text-xs font-bold">
                    ➕ จัดการสินค้า
                </button>
            </div>
        </div>
    </main>

    <!-- FOOTER -->
    <footer class="bg-slate-900 border-t border-slate-800 text-center py-4 text-[11px] text-slate-400">
        © 2026 ANIME ZERO | รหัสแอดมิน: <span class="text-cyan-400">ฟง888.</span>
    </footer>

    <!-- SCRIPT -->
    <script>
        const ADMIN_CODE = "ฟง888.";
        let fong = 100;
        let products = [
            { name: "ฟาร์มเลเวล Roblox Blox Fruits", price: 50, desc: "ฟาร์มไว ปลอดภัย การันตีผลงาน" },
            { name: "เหมาดันเจี้ยนหาไอเทม", price: 80, desc: "เก็บของครบตามจำนวนที่ต้องการ" }
        ];

        function render() {
            const list = document.getElementById('productList');
            list.innerHTML = '';
            products.forEach(p => {
                list.innerHTML += `
                    <div class="ice-card p-4 rounded-2xl flex flex-col justify-between">
                        <div>
                            <h3 class="font-bold text-white text-sm mb-1">${p.name}</h3>
                            <p class="text-slate-300 text-xs mb-3">${p.desc}</p>
                        </div>
                        <div class="flex justify-between items-center pt-3 border-t border-slate-800">
                            <span class="text-cyan-300 font-bold text-sm">${p.price} Fong</span>
                            <button onclick="buy('${p.name}', ${p.price})" class="bg-cyan-400 hover:bg-cyan-300 text-slate-950 font-bold px-3 py-1.5 rounded-xl text-xs">สั่งซื้อ</button>
                        </div>
                    </div>
                `;
            });
            document.getElementById('fongDisplay').innerText = fong;
        }

        function openAdmin() {
            Swal.fire({
                title: '🔑 ยืนยันสิทธิ์แอดมิน',
                input: 'password',
                inputPlaceholder: 'กรอกรหัสเชิญ...',
                showCancelButton: true,
                confirmButtonText: 'เข้าสู่ระบบ',
                confirmButtonColor: '#0284c7',
                background: '#0f172a',
                color: '#fff'
            }).then(res => {
                if(res.isConfirmed) {
                    if(res.value === ADMIN_CODE) {
                        document.getElementById('adminPanel').classList.remove('hidden');
                        Swal.fire({icon: 'success', title: 'เข้าสู่ระบบแอดมินสำเร็จ!', background: '#0f172a', color: '#fff', timer: 1200, showConfirmButton: false});
                    } else {
                        Swal.fire({icon: 'error', title: 'รหัสไม่ถูกต้อง!', background: '#0f172a', color: '#fff'});
                    }
                }
            });
        }

        function buy(name, price) {
            if(fong < price) {
                Swal.fire({icon: 'warning', title: 'เหรียญ Fong ไม่พอ!', background: '#0f172a', color: '#fff'});
                return;
            }
            fong -= price;
            render();
            Swal.fire({icon: 'success', title: 'สั่งซื้อสำเร็จ!', text: `คุณได้ซื้อ ${name} เรียบร้อย`, background: '#0f172a', color: '#fff'});
        }

        function addCoin() {
            fong += 500;
            render();
            Swal.fire({icon: 'success', title: 'เติมเหรียญสำเร็จ +500 Fong', background: '#0f172a', color: '#fff'});
        }

        function openOrders() {
            Swal.fire({title: '📦 รายการคำสั่งซื้อ', text: 'ยังไม่มีคำสั่งซื้อในขณะนี้', background: '#0f172a', color: '#fff', confirmButtonColor: '#0284c7'});
        }

        render();
    </script>
</body>
</html>

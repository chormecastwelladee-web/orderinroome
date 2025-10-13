<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ร้านอาหารเช้า & อาราคัต</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        body {
            box-sizing: border-box;
        }
        @import url('https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;500;600;700&display=swap');
        
        * {
            font-family: 'Kanit', sans-serif;
        }
        
        .gradient-bg {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }
        
        .card-hover {
            transition: all 0.3s ease;
        }
        
        .card-hover:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1);
        }
        
        .menu-item {
            transition: all 0.2s ease;
        }
        
        .menu-item:hover {
            background-color: #f3f4f6;
        }
        
        .active-tab {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
        }
        
        .fade-in {
            animation: fadeIn 0.5s ease-in;
        }
        #aracateSlides {
    position: relative;
    width: 100%;
}

#main-slide {
    width: 100%;
    height: 100%;
    object-fit: cover; /* ให้เต็ม container */
}

.grid img {
    height: 70px; /* Thumbnail ย่อเล็ก */
    object-fit: cover;
}




        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body class="bg-gray-50">
    <!-- Header -->
    <header class="gradient-bg text-white py-6 shadow-lg">
        <div class="container mx-auto px-4">
            <h1 class="text-4xl font-bold text-center">🍳 ร้านอาหารเช้า & อาราคัต 🥘</h1>
            <p class="text-center mt-2 text-lg opacity-90">อาหารเช้า 7:00-10:00 น. | อาราคัต ตลอดวัน | Room Service 9:00-18:00 น.</p>
        </div>
    </header>

    <!-- Navigation -->
    <nav class="bg-white shadow-md sticky top-0 z-50">
        <div class="container mx-auto px-4">
            <div class="flex justify-center space-x-8 py-4">
                <button onclick="showSection('breakfast')" id="breakfast-tab" class="px-6 py-3 rounded-full font-semibold transition-all active-tab">
                    🌅 อาหารเช้า
                </button>
                <button onclick="showSection('alacarte')" id="alacarte-tab" class="px-6 py-3 rounded-full font-semibold transition-all bg-gray-200 text-gray-700 hover:bg-gray-300">
                    🍽️ อาราคัต
                </button>
            </div>
        </div>
    </nav>

    <!-- Main Content -->
    <main class="container mx-auto px-4 py-8">
        <!-- Breakfast Section -->
        <div id="breakfast-section" class="fade-in">
            <div class="text-center mb-8">
                <h2 class="text-3xl font-bold text-gray-800 mb-4">🌅 เมนูอาหารเช้า</h2>
                <div id="breakfast-time-notice" class="bg-yellow-100 border-l-4 border-yellow-500 p-4 rounded-r-lg inline-block">
                    <p class="text-yellow-700 font-medium">⏰ สั่งได้ตั้งแต่ 7:00-10:00 น. (หลัง 10:00 น. จะเป็นออเดอร์วันพรุ่งนี้)</p>
                </div>
            </div>

            <div class="grid lg:grid-cols-2 gap-8">
                <!-- Breakfast Menu Images -->
                <div class="space-y-6">
                    <div class="bg-white rounded-xl shadow-lg p-6 card-hover">
                        <h3 class="text-xl font-bold text-gray-800 mb-4 border-b pb-2">📋 หมวดที่ 1: อาหารเช้า</h3>
                        <div class="grid grid-cols-1 gap-4">
                            <div class="flex items-center justify-between p-3 border rounded-lg menu-item cursor-pointer" onclick="addToBreakfastOrder('ข้าวต้มหมู', 45)">
                                <div class="flex items-center space-x-3">
                                    <div class="w-12 h-12 bg-orange-100 rounded-lg flex items-center justify-center">🍚</div>
                                    <span class="font-medium">ข้าวต้มหมู</span>
                                </div>
                                <span class="text-purple-600 font-bold">45 บาท</span>
                            </div>
                            <div class="flex items-center justify-between p-3 border rounded-lg menu-item cursor-pointer" onclick="addToBreakfastOrder('โจ๊กหมู', 40)">
                                <div class="flex items-center space-x-3">
                                    <div class="w-12 h-12 bg-orange-100 rounded-lg flex items-center justify-center">🥣</div>
                                    <span class="font-medium">โจ๊กหมู</span>
                                </div>
                                <span class="text-purple-600 font-bold">40 บาท</span>
                            </div>
                            <div class="flex items-center justify-between p-3 border rounded-lg menu-item cursor-pointer" onclick="addToBreakfastOrder('ข้าวผัดอเมริกัน', 55)">
                                <div class="flex items-center space-x-3">
                                    <div class="w-12 h-12 bg-orange-100 rounded-lg flex items-center justify-center">🍳</div>
                                    <span class="font-medium">ข้าวผัดอเมริกัน</span>
                                </div>
                                <span class="text-purple-600 font-bold">55 บาท</span>
                            </div>
                            <div class="flex items-center justify-between p-3 border rounded-lg menu-item cursor-pointer" onclick="addToBreakfastOrder('ขนมปังปิ้งเนยนม', 35)">
                                <div class="flex items-center space-x-3">
                                    <div class="w-12 h-12 bg-orange-100 rounded-lg flex items-center justify-center">🍞</div>
                                    <span class="font-medium">ขนมปังปิ้งเนยนม</span>
                                </div>
                                <span class="text-purple-600 font-bold">35 บาท</span>
                            </div>
                            <div class="flex items-center justify-between p-3 border rounded-lg menu-item cursor-pointer" onclick="addToBreakfastOrder('ไข่เจียวข้าว', 30)">
                                <div class="flex items-center space-x-3">
                                    <div class="w-12 h-12 bg-orange-100 rounded-lg flex items-center justify-center">🥚</div>
                                    <span class="font-medium">ไข่เจียวข้าว</span>
                                </div>
                                <span class="text-purple-600 font-bold">30 บาท</span>
                            </div>
                        </div>
                    </div>

                    <div class="bg-white rounded-xl shadow-lg p-6 card-hover">
                        <h3 class="text-xl font-bold text-gray-800 mb-4 border-b pb-2">🥤 หมวดที่ 2: เครื่องดื่ม</h3>
                        <div class="grid grid-cols-1 gap-4">
                            <div class="flex items-center justify-between p-3 border rounded-lg menu-item cursor-pointer" onclick="addToBreakfastOrder('กาแฟร้อน', 25)">
                                <div class="flex items-center space-x-3">
                                    <div class="w-12 h-12 bg-blue-100 rounded-lg flex items-center justify-center">☕</div>
                                    <span class="font-medium">กาแฟร้อน</span>
                                </div>
                                <span class="text-purple-600 font-bold">25 บาท</span>
                            </div>
                            <div class="flex items-center justify-between p-3 border rounded-lg menu-item cursor-pointer" onclick="addToBreakfastOrder('ชาเย็น', 20)">
                                <div class="flex items-center space-x-3">
                                    <div class="w-12 h-12 bg-blue-100 rounded-lg flex items-center justify-center">🧊</div>
                                    <span class="font-medium">ชาเย็น</span>
                                </div>
                                <span class="text-purple-600 font-bold">20 บาท</span>
                            </div>
                            <div class="flex items-center justify-between p-3 border rounded-lg menu-item cursor-pointer" onclick="addToBreakfastOrder('น้ำส้มคั้น', 30)">
                                <div class="flex items-center space-x-3">
                                    <div class="w-12 h-12 bg-blue-100 rounded-lg flex items-center justify-center">🍊</div>
                                    <span class="font-medium">น้ำส้มคั้น</span>
                                </div>
                                <span class="text-purple-600 font-bold">30 บาท</span>
                            </div>
                        </div>
                    </div>

                    <div class="bg-white rounded-xl shadow-lg p-6 card-hover">
                        <h3 class="text-xl font-bold text-gray-800 mb-4 border-b pb-2">🍎 หมวดที่ 3: ผลไม้</h3>
                        <div class="grid grid-cols-1 gap-4">
                            <div class="flex items-center justify-between p-3 border rounded-lg menu-item cursor-pointer" onclick="addToBreakfastOrder('สับปะรดหั่น', 25)">
                                <div class="flex items-center space-x-3">
                                    <div class="w-12 h-12 bg-green-100 rounded-lg flex items-center justify-center">🍍</div>
                                    <span class="font-medium">สับปะรดหั่น</span>
                                </div>
                                <span class="text-purple-600 font-bold">25 บาท</span>
                            </div>
                            <div class="flex items-center justify-between p-3 border rounded-lg menu-item cursor-pointer" onclick="addToBreakfastOrder('แตงโมหั่น', 20)">
                                <div class="flex items-center space-x-3">
                                    <div class="w-12 h-12 bg-green-100 rounded-lg flex items-center justify-center">🍉</div>
                                    <span class="font-medium">แตงโมหั่น</span>
                                </div>
                                <span class="text-purple-600 font-bold">20 บาท</span>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Breakfast Order Form -->
                <div class="bg-white rounded-xl shadow-lg p-6 sticky top-24">
                    <h3 class="text-xl font-bold text-gray-800 mb-4 border-b pb-2">🛒 รายการสั่งอาหารเช้า</h3>
                    <div id="breakfast-cart" class="space-y-2 mb-4 min-h-[100px]">
                        <p class="text-gray-500 text-center py-8">ยังไม่มีรายการอาหาร</p>
                    </div>
                    <div class="border-t pt-4">
                        <div class="flex justify-between items-center mb-4">
                            <span class="font-bold text-lg">รวมทั้งหมด:</span>
                            <span id="breakfast-total" class="font-bold text-xl text-purple-600">0 บาท</span>
                        </div>
                        <form id="breakfast-order-form" class="space-y-4">
                            <div>
                                <label class="block text-sm font-medium text-gray-700 mb-1">เลขห้อง *</label>
                                <input type="text" id="breakfast-room" required class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-purple-500 focus:border-transparent">
                            </div>
                            <div>
                                <label class="block text-sm font-medium text-gray-700 mb-1">วิธีการรับอาหาร *</label>
                                <select id="breakfast-delivery" required class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-purple-500 focus:border-transparent">
                                    <option value="">เลือกวิธีการรับ</option>
                                    <option value="ทานที่ร้าน">ทานที่ร้าน</option>
                                    <option value="Room Service">Room Service</option>
                                </select>
                            </div>
                            <div>
                                <label class="block text-sm font-medium text-gray-700 mb-1">หมายเหตุ</label>
                                <textarea id="breakfast-note" rows="3" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-purple-500 focus:border-transparent" placeholder="ระบุความต้องการพิเศษ..."></textarea>
                            </div>
                            <button type="submit" class="w-full gradient-bg text-white py-3 rounded-lg font-semibold hover:opacity-90 transition-opacity">
                                📤 ส่งออเดอร์อาหารเช้า
                            </button>
                        </form>
                    </div>
                </div>
            </div>
        </div>

        <!-- A la carte Section -->
<!-- A la carte Section -->
<div id="alacarte-section" class="hidden">
    <div class="text-center mb-8">
        <h2 class="text-3xl font-bold text-gray-800 mb-4">🍽️ เมนูอาราคัต</h2>
        <p class="text-gray-600">เปิดบริการตลอดวัน | Room Service 9:00-18:00 น.</p>
    </div>

    <div class="grid lg:grid-cols-2 gap-8">
        <!-- ฝั่งซ้าย: เลือกหมวด + แสดงเมนู -->
        <div class="space-y-6">
            <!-- Category Selection -->
            <div class="bg-white rounded-xl shadow-lg p-6 card-hover">
                <h3 class="text-xl font-bold text-gray-800 mb-4 border-b pb-2">📂 เลือกหมวดอาหาร</h3>
                <div class="grid grid-cols-2 gap-3">
                    <button onclick="showAlacarteCategory('Toast')" class="alacarte-category-btn p-4 border-2 border-gray-200 rounded-lg hover:border-purple-500 hover:bg-purple-50 transition-all text-center">
                        <div class="text-2xl mb-2"></div>
                        <div class="font-medium">Toast</div>
                    </button>
                    <button onclick="showAlacarteCategory('Com forting food')" class="alacarte-category-btn p-4 border-2 border-gray-200 rounded-lg hover:border-purple-500 hover:bg-purple-50 transition-all text-center">
                        <div class="text-2xl mb-2"></div>
                        <div class="font-medium">Com forting food</div>
                    </button>
                    <button onclick="showAlacarteCategory('Sarad')" class="alacarte-category-btn p-4 border-2 border-gray-200 rounded-lg hover:border-purple-500 hover:bg-purple-50 transition-all text-center">
                        <div class="text-2xl mb-2"></div>
                        <div class="font-medium">Sarad</div>
                    </button>
                    <button onclick="showAlacarteCategory('Pasta')" class="alacarte-category-btn p-4 border-2 border-gray-200 rounded-lg hover:border-purple-500 hover:bg-purple-50 transition-all text-center">
                        <div class="text-2xl mb-2"></div>
                        <div class="font-medium">Pasta</div>
                    </button>
                    <button onclick="showAlacarteCategory('Appetizer')" class="alacarte-category-btn p-4 border-2 border-gray-200 rounded-lg hover:border-purple-500 hover:bg-purple-50 transition-all text-center">
                        <div class="text-2xl mb-2"></div>
                        <div class="font-medium">Appetizer</div>
                    </button>
                    <button onclick="showAlacarteCategory('Pancake')" class="alacarte-category-btn p-4 border-2 border-gray-200 rounded-lg hover:border-purple-500 hover:bg-purple-50 transition-all text-center">
                        <div class="text-2xl mb-2"></div>
                        <div class="font-medium">Pancake</div>
                    </button>
                </div>
            </div>

            <!-- Menu Items Display -->
            <div id="alacarte-menu-display" class="bg-white rounded-xl shadow-lg p-6 card-hover hidden">
                <h3 id="alacarte-category-title" class="text-xl font-bold text-gray-800 mb-4 border-b pb-2"></h3>
                <div id="alacarte-menu-items" class="space-y-3"></div>
            </div>
        </div>

        <!-- ฝั่งขวา: Slide รูปภาพ -->
        <div class="bg-white rounded-xl shadow-lg p-4 flex flex-col h-full">
    <h3 class="text-xl font-bold text-gray-800 mb-4 border-b pb-2 text-center">🖼️ ตัวอย่างเมนูอาราคัต</h3>
    
    <!-- Main Image -->
    <div class="flex-1 mb-2">
        <img id="main-slide" src="Screenshot 2025-10-11 162604.png" class="w-full h-full object-cover rounded-lg">
    </div>

    <!-- Thumbnails -->
    <div class="grid grid-cols-4 gap-2">
        <img src="appetizer.png" class="rounded-lg cursor-pointer hover:scale-105 transition-transform" onclick="showSlide(0)">
        <img src="comfortingfood.png" class="rounded-lg cursor-pointer hover:scale-105 transition-transform" onclick="showSlide(1)">
        <img src="comfortingfood1.png" class="rounded-lg cursor-pointer hover:scale-105 transition-transform" onclick="showSlide(2)">
        <img src="pancake.png" class="rounded-lg cursor-pointer hover:scale-105 transition-transform" onclick="showSlide(3)">
        <img src="pasta.png" class="rounded-lg cursor-pointer hover:scale-105 transition-transform" onclick="showSlide(4)">
        <img src="sarad.png" class="rounded-lg cursor-pointer hover:scale-105 transition-transform" onclick="showSlide(7)">
        <img src="toast.png" class="rounded-lg cursor-pointer hover:scale-105 transition-transform" onclick="showSlide(5)">
        <img src="toast1.png" class="rounded-lg cursor-pointer hover:scale-105 transition-transform" onclick="showSlide(6)">

        
    </div>
</div>

    </div>
</div>


                <!-- A la carte Order Form -->
                <div class="bg-white rounded-xl shadow-lg p-6 sticky top-24">
                    <h3 class="text-xl font-bold text-gray-800 mb-4 border-b pb-2">🛒 รายการสั่งอาราคัต</h3>
                    <div id="alacarte-cart" class="space-y-2 mb-4 min-h-[100px]">
                        <p class="text-gray-500 text-center py-8">ยังไม่มีรายการอาหาร</p>
                    </div>
                    <div class="border-t pt-4">
                        <div class="flex justify-between items-center mb-4">
                            <span class="font-bold text-lg">รวมทั้งหมด:</span>
                            <span id="alacarte-total" class="font-bold text-xl text-purple-600">0 บาท</span>
                        </div>
                        <form id="alacarte-order-form" class="space-y-4">
                            <div>
                                <label class="block text-sm font-medium text-gray-700 mb-1">เลขห้อง *</label>
                                <input type="text" id="alacarte-room" required class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-purple-500 focus:border-transparent">
                            </div>
                            <div>
                                <label class="block text-sm font-medium text-gray-700 mb-1">วิธีการรับอาหาร *</label>
                                <select id="alacarte-delivery" required class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-purple-500 focus:border-transparent">
                                    <option value="">เลือกวิธีการรับ</option>
                                    <option value="ทานที่ร้าน">ทานที่ร้าน</option>
                                    <option value="Room Service">Room Service</option>
                                </select>
                            </div>
                            <div>
                                <label class="block text-sm font-medium text-gray-700 mb-1">หมายเหตุ</label>
                                <textarea id="alacarte-note" rows="3" class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-purple-500 focus:border-transparent" placeholder="ระบุความต้องการพิเศษ..."></textarea>
                            </div>
                            <button type="submit" class="w-full gradient-bg text-white py-3 rounded-lg font-semibold hover:opacity-90 transition-opacity">
                                📤 ส่งออเดอร์อาราคัต
                            </button>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </main>

    <!-- Success Modal -->
    <div id="success-modal" class="fixed inset-0 bg-black bg-opacity-50 hidden items-center justify-center z-50">
        <div class="bg-white rounded-xl p-8 max-w-md mx-4 text-center">
            <div class="text-6xl mb-4">✅</div>
            <h3 class="text-2xl font-bold text-gray-800 mb-2">ส่งออเดอร์สำเร็จ!</h3>
            <p class="text-gray-600 mb-6">ออเดอร์ของคุณได้ถูกส่งไปยังครัวแล้ว</p>
            <button onclick="closeSuccessModal()" class="gradient-bg text-white px-6 py-3 rounded-lg font-semibold hover:opacity-90 transition-opacity">
                ตกลง
            </button>
        </div>
    </div>

    <script>
        // Menu data
        const alacarteMenus = {
            'Toast': [
                { name: 'chikensatay on toast ', price: 160 },
                { name: 'chimpcocktail on taost', price: 200 },
                { name: 'ABF on toast (AmericanBreakfast)', price: 130 },
                { name: 'Grillied chiken and Guavamale on toast', price: 140 },
                { name: 'wellada toast', price: 120 },
                { name: 'Avocado and scrambled   egg on tast ', price: 160 },
                { name: 'popeye on toast ', price: 120 },
                { name: 'F.A.T on toast', price: 120 }
            ],
            'Comfortingfood': [
                { name: 'ต้มยำกุ้ง', price: 150 },
                { name: 'แกงเขียวหวานไก่', price: 120 },
                { name: 'ต้มข่าไก่', price: 130 },
                { name: 'แกงส้มปลา', price: 110 },
                { name: 'ต้มจืดเต้าหู้', price: 80 }
            ],
            'Sarad': [
                { name: 'Grilled zucchini with tomatoes ', price: 170 },
                { name: 'ไส้กรอกอีสาน', price: 80 },
                { name: 'ขนมจีบ', price: 90 },
                { name: 'เกี้ยวทอด', price: 85 },
                { name: 'ทอดมัน', price: 75 }
            ],
            'Pasta': [
                { name: 'ยำวุ้นเส้น', price: 95 },
                { name: 'ยำมะม่วง', price: 85 },
                { name: 'ยำถั่วพู', price: 90 },
                { name: 'ยำปลาดุกฟู', price: 120 },
                { name: 'ยำส้มโอ', price: 100 }
            ],
            'Appetizer': [
                { name: 'ผัดไทย', price: 80 },
                { name: 'ผัดซีอิ๊ว', price: 75 },
                { name: 'ผัดกะเพรา', price: 70 },
                { name: 'ผัดผักบุ้ง', price: 65 },
                { name: 'ผัดพริกแกง', price: 85 }
            ],
            'Pancake': [
                { name: 'ลาบหมู', price: 90 },
                { name: 'ลาบไก่', price: 85 },
                { name: 'ลาบปลา', price: 95 },
                { name: 'ลาบเป็ด', price: 110 },
                { name: 'ลาบเนื้อ', price: 120 }
            ]
        };

        // Cart data
        let breakfastCart = [];
        let alacarteCart = [];

        // Show section
        function showSection(section) {
            const breakfastSection = document.getElementById('breakfast-section');
            const alacarteSection = document.getElementById('alacarte-section');
            const breakfastTab = document.getElementById('breakfast-tab');
            const alacarteTab = document.getElementById('alacarte-tab');

            if (section === 'breakfast') {
                breakfastSection.classList.remove('hidden');
                alacarteSection.classList.add('hidden');
                breakfastTab.classList.add('active-tab');
                breakfastTab.classList.remove('bg-gray-200', 'text-gray-700');
                alacarteTab.classList.remove('active-tab');
                alacarteTab.classList.add('bg-gray-200', 'text-gray-700');
            } else {
                breakfastSection.classList.add('hidden');
                alacarteSection.classList.remove('hidden');
                alacarteTab.classList.add('active-tab');
                alacarteTab.classList.remove('bg-gray-200', 'text-gray-700');
                breakfastTab.classList.remove('active-tab');
                breakfastTab.classList.add('bg-gray-200', 'text-gray-700');
            }
        }


let slideIndex = 0;
const slides = document.querySelectorAll('#aracateSlides .slide-image');

function showSlide(index) {
    slides.forEach((img, i) => img.classList.remove('active'));
    slideIndex = (index + slides.length) % slides.length;
    slides[slideIndex].classList.add('active');
}

// ปุ่มเลื่อน
function prevSlide() { showSlide(slideIndex - 1); }
function nextSlide() { showSlide(slideIndex + 1); }

// เริ่มต้น
showSlide(slideIndex);

// เลื่อนอัตโนมัติทุก 5 วินาที




        

        // Add to breakfast cart
        function addToBreakfastOrder(name, price) {
            const existingItem = breakfastCart.find(item => item.name === name);
            if (existingItem) {
                existingItem.quantity += 1;
            } else {
                breakfastCart.push({ name, price, quantity: 1 });
            }
            updateBreakfastCart();
        }

        // Update breakfast cart display
        function updateBreakfastCart() {
            const cartElement = document.getElementById('breakfast-cart');
            const totalElement = document.getElementById('breakfast-total');

            if (breakfastCart.length === 0) {
                cartElement.innerHTML = '<p class="text-gray-500 text-center py-8">ยังไม่มีรายการอาหาร</p>';
                totalElement.textContent = '0 บาท';
                return;
            }

            let total = 0;
            let cartHTML = '';

            breakfastCart.forEach((item, index) => {
                const itemTotal = item.price * item.quantity;
                total += itemTotal;
                cartHTML += `
                    <div class="flex items-center justify-between p-3 bg-gray-50 rounded-lg">
                        <div class="flex-1">
                            <div class="font-medium">${item.name}</div>
                            <div class="text-sm text-gray-600">${item.price} บาท x ${item.quantity}</div>
                        </div>
                        <div class="flex items-center space-x-2">
                            <button onclick="changeBreakfastQuantity(${index}, -1)" class="w-8 h-8 bg-red-500 text-white rounded-full flex items-center justify-center hover:bg-red-600">-</button>
                            <span class="w-8 text-center">${item.quantity}</span>
                            <button onclick="changeBreakfastQuantity(${index}, 1)" class="w-8 h-8 bg-green-500 text-white rounded-full flex items-center justify-center hover:bg-green-600">+</button>
                        </div>
                        <div class="ml-4 font-bold text-purple-600">${itemTotal} บาท</div>
                    </div>
                `;
            });

            cartElement.innerHTML = cartHTML;
            totalElement.textContent = `${total} บาท`;
        }

        // Change breakfast quantity
        function changeBreakfastQuantity(index, change) {
            breakfastCart[index].quantity += change;
            if (breakfastCart[index].quantity <= 0) {
                breakfastCart.splice(index, 1);
            }
            updateBreakfastCart();
        }

        // Show alacarte category
        function showAlacarteCategory(category) {
            const menuDisplay = document.getElementById('alacarte-menu-display');
            const categoryTitle = document.getElementById('alacarte-category-title');
            const menuItems = document.getElementById('alacarte-menu-items');

            // Update active category button
            document.querySelectorAll('.alacarte-category-btn').forEach(btn => {
                btn.classList.remove('border-purple-500', 'bg-purple-50');
                btn.classList.add('border-gray-200');
            });
            event.target.closest('.alacarte-category-btn').classList.add('border-purple-500', 'bg-purple-50');
            event.target.closest('.alacarte-category-btn').classList.remove('border-gray-200');

            categoryTitle.textContent = `🍽️ หมวด${category}`;
            
            let menuHTML = '';
            alacarteMenus[category].forEach(item => {
                menuHTML += `
                    <div class="flex items-center justify-between p-3 border rounded-lg menu-item cursor-pointer" onclick="addToAlacarteOrder('${item.name}', ${item.price})">
                        <div class="flex items-center space-x-3">
                            <div class="w-12 h-12 bg-purple-100 rounded-lg flex items-center justify-center">🍽️</div>
                            <span class="font-medium">${item.name}</span>
                        </div>
                        <span class="text-purple-600 font-bold">${item.price} บาท</span>
                    </div>
                `;
            });

            menuItems.innerHTML = menuHTML;
            menuDisplay.classList.remove('hidden');
        }

        // Add to alacarte cart
        function addToAlacarteOrder(name, price) {
            const existingItem = alacarteCart.find(item => item.name === name);
            if (existingItem) {
                existingItem.quantity += 1;
            } else {
                alacarteCart.push({ name, price, quantity: 1 });
            }
            updateAlacarteCart();
        }

        // Update alacarte cart display
        function updateAlacarteCart() {
            const cartElement = document.getElementById('alacarte-cart');
            const totalElement = document.getElementById('alacarte-total');

            if (alacarteCart.length === 0) {
                cartElement.innerHTML = '<p class="text-gray-500 text-center py-8">ยังไม่มีรายการอาหาร</p>';
                totalElement.textContent = '0 บาท';
                return;
            }

            let total = 0;
            let cartHTML = '';

            alacarteCart.forEach((item, index) => {
                const itemTotal = item.price * item.quantity;
                total += itemTotal;
                cartHTML += `
                    <div class="flex items-center justify-between p-3 bg-gray-50 rounded-lg">
                        <div class="flex-1">
                            <div class="font-medium">${item.name}</div>
                            <div class="text-sm text-gray-600">${item.price} บาท x ${item.quantity}</div>
                        </div>
                        <div class="flex items-center space-x-2">
                            <button onclick="changeAlacarteQuantity(${index}, -1)" class="w-8 h-8 bg-red-500 text-white rounded-full flex items-center justify-center hover:bg-red-600">-</button>
                            <span class="w-8 text-center">${item.quantity}</span>
                            <button onclick="changeAlacarteQuantity(${index}, 1)" class="w-8 h-8 bg-green-500 text-white rounded-full flex items-center justify-center hover:bg-green-600">+</button>
                        </div>
                        <div class="ml-4 font-bold text-purple-600">${itemTotal} บาท</div>
                    </div>
                `;
            });

            cartElement.innerHTML = cartHTML;
            totalElement.textContent = `${total} บาท`;
        }
        async function sendToGoogleSheet(orderData) {
    const url = 'https://script.google.com/macros/s/AKfycbzarOSv05FXJO5sREXzu4iztb14FNv_fF6LQffajbCSBfpCUQyNaYmrwzH5YvbGI3le/exec'; // ใส่ URL ของ Apps Script

    try {
        const response = await fetch(url, {
            method: 'POST',
            body: JSON.stringify(orderData),
            headers: { 'Content-Type': 'application/json' }
        });
        const result = await response.json();
        console.log('Google Sheet response:', result);
    } catch (err) {
        console.error('Error sending to Google Sheets:', err);
        alert('เกิดข้อผิดพลาดในการส่งข้อมูล กรุณาลองอีกครั้ง');
    }
}
document.getElementById('breakfast-order-form').addEventListener('submit', function(e) {
    e.preventDefault();
    
    if (breakfastCart.length === 0) {
        alert('กรุณาเลือกอาหารก่อนส่งออเดอร์');
        return;
    }

    const room = document.getElementById('breakfast-room').value;
    const delivery = document.getElementById('breakfast-delivery').value;
    const note = document.getElementById('breakfast-note').value;

    // Check Room Service time
    const now = new Date();
    const hour = now.getHours();
    if (delivery === 'Room Service' && (hour < 9 || hour >= 18)) {
        alert('Room Service ให้บริการเฉพาะ 9:00-18:00 น. เท่านั้น');
        return;
    }

    const orderData = {
        type: 'อาหารเช้า',
        items: breakfastCart,
        room: room,
        delivery: delivery,
        note: note,
        timestamp: now.toLocaleString('th-TH'),
        total: breakfastCart.reduce((sum, item) => sum + (item.price * item.quantity), 0)
    };

    // ส่งไป Google Sheets + LINE
    sendToGoogleSheet(orderData);

    // Show success modal
    document.getElementById('success-modal').classList.remove('hidden');
    document.getElementById('success-modal').classList.add('flex');

    // Reset form & cart
    breakfastCart = [];
    updateBreakfastCart();
    this.reset();
});
document.getElementById('alacarte-order-form').addEventListener('submit', function(e) {
    e.preventDefault();
    
    if (alacarteCart.length === 0) {
        alert('กรุณาเลือกอาหารก่อนส่งออเดอร์');
        return;
    }

    const room = document.getElementById('alacarte-room').value;
    const delivery = document.getElementById('alacarte-delivery').value;
    const note = document.getElementById('alacarte-note').value;

    const now = new Date();
    const hour = now.getHours();
    if (delivery === 'Room Service' && (hour < 9 || hour >= 18)) {
        alert('Room Service ให้บริการเฉพาะ 9:00-18:00 น. เท่านั้น');
        return;
    }

    const orderData = {
        type: 'อาราคัต',
        items: alacarteCart,
        room: room,
        delivery: delivery,
        note: note,
        timestamp: now.toLocaleString('th-TH'),
        total: alacarteCart.reduce((sum, item) => sum + (item.price * item.quantity), 0)
    };

    // ส่งไป Google Sheets + LINE
    sendToGoogleSheet(orderData);

    // Show success modal
    document.getElementById('success-modal').classList.remove('hidden');
    document.getElementById('success-modal').classList.add('flex');

    // Reset form & cart
    alacarteCart = [];
    updateAlacarteCart();
    this.reset();
});


        function showSlide(index) {
    const images = [
        "appetizer.png",         
	    "comfortingfood.png", 
       "comfortingfood1.png", 
       "pancake.png",
        "pasta.png",         
	"toast.png",   
    "toast1.png",     
	"sarad.png" 
    ];
    document.getElementById("main-slide").src = images[index];
}

        // Change alacarte quantity
        function changeAlacarteQuantity(index, change) {
            alacarteCart[index].quantity += change;
            if (alacarteCart[index].quantity <= 0) {
                alacarteCart.splice(index, 1);
            }
            updateAlacarteCart();
        }

        // Check time for breakfast orders
        function checkBreakfastTime() {
            const now = new Date();
            const hour = now.getHours();
            const notice = document.getElementById('breakfast-time-notice');
            
            if (hour >= 7 && hour < 10) {
                notice.innerHTML = '<p class="text-green-700 font-medium">✅ สามารถสั่งอาหารเช้าได้ในขณะนี้</p>';
                notice.className = 'bg-green-100 border-l-4 border-green-500 p-4 rounded-r-lg inline-block';
            } else {
                notice.innerHTML = '<p class="text-yellow-700 font-medium">⏰ สั่งได้ตั้งแต่ 7:00-10:00 น. (หลัง 10:00 น. จะเป็นออเดอร์วันพรุ่งนี้)</p>';
                notice.className = 'bg-yellow-100 border-l-4 border-yellow-500 p-4 rounded-r-lg inline-block';
            }
        }

        // Submit breakfast order
        document.getElementById('breakfast-order-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            if (breakfastCart.length === 0) {
                alert('กรุณาเลือกอาหารก่อนส่งออเดอร์');
                return;
            }

            const room = document.getElementById('breakfast-room').value;
            const delivery = document.getElementById('breakfast-delivery').value;
            const note = document.getElementById('breakfast-note').value;

            // Check room service time
            const now = new Date();
            const hour = now.getHours();
            if (delivery === 'Room Service' && (hour < 9 || hour >= 18)) {
                alert('Room Service ให้บริการเฉพาะ 9:00-18:00 น. เท่านั้น');
                return;
            }

            const orderData = {
                type: 'อาหารเช้า',
                items: breakfastCart,
                room: room,
                delivery: delivery,
                note: note,
                timestamp: new Date().toLocaleString('th-TH'),
                total: breakfastCart.reduce((sum, item) => sum + (item.price * item.quantity), 0)
            };

            // Simulate sending to Google Sheets and LINE notification
            console.log('ส่งข้อมูลไป Google Sheets:', orderData);
            console.log('ส่งแจ้งเตือนไป LINE Group');

            // Show success modal
            document.getElementById('success-modal').classList.remove('hidden');
            document.getElementById('success-modal').classList.add('flex');

            // Reset form and cart
            breakfastCart = [];
            updateBreakfastCart();
            this.reset();
        });

        // Submit alacarte order
        document.getElementById('alacarte-order-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            if (alacarteCart.length === 0) {
                alert('กรุณาเลือกอาหารก่อนส่งออเดอร์');
                return;
            }

            const room = document.getElementById('alacarte-room').value;
            const delivery = document.getElementById('alacarte-delivery').value;
            const note = document.getElementById('alacarte-note').value;

            // Check room service time
            const now = new Date();
            const hour = now.getHours();
            if (delivery === 'Room Service' && (hour < 9 || hour >= 18)) {
                alert('Room Service ให้บริการเฉพาะ 9:00-18:00 น. เท่านั้น');
                return;
            }

            const orderData = {
                type: 'อาราคัต',
                items: alacarteCart,
                room: room,
                delivery: delivery,
                note: note,
                timestamp: new Date().toLocaleString('th-TH'),
                total: alacarteCart.reduce((sum, item) => sum + (item.price * item.quantity), 0)
            };

            // Simulate sending to Google Sheets and LINE notification
            console.log('ส่งข้อมูลไป Google Sheets:', orderData);
            console.log('ส่งแจ้งเตือนไป LINE Group');

            // Show success modal
            document.getElementById('success-modal').classList.remove('hidden');
            document.getElementById('success-modal').classList.add('flex');

            // Reset form and cart
            alacarteCart = [];
            updateAlacarteCart();
            this.reset();
        });

        // Close success modal
        function closeSuccessModal() {
            document.getElementById('success-modal').classList.add('hidden');
            document.getElementById('success-modal').classList.remove('flex');
        }

        // Initialize
        checkBreakfastTime();
        setInterval(checkBreakfastTime, 60000); // Check every minute
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'98d6c0d4a482d32d',t:'MTc2MDI3Mzc0NC4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>

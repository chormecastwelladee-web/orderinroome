<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>สั่งอาหารจากห้องพัก</title>
    <style>
        /* สไตล์สำหรับ Mobile First และ UI/UX */
        body { font-family: 'Arial', sans-serif; margin: 0; padding: 0; background-color: #f4f4f9; color: #333; }
        .container { max-width: 900px; margin: auto; padding: 15px; }
        h1 { text-align: center; color: #007bff; margin-bottom: 20px; }
        
        /* สไตล์สำหรับฟอร์ม */
        .form-section, .menu-section { background: white; padding: 15px; border-radius: 8px; box-shadow: 0 2px 4px rgba(0,0,0,0.1); margin-bottom: 20px; }
        label { display: block; margin-top: 10px; font-weight: bold; }
        input[type="text"], input[type="number"], input[type="time"], select { width: 100%; padding: 10px; margin-top: 5px; border: 1px solid #ccc; border-radius: 4px; box-sizing: border-box; }
        
        /* สไตล์สำหรับ Menu Tabs */
        .tabs { display: flex; overflow-x: auto; white-space: nowrap; border-bottom: 2px solid #ccc; margin-bottom: 15px; }
        .tab-button { background-color: #eee; border: none; padding: 10px 15px; cursor: pointer; font-weight: bold; margin-right: 5px; border-radius: 5px 5px 0 0; transition: background-color 0.3s; }
        .tab-button.active { background-color: #007bff; color: white; }
        .tab-content { display: none; padding-top: 10px; }
        .tab-content.active { display: block; }

        /* สไตล์สำหรับเมนูอาหารแบบภาพ */
        .menu-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); gap: 10px; }
        .menu-item { border: 1px solid #ddd; border-radius: 8px; overflow: hidden; text-align: center; cursor: pointer; transition: transform 0.2s, box-shadow 0.2s; background: #fff; position: relative; }
        .menu-item img { width: 100%; height: 100px; object-fit: cover; display: block; }
        .menu-item-info { padding: 8px; font-size: 0.9em; }
        .menu-item.selected { border: 3px solid #28a745; box-shadow: 0 0 10px rgba(40, 167, 69, 0.5); transform: scale(1.05); }
        .selected-icon { position: absolute; top: 5px; right: 5px; background: #28a745; color: white; border-radius: 50%; width: 24px; height: 24px; line-height: 24px; font-weight: bold; display: none; }
        .menu-item.selected .selected-icon { display: block; }
        
        /* สไตล์สำหรับสรุปรายการ */
        #summary { margin-top: 20px; padding: 10px; background-color: #e9ecef; border-radius: 4px; }
        
        /* สไตล์สำหรับปุ่มสั่งอาหาร */
        button#submit-order { width: 100%; padding: 15px; background-color: #28a745; color: white; border: none; border-radius: 4px; font-size: 1.1em; margin-top: 20px; cursor: pointer; transition: background-color 0.3s; }
        button#submit-order:hover { background-color: #218838; }
        
        /* ข้อความแจ้งเตือน */
        .alert-message { background-color: #ffc107; color: #333; padding: 10px; border-radius: 4px; margin-top: 10px; font-weight: bold; text-align: center; display: none; }
        
    </style>
</head>
<body>

    <div class="container">
        <h1>บริการสั่งอาหารในห้องพัก</h1>

        <div class="form-section">
            <h2>รายละเอียดคำสั่งซื้อ</h2>
            <form id="order-form">
                <label for="roomNo">เลขห้องพัก:</label>
                <input type="text" id="roomNo" required pattern="[A-Za-z0-9]+" title="กรุณากรอกเฉพาะตัวอักษรและตัวเลข" placeholder="เช่น 101" required>

                <label for="pax">จำนวนท่าน:</label>
                <input type="number" id="pax" min="1" value="1" required>

                <label for="serviceType">วิธีรับอาหาร:</label>
                <select id="serviceType" required>
                    <option value="Dine-in">ทานที่ร้าน</option>
                    <option value="Room-service">Room service</option>
                </select>

                <label for="time">เวลาที่จะลง/ให้ไปส่ง:</label>
                <input type="time" id="time" value="09:00" required>
                <div id="room-service-alert" class="alert-message">⚠️ **Room service** บริการได้ **9 โมงเช้าเป็นต้นไป** หากเลือกเวลาก่อนหน้า ระบบจะจัดส่งให้เวลา 9:00 น.</div>

            </form>
        </div>

        <div class="menu-section">
            <h2>เมนูอาหาร</h2>
            
            <div class="tabs">
                </div>

            <div id="menu-container">
                </div>
            
            <div id="summary">
                <h3>สรุปรายการที่เลือก:</h3>
                <ul id="selected-menu-list">
                    <li>ยังไม่ได้เลือกเมนู</li>
                </ul>
            </div>
        </div>

        <button id="submit-order" type="submit">ยืนยันคำสั่งซื้อ</button>

    </div>

    <script>
        // *** 1. การตั้งค่า ***
        const WEB_APP_URL = 'https://script.google.com/macros/s/AKfycbzarOSv05FXJO5sREXzu4iztb14FNv_fF6LQffajbCSBfpCUQyNaYmrwzH5YvbGI3le/exec'; // **เปลี่ยนเป็น URL ของคุณ!**
        
        // ข้อมูลเมนู (5 หมวดหมู่ x 7 รายการ)
        const MENU_DATA = [
            { category: 'อาหารเช้า 1', type: 'Breakfast', items: ['ไข่กระทะ', 'โจ๊กหมู', 'ข้าวต้มกุ้ง', 'อเมริกันเบรคฟาสต์', 'แพนเค้ก', 'ขนมปังฝรั่งเศส', 'ผลไม้รวม'] },
            { category: 'อาหารเช้า 2', type: 'Breakfast', items: ['ข้าวผัดอเมริกัน', 'ขนมปังปิ้งเนย/แยม', 'มัฟฟิน', 'ซีเรียล', 'นมสด', 'กาแฟ', 'ชา'] },
            { category: 'อาหารไทย', type: 'Alacarte', items: ['ผัดกะเพราไก่', 'ต้มยำกุ้งน้ำข้น', 'แกงเขียวหวานเนื้อ', 'ข้าวผัดสับปะรด', 'ส้มตำไทย', 'คอหมูย่าง', 'ผัดไทยกุ้งสด'] },
            { category: 'อาหารนานาชาติ', type: 'Alacarte', items: ['สปาเก็ตตี้คาโบนาร่า', 'พิซซ่ามาการิต้า', 'สเต็กไก่', 'ซุปเห็ด', 'เบอร์เกอร์เนื้อ', 'แซลมอนย่าง', 'สลัดซีซาร์'] },
            { category: 'ของหวานและเครื่องดื่ม', type: 'Alacarte', items: ['ข้าวเหนียวมะม่วง', 'ไอศกรีมวานิลลา', 'ช็อกโกแลตลาวา', 'น้ำส้มคั้น', 'น้ำมะพร้าว', 'ม็อกเทล', 'น้ำเปล่า'] }
        ];

        const BREAKFAST_START_TIME = '07:00';
        const BREAKFAST_END_TIME = '10:30';
        const ROOM_SERVICE_START_TIME = '09:00'; // Room service เริ่ม 9 โมง
        
        let selectedMenu = {}; // { menuKey: { name: '...', category: '...', type: '...' } }
        let currentTab = 0; // Index ของแท็บปัจจุบัน
        
        // *** 2. ฟังก์ชันหลัก ***

        document.addEventListener('DOMContentLoaded', () => {
            renderMenuTabs();
            renderMenuContent();
            
            // Event Listeners
            document.getElementById('serviceType').addEventListener('change', checkRoomServiceTime);
            document.getElementById('time').addEventListener('change', checkRoomServiceTime);
            document.getElementById('submit-order').addEventListener('click', submitOrder);
            
            // เริ่มต้นตรวจสอบ
            checkRoomServiceTime(); 
            updateSummary();
        });

        // 2.1 สร้าง Tabs และ Content
        function renderMenuTabs() {
            const tabsContainer = document.querySelector('.tabs');
            MENU_DATA.forEach((menu, index) => {
                const button = document.createElement('button');
                button.className = `tab-button ${index === currentTab ? 'active' : ''}`;
                button.textContent = menu.category;
                button.setAttribute('data-index', index);
                button.addEventListener('click', () => switchTab(index));
                tabsContainer.appendChild(button);
            });
        }

        function renderMenuContent() {
            const menuContainer = document.getElementById('menu-container');
            menuContainer.innerHTML = ''; 

            MENU_DATA.forEach((menu, tabIndex) => {
                const contentDiv = document.createElement('div');
                contentDiv.className = `tab-content ${tabIndex === currentTab ? 'active' : ''}`;
                contentDiv.setAttribute('data-index', tabIndex);

                const grid = document.createElement('div');
                grid.className = 'menu-grid';

                menu.items.forEach((item, itemIndex) => {
                    const menuKey = `${tabIndex}-${itemIndex}`;
                    const itemDiv = document.createElement('div');
                    itemDiv.className = `menu-item ${selectedMenu[menuKey] ? 'selected' : ''}`;
                    itemDiv.setAttribute('data-key', menuKey);
                    itemDiv.setAttribute('data-name', item);
                    itemDiv.setAttribute('data-category', menu.category);
                    itemDiv.setAttribute('data-type', menu.type);
                    itemDiv.addEventListener('click', toggleMenuItem);

                    // สร้างชื่อไฟล์ภาพสมมติ: menu1.jpg, menu2.jpg, ...
                    const imageIndex = (tabIndex * 7) + itemIndex + 1;
                    
                    itemDiv.innerHTML = `
                        <img src="menu${imageIndex}.jpg" alt="${item}" onerror="this.onerror=null; this.src='https://via.placeholder.com/150x100?text=${item.replace(/ /g, '+')}'">
                        <div class="menu-item-info">${item}</div>
                        <div class="selected-icon">✓</div>
                    `;
                    
                    grid.appendChild(itemDiv);
                });

                contentDiv.appendChild(grid);
                menuContainer.appendChild(contentDiv);
            });
        }
        
        function switchTab(index) {
            currentTab = index;
            document.querySelectorAll('.tab-button').forEach(btn => btn.classList.remove('active'));
            document.querySelector(`.tab-button[data-index="${index}"]`).classList.add('active');
            
            document.querySelectorAll('.tab-content').forEach(content => content.classList.remove('active'));
            document.querySelector(`.tab-content[data-index="${index}"]`).classList.add('active');
        }

        // 2.2 การเลือกเมนู
        function toggleMenuItem(event) {
            const itemDiv = event.currentTarget;
            const menuKey = itemDiv.getAttribute('data-key');
            const itemName = itemDiv.getAttribute('data-name');
            const itemCategory = itemDiv.getAttribute('data-category');
            const itemType = itemDiv.getAttribute('data-type');
            
            if (selectedMenu[menuKey]) {
                delete selectedMenu[menuKey];
                itemDiv.classList.remove('selected');
            } else {
                // ตรวจสอบเวลาสำหรับอาหารเช้า
                if (itemType === 'Breakfast' && !isBreakfastTimeValid()) {
                    alert(`เมนู ${itemName} เป็นอาหารเช้า สามารถสั่งได้เฉพาะช่วง ${BREAKFAST_START_TIME}–${BREAKFAST_END_TIME} น. เท่านั้น`);
                    return;
                }
                
                selectedMenu[menuKey] = { 
                    name: itemName, 
                    category: itemCategory, 
                    type: itemType 
                };
                itemDiv.classList.add('selected');
            }
            updateSummary();
        }

        function isBreakfastTimeValid() {
            const now = new Date();
            const year = now.getFullYear();
            const month = now.getMonth();
            const day = now.getDate();
            
            // แปลงเวลาให้เป็น Object Date เพื่อเปรียบเทียบ
            const nowTime = now.getHours() * 60 + now.getMinutes(); // เวลาปัจจุบันเป็นนาที
            
            const startParts = BREAKFAST_START_TIME.split(':').map(Number);
            const endParts = BREAKFAST_END_TIME.split(':').map(Number);
            
            const startTimeMinutes = startParts[0] * 60 + startParts[1];
            const endTimeMinutes = endParts[0] * 60 + endParts[1];

            return nowTime >= startTimeMinutes && nowTime <= endTimeMinutes;
        }

        function updateSummary() {
            const list = document.getElementById('selected-menu-list');
            list.innerHTML = '';
            
            if (Object.keys(selectedMenu).length === 0) {
                list.innerHTML = '<li>ยังไม่ได้เลือกเมนู</li>';
                return;
            }
            
            for (const key in selectedMenu) {
                const item = selectedMenu[key];
                const li = document.createElement('li');
                li.textContent = `${item.name} (${item.category} / ${item.type})`;
                list.appendChild(li);
            }
        }
        
        // 2.3 การตรวจสอบเวลา Room Service
        function checkRoomServiceTime() {
            const serviceType = document.getElementById('serviceType').value;
            const timeInput = document.getElementById('time');
            const alertDiv = document.getElementById('room-service-alert');

            if (serviceType === 'Room-service') {
                const selectedTime = timeInput.value;
                if (selectedTime && selectedTime < ROOM_SERVICE_START_TIME) {
                    alertDiv.style.display = 'block';
                } else {
                    alertDiv.style.display = 'none';
                }
            } else {
                alertDiv.style.display = 'none';
            }
        }
        
        // 2.4 การส่งคำสั่งซื้อ
        async function submitOrder() {
            const form = document.getElementById('order-form');
            if (!form.checkValidity()) {
                form.reportValidity();
                return;
            }
            
            if (Object.keys(selectedMenu).length === 0) {
                alert('กรุณาเลือกเมนูอาหารอย่างน้อย 1 รายการ');
                return;
            }
            
            const roomNo = document.getElementById('roomNo').value;
            const pax = document.getElementById('pax').value;
            const serviceType = document.getElementById('serviceType').value;
            let time = document.getElementById('time').value;

            // ปรับเวลา Room service หากเลือกก่อน 9:00
            if (serviceType === 'Room-service' && time < ROOM_SERVICE_START_TIME) {
                time = ROOM_SERVICE_START_TIME;
            }

            // ตรวจสอบอาหารเช้าอีกครั้งก่อนส่ง
            const hasBreakfast = Object.values(selectedMenu).some(item => item.type === 'Breakfast');
            if (hasBreakfast && !isBreakfastTimeValid()) {
                 alert(`คุณมีรายการอาหารเช้า แต่ขณะนี้ไม่ใช่ช่วงเวลาที่สามารถสั่งได้ (${BREAKFAST_START_TIME}–${BREAKFAST_END_TIME} น.)`);
                 return;
            }
            
            const orderData = {
                roomNo: roomNo,
                pax: pax,
                serviceType: serviceType,
                time: time,
                selectedMenu: selectedMenu // ส่ง Object เมนูที่เลือกไปทั้งก้อน
            };

            document.getElementById('submit-order').textContent = 'กำลังส่ง...';
            document.getElementById('submit-order').disabled = true;

            try {
                const response = await fetch(WEB_APP_URL, {
                    method: 'POST',
                    mode: 'cors', 
                    headers: {
                        'Content-Type': 'text/plain;charset=utf-8', // ใช้ text/plain เพื่อเลี่ยง preflight
                    },
                    body: JSON.stringify(orderData) 
                });

                const result = await response.json();
                
                if (result.success) {
                    alert('✅ สั่งอาหารสำเร็จ! ขอบคุณค่ะ/ครับ');
                    // Reset ฟอร์มและเมนู
                    form.reset();
                    selectedMenu = {};
                    renderMenuContent(); // เพื่ออัพเดตสถานะการเลือก
                    updateSummary();
                } else {
                    alert('❌ เกิดข้อผิดพลาดในการสั่งอาหาร: ' + result.message);
                }

            } catch (error) {
                console.error('Fetch error:', error);
                alert('❌ เกิดข้อผิดพลาดในการเชื่อมต่อ (โปรดตรวจสอบ URL ของ Web App)');
            } finally {
                document.getElementById('submit-order').textContent = 'ยืนยันคำสั่งซื้อ';
                document.getElementById('submit-order').disabled = false;
            }
        }
    </script>
</body>
</html>

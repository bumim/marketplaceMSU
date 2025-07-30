
<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8" />
  <title>ตลาดมือสองนิสิต มมส</title>
  <style>
    body {
      font-family: 'Sarabun', sans-serif, Arial, sans-serif;
      background-color: #f5f5f5;
      margin: 0; padding: 0;
      color: #333;
    }
    header {
      background-color: #ffcc00;
      color: #333;
      padding: 1rem;
      text-align: center;
      font-size: 1.5rem;
      font-weight: bold;
    }
    main {
      max-width: 900px;
      margin: auto;
      padding: 1rem;
    }

    /* Login/Register */
    #loginPage {
      max-width: 400px;
      margin: 40px auto;
      background: white;
      padding: 2rem;
      border-radius: 12px;
      box-shadow: 0 0 8px rgba(0,0,0,0.1);
      text-align: center;
    }
    #loginPage input {
      width: 100%;
      padding: 0.5rem;
      margin-top: 0.8rem;
      font-size: 1rem;
      border-radius: 8px;
      border: 1px solid #ccc;
    }
    #loginPage button {
      margin-top: 1rem;
      width: 100%;
      background-color: #ffcc00;
      border: none;
      color: #333;
      font-weight: bold;
      font-size: 1.1rem;
      padding: 0.7rem;
      border-radius: 8px;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
    #loginPage button:hover {
      background-color: #e6b800;
    }
    #loginPage hr {
      margin: 2rem 0;
    }
    #loginPage p {
      font-size: 0.9rem;
      color: #555;
    }
    #loginPage p span {
      cursor: pointer;
      color: #0066cc;
      text-decoration: underline;
    }

    /* User Panel */
    #userPanel {
      display: none;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 1rem;
      padding: 0.5rem 1rem;
      background: #ffcc00;
      border-radius: 8px;
      color: #333;
    }
    #userPanel button {
      background: #d4af37;
      border: none;
      padding: 0.3rem 0.8rem;
      border-radius: 6px;
      cursor: pointer;
      font-weight: bold;
    }
    #userPanel button:hover {
      background: #b69524;
    }

    /* Categories */
    #categories {
      display: flex;
      gap: 12px;
      flex-wrap: wrap;
      margin-bottom: 1rem;
      justify-content: center;
    }
    .category-card {
      background: white;
      border-radius: 12px;
      box-shadow: 0 0 6px rgba(0,0,0,0.1);
      cursor: pointer;
      text-align: center;
      width: 120px;
      padding: 12px;
      transition: background-color 0.3s ease;
      user-select: none;
    }
    .category-card.active,
    .category-card:hover {
      background-color: #ffec80;
    }
    .category-card img {
      width: 48px;
      height: 48px;
      object-fit: contain;
      margin-bottom: 8px;
    }
    .category-card span {
      font-weight: 600;
      font-size: 1rem;
      color: #333;
      display: block;
    }

    /* Posts */
    #posts {
      display: grid;
      grid-template-columns: repeat(auto-fill,minmax(260px,1fr));
      gap: 20px;
    }
    .post-card {
      background: white;
      border-radius: 12px;
      box-shadow: 0 0 10px rgba(0,0,0,0.12);
      overflow: hidden;
      display: flex;
      flex-direction: column;
      position: relative;
    }
    .post-card img {
      width: 100%;
      height: 160px;
      object-fit: cover;
      border-bottom: 1px solid #ddd;
    }
    .sold-badge {
      position: absolute;
      top: 8px;
      left: 8px;
      background: rgba(255,0,0,0.85);
      color: white;
      padding: 4px 10px;
      font-weight: bold;
      border-radius: 20px;
      font-size: 0.85rem;
      z-index: 2;
      user-select: none;
    }
    .post-info {
      padding: 10px 12px;
      flex-grow: 1;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }
    .post-title {
      font-weight: 700;
      font-size: 1.1rem;
      margin-bottom: 4px;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
    }
    .post-category,
    .post-seller,
    .post-contact,
    .post-delivery {
      font-size: 0.85rem;
      color: #666;
      margin-bottom: 3px;
    }
    .btn-sold {
      background: #d72631;
      color: white;
      border: none;
      padding: 6px;
      border-radius: 8px;
      font-weight: bold;
      cursor: pointer;
      margin-top: 6px;
      transition: background-color 0.3s ease;
    }
    .btn-sold:hover {
      background-color: #b71c24;
    }

    /* Notification Badge */
    .noti-badge {
      background: #e63946;
      color: white;
      font-size: 0.75rem;
      border-radius: 50%;
      padding: 0 6px;
      margin-left: 6px;
      vertical-align: middle;
      user-select: none;
    }

    /* Buttons for comments/chat */
    .post-info > div > button {
      margin: 4px 6px 0 0;
      cursor: pointer;
      background: #ffcc00;
      border: none;
      padding: 6px 10px;
      border-radius: 8px;
      font-weight: 600;
      transition: background-color 0.3s ease;
      user-select: none;
    }
    .post-info > div > button:hover {
      background-color: #e6b800;
    }

    /* Overlay for post form */
    #postFormOverlay {
      display: none;
      position: fixed;
      top:0; left:0; right:0; bottom:0;
      background: rgba(0,0,0,0.6);
      justify-content: center;
      align-items: center;
      z-index: 1000;
    }
    #postFormContainer {
      background: white;
      padding: 20px 25px;
      border-radius: 12px;
      width: 360px;
      max-width: 90%;
      box-shadow: 0 0 15px rgba(0,0,0,0.25);
      position: relative;
      text-align: center;
    }
    #postFormContainer input, #postFormContainer textarea, #postFormContainer select {
      width: 100%;
      margin: 8px 0;
      padding: 8px;
      font-size: 1rem;
      border-radius: 8px;
      border: 1px solid #ccc;
      resize: vertical;
      box-sizing: border-box;
    }
    #postFormContainer textarea {
      min-height: 80px;
    }
    #postFormContainer button {
      margin-top: 12px;
      width: 100%;
      padding: 10px;
      background-color: #ffcc00;
      border: none;
      font-weight: 700;
      font-size: 1.1rem;
      border-radius: 8px;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
    #postFormContainer button:hover {
      background-color: #e6b800;
    }
    #closePostFormBtn {
      position: absolute;
      top: 8px;
      right: 12px;
      background: transparent;
      border: none;
      font-size: 1.5rem;
      font-weight: bold;
      cursor: pointer;
      color: #999;
      transition: color 0.3s ease;
      user-select: none;
    }
    #closePostFormBtn:hover {
      color: #333;
    }

    /* Comments and Chat containers */
    .comments-container, .chat-container {
      background: white;
      border-radius: 12px;
      box-shadow: 0 0 12px rgba(0,0,0,0.15);
      padding: 15px;
      max-width: 600px;
      margin: 20px auto;
      max-height: 400px;
      overflow-y: auto;
      text-align: left;
      font-size: 0.95rem;
    }
    .comment-item, .chat-message {
      padding: 6px 10px;
      border-radius: 12px;
      margin-bottom: 8px;
      max-width: 85%;
      word-wrap: break-word;
    }
    .comment-item {
      background: #f0f0f0;
      font-weight: 600;
    }
    .chat-message {
      background: #ffec80;
      font-weight: 600;
    }
    .chat-message.mine {
      background: #ffdb4d;
      margin-left: auto;
    }
    .comment-input, .chat-input {
      width: 100%;
      padding: 10px 12px;
      border-radius: 20px;
      border: 1px solid #ccc;
      box-sizing: border-box;
      font-size: 1rem;
      margin-top: 10px;
    }
    .comments-container::-webkit-scrollbar,
    .chat-container::-webkit-scrollbar {
      width: 6px;
    }
    .comments-container::-webkit-scrollbar-thumb,
    .chat-container::-webkit-scrollbar-thumb {
      background-color: #ccc;
      border-radius: 3px;
    }

  </style>
</head>
<body>

  <header>ตลาดมือสองนิสิต มหาวิทยาลัยมหาสารคาม</header>

  <main>

    <!-- หน้าเข้าสู่ระบบและลงทะเบียน -->
    <section id="loginPage">
      <h2>เข้าสู่ระบบ / ลงทะเบียน</h2>

      <div id="loginForm">
        <input type="text" id="loginId" placeholder="กรอกรหัสนิสิต 11 หลัก เช่น 12345678901" maxlength="11" />
        <input type="password" id="loginPass" placeholder="รหัสผ่าน" />
        <button id="btnLogin">เข้าสู่ระบบ</button>
      </div>

      <hr />

      <div id="registerForm" style="display:none;">
        <input type="text" id="regId" placeholder="รหัสนิสิต 11 หลัก" maxlength="11" />
        <input type="password" id="regPass" placeholder="ตั้งรหัสผ่าน (อย่างน้อย 4 ตัว)" />
        <input type="text" id="regPhone" placeholder="เบอร์โทรศัพท์ เช่น 089xxxxxxx" maxlength="10" />
        <button id="btnRegister">ลงทะเบียน</button>
      </div>

      <p>
        <span id="toggleLoginText">สมัครสมาชิก</span>
      </p>
    </section>

    <!-- แถบแสดงชื่อผู้ใช้และปุ่มออกจากระบบ -->
    <div id="userPanel" style="display:none;">
      <div>ยินดีต้อนรับ, <span id="currentUser"></span></div>
      <button id="btnLogout">ออกจากระบบ</button>
    </div>

    <!-- ตลาดมือสอง -->
    <section id="marketplace" style="display:none;">

      <!-- หมวดหมู่สินค้า -->
      <div id="categories"></div>

      <!-- ปุ่มเพิ่มโพสต์ -->
      <div style="text-align:center; margin-bottom: 16px;">
        <button id="btnAddPost" style="background:#ffcc00; border:none; padding: 10px 20px; border-radius: 10px; font-weight: bold; cursor: pointer;">
          + โพสต์ขายสินค้า
        </button>
      </div>

      <!-- รายการโพสต์ -->
      <div id="posts"></div>

    </section>

    <!-- ฟอร์มโพสต์ขายสินค้าแบบ overlay -->
    <div id="postFormOverlay" style="display:none; align-items:center;">
      <div id="postFormContainer">
        <button id="closePostFormBtn" title="ปิดฟอร์ม">×</button>
        <h3>โพสต์ขายสินค้า</h3>
        <input type="text" id="postTitle" placeholder="ชื่อสินค้า" />
        <input type="text" id="postImage" placeholder="ลิงก์รูปภาพสินค้า (URL)" />
        <textarea id="postDescription" placeholder="รายละเอียดสินค้า"></textarea>
        <select id="postCategory"></select>
        <input type="text" id="postContact" placeholder="ช่องทางติดต่อ (เช่น ไลน์)" />
        <input type="text" id="postDelivery" placeholder="วิธีรับสินค้า (นัดรับ/ส่งของ/รับที่หอพัก)" />
        <button id="btnSubmitPost">โพสต์สินค้า</button>
      </div>
    </div>

  </main>

  <script>
    // ======= ข้อมูลหลักจาก localStorage =======
    let users = JSON.parse(localStorage.getItem('users') || '{}');
    let currentUserId = localStorage.getItem('currentUserId') || '';
    let posts = JSON.parse(localStorage.getItem('posts') || '[]');

    // หมวดหมู่สินค้า
    const categoriesData = [
      { id: 'book', name: 'หนังสือเรียน', img: 'https://cdn-icons-png.flaticon.com/512/29/29302.png' },
      { id: 'desk', name: 'โต๊ะหนังสือ', img: 'https://cdn-icons-png.flaticon.com/512/2331/2331966.png' },
      { id: 'uniform', name: 'ชุดพละ', img: 'https://cdn-icons-png.flaticon.com/512/2167/2167135.png' },
      { id: 'stuff', name: 'ตุ้งติ้ง', img: 'https://cdn-icons-png.flaticon.com/512/126/126504.png' },
      { id: 'others', name: 'ของส่งต่อต่างๆ', img: 'https://cdn-icons-png.flaticon.com/512/565/565547.png' },
    ];

    // ========== อ้างอิง element ==========
    const loginPage = document.getElementById('loginPage');
    const loginForm = document.getElementById('loginForm');
    const registerForm = document.getElementById('registerForm');
    const toggleLoginText = document.getElementById('toggleLoginText');

    const loginIdInput = document.getElementById('loginId');
    const loginPassInput = document.getElementById('loginPass');

    const regIdInput = document.getElementById('regId');
    const regPassInput = document.getElementById('regPass');
    const regPhoneInput = document.getElementById('regPhone');

    const userPanel = document.getElementById('userPanel');
    const currentUserSpan = document.getElementById('currentUser');
    const btnLogout = document.getElementById('btnLogout');

    const marketplace = document.getElementById('marketplace');
    const categoriesEl = document.getElementById('categories');
    const postsEl = document.getElementById('posts');
    const btnAddPost = document.getElementById('btnAddPost');

    const postFormOverlay = document.getElementById('postFormOverlay');
    const postFormContainer = document.getElementById('postFormContainer');
    const closePostFormBtn = document.getElementById('closePostFormBtn');

    // ==== ฟังก์ชันช่วย validate ====
    function validateStudentId(id) {
      return /^\d{11}$/.test(id);
    }
    function validatePhone(phone) {
      return /^0\d{9}$/.test(phone);
    }

    // ==== ฟังก์ชัน toggle login/register form ====
    toggleLoginText.onclick = () => {
      const showRegister = registerForm.style.display === 'none';
      if (showRegister) {
        loginForm.style.display = 'none';
        registerForm.style.display = 'block';
        toggleLoginText.textContent = 'กลับไปเข้าสู่ระบบ';
      } else {
        loginForm.style.display = 'block';
        registerForm.style.display = 'none';
        toggleLoginText.textContent = 'สมัครสมาชิก';
      }
    };

    // ==== ฟังก์ชัน ล็อกอิน ====
    document.getElementById('btnLogin').onclick = () => {
      const id = loginIdInput.value.trim();
      const pass = loginPassInput.value;

      if (!validateStudentId(id)) {
        alert('กรุณากรอกรหัสนิสิต 11 หลักให้ถูกต้อง');
        return;
      }
      if (!pass) {
        alert('กรุณากรอกรหัสผ่าน');
        return;
      }
      if (!(id in users)) {
        alert('ไม่พบรหัสนิสิตนี้ในระบบ กรุณาลงทะเบียนก่อน');
        return;
      }
      if (users[id].password !== pass) {
        alert('รหัสผ่านไม่ถูกต้อง');
        return;
      }

      loginSuccess(id);
    };

    // ==== ฟังก์ชัน ลงทะเบียน ====
    document.getElementById('btnRegister').onclick = () => {
      const id = regIdInput.value.trim();
      const pass = regPassInput.value;
      const phone = regPhoneInput.value.trim();

      if (!validateStudentId(id)) {
        alert('กรุณากรอกรหัสนิสิต 11 หลักให้ถูกต้อง');
        return;
      }
      if (pass.length < 4) {
        alert('รหัสผ่านต้องมีอย่างน้อย 4 ตัวอักษร');
        return;
      }
      if (!validatePhone(phone)) {
        alert('กรุณากรอกเบอร์โทรศัพท์ให้ถูกต้อง');
        return;
      }
      if (id in users) {
        alert('รหัสนิสิตนี้ได้ลงทะเบียนแล้ว');
        return;
      }

      users[id] = { password: pass, phone };
      localStorage.setItem('users', JSON.stringify(users));

      alert('ลงทะเบียนสำเร็จ! คุณสามารถเข้าสู่ระบบได้เลย');
      toggleLoginText.click(); // กลับไปฟอร์ม login
      clearLoginInputs();
      clearRegisterInputs();
    };

    // ==== เคลียร์ input fields ====
    function clearLoginInputs() {
      loginIdInput.value = '';
      loginPassInput.value = '';
    }
    function clearRegisterInputs() {
      regIdInput.value = '';
      regPassInput.value = '';
      regPhoneInput.value = '';
    }

    // ==== ฟังก์ชัน หลังล็อกอินสำเร็จ ====
    function loginSuccess(id) {
      currentUserId = id;
      localStorage.setItem('currentUserId', id);
      currentUserSpan.textContent = `นิสิตรหัส ${id}`;
      loginPage.style.display = 'none';
      userPanel.style.display = 'flex';
      marketplace.style.display = 'block';
      renderCategories();
      renderPosts();
      clearLoginInputs();
      clearRegisterInputs();
    }

    // ==== ฟังก์ชัน logout ====
    btnLogout.onclick = () => {
      currentUserId = '';
      localStorage.removeItem('currentUserId');
      loginPage.style.display = 'block';
      userPanel.style.display = 'none';
      marketplace.style.display = 'none';
      clearLoginInputs();
      clearRegisterInputs();
    };

    // ==== ฟังก์ชัน render หมวดหมู่ ====
    let selectedCategory = 'all';
    function renderCategories() {
      categoriesEl.innerHTML = '';
      // หมวดหมู่ 'ทั้งหมด'
      const allCard = document.createElement('div');
      allCard.className = 'category-card' + (selectedCategory==='all' ? ' active' : '');
      allCard.innerHTML = `<img src="https://cdn-icons-png.flaticon.com/512/565/565547.png" alt="ทั้งหมด" /><span>ทั้งหมด</span>`;
      allCard.onclick = () => {
        selectedCategory = 'all';
        renderCategories();
        renderPosts();
      };
      categoriesEl.appendChild(allCard);

      // หมวดหมู่ที่กำหนด
      categoriesData.forEach(cat => {
        const div = document.createElement('div');
        div.className = 'category-card' + (selectedCategory === cat.id ? ' active' : '');
        div.innerHTML = `<img src="${cat.img}" alt="${cat.name}" /><span>${cat.name}</span>`;
        div.onclick = () => {
          selectedCategory = cat.id;
          renderCategories();
          renderPosts();
        };
        categoriesEl.appendChild(div);
      });
    }

    // ==== ฟังก์ชัน render โพสต์ตามหมวดหมู่และแสดงหน้าแรก ====
    function renderPosts() {
      postsEl.innerHTML = '';

      // กรองตามหมวดหมู่
      let filteredPosts = posts;
      if(selectedCategory !== 'all'){
        filteredPosts = posts.filter(p => p.category === selectedCategory);
      }

      if(filteredPosts.length === 0) {
        postsEl.innerHTML = `<p style="text-align:center; color:#555; margin-top: 2rem;">ไม่มีสินค้าหมวดนี้ในขณะนี้</p>`;
        return;
      }

      filteredPosts.forEach((post, i) => {
        const card = document.createElement('div');
        card.className = 'post-card';

        // รูปภาพ
        const img = document.createElement('img');
        img.src = post.imageUrl || 'https://via.placeholder.com/300x160?text=ไม่มีรูปภาพ';
        img.alt = post.itemName;
        card.appendChild(img);

        // ขายแล้ว badge
        if(post.sold) {
          const soldBadge = document.createElement('div');
          soldBadge.className = 'sold-badge';
          soldBadge.textContent = 'ขายแล้ว';
          card.appendChild(soldBadge);
        }

        // ข้อมูลสินค้า
        const info = document.createElement('div');
        info.className = 'post-info';

        const title = document.createElement('div');
        title.className = 'post-title';
        title.textContent = post.itemName;
        info.appendChild(title);

        const catName = categoriesData.find(c => c.id === post.category)?.name || 'อื่นๆ';
        const categoryEl = document.createElement('div');
        categoryEl.className = 'post-category';
        categoryEl.textContent = `หมวดหมู่: ${catName}`;
        info.appendChild(categoryEl);

        const sellerEl = document.createElement('div');
        sellerEl.className = 'post-seller';
        sellerEl.textContent = `ผู้ขาย: นิสิตรหัส ${post.owner}`;
        info.appendChild(sellerEl);

        const contactEl = document.createElement('div');
        contactEl.className = 'post-contact';
        contactEl.textContent = `ติดต่อ: ${post.contact}`;
        info.appendChild(contactEl);

        const deliveryEl = document.createElement('div');
        deliveryEl.className = 'post-delivery';
        deliveryEl.textContent = `วิธีรับสินค้า: ${post.delivery}`;
        info.appendChild(deliveryEl);

        // ปุ่ม "ขายแล้ว" เฉพาะเจ้าของและยังไม่ขาย
        if(!post.sold && post.owner === currentUserId){
          const soldBtn = document.createElement('button');
          soldBtn.className = 'btn-sold';
          soldBtn.textContent = 'กดเพื่อแสดงว่าขายแล้ว';
          soldBtn.onclick = () => {
            if(confirm('ยืนยันการเปลี่ยนสถานะเป็น "ขายแล้ว" ?')){
              posts[i].sold = true;
              savePosts();
              renderPosts();
            }
          };
          info.appendChild(soldBtn);
        }

        // ปุ่มเปิดดูคอมเมนต์และแชท
        const commentChatBtn = document.createElement('button');
        commentChatBtn.textContent = `ดูคอมเมนต์และแชท 💬 `;
        // เพิ่ม badge แจ้งเตือนถ้ามีคอมเมนต์หรือแชทใหม่
        let newCommentCount = post.comments.filter(c => !c.readBy?.includes(currentUserId)).length;
        let newChatCount = post.chat.filter(c => c.to === currentUserId && !c.read).length;
        let totalNoti = newCommentCount + newChatCount;
        if(totalNoti > 0){
          const badge = document.createElement('span');
          badge.className = 'noti-badge';
          badge.textContent = totalNoti;
          commentChatBtn.appendChild(badge);
        }
        commentChatBtn.onclick = () => openCommentChat(i);
        info.appendChild(commentChatBtn);

        card.appendChild(info);
        postsEl.appendChild(card);
      });
    }

    // ==== ฟังก์ชันบันทึกโพสต์ลง localStorage ====
    function savePosts(){
      localStorage.setItem('posts', JSON.stringify(posts));
    }

    // ==== ฟังก์ชันเปิด/ปิดฟอร์มโพสต์สินค้า ====
    btnAddPost.onclick = () => {
      openPostForm();
    };
    closePostFormBtn.onclick = () => {
      closePostForm();
    };
    function openPostForm(){
      postFormOverlay.style.display = 'flex';
      // reset form
      document.getElementById('postTitle').value = '';
      document.getElementById('postImage').value = '';
      document.getElementById('postDescription').value = '';
      document.getElementById('postContact').value = '';
      document.getElementById('postDelivery').value = '';
      // กำหนดค่า category เลือกแรก
      const selectCat = document.getElementById('postCategory');
      selectCat.innerHTML = '';
      categoriesData.forEach(c=>{
        const opt = document.createElement('option');
        opt.value = c.id;
        opt.textContent = c.name;
        selectCat.appendChild(opt);
      });
      selectCat.value = categoriesData[0].id;
    }
    function closePostForm(){
      postFormOverlay.style.display = 'none';
    }

    // ==== ฟังก์ชันบันทึกโพสต์ใหม่ ====
    document.getElementById('btnSubmitPost').onclick = () => {
      const title = document.getElementById('postTitle').value.trim();
      const imageUrl = document.getElementById('postImage').value.trim();
      const description = document.getElementById('postDescription').value.trim();
      const category = document.getElementById('postCategory').value;
      const contact = document.getElementById('postContact').value.trim();
      const delivery = document.getElementById('postDelivery').value.trim();

      if(!title || !imageUrl || !description || !contact || !delivery){
        alert('กรุณากรอกข้อมูลให้ครบทุกช่อง');
        return;
      }
      // สร้างโพสต์ใหม่
      const newPost = {
        id: Date.now(),
        owner: currentUserId,
        itemName: title,
        imageUrl,
        description,
        category,
        contact,
        delivery,
        sold: false,
        comments: [],
        chat: []
      };
      posts.unshift(newPost);
      savePosts();
      closePostForm();
      renderPosts();
      alert('โพสต์ขายสินค้าสำเร็จ');
    };

    // ==== ฟังก์ชันเปิดหน้าคอมเมนต์และแชท ====
    let currentPostIndex = null;
    function openCommentChat(postIndex){
      currentPostIndex = postIndex;
      const post = posts[postIndex];

      // สร้าง popup
      const popup = document.createElement('div');
      popup.style.position = 'fixed';
      popup.style.top = '50%';
      popup.style.left = '50%';
      popup.style.transform = 'translate(-50%, -50%)';
      popup.style.background = 'white';
      popup.style.borderRadius = '12px';
      popup.style.boxShadow = '0 0 15px rgba(0,0,0,0.3)';
      popup.style.width = '400px';
      popup.style.maxWidth = '90%';
      popup.style.maxHeight = '600px';
      popup.style.overflow = 'hidden';
      popup.style.display = 'flex';
      popup.style.flexDirection = 'column';
      popup.style.zIndex = 2000;

      // Header
      const header = document.createElement('div');
      header.style.background = '#ffcc00';
      header.style.padding = '10px';
      header.style.fontWeight = 'bold';
      header.style.fontSize = '1.2rem';
      header.style.color = '#333';
      header.textContent = `คอมเมนต์และแชท - ${post.itemName}`;
      popup.appendChild(header);

      // Close button
      const closeBtn = document.createElement('button');
      closeBtn.textContent = '✕';
      closeBtn.style.position = 'absolute';
      closeBtn.style.top = '8px';
      closeBtn.style.right = '12px';
      closeBtn.style.background = 'transparent';
      closeBtn.style.border = 'none';
      closeBtn.style.fontSize = '1.5rem';
      closeBtn.style.cursor = 'pointer';
      closeBtn.style.color = '#666';
      popup.appendChild(closeBtn);

      closeBtn.onclick = () => {
        document.body.removeChild(popup);
        renderPosts(); // รีเฟรชเพื่อเคลียร์แจ้งเตือน
      };

      // Comments section
      const commentsSection = document.createElement('div');
      commentsSection.className = 'comments-container';
      commentsSection.style.flex = '1';
      commentsSection.style.overflowY = 'auto';
      popup.appendChild(commentsSection);

      // Render comments
      function renderComments() {
        commentsSection.innerHTML = '';
        post.comments.forEach((c, i) => {
          const div = document.createElement('div');
          div.className = 'comment-item';
          div.textContent = `${c.by}: ${c.msg}`;
          commentsSection.appendChild(div);

          // Mark comment as read by currentUserId
          if(!c.readBy) c.readBy = [];
          if(!c.readBy.includes(currentUserId)) c.readBy.push(currentUserId);
        });
        savePosts();
      }
      renderComments();

      // Comment input
      const commentInput = document.createElement('input');
      commentInput.className = 'comment-input';
      commentInput.placeholder = 'แสดงความคิดเห็น...';
      popup.appendChild(commentInput);

      commentInput.addEventListener('keydown', e => {
        if(e.key === 'Enter' && commentInput.value.trim() !== ''){
          post.comments.push({ by: currentUserId, msg: commentInput.value.trim(), readBy: [currentUserId] });
          commentInput.value = '';
          renderComments();
        }
      });

      // Chat section
      const chatSection = document.createElement('div');
      chatSection.className = 'chat-container';
      chatSection.style.flex = '1';
      chatSection.style.overflowY = 'auto';
      popup.appendChild(chatSection);

      // Render chat
      function renderChat() {
        chatSection.innerHTML = '';
        post.chat.forEach((c,i) => {
          const div = document.createElement('div');
          div.className = 'chat-message';
          if(c.from === currentUserId) div.classList.add('mine');
          div.textContent = `${c.from} → ${c.to}: ${c.msg}`;
          chatSection.appendChild(div);
          // mark message as read if to currentUserId
          if(c.to === currentUserId) c.read = true;
        });
        savePosts();
      }
      renderChat();

      // Chat input
      const chatInput = document.createElement('input');
      chatInput.className = 'chat-input';
      chatInput.placeholder = 'พิมพ์ข้อความแชท...';
      popup.appendChild(chatInput);

      // เลือกผู้รับแชท - (เจ้าของโพสต์หรือคนอื่น)
      // เพื่อความง่าย สมมติ แชทได้เฉพาะระหว่างเจ้าของโพสต์กับคนอื่นๆเท่านั้น
      // ถ้าผู้ส่งเป็นเจ้าของโพสต์ จะส่งไปหาคนอื่น และถ้าไม่ใช่ จะส่งหาผู้ขาย
      let chatRecipient = (currentUserId === post.owner) ? 'ผู้ซื้อ' : `นิสิตรหัส ${post.owner}`;

      chatInput.addEventListener('keydown', e => {
        if(e.key === 'Enter' && chatInput.value.trim() !== ''){
          const msg = chatInput.value.trim();
          const from = currentUserId;
          const to = (from === post.owner) ? 'ผู้ซื้อ' : post.owner;
          post.chat.push({ from, to, msg, read: false });
          chatInput.value = '';
          renderChat();
        }
      });

      document.body.appendChild(popup);
    }

    // ==== โหลดข้อมูลตอนเริ่ม ====
    window.onload = () => {
      // ถ้าเคยล็อกอินไว้
      if(currentUserId && users[currentUserId]){
        loginSuccess(currentUserId);
      }
    };

  </script>

</body>
</html>

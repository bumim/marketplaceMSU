<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8" />
  <title>ตลาดมือสองนิสิต มมส</title>
  <style>
    /* --- CSS เหมือนเดิม ปรับเพิ่มตามนี้ --- */
    body {
      font-family: 'Sarabun', Arial, sans-serif;
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
      max-height: 90vh;
      overflow-y: auto;
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
      display: flex;
      flex-direction: column;
      gap: 6px;
    }
    .comment-item, .chat-message {
      padding: 8px 12px;
      border-radius: 12px;
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
      align-self: flex-start;
      max-width: 70%;
    }
    .chat-message.mine {
      background: #ffdb4d;
      align-self: flex-end;
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
      <!-- ช่องอัปโหลดรูปภาพเป็นไฟล์ -->
      <input type="file" id="postImageFile" accept="image/*" />
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
    { id: 'sportswear', name: 'ชุดพละ มมส', img: 'https://cdn-icons-png.flaticon.com/512/992/992703.png' },
    { id: 'desk', name: 'โต๊ะ', img: 'https://cdn-icons-png.flaticon.com/512/237/237318.png' },
    { id: 'stationery', name: 'เครื่องเขียน', img: 'https://cdn-icons-png.flaticon.com/512/3514/3514974.png' }
  ];

  // สถานะหมวดหมู่ที่เลือก
  let selectedCategory = '';

  // ----- DOM Elements -----
  const loginPage = document.getElementById('loginPage');
  const loginForm = document.getElementById('loginForm');
  const registerForm = document.getElementById('registerForm');
  const toggleLoginText = document.getElementById('toggleLoginText');
  const btnLogin = document.getElementById('btnLogin');
  const btnRegister = document.getElementById('btnRegister');
  const regId = document.getElementById('regId');
  const regPass = document.getElementById('regPass');
  const regPhone = document.getElementById('regPhone');
  const loginId = document.getElementById('loginId');
  const loginPass = document.getElementById('loginPass');

  const userPanel = document.getElementById('userPanel');
  const currentUserSpan = document.getElementById('currentUser');
  const btnLogout = document.getElementById('btnLogout');

  const marketplace = document.getElementById('marketplace');
  const categoriesDiv = document.getElementById('categories');
  const postsDiv = document.getElementById('posts');
  const btnAddPost = document.getElementById('btnAddPost');

  const postFormOverlay = document.getElementById('postFormOverlay');
  const closePostFormBtn = document.getElementById('closePostFormBtn');
  const postTitle = document.getElementById('postTitle');
  const postImageFile = document.getElementById('postImageFile');
  const postDescription = document.getElementById('postDescription');
  const postCategory = document.getElementById('postCategory');
  const postContact = document.getElementById('postContact');
  const postDelivery = document.getElementById('postDelivery');
  const btnSubmitPost = document.getElementById('btnSubmitPost');

  // --- ช่วยแสดงสถานะผู้ใช้ / หน้า login/register ---
  function showLogin() {
    loginPage.style.display = 'block';
    userPanel.style.display = 'none';
    marketplace.style.display = 'none';
  }
  function showMarketplace() {
    loginPage.style.display = 'none';
    userPanel.style.display = 'flex';
    marketplace.style.display = 'block';
  }

  // ----- สลับฟอร์ม login/register -----
  toggleLoginText.addEventListener('click', () => {
    if (loginForm.style.display !== 'none') {
      loginForm.style.display = 'none';
      registerForm.style.display = 'block';
      toggleLoginText.textContent = 'กลับไปหน้าเข้าสู่ระบบ';
    } else {
      loginForm.style.display = 'block';
      registerForm.style.display = 'none';
      toggleLoginText.textContent = 'สมัครสมาชิก';
    }
  });

  // --- ลงทะเบียน ---
  btnRegister.addEventListener('click', () => {
    const id = regId.value.trim();
    const pass = regPass.value;
    const phone = regPhone.value.trim();

    if (!/^\d{11}$/.test(id)) {
      alert('กรุณากรอกรหัสนิสิตให้ครบ 11 หลัก');
      return;
    }
    if (pass.length < 4) {
      alert('รหัสผ่านต้องอย่างน้อย 4 ตัวอักษร');
      return;
    }
    if (!/^\d{9,10}$/.test(phone)) {
      alert('กรุณากรอกเบอร์โทรศัพท์ให้ถูกต้อง');
      return;
    }
    if(users[id]){
      alert('รหัสนิสิตนี้ได้ลงทะเบียนแล้ว');
      return;
    }
    users[id] = { password: pass, phone };
    localStorage.setItem('users', JSON.stringify(users));
    alert('สมัครสมาชิกสำเร็จ! กรุณาเข้าสู่ระบบ');
    toggleLoginText.click();
    regId.value = '';
    regPass.value = '';
    regPhone.value = '';
  });

  // --- เข้าสู่ระบบ ---
  btnLogin.addEventListener('click', () => {
    const id = loginId.value.trim();
    const pass = loginPass.value;
    if(!users[id]) {
      alert('ไม่พบรหัสนิสิตนี้ในระบบ');
      return;
    }
    if(users[id].password !== pass){
      alert('รหัสผ่านไม่ถูกต้อง');
      return;
    }
    currentUserId = id;
    localStorage.setItem('currentUserId', currentUserId);
    loginId.value = '';
    loginPass.value = '';
    renderUI();
  });

  // --- ออกจากระบบ ---
  btnLogout.addEventListener('click', () => {
    currentUserId = '';
    localStorage.removeItem('currentUserId');
    renderUI();
  });

  // --- แสดง UI ตามสถานะล็อกอิน ---
  function renderUI() {
    if(currentUserId && users[currentUserId]) {
      showMarketplace();
      currentUserSpan.textContent = currentUserId;
      renderCategories();
      renderPosts();
    } else {
      showLogin();
    }
  }

  // --- แสดงหมวดหมู่ ---
  function renderCategories() {
    categoriesDiv.innerHTML = '';
    categoriesData.forEach(cat => {
      const div = document.createElement('div');
      div.className = 'category-card' + (cat.id === selectedCategory ? ' active' : '');
      div.innerHTML = `
        <img src="${cat.img}" alt="${cat.name}">
        <span>${cat.name}</span>
      `;
      div.addEventListener('click', () => {
        if(selectedCategory === cat.id) selectedCategory = '';
        else selectedCategory = cat.id;
        renderCategories();
        renderPosts();
      });
      categoriesDiv.appendChild(div);
    });
  }

  // --- แสดงโพสต์สินค้า ---
  function renderPosts() {
    postsDiv.innerHTML = '';

    let filteredPosts = posts;
    if(selectedCategory){
      filteredPosts = posts.filter(p => p.category === selectedCategory);
    }
    if(filteredPosts.length === 0) {
      postsDiv.innerHTML = `<p style="text-align:center; width:100%;">ไม่มีสินค้าในหมวดนี้</p>`;
      return;
    }
    filteredPosts.forEach((post, index) => {
      const card = document.createElement('div');
      card.className = 'post-card';
      card.innerHTML = `
        ${post.sold ? '<div class="sold-badge">ขายแล้ว</div>' : ''}
        <img src="${post.image}" alt="ภาพสินค้า" onerror="this.src='https://via.placeholder.com/260x160?text=ไม่มีรูปภาพ'"/>
        <div class="post-info">
          <div>
            <div class="post-title">${post.title}</div>
            <div class="post-category">หมวด: ${categoriesData.find(c=>c.id===post.category)?.name || '-'}</div>
            <div class="post-seller">เจ้าของ: ${post.owner}</div>
            <div class="post-contact">ติดต่อ: ${post.contact}</div>
            <div class="post-delivery">รับสินค้า: ${post.delivery}</div>
          </div>
          <div>
            ${post.owner === currentUserId && !post.sold ? `<button class="btn-sold" data-index="${index}">ขายแล้ว</button>` : ''}
            <button data-index="${index}" class="btn-comment">คอมเมนต์</button>
            <button data-index="${index}" class="btn-chat">แชท</button>
          </div>
        </div>
      `;
      postsDiv.appendChild(card);
    });

    // event ปุ่มขายแล้ว
    document.querySelectorAll('.btn-sold').forEach(btn => {
      btn.addEventListener('click', e => {
        const idx = +e.target.dataset.index;
        posts[idx].sold = true;
        localStorage.setItem('posts', JSON.stringify(posts));
        renderPosts();
      });
    });

    // event ปุ่มคอมเมนต์
    document.querySelectorAll('.btn-comment').forEach(btn => {
      btn.addEventListener('click', e => {
        const idx = +e.target.dataset.index;
        openComments(idx);
      });
    });

    // event ปุ่มแชท
    document.querySelectorAll('.btn-chat').forEach(btn => {
      btn.addEventListener('click', e => {
        const idx = +e.target.dataset.index;
        openChat(idx);
      });
    });
  }

  // --- ฟอร์มโพสต์สินค้า ---
  btnAddPost.addEventListener('click', () => {
    postFormOverlay.style.display = 'flex';
    postTitle.value = '';
    postImageFile.value = '';
    postDescription.value = '';
    postCategory.innerHTML = '';
    postContact.value = '';
    postDelivery.value = '';
    categoriesData.forEach(cat => {
      const opt = document.createElement('option');
      opt.value = cat.id;
      opt.textContent = cat.name;
      postCategory.appendChild(opt);
    });
  });

  closePostFormBtn.addEventListener('click', () => {
    postFormOverlay.style.display = 'none';
  });

  // --- ส่งโพสต์ใหม่ ---
  btnSubmitPost.addEventListener('click', () => {
    const title = postTitle.value.trim();
    const imageFile = postImageFile.files[0];
    const description = postDescription.value.trim();
    const category = postCategory.value;
    const contact = postContact.value.trim();
    const delivery = postDelivery.value.trim();

    if(!title || !imageFile || !category || !contact || !delivery){
      alert('กรุณากรอกข้อมูลทุกช่องและเลือกภาพสินค้า');
      return;
    }

    // อ่านไฟล์รูปภาพเป็น base64 เพื่อเก็บใน localStorage
    const reader = new FileReader();
    reader.onload = function(e){
      const base64Image = e.target.result;

      const newPost = {
        title,
        image: base64Image,
        description,
        category,
        contact,
        delivery,
        sold: false,
        owner: currentUserId,
        comments: [],
        chats: []
      };
      posts.push(newPost);
      localStorage.setItem('posts', JSON.stringify(posts));
      postFormOverlay.style.display = 'none';
      renderPosts();
      alert('โพสต์สินค้าสำเร็จ');
    };
    reader.readAsDataURL(imageFile);
  });

  // --- คอมเมนต์ ---
  function openComments(postIndex) {
    const post = posts[postIndex];
    // สร้าง div แสดงคอมเมนต์
    const container = document.createElement('div');
    container.className = 'comments-container';

    const title = document.createElement('h4');
    title.textContent = `คอมเมนต์: ${post.title}`;
    container.appendChild(title);

    // รายการคอมเมนต์
    const commentList = document.createElement('div');
    commentList.style.flexGrow = 1;
    commentList.style.overflowY = 'auto';
    commentList.style.maxHeight = '250px';
    container.appendChild(commentList);

    // input คอมเมนต์ใหม่
    const input = document.createElement('input');
    input.className = 'comment-input';
    input.placeholder = 'พิมพ์คอมเมนต์...';
    container.appendChild(input);

    // ปุ่มส่งคอมเมนต์
    input.addEventListener('keypress', e => {
      if(e.key === 'Enter' && input.value.trim() !== '') {
        const newComment = {
          user: currentUserId,
          text: input.value.trim(),
          time: new Date().toISOString()
        };
        post.comments.push(newComment);
        localStorage.setItem('posts', JSON.stringify(posts));
        input.value = '';
        renderComments();
      }
    });

    function renderComments(){
      commentList.innerHTML = '';
      if(post.comments.length === 0){
        commentList.innerHTML = '<p>ยังไม่มีคอมเมนต์</p>';
        return;
      }
      post.comments.forEach(c => {
        const div = document.createElement('div');
        div.className = 'comment-item';
        div.textContent = `${c.user}: ${c.text}`;
        commentList.appendChild(div);
      });
    }
    renderComments();

    // แสดง popup คอมเมนต์
    showPopup(container);
  }

  // --- แชทส่วนตัว (จำลอง) ---
  function openChat(postIndex) {
    const post = posts[postIndex];
    // ผู้ส่งและผู้รับ (currentUser และ owner post)
    if(post.owner === currentUserId){
      alert('ไม่สามารถแชทกับตัวเองได้');
      return;
    }

    const container = document.createElement('div');
    container.className = 'chat-container';

    const title = document.createElement('h4');
    title.textContent = `แชทกับเจ้าของสินค้า: ${post.owner}`;
    container.appendChild(title);

    // รายการแชท
    const chatList = document.createElement('div');
    chatList.style.flexGrow = 1;
    chatList.style.overflowY = 'auto';
    chatList.style.maxHeight = '250px';
    container.appendChild(chatList);

    // input แชท
    const input = document.createElement('input');
    input.className = 'chat-input';
    input.placeholder = 'พิมพ์ข้อความ...';
    container.appendChild(input);

    // โหลดแชทเดิม (mockup)
    function renderChats(){
      chatList.innerHTML = '';
      if(!post.chats) post.chats = [];
      if(post.chats.length === 0){
        chatList.innerHTML = '<p>ยังไม่มีข้อความ</p>';
        return;
      }
      post.chats.forEach(c => {
        const div = document.createElement('div');
        div.className = 'chat-message ' + (c.sender === currentUserId ? 'mine' : '');
        div.textContent = `${c.sender === currentUserId ? 'คุณ' : post.owner}: ${c.text}`;
        chatList.appendChild(div);
      });
      chatList.scrollTop = chatList.scrollHeight;
    }

    renderChats();

    // ส่งข้อความแชท
    input.addEventListener('keypress', e => {
      if(e.key === 'Enter' && input.value.trim() !== ''){
        if(!post.chats) post.chats = [];
        post.chats.push({ sender: currentUserId, text: input.value.trim(), time: new Date().toISOString() });
        localStorage.setItem('posts', JSON.stringify(posts));
        input.value = '';
        renderChats();
      }
    });

    showPopup(container);
  }

  // --- ฟังก์ชันแสดง popup ทั่วไป ---
  function showPopup(contentElement) {
    // สร้าง overlay ปิด popup ได้ถ้าคลิกด้านนอก
    const overlay = document.createElement('div');
    overlay.style.position = 'fixed';
    overlay.style.top = 0;
    overlay.style.left = 0;
    overlay.style.right = 0;
    overlay.style.bottom = 0;
    overlay.style.backgroundColor = 'rgba(0,0,0,0.5)';
    overlay.style.display = 'flex';
    overlay.style.justifyContent = 'center';
    overlay.style.alignItems = 'center';
    overlay.style.zIndex = 10000;

    // container popup
    const popup = document.createElement('div');
    popup.style.backgroundColor = '#fff';
    popup.style.borderRadius = '12px';
    popup.style.padding = '16px';
    popup.style.width = '400px';
    popup.style.maxHeight = '80vh';
    popup.style.overflowY = 'auto';
    popup.style.position = 'relative';
    popup.style.boxShadow = '0 0 20px rgba(0,0,0,0.3)';
    popup.appendChild(contentElement);

    // ปุ่มปิด
    const closeBtn = document.createElement('button');
    closeBtn.textContent = '×';
    closeBtn.style.position = 'absolute';
    closeBtn.style.top = '8px';
    closeBtn.style.right = '12px';
    closeBtn.style.fontSize = '22px';
    closeBtn.style.background = 'transparent';
    closeBtn.style.border = 'none';
    closeBtn.style.cursor = 'pointer';
    closeBtn.style.color = '#333';
    closeBtn.addEventListener('click', () => document.body.removeChild(overlay));
    popup.appendChild(closeBtn);

    overlay.appendChild(popup);

    overlay.addEventListener('click', e => {
      if(e.target === overlay){
        document.body.removeChild(overlay);
      }
    });

    document.body.appendChild(overlay);
  }

  // --- เริ่มต้นระบบ ---
  renderUI();
</script>

</body>
</html>

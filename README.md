<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Galeri Refalina 💖</title>
  <style>
    /* GENERAL */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Poppins', sans-serif;
    }
    body {
      background: #fff6fa;
      color: #333;
      display: flex;
      min-height: 100vh;
      transition: background 0.4s, color 0.4s;
    }
    body.dark {
      background: #1b1b1b;
      color: #f5f5f5;
    }

    /* SIDEBAR */
    .sidebar {
      position: fixed;
      top: 0;
      left: 0;
      width: 220px;
      height: 100vh;
      background: #ffffff;
      padding: 30px 20px;
      border-radius: 0 20px 20px 0;
      box-shadow: 4px 0 20px rgba(0, 0, 0, 0.06);
      display: flex;
      flex-direction: column;
      gap: 25px;
      z-index: 999;
    }
    .sidebar h2 {
      font-size: 20px;
      color: #ff7fa5;
      display: flex;
      align-items: center;
      gap: 8px;
    }
    .sidebar h2 img {
      width: 24px;
      height: 24px;
    }
    .menu {
      display: flex;
      flex-direction: column;
      gap: 10px;
    }
    .menu button {
      background: none;
      border: none;
      text-align: left;
      font-size: 16px;
      padding: 10px;
      border-radius: 10px;
      color: #555;
      cursor: pointer;
      transition: all 0.3s;
    }
    .menu button:hover,
    .menu button.active {
      background: #ffe4ef;
      color: #ff7fa5;
      font-weight: 600;
    }

    /* CONTENT */
    .content {
      flex: 1;
      margin-left: 220px;
      padding: 40px;
      transition: 0.3s;
    }
    .gallery {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
      gap: 16px;
      animation: fadeIn 0.4s ease-in-out;
    }
    .gallery.hidden { display: none; }
    .gallery img,
    video {
      width: 100%;
      border-radius: 15px;
      object-fit: cover;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
      transition: transform 0.3s ease;
    }
    .gallery img:hover,
    video:hover {
      transform: scale(1.04);
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }

    /* PROFILE BUTTON */
    .profile-btn {
      position: fixed;
      top: 20px;
      right: 25px;
      background: #ffffff;
      border: none;
      border-radius: 50%;
      width: 50px;
      height: 50px;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
      cursor: pointer;
      transition: all 0.3s;
      z-index: 1000;
    }
    .profile-btn:hover {
      transform: scale(1.08);
    }
    .profile-btn img {
      width: 26px;
      height: 26px;
    }

    /* DROPDOWN MENU */
    .profile-dropdown {
      position: fixed;
      top: 80px;
      right: 25px;
      background: #fff;
      border-radius: 12px;
      box-shadow: 0 6px 20px rgba(0, 0, 0, 0.15);
      padding: 10px 0;
      display: none;
      flex-direction: column;
      z-index: 1001;
      overflow: hidden;
    }
    .profile-dropdown button {
      background: none;
      border: none;
      padding: 12px 20px;
      text-align: left;
      font-size: 15px;
      color: #333;
      display: flex;
      align-items: center;
      gap: 10px;
      cursor: pointer;
      width: 180px;
      transition: 0.3s;
    }
    .profile-dropdown button:hover {
      background: #ffe4ef;
      color: #ff7fa5;
    }
    .profile-dropdown img {
      width: 20px;
      height: 20px;
    }

    /* DARK MODE */
    body.dark .sidebar { background: #2b2b2b; }
    body.dark .menu button { color: #ccc; }
    body.dark .menu button.active,
    body.dark .menu button:hover { background: #ff99bb22; color: #ff99bb; }
    body.dark .profile-btn { background: #2b2b2b; }
    body.dark .profile-dropdown { background: #2b2b2b; }
    body.dark .profile-dropdown button { color: #f2f2f2; }
    body.dark .profile-dropdown button:hover { background: #ff99bb; color: #fff; }

    /* RESPONSIVE */
    @media (max-width: 768px) {
      .sidebar {
        width: 180px;
        padding: 20px;
      }
      .content {
        margin-left: 180px;
        padding: 25px;
      }
      .profile-btn {
        width: 44px;
        height: 44px;
      }
    }

    @media (max-width: 600px) {
      .sidebar {
        position: fixed;
        width: 100%;
        height: auto;
        flex-direction: row;
        justify-content: space-around;
        border-radius: 0;
        box-shadow: 0 4px 15px rgba(0,0,0,0.1);
      }
      .content {
        margin-left: 0;
        margin-top: 100px;
      }
    }
  </style>
</head>
<body>

  <!-- SIDEBAR -->
  <div class="sidebar">
    <h2><img src="https://cdn-icons-png.flaticon.com/512/1041/1041916.png" alt="">Galeri</h2>
    <div class="menu">
      <button class="active" onclick="showGallery('foto', this)">📸 Foto</button>
      <button onclick="showGallery('video', this)">🎥 Video</button>
      <button onclick="showGallery('audio', this)">🎵 Audio</button>
    </div>
  </div>

  <!-- PROFILE BUTTON -->
  <button class="profile-btn" onclick="toggleProfile()">
    <img src="https://cdn-icons-png.flaticon.com/512/25/25231.png" alt="profil">
  </button>

  <!-- DROPDOWN -->
  <div class="profile-dropdown" id="profileDropdown">
    <button onclick="toggleTheme()">
      <img id="themeIcon" src="https://cdn-icons-png.flaticon.com/512/6714/6714978.png" alt="tema">
      Ganti Tema
    </button>
    <button onclick="logout()">
      <img src="https://cdn-icons-png.flaticon.com/512/992/992680.png" alt="keluar">
      Keluar
    </button>
  </div>

  <!-- CONTENT -->
  <div class="content">
    <div id="foto" class="gallery">
      <img src="images/1.jpg" alt="">
      <img src="images/2.jpg" alt="">
      <img src="images/3.jpg" alt="">
      <img src="images/4.jpg" alt="">
      <img src="images/5.jpg" alt="">
      <img src="images/6.jpg" alt="">
      <img src="images/7.jpg" alt="">
      <img src="images/8.jpg" alt="">
      <img src="images/9.jpg" alt="">
      <img src="images/10.jpg" alt="">
      <img src="images/11.jpg" alt="">
      <img src="images/12.jpg" alt="">
    </div>

    <div id="video" class="gallery hidden">
      <video controls poster="https://via.placeholder.com/800x500?text=Video+Refalina">
        <source src="video/video.mp4" type="video/mp4">
      </video>
    </div>

    <div id="audio" class="gallery hidden">
      <audio controls>
        <source src="audio/audio.mp3" type="audio/mpeg">
      </audio>
    </div>
  </div>

  <script>
    function showGallery(type, el) {
      document.querySelectorAll('.gallery').forEach(g => g.classList.add('hidden'));
      document.getElementById(type).classList.remove('hidden');
      document.querySelectorAll('.menu button').forEach(b => b.classList.remove('active'));
      el.classList.add('active');
    }

    function toggleProfile() {
      const dropdown = document.getElementById('profileDropdown');
      dropdown.style.display = dropdown.style.display === 'flex' ? 'none' : 'flex';
    }

    function toggleTheme() {
      document.body.classList.toggle('dark');
      const icon = document.getElementById('themeIcon');
      icon.src = document.body.classList.contains('dark')
        ? "https://cdn-icons-png.flaticon.com/512/6714/6714977.png"
        : "https://cdn-icons-png.flaticon.com/512/6714/6714978.png";
    }

    function logout() {
      alert('Kamu telah keluar 💖');
    }
  </script>

</body>
</html>

<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Galeri Refalina</title>
  <style>
    /* GENERAL */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Poppins', sans-serif;
    }
    body {
      background: #ffeef6;
      color: #333;
      display: flex;
      min-height: 100vh;
      transition: 0.4s;
    }
    body.dark {
      background: #1e1e1e;
      color: #f2f2f2;
    }

    /* SIDEBAR */
    .sidebar {
      position: fixed;
      left: 0;
      top: 0;
      height: 100vh;
      width: 220px;
      background: #fff;
      padding: 30px 20px;
      display: flex;
      flex-direction: column;
      gap: 20px;
      box-shadow: 4px 0 20px rgba(0,0,0,0.08);
      border-radius: 0 20px 20px 0;
      z-index: 500;
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
    .menu button {
      background: none;
      border: none;
      text-align: left;
      font-size: 16px;
      padding: 10px 0;
      cursor: pointer;
      color: #555;
      transition: 0.3s;
    }
    .menu button:hover,
    .menu button.active {
      color: #ff7fa5;
      font-weight: 600;
    }

    /* CONTENT */
    .content {
      margin-left: 220px;
      padding: 40px;
      flex: 1;
    }
    .gallery {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
      gap: 15px;
    }
    .gallery.hidden { display: none; }
    .gallery img,
    video {
      width: 100%;
      height: auto;
      border-radius: 15px;
      box-shadow: 0 4px 15px rgba(0,0,0,0.08);
      transition: 0.3s;
    }
    .gallery img:hover,
    video:hover { transform: scale(1.03); }

    /* PROFILE BUTTON */
    .profile-btn {
      position: fixed;
      top: 20px;
      right: 25px;
      background: #fff;
      border: none;
      border-radius: 50%;
      width: 48px;
      height: 48px;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 2px 10px rgba(0,0,0,0.1);
      cursor: pointer;
      transition: 0.3s;
      z-index: 999;
    }
    .profile-btn:hover { transform: scale(1.05); }
    .profile-btn img { width: 26px; height: 26px; }

    /* DROPDOWN */
    .profile-dropdown {
      position: fixed;
      top: 80px;
      right: 25px;
      background: #fff;
      border-radius: 12px;
      box-shadow: 0 6px 20px rgba(0,0,0,0.15);
      padding: 10px 0;
      display: none;
      flex-direction: column;
      z-index: 999;
    }
    .profile-dropdown button {
      background: none;
      border: none;
      padding: 10px 20px;
      text-align: left;
      font-size: 15px;
      color: #333;
      display: flex;
      align-items: center;
      gap: 10px;
      cursor: pointer;
      transition: 0.3s;
      width: 180px;
    }
    .profile-dropdown button:hover {
      background: #ffeef6;
      color: #ff7fa5;
    }
    .profile-dropdown img { width: 20px; height: 20px; }

    /* DARK MODE */
    body.dark .sidebar { background: #2a2a2a; }
    body.dark .menu button { color: #ddd; }
    body.dark .menu button:hover,
    body.dark .menu button.active { color: #ff99bb; }
    body.dark .profile-btn { background: #2a2a2a; }
    body.dark .profile-dropdown { background: #2a2a2a; }
    body.dark .profile-dropdown button { color: #f2f2f2; }
    body.dark .profile-dropdown button:hover { background: #ff99bb; color: #fff; }

    /* RESPONSIVE */
    @media (max-width:768px){
      .sidebar { width: 180px; }
      .content { margin-left: 180px; padding: 25px; }
      .profile-btn { width: 42px; height: 42px; }
    }
  </style>
</head>
<body>

  <!-- SIDEBAR -->
  <div class="sidebar">
    <h2>
      <img src="https://cdn-icons-png.flaticon.com/512/1041/1041916.png" alt="">
      Galeri
    </h2>
    <div class="menu">
      <button class="active" onclick="showGallery('foto', this)">📸 Foto</button>
      <button onclick="showGallery('video', this)">🎥 Video</button>
      <button onclick="showGallery('audio', this)">🎵 Audio</button>
    </div>
  </div>

  <!-- PROFILE ICON -->
  <button class="profile-btn" onclick="toggleProfile()">
    <img src="https://cdn-icons-png.flaticon.com/512/581/581601.png" alt="mode">
  </button>

  <div class="profile-dropdown" id="profileDropdown">
    <button onclick="switchTheme('dark')">
      <img src="https://cdn-icons-png.flaticon.com/512/6714/6714978.png" alt="tema">
      Ganti Tema
    </button>
    <button onclick="alert('Keluar berhasil!')">
      <img src="https://cdn-icons-png.flaticon.com/512/992/992680.png" alt="keluar">
      Keluar
    </button>
  </div>

  <!-- CONTENT -->
  <div class="content">
    <!-- FOTO -->
    <div id="foto" class="gallery">
      <img src="images/1.jpg" alt="Refalina 1">
      <img src="images/2.jpg" alt="Refalina 2">
      <img src="images/3.jpg" alt="Refalina 3">
      <img src="images/4.jpg" alt="Refalina 4">
      <img src="images/5.jpg" alt="Refalina 5">
      <img src="images/6.jpg" alt="Refalina 6">
      <img src="images/7.jpg" alt="Refalina 7">
      <img src="images/8.jpg" alt="Refalina 8">
      <img src="images/9.jpg" alt="Refalina 9">
      <img src="images/10.jpg" alt="Refalina 10">
      <img src="images/11.jpg" alt="Refalina 11">
      <img src="images/12.jpg" alt="Refalina 12">
    </div>

    <!-- VIDEO -->
    <div id="video" class="gallery hidden">
      <video controls poster="https://via.placeholder.com/800x500?text=Video+Refalina">
        <source src="video/video.mp4" type="video/mp4">
      </video>
    </div>

    <!-- AUDIO -->
    <div id="audio" class="gallery hidden">
      <audio controls>
        <source src="audio/audio.mp3" type="audio/mpeg">
      </audio>
    </div>
  </div>

  <script>
    function showGallery(type, el){
      document.querySelectorAll('.gallery').forEach(g => g.classList.add('hidden'));
      document.getElementById(type).classList.remove('hidden');
      document.querySelectorAll('.menu button').forEach(b => b.classList.remove('active'));
      el.classList.add('active');
    }

    function toggleProfile(){
      const d = document.getElementById('profileDropdown');
      d.style.display = (d.style.display === 'flex' ? 'none' : 'flex');
    }

    function switchTheme(theme){
      if(theme === 'dark') document.body.classList.toggle('dark');
    }
  </script>
</body>
</html>

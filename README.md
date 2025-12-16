<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>tcup's archive</title>

  <style>
    html { scroll-behavior: smooth; }

    body { 
      background-color: #000; 
      color: #0099ff; 
      font-family: "Courier New", Courier, monospace; 
      margin: 0; 
      font-size: 20px; 
      text-shadow: 0 0 6px rgba(0,153,255,0.6); 
      overflow-x: hidden; 
    }

    a { 
      color: #0066cc; 
      text-decoration: none; 
      transition: 0.3s; 
    }

    a:hover { 
      text-shadow: 0 0 10px #0099ff; 
      color: #66ccff; 
    }

    header { 
      text-align: center; 
      padding: 30px 10px; 
      border-bottom: 2px solid #c0c0c0; 
    }

    header h1 { 
      margin: 0; 
      font-size: 48px; 
      letter-spacing: 2px; 
      text-shadow: 0 0 8px #0099ff; 
    }

    .cursor::after { 
      content: "_"; 
      animation: blinkPulse 1s steps(2, start) infinite; 
    }

    @keyframes blinkPulse { 
      0%,50%,100% { opacity: 1; } 
      25%,75% { opacity: 0.3; } 
    }

    .profile-pic { 
      width: 100px; 
      height: 100px; 
      border-radius: 50%; 
      border: 3px solid #c0c0c0; 
      box-shadow: 0 0 12px #c0c0c0; 
      object-fit: cover; 
      display: block; 
      margin: 0 auto 15px; 
    }

    nav { 
      text-align: center; 
      padding: 10px; 
      background: #050505; 
      border-bottom: 2px solid #c0c0c0; 
    }

    nav a { margin: 0 12px; }

    .container { 
      max-width: 900px; 
      margin: auto; 
      padding: 20px; 
    }

    .window { 
      border: 2px solid #c0c0c0; 
      padding: 15px; 
      margin-bottom: 25px; 
      background: #030303; 
      transition: 0.3s; 
    }

    .window:hover { 
      box-shadow: 0 0 15px #c0c0c0; 
      border-color: #ffffff; 
    }

    .window h2 { 
      margin-top: 0; 
      border-bottom: 1px dashed #c0c0c0; 
      padding-bottom: 5px; 
    }

    .status { color: #66ccff; }

    /* Backlog */
    ul.timeline { 
      list-style: none; 
      padding: 0; 
      display: flex; 
      flex-wrap: wrap; 
      max-height: 500px; 
      overflow: hidden; 
      transition: max-height 0.5s ease; 
    }

    ul.timeline.expanded { max-height: 5000px; }

    ul.timeline li { 
      width: 45%; 
      margin: 6px 2.5%; 
      display: flex; 
      align-items: center; 
    }

    .game-cover { 
      width: 40px; 
      height: 40px; 
      object-fit: cover; 
      margin-right: 8px; 
      border-radius: 4px; 
      box-shadow: 0 0 4px #c0c0c0; 
    }

    .view-more-btn { 
      display: block; 
      margin: 10px auto; 
      padding: 8px 16px; 
      background: linear-gradient(to right, #c0c0c0, #ffffff); 
      color: #000; 
      font-weight: bold; 
      border: 1px solid #999; 
      border-radius: 4px; 
      cursor: pointer; 
    }

    /* Vertical timeline */
    .timeline-vertical { 
      position: relative; 
      margin-left: 30px; 
      padding-left: 20px; 
    }

    .timeline-vertical::before { 
      content: ""; 
      position: absolute; 
      left: 0; 
      top: 0; 
      width: 2px; 
      height: 100%; 
      background: linear-gradient(#0099ff, #66ccff, #0099ff); 
    }

    .timeline-item { 
      position: relative; 
      margin-bottom: 35px; 
    }

    .timeline-dot { 
      position: absolute; 
      left: -11px; 
      top: 0; 
      width: 18px; 
      height: 18px; 
      border-radius: 50%; 
      background: #c0c0c0; 
      box-shadow: 0 0 10px #c0c0c0; 
    }

    footer { 
      text-align: center; 
      padding: 20px; 
      border-top: 4px solid #c0c0c0; 
      color: #66ccff; 
    }

    /* Loading screen */
    #loading-screen { 
      position: fixed; 
      inset: 0; 
      background: #000; 
      display: flex; 
      align-items: center; 
      justify-content: center; 
      font-size: 36px; 
      z-index: 9999; 
    }
  </style>
</head>

<body>

<div id="loading-screen">loading_</div>

<header>
  <img src="./pfp.png" alt="tcup" class="profile-pic">
  <h1 class="cursor">tcup's archive</h1>
</header>

<nav>
  <a href="#about">about</a>
  <a href="#backlog">backlog</a>
  <a href="#nextup">next up</a>
  <a href="#photos">photos</a>
  <a href="#updates">updates</a>
</nav>

<div class="container">

  <div class="window" id="about">
    <h2>about me</h2>
    <p>i play video games sometimes lol.</p>
  </div>

  <div class="window" id="backlog">
    <h2>video game backlog</h2>

    <ul class="timeline" id="backlog-list">
      <li><img class="game-cover" src="./images/fallout4.png">Fallout 4</li>
      <li><img class="game-cover" src="./images/fnv.png">Fallout: New Vegas</li>
      <li><img class="game-cover" src="./images/acecombat5.png">Ace Combat 5</li>
      <li><img class="game-cover" src="./images/rdr.png">Red Dead Redemption</li>
      <li><img class="game-cover" src="./images/silenthill.png">Silent Hill</li>
      <li><img class="game-cover" src="./images/smbgalaxy.png">Super Mario Galaxy</li>
    </ul>

    <button class="view-more-btn" id="view-more-btn">View More</button>
  </div>

</div>

<footer>
  © tcup • hosted on GitHub Pages
</footer>

<script>
window.addEventListener("load", () => {
  const loader = document.getElementById("loading-screen");
  setTimeout(() => loader.remove(), 1000);

  const btn = document.getElementById("view-more-btn");
  const list = document.getElementById("backlog-list");

  btn.addEventListener("click", () => {
    list.classList.toggle("expanded");
    btn.textContent = list.classList.contains("expanded")
      ? "View Less"
      : "View More";
  });
});
</script>

</body>
</html>

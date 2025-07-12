# Loja-Qifte
Loja Per Qifte
<!DOCTYPE html>
<html lang="sq">
<head>
  <meta charset="UTF-8">
  <title>Lojë për Çifte ❤️‍🔥</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body { font-family: sans-serif; text-align: center; background: #111; color: #fff; padding: 40px; }
    input { padding: 10px; margin: 5px; font-size: 16px; border-radius: 5px; border: none; }
    button { padding: 15px 30px; margin: 10px; font-size: 18px; border: none; border-radius: 10px; cursor: pointer; }
    .truth { background-color: #3498db; color: white; }
    .dare { background-color: #e74c3c; color: white; }
    .level { background-color: #2ecc71; color: white; }
    .box { margin-top: 30px; font-size: 24px; min-height: 100px; }
  </style>
</head>
<body>
  <h1>Lojë për Çifte 🔥</h1>

  <div id="nameInput">
    <p>Shkruani emrat:</p>
    <input type="text" id="player1" placeholder="Lojtari 1">
    <input type="text" id="player2" placeholder="Lojtari 2"><br>
    <button onclick="startGame()">Fillo</button>
  </div>

  <div id="game" style="display:none;">
    <p>Zgjidhni nivelin:</p>
    <button class="level" onclick="setLevel('normal')">Normal</button>
    <button class="level" onclick="setLevel('nxehtë')">Nxehtë</button>
    <button class="level" onclick="setLevel('ekstrem')">Ekstrem</button><br><br>

    <p id="turnLabel"></p>
    <button class="truth" onclick="showQuestion('truth')">E Vërtetë</button>
    <button class="dare" onclick="showQuestion('dare')">Guxim</button>
    <div class="box" id="output"></div>
  </div>

  <script>
    let players = [], currentPlayer = 0, level = 'normal';
    const questions = {
      normal: {
        truth: ["A ke pasur ndjenjë për kë do tjetër?", "Cila pjesë e trupit të partnerit të pëlqen më shumë?", "A mban sekret nga partneri?", "Cili është miku yt më i mirë?", "A ke qarë rishtazi?", "Cili është kujtimi yt më i bukur me partnerin?"],
        dare: ["Puth partnerin në faqe.", "Thuaj diçka të ëmbël në veshin e partnerit.", "Jep një kompliment të sinqertë.", "Kërce 20 sekonda duke e mbajtur për dore.", "Shiko partnerin në sy për 20 sekonda.", "Kalo gishtat nëpër flokët e partnerit për 30 sekonda."]
      },
      nxehtë: {
        truth: ["Cila është fantazia jote më e ndezshme?", "A të pëlqen kur partneri të merr iniciativën?", "Cili pozicion të ndez më shumë?", "Kur ishte hera e fundit që ishe tërësisht i/e ndezur?", "A ke provuar roleplay?", "Do të provonit ndonjë vend të çuditshëm për seks?"],
        dare: ["Puth ku të dojë partneri.", "Zhvishe një pjesë të rrobave (deri ku je rehat).", "Përshkruaj një fantazi që do ndodhte sonte.", "Bëj një masazh për një minutë.", "Puth qafën për 10 sekonda.", "Thuaj zërim se çfarë do nga partneri në shtrat."]
      },
      ekstrem: {
        truth: ["A ke menduar ndonjëherë për tresh?", "A ke bërë ndonjëherë seks në vend publik?", "Cili pozicion más ekstrem ke provuar?", "A ke përdorur lodër seksi?", "Të pëlqen të dominohesh apo të dominosh?", "Ku është vendi më i çuditshëm që ke bërë seks?"],
        dare: ["Bëj një striptizë të shkurtër.", "Vendos partnerin të rrijë mbi ty për 10 sekonda.", "Përshkruaj me detaje një ëndërr erotike.", "Zbulo një pjesë të trupit që zakonisht s’e zbuloje.", "Vendos pozicion seksi dhe ndal për 20 sekonda.", "Luaj me gishtat në trup për 30 sekonda."]
      }
    };

    function startGame() {
      const p1 = document.getElementById("player1").value.trim();
      const p2 = document.getElementById("player2").value.trim();
      if (!p1 || !p2) return alert("Vendosni emrat e dy lojtarëve!");
      players = [p1,p2];
      document.getElementById("nameInput").style.display="none";
      document.getElementById("game").style.display="block";
      updateTurn();
    }

    function setLevel(l) {
      level = l;
      document.getElementById("output").innerText = "Niveli: "+l.toUpperCase();
    }

    function updateTurn() {
      document.getElementById("turnLabel").innerText = "Rradha e: " + players[currentPlayer];
    }

    function showQuestion(type) {
      const arr = questions[level][type];
      document.getElementById("output").innerText = arr[Math.floor(Math.random()*arr.length)];
      currentPlayer = 1-currentPlayer;
      updateTurn();
    }
  </script>
</body>
</html>

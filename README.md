<!DOCTYPE html>
<html>
<head>
  <title>ToadBerds Cat Roller</title>
  <style>
    body {
      background-color: #ffffff;
    }
    img {
      border-radius: 8px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      /* align-items: center; */ /* Remove this, not needed for images */
      display: block;
      margin-left: auto;
      margin-right: auto;
    }
  </style>
</head>
<body style="text-align:center; font-family:sans-serif; background:#f0f0f0; padding:50px;">

  <h1>Roll for Cats</h1>

  <input id="nameInput" type="text" placeholder="Your name">
  <button onclick="rollCat()">Roll</button>

  <div style="margin-top:20px;">
    <img id="catImage" src="" alt="Your cat will appear here" style="max-width:300px; display:none;">
  </div>

  <script>
    function rollCat() {
      const name = document.getElementById("nameInput").value.trim();
      if (!name) {
        alert("Please enter your name.");
        return;
      }

      fetch("https://api.thecatapi.com/v1/images/search")
        .then(res => res.json())
        .then(data => {
          const img = document.getElementById("catImage");
          img.src = data[0].url;
          img.style.display = "block";
        })
        .catch(() => alert("Could not load a cat."));
    }
  </script>

</body>
</html>

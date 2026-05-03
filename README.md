# MARKFASHION
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Mark Fashion</title>
  <style>
    body {
      margin: 0;
      font-family: Arial;
      background: #0d0d0d;
      color: white;
    }
    header {
      padding: 15px;
      text-align: center;
      background: black;
      font-size: 24px;
      font-weight: bold;
    }
    .container {
      display: flex;
      padding: 20px;
      gap: 20px;
    }
    .tshirt {
      width: 50%;
    }
    .tshirt img {
      width: 100%;
    }
    .controls {
      width: 50%;
    }
    input, button {
      padding: 10px;
      margin: 10px 0;
      width: 100%;
    }
    canvas {
      background: white;
      margin-top: 10px;
    }
  </style>
</head>
<body>

<header>🔥 Mark Fashion - Custom T-Shirts</header>

<div class="container">
  <div class="tshirt">
    <img src="https://i.imgur.com/3ZQ3Z4H.png" alt="T-shirt">
    <canvas id="canvas" width="300" height="400"></canvas>
  </div>

  <div class="controls">
    <h3>Customize Your T-Shirt</h3>

    <input type="text" id="textInput" placeholder="Enter text">

    <input type="file" id="imageInput">

    <button onclick="addText()">Add Text</button>
    <button onclick="addImage()">Add Image</button>
  </div>
</div>

<script>
  const canvas = document.getElementById("canvas");
  const ctx = canvas.getContext("2d");

  function addText() {
    const text = document.getElementById("textInput").value;
    ctx.font = "20px Arial";
    ctx.fillStyle = "black";
    ctx.fillText(text, 50, 50);
  }

  function addImage() {
    const file = document.getElementById("imageInput").files[0];
    const reader = new FileReader();

    reader.onload = function(event) {
      const img = new Image();
      img.onload = function() {
        ctx.drawImage(img, 50, 80, 150, 150);
      }
      img.src = event.target.result;
    }

    reader.readAsDataURL(file);
  }
</script>

</body>
</html>

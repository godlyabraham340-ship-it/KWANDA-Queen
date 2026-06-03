<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Kwanda Queen</title>
  <style>
    body {
      font-family: Arial;
      background: #111;
      color: white;
      text-align: center;
      margin: 0;
      padding: 0;
    }

    header {
      background: purple;
      padding: 15px;
      font-size: 24px;
      font-weight: bold;
    }

    .container {
      padding: 20px;
    }

    input, button, textarea {
      margin: 10px;
      padding: 10px;
      width: 80%;
      max-width: 400px;
    }

    button {
      background: purple;
      color: white;
      border: none;
      cursor: pointer;
    }

    .box {
      background: #222;
      margin: 15px auto;
      padding: 15px;
      width: 90%;
      max-width: 500px;
      border-radius: 10px;
    }

    a {
      color: cyan;
    }
  </style>
</head>
<body>

<header>
  👑 Kwanda Queen Platform
</header>

<div class="container">

  <!-- UPLOAD -->
  <div class="box">
    <h2>📤 Upload File</h2>
    <input type="file" id="fileInput">
    <button onclick="uploadFile()">Upload</button>
    <p id="uploadMsg"></p>
  </div>

  <!-- DOWNLOAD -->
  <div class="box">
    <h2>📥 Download File</h2>
    <p id="fileList"></p>
  </div>

  <!-- COMMENTS -->
  <div class="box">
    <h2>💬 Comments</h2>
    <textarea id="comment" placeholder="Andika igitekerezo..."></textarea><br>
    <button onclick="addComment()">Send</button>
    <div id="comments"></div>
  </div>

</div>

<script>
  let files = [];
  let comments = [];

  function uploadFile() {
    let fileInput = document.getElementById("fileInput");
    if (fileInput.files.length === 0) {
      alert("Hitamo file!");
      return;
    }

    let file = fileInput.files[0];
    files.push(file.name);

    document.getElementById("uploadMsg").innerText =
      "Uploaded: " + file.name;

    showFiles();
  }

  function showFiles() {
    let list = document.getElementById("fileList");
    list.innerHTML = "";

    files.forEach((f, index) => {
      list.innerHTML += `
        <p>
          📄 ${f} 
          <a href="#">Download</a>
        </p>
      `;
    });
  }

  function addComment() {
    let c = document.getElementById("comment").value;
    if (c === "") return;

    comments.push(c);
    document.getElementById("comment").value = "";

    showComments();
  }

  function showComments() {
    let div = document.getElementById("comments");
    div.innerHTML = "";

    comments.forEach(c => {
      div.innerHTML += "<p>💬 " + c + "</p>";
    });
  }
</script>

</body>
</html>

# index.html-
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>رفع وتحميل ملفات</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f9f9f9;
      padding: 20px;
      text-align: center;
    }

    h2 {
      color: #2d89ef;
    }

    .upload-section {
      background: #fff;
      padding: 20px;
      margin: 20px auto;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.1);
      max-width: 500px;
    }

    input[type="file"] {
      margin: 10px 0;
    }

    ul {
      list-style-type: none;
      padding: 0;
    }

    li {
      background: #e7f0fd;
      margin: 5px 0;
      padding: 10px;
      border-radius: 6px;
    }

    a.download-link {
      text-decoration: none;
      color: #2d89ef;
    }

    .footer {
      margin-top: 40px;
      color: #444;
    }
  </style>
</head>
<body>

  <h1>📁 ملفات الأستاذ</h1>
  <div class="upload-section">
    <h2>🔼 رفع ملف PDF أو Word</h2>
    <input type="file" id="fileInput" accept=".pdf,.doc,.docx" />
    <button onclick="uploadFile()">رفع الملف</button>

    <h2>⬇️ الملفات المرفوعة:</h2>
    <ul id="fileList"></ul>
  </div>

  <div class="footer">💬 لا تنسونا من جميل الدعاء</div>

  <script>
    const fileList = document.getElementById('fileList');

    function uploadFile() {
      const input = document.getElementById('fileInput');
      const file = input.files[0];
      if (!file) return alert("يرجى اختيار ملف أولاً.");

      const reader = new FileReader();
      reader.onload = function(e) {
        const li = document.createElement('li');
        const a = document.createElement('a');
        a.href = e.target.result;
        a.download = file.name;
        a.className = 'download-link';
        a.textContent = '📥 ' + file.name;
        li.appendChild(a);
        fileList.appendChild(li);
      };
      reader.readAsDataURL(file);
    }
  </script>

</body>
</html>

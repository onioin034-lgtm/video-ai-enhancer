<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>MDL Video AI</title>

<style>
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    min-height: 100vh;
    font-family: Arial, sans-serif;
    background: #0b0b0f;
    color: white;
    display: flex;
    justify-content: center;
    padding: 25px 12px;
}

.container {
    width: 100%;
    max-width: 700px;
}

h1 {
    text-align: center;
    font-size: 34px;
    margin-bottom: 8px;
}

.subtitle {
    text-align: center;
    color: #aaa;
    margin-bottom: 25px;
}

.card {
    background: #15151c;
    border: 1px solid #292936;
    border-radius: 20px;
    padding: 20px;
    margin-bottom: 18px;
}

.upload {
    border: 2px dashed #555;
    border-radius: 15px;
    padding: 35px 15px;
    text-align: center;
    cursor: pointer;
}

.upload:hover {
    border-color: white;
}

input[type="file"] {
    display: none;
}

button, select {
    width: 100%;
    padding: 15px;
    border-radius: 12px;
    border: none;
    margin-top: 12px;
    font-size: 16px;
}

select {
    background: #22222b;
    color: white;
}

button {
    background: white;
    color: black;
    font-weight: bold;
    cursor: pointer;
}

button:hover {
    opacity: .85;
}

video {
    width: 100%;
    border-radius: 14px;
    margin-top: 15px;
    display: none;
}

.progress {
    height: 12px;
    background: #292936;
    border-radius: 20px;
    overflow: hidden;
    margin-top: 15px;
    display: none;
}

.bar {
    height: 100%;
    width: 0%;
    background: white;
    transition: width .3s;
}

.status {
    text-align: center;
    margin-top: 10px;
    color: #aaa;
}
</style>
</head>

<body>

<div class="container">

<h1>🚀 MDL Video AI</h1>
<div class="subtitle">تحسين جودة الفيديو من المتصفح</div>

<div class="card">

<label class="upload">
    🎥
    <br><br>
    اضغط هنا لاختيار الفيديو
    <input type="file" id="videoInput" accept="video/*">
</label>

<video id="preview" controls></video>

</div>

<div class="card">

<label>دقة الفيديو</label>

<select id="quality">
    <option value="1080">1080p Full HD</option>
    <option value="1440">2K</option>
    <option value="2160">4K</option>
</select>

<label style="display:block;margin-top:18px;">
    مستوى التحسين
</label>

<select id="enhance">
    <option value="1">خفيف</option>
    <option value="2">متوسط</option>
    <option value="3">قوي</option>
</select>

<button onclick="startEnhancement()">
    ✨ تحسين الفيديو
</button>

<div class="progress" id="progress">
    <div class="bar" id="bar"></div>
</div>

<div class="status" id="status">
    جاهز
</div>

</div>

</div>

<script>

const videoInput = document.getElementById("videoInput");
const preview = document.getElementById("preview");
const statusText = document.getElementById("status");
const progress = document.getElementById("progress");
const bar = document.getElementById("bar");

videoInput.addEventListener("change", function() {

    const file = this.files[0];

    if (!file) return;

    const url = URL.createObjectURL(file);

    preview.src = url;
    preview.style.display = "block";

    statusText.textContent = "تم اختيار الفيديو ✅";
});

function startEnhancement() {

    if (!videoInput.files.length) {
        alert("اختر فيديو أولاً 🎥");
        return;
    }

    progress.style.display = "block";
    bar.style.width = "0%";

    let value = 0;

    statusText.textContent = "جاري تجهيز الفيديو...";

    const timer = setInterval(() => {

        value += 5;

        bar.style.width = value + "%";

        if (value >= 100) {

            clearInterval(timer);

            statusText.textContent =
                "تم تجهيز المعالجة ✅ — الخطوة التالية هي إضافة محرك AI الحقيقي";

        }

    }, 150);

}

</script>

</body>
</html>

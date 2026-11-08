
<!DOCTYPE html>
<html lang="km">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AI Drama Auto Cutter</title>
<style>
*{box-sizing:border-box}
body{margin:0;background:#101322;color:white;font-family:Arial,sans-serif;padding:20px}
.container{max-width:650px;margin:auto}
h1{color:#8c9eff;text-align:center}
.card{background:#1d2338;padding:20px;border-radius:16px;margin:18px 0}
button,select,input{width:100%;padding:13px;margin:8px 0;border-radius:9px;border:0;font-size:16px}
button{background:#6478ff;color:white;font-weight:bold}
video{width:100%;margin-top:12px;border-radius:10px}
.status{color:#9fb0ff}
</style>
</head>
<body>
<div class="container">
<h1>🎬 AI Drama Auto Cutter</h1>
<p style="text-align:center">Automatic Video Cutting Studio</p>

<div class="card">
<h3>📁 Upload Video</h3>
<input type="file" id="videoFile" accept="video/mp4,video/*">
<video id="preview" controls hidden></video>
</div>

<div class="card">
<h3>✂️ Cutting Mode</h3>
<select id="mode">
<option value="time">Auto Time Cutter</option>
<option value="scene">AI Scene Cutter</option>
</select>

<label>Part Duration</label>
<select id="duration">
<option value="60">1 Minute</option>
<option value="120">2 Minutes</option>
<option value="180">3 Minutes</option>
</select>

<button onclick="startCut()">START CUTTING</button>
<p class="status" id="status">Ready to start</p>
<div id="results"></div>
</div>
</div>

<script>
const fileInput=document.getElementById('videoFile');
const preview=document.getElementById('preview');
let videoFile=null;

fileInput.onchange=()=>{
 videoFile=fileInput.files[0];
 if(!videoFile)return;
 preview.src=URL.createObjectURL(videoFile);
 preview.hidden=false;
 document.getElementById('status').textContent='Video loaded: '+videoFile.name;
};

function startCut(){
 if(!videoFile){
 alert('Please upload a video first!');
 return;
 }
 if(document.getElementById('mode').value==='scene'){
 document.getElementById('status').textContent=
 'AI Scene Cutter requires AI processing backend. Not connected yet.';
 return;
 }
 document.getElementById('status').textContent=
 'Video ready. Backend processing is required to export MP4 parts.';
}
</script>
</body>
</html>

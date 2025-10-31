<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>La Malédiction du Manoir — Mémoire persistante</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Creepster&display=swap');
  body{background:#0a0a0c;color:#eee;font-family:"Creepster",cursive;margin:0;overflow-x:hidden}
  h1{color:#ff3c00;text-align:center;text-shadow:0 0 10px #ff3c00;margin-top:20px}
  #story{max-width:800px;margin:20px auto;padding:20px;background:rgba(0,0,0,0.6);border:2px solid rgba(255,255,255,0.1);border-radius:12px;box-shadow:0 0 20px rgba(0,0,0,0.6)}
  button{display:block;width:100%;background:#111;color:#ff3c00;border:2px solid #ff3c00;padding:12px;border-radius:10px;margin-top:10px;font-size:1rem;cursor:pointer}
  button:hover{background:#ff3c00;color:#111}
  #hud{display:flex;justify-content:center;gap:10px;margin-top:10px}
  .bar{background:#222;padding:8px 12px;border-radius:10px;font-size:14px}
  #memoryBox{position:fixed;top:0;left:0;right:0;bottom:0;background:rgba(0,0,0,0.92);color:#fff;display:none;flex-direction:column;align-items:center;justify-content:center;text-align:center;z-index:1000;padding:20px}
  #memoryBox button{width:auto;margin-top:20px}
</style>
</head>
<body>

<h1>🏚️ La Malédiction du Manoir</h1>
<div id="hud">
  <div class="bar">🧠 Santé : <span id="sanity">100</span></div>
  <div class="bar">👁️ Curiosité : <span id="curiosity">0</span></div>
  <div class="bar">💀 Corruption : <span id="corruption">0</span></div>
  <button id="memBtn" style="width:auto;background:#333;border-color:#666;color:#ccc">👁️ Souvenirs</button>
</div>
<div id="story"></div>

<div id="memoryBox">
  <h2>🕯️ Souvenirs du Manoir</h2>
  <div id="memoryContent"></div>
  <button onclick="closeMemory()">Fermer</button>
</div>

<script>
let sanity=100, curiosity=0, corruption=0;
let memory = JSON.parse(localStorage.getItem('manoirMemory')) || {
  runs:0,
  goodEnds:0,
  badEnds:0,
  maxSanity:100,
  totalCorruption:0
};

const storyEl=document.getElementById('story');
const sanityEl=document.getElementById('sanity');
const curiosityEl=document.getElementById('curiosity');
const corruptionEl=document.getElementById('corruption');
const memBtn=document.getElementById('memBtn');
const memoryBox=document.getElementById('memoryBox');
const memoryContent=document.getElementById('memoryContent');

memBtn.onclick=()=>openMemory();

function updateHUD(){
  sanityEl.textContent=sanity;
  curiosityEl.textContent=curiosity;
  corruptionEl.textContent=corruption;
}

// --- Scenes ---
const scenes={
  start:{
    text:getIntroText(),
    choices:[
      {text:"Entrer dans le manoir",next:"hall"},
      {text:"Fuir dans la nuit",next:"fuite"}
    ]
  },
  hall:{
    text:"Le hall te semble familier. Les murs murmurent ton nom. Une porte s’ouvre seule.",
    sanity:-5,choices:[
      {text:"Suivre le murmure",next:"ombre"},
      {text:"Explorer la bibliothèque",next:"biblio"}
    ]
  },
  ombre:{
    text:"Une ombre t’enlace et te chuchote des vérités interdites.",
    sanity:-20,corruption:+20,end:"Tu t’abandonnes à la voix… et deviens l’un des leurs."
  },
  biblio:{
    text:"Un grimoire t’attend. Il semble t’avoir déjà vu. Sur la couverture, un mot : *LUMEN*.",
    curiosity:+10,choices:[
      {text:"Lire le mot à voix haute",next:"rituel"},
      {text:"Refermer doucement",next:"fin_bonne"}
    ]
  },
  rituel:{
    text:"Tu prononces le mot... La pièce tremble, la corruption t’envahit.",
    sanity:-30,corruption:+40,end:"Le manoir rit. Tu es désormais son écho éternel."
  },
  fuite:{
    text:"Tu fuis. Le manoir t’observe s’éloigner sous la pluie.",
    sanity:+10,end:"Tu es libre, mais il reviendra dans tes cauchemars."
  },
  fin_bonne:{
    text:"Une lumière douce traverse la pièce. Tu as résisté à l’appel du manoir.",
    sanity:+30,corruption:-10,end:"Tu quittes le manoir. Pour cette fois, il dort paisiblement."
  }
};

// --- Display scene ---
function showScene(name){
  const scene=scenes[name];
  if(!scene) return;
  if(scene.sanity) sanity+=scene.sanity;
  if(scene.curiosity) curiosity+=scene.curiosity;
  if(scene.corruption) corruption+=scene.corruption;
  updateHUD();

  let html=`<p>${scene.text}</p>`;
  if(scene.choices){
    scene.choices.forEach(ch=>{
      html+=`<button onclick="choose('${ch.next}')">${ch.text}</button>`;
    });
  }else if(scene.end){
    html+=`<p><em>${scene.end}</em></p><button onclick="restart()">Rejouer</button>`;
    saveRun(scene.end);
  }
  storyEl.innerHTML=html;
}

function choose(next){ showScene(next); }

// --- Memory system ---
function saveRun(endText){
  memory.runs++;
  if(endText.includes("libre")||endText.includes("lumière")||endText.includes("paisiblement")){
    memory.goodEnds++;
  } else {
    memory.badEnds++;
  }
  memory.maxSanity = Math.max(memory.maxSanity,sanity);
  memory.totalCorruption += corruption;
  localStorage.setItem('manoirMemory',JSON.stringify(memory));
}

function getIntroText(){
  if(memory.runs===0){
    return "La pluie tombe. Devant toi, un manoir oublié t’invite à franchir le seuil.";
  } else if(memory.totalCorruption>300){
    return "Le manoir te reconnaît. Ses murs te murmurent : « encore toi... »";
  } else if(memory.goodEnds>2){
    return "Une aura familière émane du manoir. Tu sens qu’il t’attend, reconnaissant.";
  } else {
    return "Tu reviens. Le manoir semble plus sombre, plus conscient de ta présence.";
  }
}

function openMemory(){
  memoryContent.innerHTML=`
    <p>Parties jouées : ${memory.runs}</p>
    <p>Fins lumineuses : ${memory.goodEnds}</p>
    <p>Fins sombres : ${memory.badEnds}</p>
    <p>Corruption cumulée : ${memory.totalCorruption}</p>
    <p>Meilleure santé mentale : ${memory.maxSanity}</p>
  `;
  if(memory.totalCorruption>500){
    memoryContent.innerHTML+=`<p style="color:#ff3c00">👁️ Le manoir connaît ton nom maintenant...</p>`;
  }
  memoryBox.style.display='flex';
}

function closeMemory(){memoryBox.style.display='none';}

function restart(){
  sanity=100;curiosity=0;corruption=0;
  updateHUD();
  showScene('start');
}

updateHUD();
showScene('start');
</script>
</body>
</html>

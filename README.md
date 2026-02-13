<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>A Love Mail 💌</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<link href="https://fonts.googleapis.com/css2?family=Playfair+Display&family=Poppins&family=Sacramento&display=swap" rel="stylesheet">

<style>
body {
  margin: 0;
  font-family: 'Poppins', sans-serif;
  background: radial-gradient(circle at top, #ffccd5, #6a0f2e);
  overflow: hidden;
}

.page {
  display: none;
  height: 100vh;
  padding: 30px 20px;
  box-sizing: border-box;
  text-align: center;
}

.page.active {
  display: block;
  animation: fade 1s ease;
}

@keyframes fade {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

/* Floating hearts */
.heart {
  position: fixed;
  color: rgba(255,255,255,0.6);
  font-size: 18px;
  animation: float 8s linear infinite;
}

@keyframes float {
  from { transform: translateY(100vh); }
  to { transform: translateY(-10vh); }
}

/* Envelope */
.envelope {
  width: 320px;
  height: 200px;
  background: #fff;
  margin: 120px auto 20px;
  position: relative;
  border-radius: 10px;
  box-shadow: 0 15px 35px rgba(0,0,0,0.4);
  cursor: pointer;
  animation: shake 2s infinite;
}

@keyframes shake {
  0%,100% { transform: rotate(0); }
  25% { transform: rotate(1deg); }
  75% { transform: rotate(-1deg); }
}

.envelope.open {
  animation: none;
}

.flap {
  position: absolute;
  width: 100%;
  height: 100%;
  background: #f4a6b8;
  clip-path: polygon(0 0, 50% 55%, 100% 0);
  transform-origin: top;
  transition: transform 1s ease;
}

.envelope.open .flap {
  transform: rotateX(180deg);
}

.seal {
  width: 55px;
  height: 55px;
  background: #6a0f2e;
  border-radius: 50%;
  color: white;
  line-height: 55px;
  font-size: 24px;
  position: absolute;
  bottom: -28px;
  left: 50%;
  transform: translateX(-50%);
}

/* Buttons */
.button {
  margin-top: 25px;
  padding: 14px 32px;
  background: white;
  color: #6a0f2e;
  border: none;
  border-radius: 30px;
  font-size: 1em;
  cursor: pointer;
  transition: 0.3s;
}

.button:hover {
  transform: scale(1.1);
}

/* Letter FIXED */
.letter {
  background: rgba(255,255,255,0.96);
  border-radius: 20px;
  padding: 30px;
  max-width: 850px;
  margin: auto;
  font-family: 'Sacramento', cursive;
  font-size: 1.6em;
  line-height: 1.9;
  color: #4a0f22;
  max-height: 55vh;
  overflow-y: auto;
}

/* Gallery */
.gallery img {
  width: 300px;
  height: 400px;
  border-radius: 15px;
  margin: 10px;
  box-shadow: 0 10px 25px rgba(0,0,0,0.35);
}

h1 {
  font-family: 'Playfair Display', serif;
  color: white;
  font-size: 2.6em;
}

p {
  color: white;
  font-size: 1.2em;
}

/* Kiss animation */
.kiss {
  position: fixed;
  font-size: 40px;
  animation: kiss 2s ease forwards;
}

@keyframes kiss {
  0% { opacity: 0; transform: scale(0); }
  50% { opacity: 1; transform: scale(1.5); }
  100% { opacity: 0; transform: translateY(-200px); }
}
</style>
</head>

<body>

<audio id="music" loop>
  <source src="music.mp3" type="audio/mpeg">
</audio>

<script>
/* hearts */
for (let i = 0; i < 25; i++) {
  let h = document.createElement("div");
  h.className = "heart";
  h.innerHTML = "❤";
  h.style.left = Math.random() * 100 + "vw";
  h.style.animationDuration = (5 + Math.random() * 5) + "s";
  document.body.appendChild(h);
}

function showPage(id) {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  document.getElementById(id).classList.add('active');
}

function openEnvelope() {
  document.getElementById('env').classList.add('open');
  document.getElementById('music').play();
  setTimeout(() => {
    showPage('page2');
    typeLetter();
  }, 1200);
}

/* typing effect */
const letterText = `Happy Valentine’s Day, baby.

I love you so much, and I miss you more than I can ever put into words.
I’m sorry if I wasn’t able to buy you flowers this Valentine’s because I didn’t have enough money,
and I’m also sorry for not being there with you on such a special day.
Still, I hope this letter and what I got for you can somehow make you feel how much you truly mean to me.

Even though I can’t be by your side right now, please know that you will always be my princess,
my baby, my partner, and my future wife.

I may not be the perfect man, but I promise to give you all the love, care, respect,
and effort you deserve.
Falling for you was the biggest decision I’ve ever made, and I’ve never regretted it.
You complete my life more and more each day.
Every time I talk to you and see that warm, beautiful smile of yours,
my world instantly feels brighter and more complete.

I love you so much baby, and I miss you.
<3 <3 <3`;

let i = 0;
function typeLetter() {
  const el = document.getElementById("typed");
  el.innerHTML = "";
  i = 0;
  const interval = setInterval(() => {
    el.innerHTML += letterText[i] === "\n" ? "<br>" : letterText[i];
    i++;
    if (i >= letterText.length) clearInterval(interval);
  }, 25);
}

/* kiss effect */
function yesKiss() {
  for (let i = 0; i < 15; i++) {
    const k = document.createElement("div");
    k.className = "kiss";
    k.innerHTML = "💋";
    k.style.left = Math.random() * 100 + "vw";
    k.style.top = "70vh";
    document.body.appendChild(k);
    setTimeout(() => k.remove(), 2000);
  }
}
</script>

<!-- PAGE 1 -->
<div class="page active" id="page1">
  <div class="envelope" id="env" onclick="openEnvelope()">
    <div class="flap"></div>
    <div class="seal">❤</div>
  </div>
  <h1>You’ve Got a Love Mail</h1>
  <p>Tap the envelope 💌</p>
</div>

<!-- PAGE 2 -->
<div class="page" id="page2">
  <h1>My Love Letter 💌 </h1>
  <div class="letter" id="typed"></div>
  <button class="button" onclick="showPage('page3')">Our Memories 📸</button>
</div>

<!-- PAGE 3 -->
<div class="page" id="page3">
  <h1>Our Moments</h1>
  <div class="gallery">
    <img src="Partner 1.jpg">
    <img src="Partner 2.jpg">
    <img src="Partner 3.jpg">
  </div>
  <button class="button" onclick="showPage('page4')">One Last Thing 💖</button>
</div>

<!-- PAGE 4 -->
<div class="page" id="page4">
  <h1>From My Heart 💍</h1>
  
  <!-- Scrollable letter area -->
  <div class="letter" id="typed4" style="max-height:55vh; overflow-y:auto; padding:20px; margin-bottom:20px;"></div>
  
  <!-- Signature always visible -->
  <p id="signature" style="margin-top:10px; font-size:1.5em; font-weight:bold; text-align:center; color:#6a0f2e; opacity:0;">
    Forever yours,<br>Your Partner
  </p>
</div>

<script>
// Typing effect for Page 4 confession
const confessionText = `Baby, I want to ask you something from the bottom of my heart. 
I hope my timing is right, and I hope you’re ready to enter a new relationship this time, with me. 
I know we are already in this kind of relationship, but I want it to be official and have a label. 
I want you, baby, forever in my life, and I truly want to pursue you the right way.

I know we started in a rough situation, where part of me wanted to give up because of certain actions, 
but I chose the part of me that understands you, that is willing to take the risk and patiently wait for you. 
You are the risk I am willing to take, baby, and I want you to know that no matter what happens, 
even if things go south, you will always be the one I choose to have in my entire life.

So, Baby...

May I court you, Doctor Salazar?`;

let j = 0;
function typeConfession() {
  const el = document.getElementById("typed4");
  const sig = document.getElementById("signature");
  el.innerHTML = "";
  sig.style.opacity = 0; // hide signature before typing
  j = 0;
  const interval = setInterval(() => {
    el.innerHTML += confessionText[j] === "\n" ? "<br>" : confessionText[j];
    j++;
    el.scrollTop = el.scrollHeight; // scroll as typing progresses
    if (j >= confessionText.length) {
      clearInterval(interval);
      // Fade in signature after typing
      sig.style.transition = "opacity 2s ease-in-out, text-shadow 1s ease-in-out";
      sig.style.opacity = 1;
      sig.style.textShadow = "0 0 20px #ffccd5, 0 0 40px #6a0f2e";
    }
  }, 25);
}

// Trigger typing when page 4 is shown
document.querySelector('[onclick="showPage(\'page4\')"]').addEventListener('click', () => {
  typeConfession();
});
</script>
</body>
</html>

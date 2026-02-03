animate([
   {transform:"translateY(0)",opacity:1},
   {transform:"translateY(-120vh)",opacity:0}
  ],{duration:3000});

  setTimeout(()=>h.remove(),3000);
 }
}

/* ===== AI NARATOR ===== */

const aiTexts=[
"Universul analizează emoțiile...",
"Destin recalculat...",
"Compatibilitate detectată...",
"Stelele aprobă alegerea...",
"Iubire detectată în sistem..."
];

setInterval(()=>{
 document.getElementById("ai").innerText=
 aiTexts[Math.floor(Math.random()*aiTexts.length)];
},3000);

/* ===== HAOS BUTON NU ===== */

function chaos(btn){

 let rect=btn.getBoundingClientRect();
 explode(rect.left,rect.top);

 let effects=[

 ()=>randomPos(btn),

 ()=>btn.animate([{transform:"rotate(0)"},{transform:"rotate(360deg)"}],{duration:600}),

 ()=>btn.animate([{transform:"scale(1)"},{transform:"scale(1.6)"},{transform:"scale(1)"}],{duration:600}),

 ()=>screenShake(),

 ()=>cloneBtn(btn),

 ()=>gravity(btn),

 ()=>hearts()

 ];

 effects[Math.floor(Math.random()*effects.length)]();
}

/* ===== SHAKE ===== */

function screenShake(){
 document.body.animate([
  {transform:"translate(0)"},
  {transform:"translate(-10px,5px)"},
  {transform:"translate(10px,-5px)"},
  {transform:"translate(0)"}
 ],{duration:300});
}

/* ===== MULTIPLICARE ===== */

function cloneBtn(btn){
 let c=btn.cloneNode(true);
 document.body.appendChild(c);
 randomPos(c);
 c.onclick=()=>chaos(c);
 setTimeout(()=>c.remove(),4000);
}

/* ===== GRAVITATIE ===== */

function gravity(btn){
 let x=Math.random()*200-100;
 let y=Math.random()*200-100;

 btn.animate([
  {transform:"translate(0,0)"},
  {transform:`translate(${x}px,${y}px)`},
  {transform:"translate(0,0)"}
 ],{duration:800});
}

/* ===== CLICK NU ===== */

no.onclick=()=>{
 startMusic();
 chaos(no);
 if(navigator.vibrate) navigator.vibrate(60);
};

/* ===== CLICK DA ===== */

yes.onclick=()=>{

 startMusic();

 hearts();
 explode(yes.getBoundingClientRect().left,yes.getBoundingClientRect().top);

 step++;

 if(step<questions.length){
  question.innerHTML=questions[step];
  randomPos(yes);
  randomPos(no);
 }else{
  ending();
 }

 if(navigator.vibrate) navigator.vibrate([100,50,100]);
};

/* ===== FINAL CINEMATIC ===== */

function ending(){

 document.body.innerHTML=`
 <div style="
 display:flex;
 justify-content:center;
 align-items:center;
 height:100vh;
 text-align:center;
 font-size:34px;
 background:black;
 animation:fade 3s;
 ">
 Din toate galaxiile existente... 🌌<br><br>
 alegerea mea rămâne TU 💖<br><br>
 Happy Valentine's Day 🥹
 </div>
 `;
}

</script>

</body>
</html>

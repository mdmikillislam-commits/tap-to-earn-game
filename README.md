<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#07101f">
<title>SK GOLD RUSH</title>
<style>
:root{--gold:#ffd34e;--gold2:#ff9e17;--bg:#07101f;--panel:#101d32;--muted:#9eacc3;--cyan:#39d9e8}
*{box-sizing:border-box}body{margin:0;background:radial-gradient(ellipse at 50% 20%,#18365a 0,#0a1830 38%,#050b16 100%);color:#fff;font-family:Arial,Helvetica,sans-serif;min-height:100vh}
.app{max-width:480px;margin:auto;min-height:100vh;padding:16px 15px 96px;overflow:hidden}
header{display:flex;align-items:center;justify-content:space-between;margin:4px 0 18px}
.brand{display:flex;align-items:center;gap:10px}.brandmark{width:46px;height:46px;border-radius:14px;background:linear-gradient(145deg,#fff3a2,#ffb400 48%,#9b4d00);display:grid;place-items:center;color:#422300;font-size:25px;box-shadow:0 0 22px #ffb72b66;border:2px solid #ffe58a}
.brand h1{font-size:19px;letter-spacing:1.4px;margin:0;color:#ffe17b}.brand small{display:block;color:#8ea4c4;font-size:10px;letter-spacing:2px;margin-top:3px}
.avatar{border:1px solid #36506f;background:#142640;border-radius:13px;padding:10px 12px;font-size:13px}
.panel{background:linear-gradient(145deg,#142640dd,#0c192ddd);border:1px solid #284565;border-radius:19px;padding:15px;box-shadow:0 10px 30px #0005}
.balance{display:flex;align-items:center;justify-content:space-between}.eyebrow{font-size:11px;color:#9db0ca;letter-spacing:1.5px}.amount{font-size:30px;font-weight:900;color:#ffe17b;margin-top:5px;text-shadow:0 0 15px #ffb31d55}.coinmini{font-size:38px;filter:drop-shadow(0 0 10px #ffbd32)}
.stats{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-top:12px}.stat{background:#09172a;border:1px solid #243c5a;border-radius:13px;padding:11px}.stat strong{display:block;font-size:16px;margin-top:5px}.bar{height:7px;background:#263b55;border-radius:9px;margin-top:8px;overflow:hidden}.bar span{display:block;height:100%;width:100%;background:linear-gradient(90deg,#1ed7e8,#6df6c5);border-radius:9px}
.center{text-align:center;padding:18px 0 12px}.level{display:inline-block;border:1px solid #82632c;color:#ffdf80;background:#4c351b66;border-radius:20px;padding:7px 13px;font-size:11px;letter-spacing:1px;margin-bottom:14px}
.coin-wrap{width:238px;height:238px;margin:0 auto 13px;display:grid;place-items:center;position:relative;filter:drop-shadow(0 0 24px #ffb51d55)}
.coin{width:218px;height:218px;border-radius:50%;border:8px solid #ffe98a;background:radial-gradient(circle at 34% 24%,#fffbd0 0,#ffe46c 16%,#ffb914 42%,#d97800 73%,#7b3900 100%);box-shadow:inset 0 0 0 5px #b86a06,inset 0 0 24px #fff7b0,0 9px 0 #703800,0 14px 25px #0009;display:flex;flex-direction:column;align-items:center;justify-content:center;color:#693600;text-shadow:0 1px 0 #fff6a8;cursor:pointer;user-select:none;transition:transform .08s}
.coin:active{transform:scale(.93)}.coin .symbol{font-size:74px;line-height:1}.coin .taplabel{font-weight:1000;font-size:20px;letter-spacing:1px;margin-top:3px}.coin .subtap{font-size:10px;font-weight:bold;letter-spacing:2px}
.tap-hint{color:#9aabc2;font-size:12px}.tap-hint b{color:#ffe17b}
.float{position:absolute;color:#fff1a4;font-size:22px;font-weight:900;pointer-events:none;animation:rise .8s ease-out forwards;text-shadow:0 2px 8px #000}
@keyframes rise{to{transform:translateY(-80px);opacity:0}}
.actions{display:grid;grid-template-columns:repeat(4,1fr);gap:9px;margin:16px 0}.action{background:linear-gradient(160deg,#172b47,#0c1a2d);border:1px solid #2c496a;border-radius:14px;padding:12px 4px;text-align:center;color:#dce8fa;font-size:11px;cursor:pointer}.action span{display:block;font-size:23px;margin-bottom:6px}
.section-title{display:flex;justify-content:space-between;align-items:center;margin:18px 2px 10px;font-size:14px}.section-title small{color:#8fa3bf;font-size:11px}
.mission{display:flex;align-items:center;gap:10px;padding:11px 0;border-bottom:1px solid #263c58}.mission:last-child{border:0}.mission .mi{font-size:23px}.mission .desc{flex:1;font-size:12px}.mission .desc small{display:block;color:#91a4bf;margin-top:4px}.reward{color:#ffdc76;font-weight:bold;font-size:12px}
button{font-family:inherit}.claim{border:0;border-radius:10px;background:linear-gradient(135deg,#ffe98a,#ffad18);color:#4c2b00;font-weight:900;padding:9px 11px;cursor:pointer}.claim:disabled{opacity:.45;cursor:not-allowed}
.bottom{position:fixed;bottom:0;left:50%;transform:translateX(-50%);width:min(480px,100%);display:grid;grid-template-columns:repeat(4,1fr);background:#081426f2;border-top:1px solid #29415f;padding:10px 8px calc(10px + env(safe-area-inset-bottom));backdrop-filter:blur(12px);z-index:5}.nav{background:none;border:0;color:#8296b2;font-size:10px;cursor:pointer}.nav span{display:block;font-size:20px;margin-bottom:4px}.nav.active{color:#ffdc75}
.toast{position:fixed;top:18px;left:50%;transform:translateX(-50%);background:#ffe17b;color:#392300;padding:11px 16px;border-radius:12px;font-weight:bold;font-size:13px;display:none;z-index:10;box-shadow:0 8px 25px #0008}
.modalback{display:none;position:fixed;inset:0;background:#000a;z-index:8;align-items:center;justify-content:center;padding:20px}.modal{width:min(400px,100%);background:#10213a;border:1px solid #456080;border-radius:20px;padding:20px;box-shadow:0 20px 60px #000b}.modal h2{margin:0 0 8px;color:#ffe17b}.modal p{color:#b4c3d8;font-size:13px;line-height:1.5}.modal .close{float:right;background:none;border:0;color:white;font-size:23px;cursor:pointer}
@media(max-width:360px){.coin-wrap{width:210px;height:210px}.coin{width:194px;height:194px}.coin .symbol{font-size:63px}.amount{font-size:26px}}
</style>
</head>
<body>
<div class="app">
<header><div class="brand"><div class="brandmark">₿</div><div><h1>SK GOLD RUSH</h1><small>TAP • COLLECT • LEVEL UP</small></div></div><div class="avatar">👤 Player</div></header>
<section class="panel">
 <div class="balance"><div><div class="eyebrow">YOUR GOLD BALANCE</div><div class="amount" id="balance">0 <small style="font-size:12px">GOLD</small></div></div><div class="coinmini">🪙</div></div>
 <div class="stats">
  <div class="stat"><div class="eyebrow">⚡ ENERGY</div><strong><span id="energy">500</span> / 500</strong><div class="bar"><span id="energybar"></span></div></div>
  <div class="stat"><div class="eyebrow">🏅 YOUR LEVEL</div><strong id="level">Level 1</strong><div class="bar"><span id="levelbar" style="width:8%;background:linear-gradient(90deg,#ff9d19,#ffe17b)"></span></div></div>
 </div>
</section>
<div class="center">
 <div class="level">✦ GOLD MINER • LEVEL <span id="levelBadge">1</span> ✦</div>
 <div class="coin-wrap" id="coinWrap"><button class="coin" id="tap" aria-label="Tap to earn"><span class="symbol">₿</span><span class="taplabel">TAP TO EARN</span><span class="subtap">+<span id="power">1</span> GOLD</span></button></div>
 <div class="tap-hint">Tap the gold coin to collect <b>GOLD</b></div>
</div>
<div class="actions">
 <button class="action" onclick="daily()"><span>🎁</span>Daily Gift</button>
 <button class="action" onclick="spin()"><span>🎡</span>Lucky Spin</button>
 <button class="action" onclick="upgrade()"><span>⚡</span>Upgrade</button>
 <button class="action" onclick="invite()"><span>👥</span>Invite</button>
</div>
<div class="section-title"><b>🎯 Missions</b><small>Complete tasks • Earn rewards</small></div>
<section class="panel" id="missions">
 <div class="mission"><div class="mi">👆</div><div class="desc">Tap 10 times<small id="m10">0 / 10 taps</small></div><div class="reward">+20</div><button class="claim" id="c10" onclick="claimMission(10)">Claim</button></div>
 <div class="mission"><div class="mi">🔥</div><div class="desc">Tap 50 times<small id="m50">0 / 50 taps</small></div><div class="reward">+100</div><button class="claim" id="c50" onclick="claimMission(50)">Claim</button></div>
 <div class="mission"><div class="mi">💎</div><div class="desc">Tap 100 times<small id="m100">0 / 100 taps</small></div><div class="reward">+250</div><button class="claim" id="c100" onclick="claimMission(100)">Claim</button></div>
 <div class="mission"><div class="mi">👑</div><div class="desc">Tap 500 times<small id="m500">0 / 500 taps</small></div><div class="reward">+1,000</div><button class="claim" id="c500" onclick="claimMission(500)">Claim</button></div>
</section>
<div class="section-title"><b>🏆 Your Progress</b><small>Keep collecting gold</small></div>
<section class="panel" style="display:flex;justify-content:space-between;text-align:center">
 <div><div style="font-size:23px">👆</div><b id="totalTaps">0</b><div class="eyebrow">TOTAL TAPS</div></div>
 <div><div style="font-size:23px">🪙</div><b id="earned">0</b><div class="eyebrow">GOLD EARNED</div></div>
 <div><div style="font-size:23px">⚡</div><b id="powerStat">1x</b><div class="eyebrow">TAP POWER</div></div>
</section>
<div class="section-title"><b>👛 My Wallet</b><small>Demo mode</small></div>
<section class="panel"><div style="display:flex;justify-content:space-between;align-items:center"><div><div class="eyebrow">AVAILABLE GOLD</div><b style="font-size:21px;color:#ffe17b" id="walletBalance">0</b></div><button class="claim" onclick="showModal('wallet')">Wallet details</button></div><p style="font-size:11px;color:#9aabc2;line-height:1.5;margin-bottom:0">Gold points are demo game points only. They are not cryptocurrency or cash and cannot currently be withdrawn.</p></section>
</div>
<nav class="bottom"><button class="nav active" onclick="navTo('home',this)"><span>⌂</span>Home</button><button class="nav" onclick="navTo('earn',this)"><span>🪙</span>Earn</button><button class="nav" onclick="navTo('rank',this)"><span>🏆</span>Rank</button><button class="nav" onclick="navTo('wallet',this)"><span>👛</span>Wallet</button></nav>
<div class="toast" id="toast"></div>
<div class="modalback" id="modalback" onclick="if(event.target===this)closeModal()"><div class="modal"><button class="close" onclick="closeModal()">×</button><div id="modalcontent"></div></div></div>
<script>
const defaults={gold:0,energy:500,taps:0,power:1,earned:0,lastEnergy:Date.now(),daily:'',spin:'',claimed:[]};
let s={...defaults,...JSON.parse(localStorage.getItem('skGoldRush')||'{}')};
function save(){localStorage.setItem('skGoldRush',JSON.stringify(s));render()}
function toast(t){let e=document.getElementById('toast');e.textContent=t;e.style.display='block';clearTimeout(window.toastTimer);window.toastTimer=setTimeout(()=>e.style.display='none',1900)}
function render(){
 document.getElementById('balance').innerHTML=s.gold.toLocaleString()+' <small style="font-size:12px">GOLD</small>';
 document.getElementById('walletBalance').textContent=s.gold.toLocaleString();
 document.getElementById('energy').textContent=s.energy;document.getElementById('energybar').style.width=(s.energy/5)+'%';
 let lv=Math.floor(s.earned/1000)+1;document.getElementById('level').textContent='Level '+lv;document.getElementById('levelBadge').textContent=lv;
 document.getElementById('levelbar').style.width=Math.min(100,(s.earned%1000)/10)+'%';
 document.getElementById('power').textContent=s.power;document.getElementById('powerStat').textContent=s.power+'x';
 document.getElementById('totalTaps').textContent=s.taps.toLocaleString();document.getElementById('earned').textContent=s.earned.toLocaleString();
 [10,50,100,500].forEach(n=>{document.getElementById('m'+n).textContent=Math.min(s.taps,n)+' / '+n+' taps';let b=document.getElementById('c'+n);b.disabled=s.taps<n||s.claimed.includes(n);b.textContent=s.claimed.includes(n)?'Done':s.taps>=n?'Claim':'Locked'});
}
document.getElementById('tap').addEventListener('click',e=>{if(s.energy<=0){toast('Energy finished! Wait to recharge.');return}s.gold+=s.power;s.earned+=s.power;s.taps++;s.energy--;let f=document.createElement('div');f.className='float';f.textContent='+'+s.power;f.style.left=(e.clientX-10)+'px';f.style.top=(e.clientY-10)+'px';document.body.appendChild(f);setTimeout(()=>f.remove(),800);save()});
function daily(){let d=new Date().toDateString();if(s.daily===d){toast('Daily gift already collected today');return}s.daily=d;s.gold+=100;s.earned+=100;save();toast('🎁 Daily gift: +100 GOLD')}
function spin(){let d=new Date().toDateString();if(s.spin===d){toast('You already used today’s spin');return}s.spin=d;let prize=[10,25,50,100,200][Math.floor(Math.random()*5)];s.gold+=prize;s.earned+=prize;save();toast('🎡 You won '+prize+' GOLD!')}
function upgrade(){let cost=s.power*100;if(s.gold<cost){toast('Need '+cost+' GOLD to upgrade');return}s.gold-=cost;s.power++;save();toast('⚡ Tap power upgraded!')}
function claimMission(n){if(s.taps<n||s.claimed.includes(n))return;let prize={10:20,50:100,100:250,500:1000}[n];s.claimed.push(n);s.gold+=prize;s.earned+=prize;save();toast('Mission reward +'+prize+' GOLD')}
function invite(){let code='SK'+String(s.taps+48271).slice(-6);showModal('invite',code)}
function showModal(type,code=''){let c=document.getElementById('modalcontent');if(type==='invite'){c.innerHTML='<h2>👥 Invite Friends</h2><p>Share your game with friends. Referral tracking and referral rewards are not active in this demo.</p><div class="panel" style="text-align:center;color:#ffe17b;font-size:22px;letter-spacing:3px">'+code+'</div><button class="claim" style="width:100%;margin-top:12px" onclick="copyCode(\\''+code+'\\')">Copy invite code</button>'}else if(type==='wallet'){c.innerHTML='<h2>👛 My Wallet</h2><p>Your balance is '+s.gold.toLocaleString()+' GOLD demo points.</p><p>Real withdrawals, crypto transfers and cash payments are not connected. A secure server, payment integration and verified rules would be required before enabling them.</p>'}else{c.innerHTML='<h2>SK GOLD RUSH</h2><p>Demo game</p>'}document.getElementById('modalback').style.display='flex'}
function copyCode(code){if(navigator.clipboard){navigator.clipboard.writeText(code).then(()=>toast('Invite code copied')).catch(()=>toast('Code: '+code))}else toast('Code: '+code)}
function closeModal(){document.getElementById('modalback').style.display='none'}
function navTo(where,el){document.querySelectorAll('.nav').forEach(n=>n.classList.remove('active'));el.classList.add('active');if(where==='earn')document.getElementById('tap').scrollIntoView({behavior:'smooth',block:'center'});else if(where==='rank'){showModal('rank');document.getElementById('modalcontent').innerHTML='<h2>🏆 Leaderboard</h2><p>A real global leaderboard will be available after secure online accounts and a server are connected. This demo stores progress only on this device.</p>'}else if(where==='wallet')document.querySelector('.app').lastElementChild.scrollIntoView({behavior:'smooth'});else window.scrollTo({top:0,behavior:'smooth'})}
function recharge(){let now=Date.now(),mins=Math.floor((now-s.lastEnergy)/60000);if(mins>0&&s.energy<500){s.energy=Math.min(500,s.energy+mins);s.lastEnergy+=mins*60000;save()}}
recharge();render();setInterval(recharge,15000);
</script>
</body></html>

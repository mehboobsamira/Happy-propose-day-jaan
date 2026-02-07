const pages=document.querySelectorAll('.page');let current=0;
function nextPage(){pages[current].classList.remove('active');current=(current+1)%pages.length;pages[current].classList.add('active');}
document.addEventListener('click',()=>nextPage());
let startX=0;document.addEventListener('touchstart',e=>startX=e.touches[0].clientX);
document.addEventListener('touchend',e=>{if(startX-e.changedTouches[0].clientX>40)nextPage();});

function unlock(){if(document.getElementById('pass').value==='2828'){document.getElementById('lock').style.display='none';document.getElementById('content').style.display='block';typeName();}}

const text='samira mommy';let i=0;
function typeName(){if(i<text.length){document.getElementById('type').innerHTML+=text.charAt(i);i++;setTimeout(typeName,150);}}

const canvas=document.getElementById('fireworks'),ctx=canvas.getContext('2d');
canvas.width=innerWidth;canvas.height=innerHeight;
let particles=[];
function boom(){for(let i=0;i<80;i++)particles.push({x:innerWidth/2,y:innerHeight/2,dx:(Math.random()-0.5)*6,dy:(Math.random()-0.5)*6,life:60});}
setInterval(boom,2000);
function animate(){ctx.clearRect(0,0,canvas.width,canvas.height);
particles.forEach((p,i)=>{p.x+=p.dx;p.y+=p.dy;p.life--;ctx.fillStyle='pink';ctx.fillRect(p.x,p.y,2,2);if(p.life<=0)particles.splice(i,1);});
requestAnimationFrame(animate);}
animate();

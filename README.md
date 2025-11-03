<!doctype html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>مدرسة الإبداع الوطنية الخاصة</title>
  <style>
    body { font-family: system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial; margin:0; background:#f8fbff; color:#072a40; direction:rtl; }
    header{display:flex;align-items:center;justify-content:space-between;background:#0571c9;color:#fff;padding:12px;border-radius:8px;}
    header img{height:50px}
    nav button{background:none;border:none;color:#fff;font-weight:700;margin-left:10px;cursor:pointer;}
    .card{background:#fff;padding:16px;border-radius:12px;box-shadow:0 6px 18px rgba(7,42,64,0.06);}
    input,textarea{width:100%;padding:10px;border-radius:8px;border:1px solid #dbeefc;margin-top:6px;}
    .blue-btn{background:#0571c9;color:#fff;border:none;padding:10px 14px;border-radius:8px;cursor:pointer;}
    .grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:12px;margin-top:12px;}
    footer{text-align:center;margin-top:24px;color:#055085;}
  </style>
</head>
<body>
<header>
  <div style="display:flex;align-items:center;gap:10px">
    <img src="https://upload.wikimedia.org/wikipedia/commons/a/a7/React-icon.svg" alt="logo">
    <h2>مدرسة الإبداع الوطنية الخاصة</h2>
  </div>
  <nav>
    <button onclick="showPage('home')">الرئيسية</button>
    <button onclick="showPage('register')">تسجيل الطلبة</button>
    <button onclick="showPage('works')">أعمال المعلمات</button>
    <button onclick="showPage('admin')">صفحة المديرة</button>
  </nav>
</header>
<main id="content" style="padding:20px"></main>
<footer>© 2025 مدرسة الإبداع الوطنية الخاصة</footer>

<script>
const adminUser="admin123",adminPass="a@1234567";
function showPage(p){
  const c=document.getElementById("content");c.innerHTML="";
  if(p==="home")c.innerHTML="<h3>مرحبًا بكم 🌟</h3><p>موقع تفاعلي لروضة والمرحلة الأساسية.</p>";
  else if(p==="register"){
    c.innerHTML='<div class="card"><h3>تسجيل طالب جديد</h3><input id="n" placeholder="اسم الطالب"><input id="g" placeholder="الصف"><input id="p" placeholder="اسم ولي الأمر"><input id="ph" placeholder="الهاتف"><button class="blue-btn" onclick="save()">إرسال</button></div>';
  } else if(p==="works") c.innerHTML="<h3>أعمال المعلمات</h3><div class='card'>روضة - تلوين الأشكال</div><div class='card'>صف 1 - نشاط القراءة</div>";
  else if(p==="admin"){
    const u=prompt('اسم المستخدم:'),pw=prompt('كلمة المرور:');
    if(u===adminUser&&pw===adminPass){
      const s=JSON.parse(localStorage.getItem('regs')||'[]');
      c.innerHTML="<h3>طلبات التسجيل</h3>"+s.map(x=>`<div class='card'>👧 ${x.n} - ${x.g} (${x.p})</div>`).join("")||"<p>لا توجد طلبات بعد.</p>";
    } else alert('خطأ في الدخول');
  }
}
function save(){
  const n=document.getElementById('n').value,g=document.getElementById('g').value,p=document.getElementById('p').value,ph=document.getElementById('ph').value;
  const arr=JSON.parse(localStorage.getItem('regs')||'[]');arr.unshift({n,g,p,ph});
  localStorage.setItem('regs',JSON.stringify(arr));alert('تم الحفظ');showPage('home');
}
showPage('home');
</script>
</body></html

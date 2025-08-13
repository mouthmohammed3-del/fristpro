# fristpro
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>تسجيل الدخول - مدرسة الإبداع</title>
  <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;700&display=swap" rel="stylesheet">
  <style>
    *{box-sizing:border-box;margin:0;padding:0}
    body{
      font-family:'Tajawal',sans-serif;
      background:linear-gradient(135deg,#0061ff,#60efff);
      display:flex;
      justify-content:center;
      align-items:center;
      height:100vh;
    }
    .login-box{
      background:white;
      border-radius:15px;
      padding:30px;
      max-width:360px;
      width:90%;
      box-shadow:0 10px 25px rgba(0,0,0,0.1);
      animation:fadeIn 0.6s ease-out;
    }
    @keyframes fadeIn{from{opacity:0;transform:translateY(20px);}to{opacity:1;transform:translateY(0);}}
    h2{
      text-align:center;
      margin-bottom:20px;
      color:#0061ff;
    }
    .role-select{
      display:flex;
      justify-content:space-between;
      margin-bottom:20px;
      background:#f5f7fa;
      padding:5px;
      border-radius:8px;
    }
    .role-select button{
      flex:1;
      background:none;
      border:none;
      padding:10px;
      cursor:pointer;
      border-radius:6px;
      font-weight:700;
      transition:all 0.3s;
      color:#555;
    }
    .role-select button.active{
      background:#0061ff;
      color:white;
    }
    input{
      width:100%;
      padding:10px;
      margin-bottom:12px;
      border:1px solid #ddd;
      border-radius:8px;
      font-family:inherit;
    }
    button.login-btn{
      width:100%;
      padding:10px;
      background:#0061ff;
      border:none;
      border-radius:8px;
      color:white;
      font-weight:700;
      cursor:pointer;
      transition:background 0.3s;
    }
    button.login-btn:hover{
      background:#004bcc;
    }
    .note{
      font-size:0.85rem;
      text-align:center;
      margin-top:15px;
      color:#777;
    }
  </style>
</head>
<body>

  <div class="login-box">
    <h2>تسجيل الدخول</h2>
    <div class="role-select">
      <button class="role-btn active" data-role="مدير">مدير</button>
      <button class="role-btn" data-role="معلم">معلم</button>
      <button class="role-btn" data-role="طالب">طالب</button>
    </div>
    <form onsubmit="event.preventDefault();login();">
      <input type="text" id="username" placeholder="اسم المستخدم" required>
      <input type="password" id="password" placeholder="كلمة المرور" required>
      <button type="submit" class="login-btn">دخول</button>
    </form>
    <div class="note" id="roleNote">تسجيل الدخول كـ <strong>مدير</strong></div>
  </div>

  <script>
    const roleBtns = document.querySelectorAll('.role-btn');
    const roleNote = document.getElementById('roleNote');
    let selectedRole = 'مدير';

    roleBtns.forEach(btn=>{
      btn.addEventListener('click',()=>{
        roleBtns.forEach(b=>b.classList.remove('active'));
        btn.classList.add('active');
        selectedRole = btn.dataset.role;
        roleNote.innerHTML = `تسجيل الدخول كـ <strong>${selectedRole}</strong>`;
      });
    });

    function login(){
      const user = document.getElementById('username').value.trim();
      const pass = document.getElementById('password').value.trim();
      
      if(user && pass){
        if(selectedRole === 'مدير'){
          window.location.href = "index.html";
        } else if(selectedRole === 'معلم'){
          window.location.href = ".";
        } else if(selectedRole === 'طالب'){
          window.location.href = "student.html";
        }
      } else {
        alert('يرجى إدخال اسم المستخدم وكلمة المرور');
      }
    }
  </script>

</body>
</html>

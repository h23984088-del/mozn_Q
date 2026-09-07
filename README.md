<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🌱 براعم المُزن | منصة الحلقات القرآنية</title>
    <style>
        /* ... same CSS as before, but I'll include the full CSS for completeness ... */
        :root {
            --sky: #5BA8D9;
            --sky-light: #E8F4FD;
            --pink: #F4A0B5;
            --pink-light: #FDF0F3;
            --mint: #6BC5A0;
            --mint-light: #E8F8F0;
            --gold: #E8C547;
            --gold-light: #FEF9E7;
            --white: #fff;
            --dark: #2C3E50;
            --medium: #5D6D7E;
            --light: #85929E;
            --bg: #F7F9FC;
            --danger: #E74C3C;
            --warning: #F5A623;
            --shadow-sm: 0 2px 8px rgba(0,0,0,0.05);
            --shadow-md: 0 4px 16px rgba(0,0,0,0.07);
            --shadow-lg: 0 8px 30px rgba(0,0,0,0.1);
            --radius: 14px;
            --radius-sm: 8px;
            --radius-lg: 20px;
            --transition: 0.25s ease;
            --font: 'Segoe UI', 'Tajawal', 'Cairo', system-ui, sans-serif;
        }
        * { margin:0; padding:0; box-sizing:border-box; }
        body {
            font-family: var(--font);
            background: var(--bg);
            color: var(--dark);
            min-height:100vh;
            overflow-x:hidden;
            position:relative;
            display:flex;
            align-items:center;
            justify-content:center;
        }
        .bg-decor { position:fixed; top:0; left:0; width:100%; height:100%; pointer-events:none; z-index:0; overflow:hidden; }
        .bg-decor .star { position:absolute; opacity:0.2; animation:twinkle 3s ease-in-out infinite; font-size:12px; }
        .bg-decor .cloud { position:absolute; opacity:0.07; animation:floatCloud 25s ease-in-out infinite; font-size:40px; }
        @keyframes twinkle { 0%,100%{opacity:0.12;transform:scale(1);} 50%{opacity:0.3;transform:scale(1.25);} }
        @keyframes floatCloud { 0%,100%{transform:translateX(0);} 50%{transform:translateX(50px);} }

        .login-screen { position:fixed; top:0; left:0; width:100%; height:100%; z-index:1000; display:flex; align-items:center; justify-content:center; background:linear-gradient(135deg, var(--sky-light), var(--pink-light), var(--mint-light)); transition:opacity 0.4s, transform 0.4s; }
        .login-screen.hidden { opacity:0; transform:scale(0.95); pointer-events:none; }
        .login-card { background:var(--white); border-radius:var(--radius-lg); padding:36px 28px; width:90%; max-width:400px; box-shadow:var(--shadow-lg); text-align:center; position:relative; z-index:10; }
        .login-card .logo { font-size:52px; margin-bottom:6px; }
        .login-card h1 { font-size:22px; font-weight:700; color:var(--dark); margin-bottom:2px; }
        .login-card .sub { font-size:13px; color:var(--medium); margin-bottom:24px; }
        .login-tabs { display:flex; gap:6px; margin-bottom:20px; background:var(--bg); border-radius:var(--radius-sm); padding:4px; }
        .login-tab { flex:1; padding:10px 14px; border-radius:var(--radius-sm); border:none; background:transparent; font-size:13px; font-weight:600; cursor:pointer; color:var(--medium); transition:var(--transition); font-family:var(--font); }
        .login-tab.active { background:var(--white); color:var(--sky); box-shadow:var(--shadow-sm); }
        .login-form input { width:100%; padding:13px 16px; border:2px solid #E8ECF0; border-radius:var(--radius-sm); font-size:14px; margin-bottom:10px; transition:var(--transition); font-family:var(--font); background:var(--bg); text-align:center; }
        .login-form input:focus { outline:none; border-color:var(--sky); background:var(--white); }
        .login-btn { width:100%; padding:13px; border:none; border-radius:var(--radius-sm); font-size:15px; font-weight:700; cursor:pointer; transition:var(--transition); font-family:var(--font); background:linear-gradient(135deg, var(--sky), #3D8BC4); color:var(--white); box-shadow:0 4px 14px rgba(91,168,217,0.35); }
        .login-btn:hover { transform:translateY(-2px); box-shadow:0 6px 20px rgba(91,168,217,0.45); }
        .login-error { color:var(--danger); font-size:12px; margin-top:8px; display:none; }
        .login-error.show { display:block; }

        .app-container { position:relative; z-index:1; display:none; width:100%; min-height:100vh; }
        .app-container.show { display:block; }
        .top-bar { background:var(--white); padding:10px 16px; box-shadow:var(--shadow-sm); display:flex; align-items:center; justify-content:space-between; position:sticky; top:0; z-index:100; border-bottom:2px solid var(--sky-light); }
        .top-bar .brand { display:flex; align-items:center; gap:8px; font-size:16px; font-weight:700; color:var(--dark); }
        .top-bar .brand .logo-icon { font-size:26px; }
        .top-bar .user-info { display:flex; align-items:center; gap:8px; font-size:12px; color:var(--medium); }
        .badge-role { padding:4px 12px; border-radius:16px; font-size:11px; font-weight:600; background:var(--sky-light); color:var(--sky); }
        .logout-btn { padding:6px 14px; border:none; border-radius:var(--radius-sm); background:var(--pink-light); color:var(--pink); font-size:12px; font-weight:600; cursor:pointer; font-family:var(--font); transition:var(--transition); }
        .logout-btn:hover { background:var(--pink); color:var(--white); }

        .nav-tabs { background:var(--white); padding:0 12px; box-shadow:var(--shadow-sm); display:flex; gap:2px; overflow-x:auto; position:sticky; top:49px; z-index:99; border-bottom:2px solid var(--sky-light); scrollbar-width:none; }
        .nav-tabs::-webkit-scrollbar { display:none; }
        .nav-tab { padding:10px 16px; border:none; background:transparent; font-size:12px; font-weight:600; cursor:pointer; color:var(--medium); white-space:nowrap; font-family:var(--font); border-bottom:3px solid transparent; transition:var(--transition); display:flex; align-items:center; gap:4px; }
        .nav-tab:hover { color:var(--sky); background:var(--sky-light); }
        .nav-tab.active { color:var(--sky); border-bottom-color:var(--sky); background:var(--sky-light); }

        .main-content { padding:16px 12px; max-width:1050px; margin:0 auto; padding-bottom:80px; }
        .page-section { display:none; animation:fadeIn 0.3s ease; }
        .page-section.active { display:block; }
        @keyframes fadeIn { from{opacity:0; transform:translateY(8px);} to{opacity:1; transform:translateY(0);} }

        .card { background:var(--white); border-radius:var(--radius); padding:16px; box-shadow:var(--shadow-sm); margin-bottom:14px; border:1px solid #F0F3F7; transition:var(--transition); }
        .card:hover { box-shadow:var(--shadow-md); }
        .card-title { font-size:15px; font-weight:700; margin-bottom:12px; color:var(--dark); display:flex; align-items:center; gap:6px; }

        .stats-grid { display:grid; grid-template-columns:repeat(auto-fit, minmax(130px,1fr)); gap:8px; margin-bottom:14px; }
        .stat-card { background:var(--white); border-radius:var(--radius); padding:13px 10px; text-align:center; box-shadow:var(--shadow-sm); border-top:3px solid var(--sky); transition:var(--transition); }
        .stat-card:hover { transform:translateY(-2px); box-shadow:var(--shadow-md); }
        .stat-card.mint { border-top-color:var(--mint); }
        .stat-card.pink { border-top-color:var(--pink); }
        .stat-card.gold { border-top-color:var(--gold); }
        .stat-card.danger { border-top-color:var(--danger); }
        .stat-card.warning { border-top-color:var(--warning); }
        .stat-icon { font-size:22px; margin-bottom:3px; }
        .stat-value { font-size:20px; font-weight:700; }
        .stat-label { font-size:10px; color:var(--medium); }

        .progress-bar { width:100%; height:8px; background:#E8ECF0; border-radius:10px; overflow:hidden; margin:4px 0; }
        .progress-fill { height:100%; border-radius:10px; transition:width 0.5s ease; background:linear-gradient(90deg, var(--mint), #4DA883); }
        .progress-fill.pink { background:linear-gradient(90deg, var(--pink), #E07B96); }
        .progress-fill.blue { background:linear-gradient(90deg, var(--sky), #3D8BC4); }
        .progress-fill.gold { background:linear-gradient(90deg, var(--gold), #D4A92C); }

        .table-container { overflow-x:auto; }
        table { width:100%; border-collapse:collapse; font-size:12px; }
        table th { background:var(--sky-light); color:var(--dark); font-weight:700; padding:8px 8px; text-align:right; white-space:nowrap; font-size:11px; }
        table td { padding:7px 8px; border-bottom:1px solid #F0F3F7; text-align:right; white-space:nowrap; }
        table tr:hover td { background:#FAFCFE; }

        .btn { padding:8px 14px; border:none; border-radius:var(--radius-sm); font-size:12px; font-weight:600; cursor:pointer; transition:var(--transition); font-family:var(--font); display:inline-flex; align-items:center; gap:4px; }
        .btn-sm { padding:5px 10px; font-size:11px; }
        .btn-primary { background:var(--sky); color:var(--white); }
        .btn-primary:hover { background:#3D8BC4; }
        .btn-mint { background:var(--mint); color:var(--white); }
        .btn-pink { background:var(--pink); color:var(--white); }
        .btn-gold { background:var(--gold); color:var(--dark); }
        .btn-outline { background:transparent; border:2px solid var(--sky); color:var(--sky); }
        .btn-outline:hover { background:var(--sky-light); }
        .btn-danger { background:var(--danger); color:var(--white); }

        .att-btn { padding:7px 10px; border:2px solid #E8ECF0; border-radius:var(--radius-sm); font-size:10px; font-weight:600; cursor:pointer; transition:var(--transition); font-family:var(--font); background:var(--white); white-space:nowrap; }
        .att-btn:hover { transform:scale(1.04); }
        .att-btn.present.active { background:var(--mint); color:var(--white); border-color:var(--mint); box-shadow:0 2px 8px rgba(107,197,160,0.4); }
        .att-btn.excused.active { background:var(--gold); color:var(--dark); border-color:var(--gold); }
        .att-btn.late.active { background:var(--warning); color:var(--white); border-color:var(--warning); }
        .att-btn.absent.active { background:var(--danger); color:var(--white); border-color:var(--danger); }

        .badge-item { display:inline-flex; align-items:center; gap:3px; padding:4px 10px; border-radius:14px; font-size:10px; font-weight:600; background:var(--gold-light); color:#B8860B; margin:2px; }
        .badge-item.earned { background:var(--gold); color:var(--dark); }

        .modal-overlay { position:fixed; top:0; left:0; width:100%; height:100%; background:rgba(0,0,0,0.5); z-index:500; display:none; align-items:center; justify-content:center; padding:16px; }
        .modal-overlay.show { display:flex; }
        .modal { background:var(--white); border-radius:var(--radius-lg); padding:22px; width:90%; max-width:420px; max-height:80vh; overflow-y:auto; box-shadow:var(--shadow-lg); animation:modalIn 0.3s ease; }
        @keyframes modalIn { from{opacity:0; transform:scale(0.9) translateY(20px);} to{opacity:1; transform:scale(1) translateY(0);} }
        .modal h3 { font-size:16px; margin-bottom:14px; }
        .modal .form-group { margin-bottom:12px; }
        .modal .form-group label { display:block; font-size:12px; font-weight:600; margin-bottom:4px; color:var(--medium); }
        .modal .form-group input, .modal .form-group select, .modal .form-group textarea { width:100%; padding:9px 12px; border:2px solid #E8ECF0; border-radius:var(--radius-sm); font-size:13px; font-family:var(--font); }
        .modal .form-group input:focus, .modal .form-group select:focus, .modal .form-group textarea:focus { outline:none; border-color:var(--sky); }
        .modal-actions { display:flex; gap:8px; margin-top:16px; justify-content:flex-end; }

        .toast { position:fixed; bottom:70px; right:16px; z-index:600; padding:12px 18px; border-radius:var(--radius-sm); font-size:12px; font-weight:600; color:var(--white); box-shadow:var(--shadow-md); animation:toastIn 0.3s ease; max-width:300px; }
        .toast.success { background:var(--mint); }
        .toast.error { background:var(--danger); }
        .toast.info { background:var(--sky); }
        @keyframes toastIn { from{opacity:0; transform:translateY(15px);} to{opacity:1; transform:translateY(0);} }

        .excellence-card { background:linear-gradient(135deg, var(--gold-light), #FFF8E1); border:2px solid var(--gold); border-radius:var(--radius); padding:14px; margin-bottom:8px; }
        .excellence-card .rank { font-size:26px; font-weight:700; color:var(--gold); }
        .excellence-card .name { font-size:14px; font-weight:700; margin:2px 0; }
        .excellence-card .reason { font-size:11px; color:var(--medium); }

        .ai-chat { background:var(--white); border-radius:var(--radius); padding:14px; box-shadow:var(--shadow-sm); max-height:300px; overflow-y:auto; margin-bottom:10px; }
        .ai-msg { padding:10px 14px; border-radius:var(--radius-sm); margin-bottom:8px; font-size:12px; line-height:1.5; }
        .ai-msg.bot { background:var(--sky-light); margin-left:16px; }
        .ai-msg.user { background:var(--mint-light); margin-right:16px; text-align:left; }

        .week-days { display:flex; gap:5px; flex-wrap:wrap; margin-bottom:12px; }
        .week-day { padding:6px 12px; border-radius:16px; font-size:11px; font-weight:600; background:var(--bg); color:var(--medium); }
        .week-day.active { background:var(--sky); color:var(--white); }
        .week-day.result { background:var(--gold-light); color:#B8860B; border:2px solid var(--gold); }

        .bottom-nav { position:fixed; bottom:0; left:0; right:0; background:var(--white); box-shadow:0 -2px 12px rgba(0,0,0,0.06); display:flex; justify-content:space-around; padding:6px 4px 10px; z-index:200; border-top:2px solid var(--sky-light); }
        .bottom-nav-item { display:flex; flex-direction:column; align-items:center; font-size:9px; font-weight:600; color:var(--light); cursor:pointer; padding:4px 8px; border-radius:var(--radius-sm); transition:var(--transition); border:none; background:transparent; font-family:var(--font); }
        .bottom-nav-item .nav-icon { font-size:20px; }
        .bottom-nav-item.active { color:var(--sky); background:var(--sky-light); }

        .empty-state { text-align:center; padding:28px 16px; color:var(--light); font-size:12px; }
        .empty-state .icon { font-size:40px; margin-bottom:8px; }

        @media (max-width:600px) {
            .stats-grid { grid-template-columns:repeat(2,1fr); gap:6px; }
            .stat-card { padding:10px 6px; }
            .stat-value { font-size:17px; }
            .main-content { padding:10px 6px 90px; }
            .card { padding:12px; border-radius:var(--radius-sm); }
            table { font-size:10px; }
            table th, table td { padding:6px 4px; font-size:10px; }
            .att-btn { padding:5px 7px; font-size:9px; }
            .top-bar { padding:8px 10px; }
            .top-bar .brand { font-size:13px; }
            .nav-tabs { top:44px; }
            .login-card { padding:24px 16px; }
        }
        @media (min-width:768px) { .bottom-nav { display:none; } .main-content { padding-bottom:30px; } }
        @media (max-width:767px) { .nav-tabs { display:none; } .table-container table { font-size:10px; } .att-btn { font-size:8px; padding:4px 6px; } }
    </style>
</head>
<body>
    <div class="bg-decor" id="bgDecor"></div>

    <!-- شاشة تسجيل الدخول -->
    <div class="login-screen" id="loginScreen">
        <div class="login-card">
            <div class="logo">🌱</div>
            <h1>براعم المُزن</h1>
            <p class="sub">منصة الحلقات القرآنية</p>
            <div class="login-tabs">
                <button class="login-tab active" data-role="teacher" onclick="switchLogin('teacher')">👩🏻‍🏫 معلمة</button>
                <button class="login-tab" data-role="parent" onclick="switchLogin('parent')">👨🏻‍👩🏻 ولي أمر</button>
            </div>
            <div class="login-form">
                <input type="text" id="loginUser" placeholder="رمز المعلمة (000)" style="text-align:center;">
                <input type="password" id="loginPass" placeholder="كلمة المرور (فارغة)" style="text-align:center;">
                <button class="login-btn" onclick="handleLogin()">دخول</button>
                <p class="login-error" id="loginError">بيانات غير صحيحة</p>
            </div>
        </div>
    </div>

    <!-- التطبيق الرئيسي -->
    <div class="app-container" id="appContainer">
        <div class="top-bar">
            <div class="brand"><span class="logo-icon">🌱</span> براعم المُزن</div>
            <div class="user-info">
                <span class="badge-role" id="roleBadge">👩🏻‍🏫 معلمة</span>
                <span id="userName">رمز: 000</span>
                <button class="logout-btn" onclick="handleLogout()">خروج</button>
            </div>
        </div>

        <div class="nav-tabs" id="desktopNav">
            <button class="nav-tab active" data-page="dashboard" onclick="navTo('dashboard')">📊 الرئيسية</button>
            <button class="nav-tab" data-page="attendance" onclick="navTo('attendance')">📅 الحضور</button>
            <button class="nav-tab" data-page="students" onclick="navTo('students')">👦🏻 الطلاب</button>
            <button class="nav-tab" data-page="nisab" onclick="navTo('nisab')">📖 النصاب</button>
            <button class="nav-tab" data-page="excellence" onclick="navTo('excellence')">🏆 التميز</button>
            <button class="nav-tab" data-page="reports" onclick="navTo('reports')">📊 التقارير</button>
            <button class="nav-tab" data-page="ai" onclick="navTo('ai')">🤖 المساعد</button>
        </div>

        <div class="main-content" id="mainContent">
            <div class="page-section active" id="page-dashboard"></div>
            <div class="page-section" id="page-attendance"></div>
            <div class="page-section" id="page-students"></div>
            <div class="page-section" id="page-nisab"></div>
            <div class="page-section" id="page-excellence"></div>
            <div class="page-section" id="page-reports"></div>
            <div class="page-section" id="page-ai"></div>
        </div>

        <div class="bottom-nav" id="bottomNav">
            <button class="bottom-nav-item active" data-page="dashboard" onclick="navTo('dashboard')"><span class="nav-icon">📊</span>الرئيسية</button>
            <button class="bottom-nav-item" data-page="attendance" onclick="navTo('attendance')"><span class="nav-icon">📅</span>الحضور</button>
            <button class="bottom-nav-item" data-page="students" onclick="navTo('students')"><span class="nav-icon">👦🏻</span>الطلاب</button>
            <button class="bottom-nav-item" data-page="excellence" onclick="navTo('excellence')"><span class="nav-icon">🏆</span>التميز</button>
            <button class="bottom-nav-item" data-page="ai" onclick="navTo('ai')"><span class="nav-icon">🤖</span>الذكي</button>
        </div>
    </div>

    <!-- النوافذ المنبثقة -->
    <div class="modal-overlay" id="studentModal">
        <div class="modal">
            <h3 id="studentModalTitle">➕ إضافة طالب</h3>
            <div class="form-group"><label>الاسم الكامل *</label><input type="text" id="fName"></div>
            <div class="form-group"><label>المجموعة</label><input type="text" id="fGroup"></div>
            <div class="form-group"><label>النصاب المطلوب</label><input type="text" id="fNisab" placeholder="مثال: سورة النبأ 1-20"></div>
            <div class="form-group"><label>ملاحظات</label><textarea id="fNotes" rows="2"></textarea></div>
            <div class="modal-actions">
                <button class="btn btn-outline btn-sm" onclick="closeStudentModal()">إلغاء</button>
                <button class="btn btn-primary btn-sm" onclick="saveStudent()">حفظ</button>
            </div>
        </div>
    </div>

    <div class="modal-overlay" id="absenceModal">
        <div class="modal">
            <h3>🚨 تنبيه: تجاوز حد الغياب</h3>
            <p id="absenceText" style="font-size:13px;margin-bottom:12px;"></p>
            <div class="modal-actions">
                <button class="btn btn-outline btn-sm" onclick="keepStudent()">إبقاء الطالب</button>
                <button class="btn btn-danger btn-sm" onclick="archiveStudent()">🗄️ نقل للأرشيف</button>
            </div>
        </div>
    </div>

    <script>
        // تجنب الأخطاء في المتصفحات القديمة
        (function() {
            // ========== بيانات ==========
            var STORAGE_KEY = 'baraem_almazn_data';
            var TEACHER_CODE = '000';
            var ABSENCE_LIMIT = 7;
            var STUDENT_NAMES = [
                'نور معاذ', 'وتين عادل', 'احمد اسامه', 'مسك ياسر', 'ادم زيد', 'عسل عقيل',
                'نور صالح', 'ملاك صالح', 'مهره فهد', 'سعد مبارك', 'همام علي', 'امنه محمد',
                'يوسف عمار', 'تركي فهد', 'ريم التميمي', 'محمد احمد', 'زياد هاشم', 'رودينا ناظر',
                'سيلينا ناظر', 'رند مجول', 'ريتال مجول', 'محمد ناظر', 'متيم ناظر', 'مريم محمد'
            ];

            var data = null;
            var currentUser = null;
            var currentPage = 'dashboard';
            var loginRole = 'teacher';
            var editingStudentId = null;
            var pendingArchiveId = null;

            function getDefaultData() {
                return { students: [], attendance: {}, nisabLog: {}, archived: [], weeklyExcellence: {}, monthlyExcellence: {} };
            }

            function safeStorageGet(key) {
                try { return localStorage.getItem(key); } catch(e) { return null; }
            }
            function safeStorageSet(key, value) {
                try { localStorage.setItem(key, value); } catch(e) { /* ignore */ }
            }

            function loadData() {
                var stored = safeStorageGet(STORAGE_KEY);
                if (stored) {
                    try {
                        data = JSON.parse(stored);
                    } catch(e) { data = getDefaultData(); }
                } else {
                    data = getDefaultData();
                }
                if (!data.students || !Array.isArray(data.students) || data.students.length === 0) {
                    data = getDefaultData();
                    seedData();
                }
                if (!data.attendance) data.attendance = {};
                if (!data.nisabLog) data.nisabLog = {};
                if (!data.archived) data.archived = [];
                if (!data.weeklyExcellence) data.weeklyExcellence = {};
                if (!data.monthlyExcellence) data.monthlyExcellence = {};
                safeStorageSet(STORAGE_KEY, JSON.stringify(data));
            }

            function seedData() {
                data.students = STUDENT_NAMES.map(function(name, i) {
                    return {
                        id: 's' + Date.now() + '_' + i,
                        grsId: 'GRS-' + String(i + 1).padStart(4, '0'),
                        name: name,
                        group: ['حلقة الفجر', 'حلقة العصر', 'حلقة المساء'][i % 3],
                        teacher: 'المعلمة',
                        joinDate: new Date().toISOString().split('T')[0],
                        nisabRequired: 'سورة النبأ 1-20',
                        nisabCompleted: '1-15',
                        nisabPercentage: 70 + Math.floor(Math.random() * 30),
                        attendanceCount: 10 + Math.floor(Math.random() * 15),
                        absenceCount: Math.floor(Math.random() * 5),
                        excusedCount: Math.floor(Math.random() * 3),
                        lateCount: Math.floor(Math.random() * 3),
                        status: 'نشط',
                        badges: [],
                        notes: []
                    };
                });
                var today = new Date();
                for (var d = 0; d < 20; d++) {
                    var dt = new Date(today);
                    dt.setDate(dt.getDate() - d);
                    var ds = dt.toISOString().split('T')[0];
                    var day = dt.getDay();
                    if (day >= 0 && day <= 3) {
                        if (!data.attendance[ds]) data.attendance[ds] = {};
                        data.students.forEach(function(s) {
                            var r = Math.random();
                            if (r > 0.85) data.attendance[ds][s.id] = 'absent';
                            else if (r > 0.78) data.attendance[ds][s.id] = 'excused';
                            else if (r > 0.70) data.attendance[ds][s.id] = 'late';
                            else data.attendance[ds][s.id] = 'present';
                        });
                    }
                }
                data.students.forEach(function(s) {
                    if (Math.random() > 0.6) s.badges.push('🌟 بطل الأسبوع');
                    if (Math.random() > 0.7) s.badges.push('📖 حافظ مجتهد');
                });
                safeStorageSet(STORAGE_KEY, JSON.stringify(data));
            }

            function generateGrsId() { return 'GRS-' + String(data.students.length + data.archived.length + 1).padStart(4, '0'); }
            function getToday() { return new Date().toISOString().split('T')[0]; }
            function getDayName(ds) { var days = ['الأحد', 'الاثنين', 'الثلاثاء', 'الأربعاء', 'الخميس', 'الجمعة', 'السبت']; return days[new Date(ds).getDay()]; }
            function getWeekKey(ds) { var d = new Date(ds); var ys = new Date(d.getFullYear(), 0, 1); var wk = Math.ceil((((d - ys) / 86400000) + ys.getDay() + 1) / 7); return d.getFullYear() + '-W' + String(wk).padStart(2, '0'); }
            function getMonthKey(ds) { return ds.substring(0, 7); }
            function isThursday(ds) { return new Date(ds).getDay() === 4; }

            function showToast(msg, type) {
                var el = document.createElement('div');
                el.className = 'toast ' + (type || 'info');
                el.textContent = msg;
                document.body.appendChild(el);
                setTimeout(function() { el.remove(); }, 2500);
            }

            function initBg() {
                var bg = document.getElementById('bgDecor');
                if (!bg) return;
                bg.innerHTML = '';
                var stars = ['✦', '⭐', '✨', '🌟'];
                for (var i = 0; i < 18; i++) {
                    var s = document.createElement('span');
                    s.className = 'star';
                    s.textContent = stars[i % 4];
                    s.style.left = Math.random() * 95 + '%';
                    s.style.top = Math.random() * 85 + '%';
                    s.style.animationDelay = Math.random() * 3 + 's';
                    s.style.fontSize = (7 + Math.random() * 8) + 'px';
                    bg.appendChild(s);
                }
                for (var j = 0; j < 4; j++) {
                    var c = document.createElement('span');
                    c.className = 'cloud';
                    c.textContent = '☁️';
                    c.style.left = Math.random() * 80 + '%';
                    c.style.top = Math.random() * 70 + '%';
                    c.style.animationDelay = Math.random() * 10 + 's';
                    bg.appendChild(c);
                }
            }

            // ========== تسجيل الدخول ==========
            window.switchLogin = function(role) {
                loginRole = role;
                var tabs = document.querySelectorAll('.login-tab');
                tabs.forEach(function(t) { t.classList.toggle('active', t.dataset.role === role); });
                var u = document.getElementById('loginUser');
                var p = document.getElementById('loginPass');
                if (role === 'teacher') {
                    u.placeholder = 'رمز المعلمة (000)';
                    p.style.display = 'block';
                    p.placeholder = 'كلمة المرور (فارغة)';
                } else {
                    u.placeholder = 'الاسم الثنائي للطالب';
                    p.style.display = 'none';
                }
                document.getElementById('loginError').classList.remove('show');
            };

            window.handleLogin = function() {
                var u = document.getElementById('loginUser').value.trim();
                var p = document.getElementById('loginPass').value.trim();
                var err = document.getElementById('loginError');
                if (loginRole === 'teacher') {
                    if (u === TEACHER_CODE && p === '') {
                        currentUser = { role: 'teacher', name: 'المعلمة' };
                        enterApp();
                    } else {
                        err.textContent = 'رمز المعلمة غير صحيح أو كلمة المرور غير فارغة';
                        err.classList.add('show');
                    }
                } else {
                    var student = data.students.find(function(s) { return s.name.trim() === u; });
                    if (student) {
                        currentUser = { role: 'parent', studentId: student.id, name: student.name };
                        enterApp();
                    } else {
                        err.textContent = 'لم يتم العثور على طالب بهذا الاسم';
                        err.classList.add('show');
                    }
                }
            };

            function enterApp() {
                document.getElementById('loginScreen').classList.add('hidden');
                document.getElementById('appContainer').classList.add('show');
                if (currentUser.role === 'teacher') {
                    document.getElementById('roleBadge').textContent = '👩🏻‍🏫 معلمة';
                    document.getElementById('userName').textContent = 'رمز: 000';
                    document.getElementById('desktopNav').style.display = 'flex';
                    document.getElementById('bottomNav').style.display = 'flex';
                } else {
                    document.getElementById('roleBadge').textContent = '👨🏻‍👩🏻 ولي أمر';
                    document.getElementById('userName').textContent = 'ولي أمر: ' + currentUser.name;
                    document.getElementById('desktopNav').style.display = 'none';
                    document.getElementById('bottomNav').style.display = 'none';
                }
                navTo('dashboard');
            }

            window.handleLogout = function() {
                currentUser = null;
                document.getElementById('appContainer').classList.remove('show');
                document.getElementById('loginScreen').classList.remove('hidden');
                document.getElementById('loginUser').value = '';
                document.getElementById('loginPass').value = '';
            };

            // ========== التنقل ==========
            window.navTo = function(page) {
                currentPage = page;
                var sections = document.querySelectorAll('.page-section');
                sections.forEach(function(p) { p.classList.remove('active'); });
                document.getElementById('page-' + page).classList.add('active');
                var navTabs = document.querySelectorAll('.nav-tab');
                navTabs.forEach(function(t) { t.classList.toggle('active', t.dataset.page === page); });
                var bottomItems = document.querySelectorAll('.bottom-nav-item');
                bottomItems.forEach(function(t) { t.classList.toggle('active', t.dataset.page === page); });
                renderPage(page);
                window.scrollTo({ top: 0, behavior: 'smooth' });
            };

            function renderPage(page) {
                if (currentUser && currentUser.role === 'parent') { renderParent(); return; }
                switch (page) {
                    case 'dashboard': renderDashboard(); break;
                    case 'attendance': renderAttendance(); break;
                    case 'students': renderStudents(); break;
                    case 'nisab': renderNisab(); break;
                    case 'excellence': renderExcellence(); break;
                    case 'reports': renderReports(); break;
                    case 'ai': renderAI(); break;
                }
            }

            // ========== لوحة التحكم ==========
            function renderDashboard() {
                var today = getToday();
                var att = data.attendance[today] || {};
                var pres = 0, abs = 0, exc = 0, late = 0;
                data.students.forEach(function(s) { 
                    var st = att[s.id];
                    if (st === 'present') pres++;
                    else if (st === 'absent') abs++;
                    else if (st === 'excused') exc++;
                    else if (st === 'late') late++;
                });
                var avg = data.students.length ? Math.round(data.students.reduce(function(sum, s) { return sum + (s.nisabPercentage || 0); }, 0) / data.students.length) : 0;
                var high = data.students.filter(function(s) { return (s.nisabPercentage || 0) >= 85; }).length;
                var needAtt = data.students.filter(function(s) { return (s.nisabPercentage || 0) < 60; }).length;
                var overLim = data.students.filter(function(s) { return (s.absenceCount || 0) >= ABSENCE_LIMIT; }).length;

                var html = '<div class="stats-grid">' +
                    '<div class="stat-card"><div class="stat-icon">👥</div><div class="stat-value">' + data.students.length + '</div><div class="stat-label">إجمالي الطلاب</div></div>' +
                    '<div class="stat-card mint"><div class="stat-icon">🟢</div><div class="stat-value">' + pres + '</div><div class="stat-label">حاضر اليوم</div></div>' +
                    '<div class="stat-card pink"><div class="stat-icon">🔴</div><div class="stat-value">' + abs + '</div><div class="stat-label">غائب</div></div>' +
                    '<div class="stat-card gold"><div class="stat-icon">🟡</div><div class="stat-value">' + exc + '</div><div class="stat-label">معتذر</div></div>' +
                    '<div class="stat-card"><div class="stat-icon">📊</div><div class="stat-value">' + avg + '%</div><div class="stat-label">متوسط الإنجاز</div></div>' +
                    '<div class="stat-card mint"><div class="stat-icon">🏆</div><div class="stat-value">' + high + '</div><div class="stat-label">متفوقون</div></div>' +
                    '<div class="stat-card warning"><div class="stat-icon">⚠️</div><div class="stat-value">' + needAtt + '</div><div class="stat-label">يحتاجون متابعة</div></div>' +
                    '<div class="stat-card danger"><div class="stat-icon">🚨</div><div class="stat-value">' + overLim + '</div><div class="stat-label">تجاوزوا الحد</div></div>' +
                '</div>';

                html += '<div class="card"><div class="card-title">📋 جدول سريع</div><div class="table-container"><table>' +
                    '<thead><tr><th>الطالب</th><th>الحضور</th><th>النصاب</th><th>الإنجاز</th><th>الغياب</th><th>الحالة</th></tr></thead><tbody>';
                data.students.forEach(function(s) {
                    var st = att[s.id] || '-';
                    var stL = st === 'present' ? '🟢' : st === 'absent' ? '🔴' : st === 'excused' ? '🟡' : st === 'late' ? '🟠' : '⚪';
                    var warn = (s.absenceCount || 0) >= ABSENCE_LIMIT ? '🚨 مرشح' : (s.absenceCount || 0) >= ABSENCE_LIMIT - 2 ? '⚠️ قريب' : '✅';
                    html += '<tr><td>' + s.name + '</td><td>' + stL + '</td><td>' + (s.nisabRequired || '-') + '</td>' +
                        '<td><div class="progress-bar" style="width:60px;margin:0;"><div class="progress-fill ' + ((s.nisabPercentage || 0) >= 90 ? '' : (s.nisabPercentage || 0) < 60 ? 'pink' : 'blue') + '" style="width:' + (s.nisabPercentage || 0) + '%;"></div></div>' + (s.nisabPercentage || 0) + '%</td>' +
                        '<td>' + (s.absenceCount || 0) + '</td><td>' + warn + '</td></tr>';
                });
                html += '</tbody></table></div></div>';

                if (overLim > 0) {
                    html += '<div class="card" style="border-color:var(--danger);"><div class="card-title">🚨 طلاب تجاوزوا حد الغياب</div>';
                    data.students.filter(function(s) { return (s.absenceCount || 0) >= ABSENCE_LIMIT; }).forEach(function(s) {
                        html += '<p style="font-size:12px;margin-bottom:4px;">🚨 <strong>' + s.name + '</strong> (' + s.absenceCount + ' غياب) — <button class="btn btn-sm btn-danger" onclick="showAbsenceModal(\'' + s.id + '\')">مراجعة</button></p>';
                    });
                    html += '</div>';
                }
                document.getElementById('page-dashboard').innerHTML = html;
            }

            // ========== الحضور ==========
            function renderAttendance() {
                var today = getToday();
                var dayName = getDayName(today);
                var att = data.attendance[today] || {};
                var pres = 0, abs = 0, exc = 0, late = 0;
                data.students.forEach(function(s) { var st = att[s.id]; if (st === 'present') pres++; else if (st === 'absent') abs++; else if (st === 'excused') exc++; else if (st === 'late') late++; });
                var weekDays = ['الأحد', 'الاثنين', 'الثلاثاء', 'الأربعاء', 'الخميس', 'الجمعة', 'السبت'];
                var todayDow = new Date().getDay();
                var wdHtml = '';
                weekDays.forEach(function(d, i) {
                    var cls = i === todayDow ? 'active' : '';
                    var isR = i === 4;
                    wdHtml += '<span class="week-day ' + cls + ' ' + (isR ? 'result' : '') + '">' + d + (isR ? ' 🏆' : '') + '</span>';
                });

                var html = '<div class="week-days">' + wdHtml + '</div>' +
                    '<div class="stats-grid">' +
                    '<div class="stat-card"><div class="stat-icon">👥</div><div class="stat-value">' + data.students.length + '</div><div class="stat-label">إجمالي</div></div>' +
                    '<div class="stat-card mint"><div class="stat-icon">🟢</div><div class="stat-value">' + pres + '</div><div class="stat-label">حاضر</div></div>' +
                    '<div class="stat-card gold"><div class="stat-icon">🟡</div><div class="stat-value">' + exc + '</div><div class="stat-label">معتذر</div></div>' +
                    '<div class="stat-card warning"><div class="stat-icon">🟠</div><div class="stat-value">' + late + '</div><div class="stat-label">متأخر</div></div>' +
                    '<div class="stat-card pink"><div class="stat-icon">🔴</div><div class="stat-value">' + abs + '</div><div class="stat-label">غائب</div></div>' +
                    '</div>' +
                    '<div class="card"><div class="card-title">📅 تسجيل حضور ' + dayName + ' (' + today + ')</div><div class="table-container"><table>' +
                    '<thead><tr><th>الطالب</th><th>الحالة</th><th>أزرار سريعة</th></tr></thead><tbody>';
                data.students.forEach(function(s) {
                    var st = att[s.id] || '';
                    var stL = st === 'present' ? '🟢 حاضر' : st === 'absent' ? '🔴 غائب' : st === 'excused' ? '🟡 معتذر' : st === 'late' ? '🟠 متأخر' : '⚪ —';
                    html += '<tr><td>' + s.name + '<br><small style="color:var(--light)">' + s.grsId + '</small></td><td>' + stL + '</td><td><div style="display:flex;gap:3px;flex-wrap:wrap;">' +
                        '<button class="att-btn present ' + (st === 'present' ? 'active' : '') + '" onclick="markAtt(\'' + s.id + '\',\'present\')">🟢 حاضر</button>' +
                        '<button class="att-btn excused ' + (st === 'excused' ? 'active' : '') + '" onclick="markAtt(\'' + s.id + '\',\'excused\')">🟡 معتذر</button>' +
                        '<button class="att-btn late ' + (st === 'late' ? 'active' : '') + '" onclick="markAtt(\'' + s.id + '\',\'late\')">🟠 متأخر</button>' +
                        '<button class="att-btn absent ' + (st === 'absent' ? 'active' : '') + '" onclick="markAtt(\'' + s.id + '\',\'absent\')">🔴 غائب</button>' +
                    '</div></td></tr>';
                });
                html += '</tbody></table></div></div>';
                document.getElementById('page-attendance').innerHTML = html;
            }

            window.markAtt = function(sid, status) {
                var today = getToday();
                if (!data.attendance[today]) data.attendance[today] = {};
                var prev = data.attendance[today][sid];
                data.attendance[today][sid] = status;
                var s = data.students.find(function(x) { return x.id === sid; });
                if (s) {
                    if (prev === 'absent') s.absenceCount = Math.max(0, (s.absenceCount || 0) - 1);
                    if (prev === 'present') s.attendanceCount = Math.max(0, (s.attendanceCount || 0) - 1);
                    if (prev === 'excused') s.excusedCount = Math.max(0, (s.excusedCount || 0) - 1);
                    if (prev === 'late') s.lateCount = Math.max(0, (s.lateCount || 0) - 1);
                    if (status === 'absent') s.absenceCount = (s.absenceCount || 0) + 1;
                    if (status === 'present') s.attendanceCount = (s.attendanceCount || 0) + 1;
                    if (status === 'excused') s.excusedCount = (s.excusedCount || 0) + 1;
                    if (status === 'late') s.lateCount = (s.lateCount || 0) + 1;
                }
                safeStorageSet(STORAGE_KEY, JSON.stringify(data));
                renderAttendance();
                showToast('تم التسجيل ✓', 'success');
            };

            // ========== الطلاب ==========
            function renderStudents() {
                var html = '<div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:12px;flex-wrap:wrap;gap:8px;">' +
                    '<h3 style="font-size:15px;font-weight:700;">👦🏻 إدارة الطلاب</h3>' +
                    '<button class="btn btn-primary btn-sm" onclick="openAddStudent()">➕ إضافة</button></div>' +
                    '<div class="card"><div class="table-container"><table>' +
                    '<thead><tr><th>الطالب</th><th>المعرف</th><th>المجموعة</th><th>الإنجاز</th><th>الغياب</th><th>إجراءات</th></tr></thead><tbody>';
                data.students.forEach(function(s) {
                    html += '<tr><td>' + s.name + '</td><td>' + s.grsId + '</td><td>' + (s.group || '-') + '</td>' +
                        '<td><div class="progress-bar" style="width:55px;margin:0;"><div class="progress-fill ' + ((s.nisabPercentage || 0) >= 60 ? '' : 'pink') + '" style="width:' + (s.nisabPercentage || 0) + '%;"></div></div>' + (s.nisabPercentage || 0) + '%</td>' +
                        '<td>' + (s.absenceCount || 0) + '</td>' +
                        '<td><button class="btn btn-sm btn-outline" onclick="openEditStudent(\'' + s.id + '\')">✏️</button> <button class="btn btn-sm btn-danger" onclick="showAbsenceModal(\'' + s.id + '\')">🚨</button></td></tr>';
                });
                html += '</tbody></table></div></div>';
                document.getElementById('page-students').innerHTML = html;
            }

            window.openAddStudent = function() {
                editingStudentId = null;
                document.getElementById('studentModalTitle').textContent = '➕ إضافة طالب';
                document.getElementById('fName').value = '';
                document.getElementById('fGroup').value = '';
                document.getElementById('fNisab').value = '';
                document.getElementById('fNotes').value = '';
                document.getElementById('studentModal').classList.add('show');
            };

            window.openEditStudent = function(sid) {
                var s = data.students.find(function(x) { return x.id === sid; });
                if (!s) return;
                editingStudentId = sid;
                document.getElementById('studentModalTitle').textContent = '✏️ تعديل طالب';
                document.getElementById('fName').value = s.name;
                document.getElementById('fGroup').value = s.group || '';
                document.getElementById('fNisab').value = s.nisabRequired || '';
                document.getElementById('fNotes').value = (s.notes || []).join(', ');
                document.getElementById('studentModal').classList.add('show');
            };

            window.closeStudentModal = function() {
                document.getElementById('studentModal').classList.remove('show');
                editingStudentId = null;
            };

            window.saveStudent = function() {
                var name = document.getElementById('fName').value.trim();
                if (!name) { showToast('الاسم مطلوب', 'error'); return; }
                var group = document.getElementById('fGroup').value.trim();
                var nisab = document.getElementById('fNisab').value.trim();
                var notes = document.getElementById('fNotes').value.trim();
                if (editingStudentId) {
                    var s = data.students.find(function(x) { return x.id === editingStudentId; });
                    if (s) { s.name = name; s.group = group; s.nisabRequired = nisab; if (notes) s.notes = notes.split(',').map(function(n) { return n.trim(); }); }
                    showToast('تم التعديل ✓', 'success');
                } else {
                    data.students.push({
                        id: 's' + Date.now(),
                        grsId: generateGrsId(),
                        name: name,
                        group: group,
                        teacher: 'المعلمة',
                        joinDate: getToday(),
                        nisabRequired: nisab,
                        nisabCompleted: '',
                        nisabPercentage: 0,
                        attendanceCount: 0,
                        absenceCount: 0,
                        excusedCount: 0,
                        lateCount: 0,
                        status: 'نشط',
                        badges: [],
                        notes: notes ? notes.split(',').map(function(n) { return n.trim(); }) : []
                    });
                    showToast('تمت الإضافة 🎉', 'success');
                }
                safeStorageSet(STORAGE_KEY, JSON.stringify(data));
                closeStudentModal();
                renderStudents();
                renderDashboard();
            };

            window.showAbsenceModal = function(sid) {
                var s = data.students.find(function(x) { return x.id === sid; });
                if (!s) return;
                pendingArchiveId = sid;
                document.getElementById('absenceText').textContent = 'الطالب ' + s.name + ' (' + s.grsId + ') تجاوز حد الغياب (' + ABSENCE_LIMIT + ' غيابات). عدد غياباته: ' + (s.absenceCount || 0) + '. هل تريدين نقله للأرشيف؟';
                document.getElementById('absenceModal').classList.add('show');
            };

            window.keepStudent = function() {
                document.getElementById('absenceModal').classList.remove('show');
                pendingArchiveId = null;
                showToast('تم إبقاء الطالب', 'info');
            };

            window.archiveStudent = function() {
                if (!pendingArchiveId) return;
                var idx = data.students.findIndex(function(s) { return s.id === pendingArchiveId; });
                if (idx > -1) {
                    var s = data.students[idx];
                    s.status = 'مؤرشف';
                    data.archived.push(s);
                    data.students.splice(idx, 1);
                    safeStorageSet(STORAGE_KEY, JSON.stringify(data));
                    showToast('تم النقل للأرشيف 🗄️', 'success');
                    renderStudents();
                    renderDashboard();
                }
                document.getElementById('absenceModal').classList.remove('show');
                pendingArchiveId = null;
            };

            // ========== النصاب ==========
            function renderNisab() {
                if (data.students.length === 0) {
                    document.getElementById('page-nisab').innerHTML = '<div class="empty-state">لا يوجد طلاب مسجلون</div>';
                    return;
                }
                var firstStudent = data.students[0];
                renderNisabFor(firstStudent.id);
            }

            function renderNisabFor(sid) {
                var s = data.students.find(function(x) { return x.id === sid; });
                if (!s) return;
                var log = data.nisabLog[sid] || [];
                var selectHtml = '<select id="nisabSelect" onchange="renderNisabFor(this.value)" style="padding:8px 12px;border:2px solid #E8ECF0;border-radius:8px;font-family:var(--font);font-size:12px;">';
                data.students.forEach(function(stu) {
                    selectHtml += '<option value="' + stu.id + '"' + (stu.id === sid ? ' selected' : '') + '>' + stu.name + '</option>';
                });
                selectHtml += '</select>';
                var html = '<div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:12px;flex-wrap:wrap;gap:8px;"><h3 style="font-size:15px;font-weight:700;">📖 متابعة النصاب</h3>' + selectHtml + '</div>';
                html += '<div class="card"><div class="card-title">' + s.name + ' — النصاب اليومي</div>' +
                    '<p style="font-size:12px;">المطلوب: ' + (s.nisabRequired || '-') + '</p>' +
                    '<p style="font-size:12px;">المنجز: ' + (s.nisabCompleted || '-') + '</p>' +
                    '<div class="progress-bar" style="height:12px;"><div class="progress-fill blue" style="width:' + (s.nisabPercentage || 0) + '%;"></div></div>' +
                    '<p style="font-size:12px;">الإنجاز: <strong>' + (s.nisabPercentage || 0) + '%</strong></p>' +
                    '<div style="display:flex;gap:6px;margin-top:10px;flex-wrap:wrap;">' +
                    '<button class="btn btn-sm btn-mint" onclick="updateNisab(\'' + s.id + '\',10)">+10%</button>' +
                    '<button class="btn btn-sm btn-mint" onclick="updateNisab(\'' + s.id + '\',25)">+25%</button>' +
                    '<button class="btn btn-sm btn-mint" onclick="updateNisab(\'' + s.id + '\',50)">+50%</button>' +
                    '<button class="btn btn-sm btn-gold" onclick="updateNisab(\'' + s.id + '\',100)">🌟 إنجاز كامل</button>' +
                    '</div></div>' +
                    '<div class="card"><div class="card-title">📜 سجل النصاب</div>';
                if (log.length > 0) {
                    html += '<table><thead><tr><th>التاريخ</th><th>النسبة</th></tr></thead><tbody>';
                    log.forEach(function(l) { html += '<tr><td>' + l.date + '</td><td>' + l.percentage + '%</td></tr>'; });
                    html += '</tbody></table>';
                } else {
                    html += '<div class="empty-state">لا يوجد سجل</div>';
                }
                html += '</div>';
                document.getElementById('page-nisab').innerHTML = html;
            }

            window.renderNisabFor = function(sid) { renderNisabFor(sid); };

            window.updateNisab = function(sid, inc) {
                var s = data.students.find(function(x) { return x.id === sid; });
                if (!s) return;
                var cur = s.nisabPercentage || 0;
                s.nisabPercentage = Math.min(100, cur + inc);
                s.nisabCompleted = s.nisabRequired || s.nisabCompleted || '';
                if (!data.nisabLog[sid]) data.nisabLog[sid] = [];
                data.nisabLog[sid].push({ date: getToday(), percentage: s.nisabPercentage });
                if (s.nisabPercentage >= 100 && s.badges.indexOf('🏆 إنجاز النصاب') === -1) {
                    s.badges.push('🏆 إنجاز النصاب');
                    showToast('🎉 شارة إنجاز النصاب!', 'success');
                }
                safeStorageSet(STORAGE_KEY, JSON.stringify(data));
                renderNisabFor(sid);
            };

            // ========== التميز ==========
            function renderExcellence() {
                if (currentUser && currentUser.role === 'parent') {
                    var s = data.students.find(function(x) { return x.id === currentUser.studentId; });
                    if (!s) return;
                    var badges = s.badges || [];
                    document.getElementById('page-excellence').innerHTML = '<div class="card"><div class="card-title">🏆 شارات ' + s.name + '</div>' + (badges.length ? badges.map(function(b) { return '<span class="badge-item earned">' + b + '</span>'; }).join(' ') : '<div class="empty-state">لا توجد شارات</div>') + '</div>';
                    return;
                }
                var today = getToday();
                var wkKey = getWeekKey(today);
                var monKey = getMonthKey(today);
                var wkWinners = data.weeklyExcellence[wkKey] || [];
                if (isThursday(today) && wkWinners.length === 0) {
                    autoCalcWeekly();
                    wkWinners = data.weeklyExcellence[wkKey] || [];
                }
                var monWinners = data.monthlyExcellence[monKey] || [];
                var html = '<h3 style="font-size:15px;font-weight:700;margin-bottom:12px;">🏆 مركز التميز</h3>';
                html += '<div class="card"><div class="card-title">🌟 متميزو الأسبوع (' + wkKey + ')</div>';
                if (wkWinners.length) {
                    wkWinners.forEach(function(sid) {
                        var s = data.students.find(function(x) { return x.id === sid; });
                        if (!s) return;
                        html += '<div class="excellence-card"><span class="rank">🏆</span><div class="name">' + s.name + '</div><div style="font-size:11px;">إنجاز: ' + (s.nisabPercentage || 0) + '% | غياب: ' + (s.absenceCount || 0) + '</div><div class="reason">⭐ حضور كامل والتزام بالنصاب</div></div>';
                    });
                } else {
                    html += '<div class="empty-state">لم يُحتسب بعد</div>';
                }
                html += '</div>';
                html += '<div class="card"><div class="card-title">💎 متميزو الشهر (' + monKey + ')</div>';
                if (monWinners.length) {
                    var ranks = ['🥇', '🥈', '🥉'];
                    monWinners.forEach(function(sid, i) {
                        var s = data.students.find(function(x) { return x.id === sid; });
                        if (!s) return;
                        html += '<div class="excellence-card"><span class="rank">' + (ranks[i] || '⭐') + '</span><div class="name">' + s.name + '</div><div style="font-size:11px;">المركز ' + (i + 1) + '</div><div class="reason">💎 ثبات ومثابرة</div></div>';
                    });
                } else {
                    html += '<div class="empty-state">لم يُحتسب بعد</div>';
                }
                html += '</div>';
                html += '<div class="card"><div class="card-title">📜 سجل الشارات</div>';
                var studentsWithBadges = data.students.filter(function(s) { return (s.badges && s.badges.length > 0); });
                if (studentsWithBadges.length) {
                    studentsWithBadges.forEach(function(s) {
                        html += '<p style="font-size:11px;margin-bottom:3px;"><strong>' + s.name + ':</strong> ' + s.badges.map(function(b) { return '<span class="badge-item earned">' + b + '</span>'; }).join(' ') + '</p>';
                    });
                } else {
                    html += '<div class="empty-state">لا شارات بعد</div>';
                }
                html += '</div>';
                document.getElementById('page-excellence').innerHTML = html;
            }

            function autoCalcWeekly() {
                var today = getToday();
                var wk = getWeekKey(today);
                var elig = data.students.filter(function(s) { return (s.absenceCount || 0) <= 1 && (s.nisabPercentage || 0) >= 80; })
                    .sort(function(a, b) { return (b.nisabPercentage || 0) - (a.nisabPercentage || 0); });
                var winners = elig.slice(0, 5).map(function(s) { return s.id; });
                data.weeklyExcellence[wk] = winners;
                winners.forEach(function(sid) {
                    var s = data.students.find(function(x) { return x.id === sid; });
                    if (s && s.badges.indexOf('🌟 بطل الأسبوع') === -1) s.badges.push('🌟 بطل الأسبوع');
                });
                var mon = getMonthKey(today);
                var wkCount = Object.keys(data.weeklyExcellence).filter(function(k) { return k.indexOf(today.substring(0, 4)) === 0; }).length;
                if (wkCount >= 4 && !data.monthlyExcellence[mon]) {
                    var mElig = data.students.filter(function(s) { return (s.absenceCount || 0) <= 2 && (s.nisabPercentage || 0) >= 75; })
                        .sort(function(a, b) { return (b.nisabPercentage || 0) - (a.nisabPercentage || 0); });
                    data.monthlyExcellence[mon] = mElig.slice(0, 3).map(function(s) { return s.id; });
                    mElig.slice(0, 3).forEach(function(s) {
                        if (s.badges.indexOf('💎 متميز الشهر') === -1) s.badges.push('💎 متميز الشهر');
                    });
                }
                safeStorageSet(STORAGE_KEY, JSON.stringify(data));
            }

            // ========== التقارير ==========
            function renderReports() {
                var overLim = data.students.filter(function(s) { return (s.absenceCount || 0) >= ABSENCE_LIMIT; }).length;
                var html = '<h3 style="font-size:15px;font-weight:700;margin-bottom:12px;">📊 التقارير</h3>' +
                    '<div class="stats-grid">' +
                    '<div class="stat-card"><div class="stat-icon">📅</div><div class="stat-value">' + data.students.length + '</div><div class="stat-label">إجمالي</div></div>' +
                    '<div class="stat-card mint"><div class="stat-icon">📊</div><div class="stat-value">' + Object.keys(data.attendance).length + '</div><div class="stat-label">أيام مسجلة</div></div>' +
                    '<div class="stat-card danger"><div class="stat-icon">⚠️</div><div class="stat-value">' + overLim + '</div><div class="stat-label">مرشحون للحذف</div></div>' +
                    '<div class="stat-card gold"><div class="stat-icon">🏆</div><div class="stat-value">' + data.students.filter(function(s) { return s.badges && s.badges.length > 0; }).length + '</div><div class="stat-label">متميزون</div></div>' +
                    '</div>' +
                    '<div class="card"><div class="card-title">📋 أنواع التقارير</div><div style="display:flex;flex-wrap:wrap;gap:6px;">' +
                    '<button class="btn btn-sm btn-outline" onclick="genReport(\'att\')">📅 الحضور اليومي</button>' +
                    '<button class="btn btn-sm btn-outline" onclick="genReport(\'abs\')">📊 الغياب</button>' +
                    '<button class="btn btn-sm btn-outline" onclick="genReport(\'nisab\')">📖 النصاب</button>' +
                    '<button class="btn btn-sm btn-outline" onclick="genReport(\'prog\')">📈 التقدم</button>' +
                    '<button class="btn btn-sm btn-outline" onclick="genReport(\'exc\')">🏆 المتفوقون</button>' +
                    '<button class="btn btn-sm btn-outline" onclick="genReport(\'attn\')">⚠️ يحتاجون متابعة</button>' +
                    '<button class="btn btn-sm btn-outline" onclick="genReport(\'arch\')">🗄️ المرشحون</button>' +
                    '</div><div id="reportOutput" style="margin-top:10px;"><div class="empty-state">اختر نوع التقرير</div></div></div>';
                document.getElementById('page-reports').innerHTML = html;
            }

            window.genReport = function(type) {
                var today = getToday();
                var html = '';
                switch (type) {
                    case 'att':
                        var att = data.attendance[today] || {};
                        html = '<h4 style="font-size:13px;margin-bottom:8px;">📅 الحضور — ' + today + '</h4><table><thead><tr><th>الطالب</th><th>الحالة</th></tr></thead><tbody>';
                        data.students.forEach(function(s) {
                            var st = att[s.id] || 'لم يسجل';
                            var l = st === 'present' ? '🟢 حاضر' : st === 'absent' ? '🔴 غائب' : st === 'excused' ? '🟡 معتذر' : st === 'late' ? '🟠 متأخر' : '⚪ لم يسجل';
                            html += '<tr><td>' + s.name + '</td><td>' + l + '</td></tr>';
                        });
                        html += '</tbody></table>';
                        break;
                    case 'abs':
                        var sorted = data.students.slice().sort(function(a, b) { return (b.absenceCount || 0) - (a.absenceCount || 0); });
                        html = '<h4 style="font-size:13px;margin-bottom:8px;">📊 الغياب</h4><table><thead><tr><th>الطالب</th><th>الغياب</th><th>الاعتذار</th><th>التأخر</th></tr></thead><tbody>';
                        sorted.forEach(function(s) {
                            html += '<tr><td>' + s.name + '</td><td>' + (s.absenceCount || 0) + '</td><td>' + (s.excusedCount || 0) + '</td><td>' + (s.lateCount || 0) + '</td></tr>';
                        });
                        html += '</tbody></table>';
                        break;
                    case 'nisab':
                        html = '<h4 style="font-size:13px;margin-bottom:8px;">📖 النصاب</h4><table><thead><tr><th>الطالب</th><th>المطلوب</th><th>المنجز</th><th>النسبة</th></tr></thead><tbody>';
                        data.students.forEach(function(s) {
                            html += '<tr><td>' + s.name + '</td><td>' + (s.nisabRequired || '-') + '</td><td>' + (s.nisabCompleted || '-') + '</td><td>' + (s.nisabPercentage || 0) + '%</td></tr>';
                        });
                        html += '</tbody></table>';
                        break;
                    case 'prog':
                        html = '<h4 style="font-size:13px;margin-bottom:8px;">📈 التقدم</h4><table><thead><tr><th>الطالب</th><th>الإنجاز</th><th>الحضور</th><th>الغياب</th><th>التقييم</th></tr></thead><tbody>';
                        data.students.forEach(function(s) {
                            var ev = (s.nisabPercentage || 0) >= 90 ? 'ممتاز' : (s.nisabPercentage || 0) >= 75 ? 'جيد جداً' : (s.nisabPercentage || 0) >= 60 ? 'جيد' : 'يحتاج متابعة';
                            html += '<tr><td>' + s.name + '</td><td>' + (s.nisabPercentage || 0) + '%</td><td>' + (s.attendanceCount || 0) + '</td><td>' + (s.absenceCount || 0) + '</td><td>' + ev + '</td></tr>';
                        });
                        html += '</tbody></table>';
                        break;
                    case 'exc':
                        var exc = data.students.filter(function(s) { return (s.nisabPercentage || 0) >= 85; }).sort(function(a, b) { return (b.nisabPercentage || 0) - (a.nisabPercentage || 0); });
                        html = '<h4 style="font-size:13px;margin-bottom:8px;">🏆 المتفوقون (≥85%)</h4>';
                        if (exc.length === 0) html += '<div class="empty-state">لا يوجد</div>';
                        else {
                            html += '<table><thead><tr><th>الطالب</th><th>الإنجاز</th><th>الشارات</th></tr></thead><tbody>';
                            exc.forEach(function(s) {
                                html += '<tr><td>' + s.name + '</td><td>' + (s.nisabPercentage || 0) + '%</td><td>' + (s.badges && s.badges.length ? s.badges.map(function(b) { return '<span class="badge-item earned">' + b + '</span>'; }).join(' ') : '-') + '</td></tr>';
                            });
                            html += '</tbody></table>';
                        }
                        break;
                    case 'attn':
                        var attn = data.students.filter(function(s) { return (s.nisabPercentage || 0) < 60 || (s.absenceCount || 0) >= 3; });
                        html = '<h4 style="font-size:13px;margin-bottom:8px;">⚠️ يحتاجون متابعة</h4>';
                        if (attn.length === 0) html += '<div class="empty-state">الجميع بخير ✅</div>';
                        else {
                            html += '<table><thead><tr><th>الطالب</th><th>الإنجاز</th><th>الغياب</th></tr></thead><tbody>';
                            attn.forEach(function(s) {
                                html += '<tr><td>' + s.name + '</td><td>' + (s.nisabPercentage || 0) + '%</td><td>' + (s.absenceCount || 0) + '</td></tr>';
                            });
                            html += '</tbody></table>';
                        }
                        break;
                    case 'arch':
                        var arch = data.students.filter(function(s) { return (s.absenceCount || 0) >= ABSENCE_LIMIT; });
                        html = '<h4 style="font-size:13px;margin-bottom:8px;">🗄️ مرشحون للحذف (' + ABSENCE_LIMIT + '+ غياب)</h4>';
                        if (arch.length === 0) html += '<div class="empty-state">لا يوجد ✅</div>';
                        else {
                            html += '<table><thead><tr><th>الطالب</th><th>الغياب</th><

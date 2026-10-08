<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>لوحة تحكم - فستق حلب</title>

<style>
*{
    box-sizing:border-box;
}

body{
    margin:0;
    font-family:Arial,sans-serif;
    background:#f5f5f5;
    color:#222;
}

.container{
    max-width:1100px;
    margin:auto;
    padding:15px;
}

.card{
    background:#fff;
    border-radius:16px;
    padding:20px;
    margin-bottom:20px;
    box-shadow:0 2px 10px #0001;
}

h1,h2,h3{
    margin-top:0;
}

input,
textarea,
select,
button{
    width:100%;
    padding:12px;
    margin:6px 0;
    border:1px solid #ddd;
    border-radius:9px;
    font-size:16px;
}

textarea{
    min-height:90px;
    resize:vertical;
}

button{
    background:#222;
    color:#fff;
    border:none;
    cursor:pointer;
}

button:active{
    opacity:.8;
}

.logout{
    background:#b00020;
}

#adminPanel{
    display:none;
}

.message{
    text-align:center;
    font-weight:bold;
    min-height:20px;
}

.success{
    color:green;
}

.error{
    color:#c62828;
}

.small{
    color:#666;
    font-size:14px;
}

.info{
    background:#e7f1ff;
    border-radius:10px;
    padding:12px;
    margin-bottom:15px;
    font-size:14px;
}

.warning{
    background:#fff3cd;
    color:#664d03;
    border-radius:10px;
    padding:12px;
    margin-bottom:15px;
}

.section-title{
    display:flex;
    justify-content:space-between;
    align-items:center;
    gap:10px;
    flex-wrap:wrap;
}

.section-title button{
    width:auto;
    min-width:140px;
}

.tabs{
    display:flex;
    gap:8px;
    flex-wrap:wrap;
    margin-bottom:20px;
}

.tab-button{
    width:auto;
    padding:11px 18px;
    background:#777;
}

.tab-button.active{
    background:#198754;
}

.tab-content{
    display:none;
}

.tab-content.active{
    display:block;
}

.grid{
    display:grid;
    grid-template-columns:repeat(2,1fr);
    gap:12px;
}

@media(max-width:700px){
    .grid{
        grid-template-columns:1fr;
    }
}

.field{
    margin-bottom:5px;
}

.field label{
    display:block;
    font-weight:bold;
    margin:7px 0;
}

.options{
    border:1px solid #ddd;
    border-radius:12px;
    padding:14px;
    margin:12px 0;
    background:#fafafa;
}

.unit-row{
    display:grid;
    grid-template-columns:40px 1fr 150px;
    gap:8px;
    align-items:center;
    padding:8px 0;
    border-bottom:1px solid #eee;
}

.unit-row:last-child{
    border-bottom:none;
}

.unit-row input[type="checkbox"]{
    width:auto;
    margin:0;
}

.auto-price{
    background:#eee;
}

.product{
    border:1px solid #ddd;
    border-radius:14px;
    padding:15px;
    margin:12px 0;
    background:#fafafa;
}

.product.hidden{
    opacity:.65;
    background:#eee;
}

.product.dragging{
    opacity:.4;
}

.product img{
    width:120px;
    height:120px;
    object-fit:cover;
    border-radius:10px;
    display:block;
    margin-bottom:10px;
}

.actions{
    display:flex;
    gap:8px;
    margin-top:10px;
    flex-wrap:wrap;
}

.actions button{
    flex:1;
    min-width:120px;
}

.edit{
    background:#0069d9;
}

.hide{
    background:#777;
}

.show{
    background:#198754;
}

.delete{
    background:#c62828;
}

.move{
    background:#6f42c1;
}

.save{
    background:#198754;
}

.add{
    background:#0069d9;
}

.item-box{
    border:1px solid #ddd;
    border-radius:12px;
    padding:12px;
    margin:10px 0;
    background:#fafafa;
}

.drag-item{
    display:flex;
    align-items:center;
    gap:10px;
    padding:12px;
    margin:8px 0;
    border:1px solid #ddd;
    border-radius:10px;
    background:#fff;
    cursor:grab;
}

.drag-item:active{
    cursor:grabbing;
}

.drag-handle{
    font-size:22px;
}

.drag-number{
    min-width:30px;
    font-weight:bold;
}

.drag-name{
    flex:1;
    font-weight:bold;
}

.drag-buttons{
    display:flex;
    gap:5px;
}

.drag-buttons button{
    width:auto;
    padding:8px 12px;
    margin:0;
}

.status{
    display:inline-block;
    padding:6px 10px;
    border-radius:20px;
    font-size:13px;
    margin:5px 0;
}

.status-visible{
    background:#d1e7dd;
    color:#0f5132;
}

.status-hidden{
    background:#f8d7da;
    color:#842029;
}

.empty{
    text-align:center;
    padding:25px;
    color:#777;
}

.zone-row,
.branch-row,
.social-row{
    border:1px solid #ddd;
    border-radius:12px;
    padding:12px;
    margin:10px 0;
    background:#fafafa;
}

.zone-header,
.branch-header,
.social-header{
    display:flex;
    justify-content:space-between;
    align-items:center;
    gap:10px;
}

.zone-header button,
.branch-header button,
.social-header button{
    width:auto;
    padding:8px 12px;
}

.danger{
    background:#c62828;
}

.gray{
    background:#777;
}

.green{
    background:#198754;
}

.blue{
    background:#0069d9;
}

.purple{
    background:#6f42c1;
}

.orange{
    background:#fd7e14;
}

.backup-box{
    background:#f8f9fa;
    border:1px solid #ddd;
    border-radius:12px;
    padding:15px;
    margin:12px 0;
}

.file-input{
    background:#fff;
}

.category-badge{
    display:inline-block;
    background:#e9ecef;
    padding:5px 9px;
    border-radius:20px;
    font-size:13px;
}

.product-list-title{
    background:#f1f3f5;
    padding:10px;
    border-radius:10px;
    margin-top:15px;
    font-weight:bold;
}

hr{
    border:0;
    border-top:1px solid #eee;
    margin:20px 0;
}
</style>
</head>

<body>

<div class="container">

<!-- LOGIN -->

<div id="loginPanel" class="card">

    <h1>🔐 لوحة تحكم فستق حلب</h1>

    <p>تسجيل دخول الإدارة</p>

    <input
        type="email"
        id="email"
        placeholder="البريد الإلكتروني"
        autocomplete="email">

    <input
        type="password"
        id="password"
        placeholder="كلمة المرور"
        autocomplete="current-password">

    <button onclick="login()">
        تسجيل الدخول
    </button>

    <p id="loginMessage" class="message"></p>

</div>


<!-- ADMIN -->

<div id="adminPanel">

    <div class="card">

        <div class="section-title">

            <div>
                <h1>🍰 فستق حلب</h1>

                <p class="small">
                    لوحة التحكم الكاملة للمنيو
                </p>
            </div>

            <button
                class="logout"
                onclick="logout()">
                تسجيل الخروج
            </button>

        </div>

    </div>


    <!-- TABS -->

    <div class="tabs">

        <button
            class="tab-button active"
            onclick="showTab('productsTab',this)">
            🍰 الأصناف
        </button>

        <button
            class="tab-button"
            onclick="showTab('categoriesTab',this)">
            🗂️ الأقسام
        </button>

        <button
            class="tab-button"
            onclick="showTab('deliveryTab',this)">
            🚚 التوصيل والفروع
        </button>

        <button
            class="tab-button"
            onclick="showTab('socialTab',this)">
            📱 السوشيال ميديا
        </

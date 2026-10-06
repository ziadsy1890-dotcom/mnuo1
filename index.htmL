<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Pistach D'Alep</title>

<style>
*{box-sizing:border-box}

body{
    margin:0;
    font-family:Arial,sans-serif;
    background:#f5f5f5;
    color:#222;
}

header{
    background:#222;
    color:white;
    text-align:center;
    padding:22px 10px;
}

header h1{
    margin:0;
    font-size:28px;
}

header p{
    margin:8px 0 0;
    color:#ddd;
}

.container{
    max-width:700px;
    margin:auto;
    padding:15px;
}

.categories{
    display:flex;
    gap:8px;
    overflow-x:auto;
    margin-bottom:15px;
}

.categories button{
    border:0;
    background:white;
    padding:10px 16px;
    border-radius:20px;
    white-space:nowrap;
}

.categories button.active{
    background:#222;
    color:white;
}

.menu{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:14px;
}

.item{
    background:white;
    border-radius:12px;
    overflow:hidden;
    box-shadow:0 2px 8px #00000015;
}

.item img{
    width:100%;
    height:150px;
    object-fit:cover;
}

.item-content{
    padding:12px;
}

.item h3{
    margin:0 0 6px;
}

.description{
    color:#777;
    font-size:13px;
    min-height:35px;
}

.price{
    font-size:18px;
    font-weight:bold;
    margin:8px 0;
}

.add{
    width:100%;
    padding:10px;
    border:0;
    border-radius:8px;
    background:#222;
    color:white;
}

.cart{
    background:white;
    margin-top:20px;
    padding:15px;
    border-radius:12px;
}

.cart-item{
    display:flex;
    justify-content:space-between;
    align-items:center;
    border-bottom:1px solid #eee;
    padding:10px 0;
}

.qty{
    display:flex;
    align-items:center;
    gap:7px;
}

.qty button{
    width:30px;
    height:30px;
    border:0;
    border-radius:6px;
}

.total{
    font-size:20px;
    font-weight:bold;
    margin:15px 0;
}

input,textarea{
    width:100%;
    padding:12px;
    margin:6px 0;
    border:1px solid #ddd;
    border-radius:8px;
    font-family:inherit;
}

.whatsapp{
    width:100%;
    padding:14px;
    border:0;
    border-radius:8px;
    background:#25D366;
    color:white;
    font-size:18px;
    font-weight:bold;
}

.empty{
    text-align:center;
    color:#888;
    padding:15px;
}

@media(max-width:500px){
    .menu{
        grid-template-columns:1fr;
    }
}
</style>
</head>

<body>

<header>
    <h1>🍰 Pistach D'Alep</h1>
    <p>بيستاش دي ألب</p>
</header>

<div class="container">

    <div class="categories" id="categories"></div>

    <div class="menu" id="menu"></div>

    <div class="cart">

        <h2>🛒 سلة الطلب</h2>

        <div id="cartItems">
            <div class="empty">السلة فارغة</div>
        </div>

        <div class="total">
            الإجمالي: <span id="total">0</span> جنيه
        </div>

        <input id="name" placeholder="اسم العميل">

        <input id="phone" type="tel" placeholder="رقم الهاتف">

        <textarea id="address"
        rows="3"
        placeholder="العنوان بالتفصيل"></textarea>

        <button class="whatsapp" onclick="sendWhatsApp()">
            📲 إرسال الطلب عبر واتساب
        </button>

    </div>

</div>

<script>

/* ==========================================
   الأصناف
   لتعديل المنيو غيّر هذه القائمة فقط
   ========================================== */

const products = [

    {
        id:1,
        name:"بيستاش دي ألب",
        description:"حلو فستق حلب الأصلي",
        price:150,
        category:"حلويات",
        image:"https://images.unsplash.com/photo-1578985545062-69928b1d9587"
    },

    {
        id:2,
        name:"كنافة",
        description:"كنافة طازجة بالفستق",
        price:120,
        category:"حلويات",
        image:"https://images.unsplash.com/photo-1571115177098-24ec42ed204d"
    },

    {
        id:3,
        name:"بقلاوة",
        description:"بقلاوة مشكلة",
        price:100,
        category:"حلويات",
        image:"https://images.unsplash.com/photo-1551024506-0bccd828d307"
    },

    {
        id:4,
        name:"قهوة",
        description:"قهوة عربية",
        price:50,
        category:"مشروبات",
        image:"https://images.unsplash.com/photo-1495474472287-4d71bcdd2085"
    }

];


/* رقم واتساب */

const whatsappNumber="201140653708";


let cart=[];
let currentCategory="الكل";


/* التصنيفات */

function showCategories(){

    const categories=document.getElementById("categories");

    const list=[
        "الكل",
        ...new Set(products.map(p=>p.category))
    ];

    categories.innerHTML="";

    list.forEach(category=>{

        categories.innerHTML+=`
        <button
        class="${category===currentCategory?"active":""}"
        onclick="selectCategory('${category}')">

        ${category}

        </button>
        `;

    });

}


/* اختيار التصنيف */

function selectCategory(category){

    currentCategory=category;

    showCategories();
    showProducts();

}


/* عرض المنتجات */

function showProducts(){

    const menu=document.getElementById("menu");

    menu.innerHTML="";

    const list=currentCategory==="الكل"
        ?products
        :products.filter(p=>p.category===currentCategory);

    list.forEach(product=>{

        menu.innerHTML+=`

        <div class="item">

            <img src="${product.image}"
            alt="${product.name}">

            <div class="item-content">

                <h3>${product.name}</h3>

                <div class="description">
                    ${product.description}
                </div>

                <div class="price">
                    ${product.price} جنيه
                </div>

                <button class="add"
                onclick="addToCart(${product.id})">

                    ➕ إضافة للسلة

                </button>

            </div>

        </div>

        `;

    });

}


/* إضافة للسلة */

function addToCart(id){

    const product=products.find(p=>p.id===id);

    const existing=cart.find(p=>p.id===id);

    if(existing){
        existing.quantity++;
    }else{
        cart.push({
            ...product,
            quantity:1
        });
    }

    updateCart();

}


/* زيادة */

function increase(id){

    const item=cart.find(p=>p.id===id);

    if(item) item.quantity++;

    updateCart();

}


/* نقصان */

function decrease(id){

    const item=cart.find(p=>p.id===id);

    if(!item) return;

    item.quantity--;

    if(item.quantity<=0){
        cart=cart.filter(p=>p.id!==id);
    }

    updateCart();

}


/* تحديث السلة */

function updateCart(){

    const box=document.getElementById("cartItems");

    const totalElement=document.getElementById("total");

    if(cart.length===0){

        box.innerHTML=
        '<div class="empty">السلة فارغة</div>';

        totalElement.innerText="0";

        return;
    }

    let total=0;

    box.innerHTML="";

    cart.forEach(item=>{

        const itemTotal=item.price*item.quantity;

        total+=itemTotal;

        box.innerHTML+=`

        <div class="cart-item">

            <div>
                <strong>${item.name}</strong>
                <br>
                ${item.price} × ${item.quantity}
                = ${itemTotal} جنيه
            </div>

            <div class="qty">

                <button onclick="increase(${item.id})">
                    +
                </button>

                <span>${item.quantity}</span>

                <button onclick="decrease(${item.id})">
                    -
                </button>

            </div>

        </div>

        `;

    });

    totalElement.innerText=total;

}


/* إرسال واتساب */

function sendWhatsApp(){

    if(cart.length===0){

        alert("أضف صنفًا إلى السلة أولاً");

        return;
    }

    const name=document.getElementById("name").value;
    const phone=document.getElementById("phone").value;
    const address=document.getElementById("address").value;

    let total=0;

    let message="🛒 طلب جديد\n\n";

    message+="👤 الاسم: "+name+"\n";
    message+="📞 الهاتف: "+phone+"\n";
    message+="📍 العنوان: "+address+"\n\n";

    message+="الطلب:\n";

    cart.forEach(item=>{

        const itemTotal=item.price*item.quantity;

        total+=itemTotal;

        message+=
        "• "+item.name+
        " × "+item.quantity+
        " = "+itemTotal+" جنيه\n";

    });

    message+="\n💰 إجمالي المنتجات: "+total+" جنيه";

    const url=
    "https://wa.me/"+
    whatsappNumber+
    "?text="+
    encodeURIComponent(message);

    window.open(url,"_blank");

}


/* تشغيل الصفحة */

showCategories();
showProducts();
updateCart();

</script>

</body>
</html>

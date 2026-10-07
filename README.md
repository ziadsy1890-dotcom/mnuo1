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

        <textarea
            id="address"
            rows="3"
            placeholder="العنوان بالتفصيل"></textarea>

        <button class="whatsapp" onclick="sendWhatsApp()">
            📲 إرسال الطلب عبر واتساب
        </button>

    </div>

</div>

<script>

/* ==================================================
   ⭐ عدّل الأصناف من هنا فقط ⭐

   لكل صنف:
   name       = اسم الصنف
   description= الوصف
   price      = السعر
   category   = التصنيف
   image      = صورة الصنف

   الصور موجودة داخل مجلد images
   ================================================== */

const products = [

/* ===== حلويات ===== */

{
id:1,
name:"بيستاش دي ألب",
description:"حلو فستق حلب الأصلي",
price:150,
category:"حلويات",
image:"images/item1.jpg"
},

{
id:2,
name:"كنافة",
description:"كنافة طازجة بالفستق",
price:120,
category:"حلويات",
image:"images/item2.jpg"
},

{
id:3,
name:"بقلاوة",
description:"بقلاوة مشكلة",
price:100,
category:"حلويات",
image:"images/item3.jpg"
},

{
id:4,
name:"معمول فستق",
description:"معمول بالفستق",
price:120,
category:"حلويات",
image:"images/item4.jpg"
},

{
id:5,
name:"معمول تمر",
description:"معمول بالتمر",
price:100,
category:"حلويات",
image:"images/item5.jpg"
},

{
id:6,
name:"غريبة",
description:"غريبة ناعمة",
price:90,
category:"حلويات",
image:"images/item6.jpg"
},

{
id:7,
name:"بسبوسة",
description:"بسبوسة طازجة",
price:90,
category:"حلويات",
image:"images/item7.jpg"
},

{
id:8,
name:"هريسة",
description:"هريسة بالفستق",
price:100,
category:"حلويات",
image:"images/item8.jpg"
},

{
id:9,
name:"بلح الشام",
description:"بلح الشام الطازج",
price:80,
category:"حلويات",
image:"images/item9.jpg"
},

{
id:10,
name:"عوامة",
description:"عوامة مقرمشة",
price:80,
category:"حلويات",
image:"images/item10.jpg"
},

{
id:11,
name:"وربات",
description:"وربات بالقشطة",
price:110,
category:"حلويات",
image:"images/item11.jpg"
},

{
id:12,
name:"قطايف",
description:"قطايف بالفستق",
price:100,
category:"حلويات",
image:"images/item12.jpg"
},

{
id:13,
name:"حلاوة الجبن",
description:"حلاوة الجبن بالقشطة",
price:120,
category:"حلويات",
image:"images/item13.jpg"
},

{
id:14,
name:"أم علي",
description:"أم علي بالمكسرات",
price:100,
category:"حلويات",
image:"images/item14.jpg"
},

{
id:15,
name:"رز بحليب",
description:"رز بحليب بالفستق",
price:70,
category:"حلويات",
image:"images/item15.jpg"
},

/* ===== كيك ===== */

{
id:16,
name:"تشيز كيك",
description:"تشيز كيك كريمي",
price:150,
category:"كيك",
image:"images/item16.jpg"
},

{
id:17,
name:"كيك شوكولاتة",
description:"كيك شوكولاتة",
price:140,
category:"كيك",
image:"images/item17.jpg"
},

{
id:18,
name:"كيك فانيلا",
description:"كيك فانيلا",
price:120,
category:"كيك",
image:"images/item18.jpg"
},

{
id:19,
name:"كيك فستق",
description:"كيك بالفستق",
price:160,
category:"كيك",
image:"images/item19.jpg"
},

{
id:20,
name:"براونيز",
description:"براونيز بالشوكولاتة",
price:120,
category:"كيك",
image:"images/item20.jpg"
},

/* ===== مشروبات ===== */

{
id:21,
name:"قهوة عربية",
description:"قهوة عربية",
price:50,
category:"مشروبات",
image:"images/item21.jpg"
},

{
id:22,
name:"قهوة تركية",
description:"قهوة تركية",
price:50,
category:"مشروبات",
image:"images/item22.jpg"
},

{
id:23,
name:"إسبريسو",
description:"إسبريسو",
price:60,
category:"مشروبات",
image:"images/item23.jpg"
},

{
id:24,
name:"كابتشينو",
description:"كابتشينو",
price:80,
category:"مشروبات",
image:"images/item24.jpg"
},

{
id:25,
name:"لاتيه",
description:"لاتيه",
price:80,
category:"مشروبات",
image:"images/item25.jpg"
},

{
id:26,
name:"لاتيه فستق",
description:"لاتيه بنكهة الفستق",
price:100,
category:"مشروبات",
image:"images/item26.jpg"
},

{
id:27,
name:"موكا",
description:"موكا بالشوكولاتة",
price:90,
category:"مشروبات",
image:"images/item27.jpg"
},

{
id:28,
name:"هوت شوكليت",
description:"شوكولاتة ساخنة",
price:90,
category:"مشروبات",
image:"images/item28.jpg"
},

{
id:29,
name:"شاي",
description:"شاي ساخن",
price:40,
category:"مشروبات",
image:"images/item29.jpg"
},

{
id:30,
name:"شاي بالنعناع",
description:"شاي بالنعناع",
price:45,
category:"مشروبات",
image:"images/item30.jpg"
},

/* ===== عصائر ===== */

{
id:31,
name:"عصير برتقال",
description:"عصير برتقال طازج",
price:70,
category:"عصائر",
image:"images/item31.jpg"
},

{
id:32,
name:"عصير مانجو",
description:"عصير مانجو",
price:80,
category:"عصائر",
image:"images/item32.jpg"
},

{
id:33,
name:"عصير فراولة",
description:"عصير فراولة",
price:80,
category:"عصائر",
image:"images/item33.jpg"
},

{
id:34,
name:"عصير ليمون",
description:"ليمون طازج",
price:60,
category:"عصائر",
image:"images/item34.jpg"
},

{
id:35,
name:"ليمون بالنعناع",
description:"ليمون بالنعناع",
price:70,
category:"عصائر",
image:"images/item35.jpg"
},

{
id:36,
name:"عصير جوافة",
description:"عصير جوافة",
price:75,
category:"عصائر",
image:"images/item36.jpg"
},

{
id:37,
name:"عصير رمان",
description:"عصير رمان",
price:90,
category:"عصائر",
image:"images/item37.jpg"
},

/* ===== آيس كريم ===== */

{
id:38,
name:"آيس كريم فانيلا",
description:"آيس كريم فانيلا",
price:70,
category:"آيس كريم",
image:"images/item38.jpg"
},

{
id:39,
name:"آيس كريم شوكولاتة",
description:"آيس كريم شوكولاتة",
price:70,
category:"آيس كريم",
image:"images/item39.jpg"
},

{
id:40,
name:"آيس كريم فستق",
description:"آيس كريم فستق",
price:90,
category:"آيس كريم",
image:"images/item40.jpg"
},

/* ===== ساندويتشات ===== */

{
id:41,
name:"ساندويتش جبنة",
description:"ساندويتش جبنة",
price:70,
category:"ساندويتشات",
image:"images/item41.jpg"
},

{
id:42,
name:"ساندويتش حلوم",
description:"ساندويتش حلوم",
price:90,
category:"ساندويتشات",
image:"images/item42.jpg"
},

{
id:43,
name:"ساندويتش دجاج",
description:"ساندويتش دجاج",
price:120,
category:"ساندويتشات",
image:"images/item43.jpg"
},

{
id:44,
name:"ساندويتش تونة",
description:"ساندويتش تونة",
price:110,
category:"ساندويتشات",
image:"images/item44.jpg"
},

/* ===== مخبوزات ===== */

{
id:45,
name:"كرواسون جبنة",
description:"كرواسون بالجبنة",
price:70,
category:"مخبوزات",
image:"images/item45.jpg"
},

{
id:46,
name:"كرواسون زعتر",
description:"كرواسون بالزعتر",
price:65,
category:"مخبوزات",
image:"images/item46.jpg"
},

{
id:47,
name:"مناقيش زعتر",
description:"مناقيش زعتر",
price:70,
category:"مخبوزات",
image:"images/item47.jpg"
},

{
id:48,
name:"مناقيش جبنة",
description:"مناقيش جبنة",
price:80,
category:"مخبوزات",
image:"images/item48.jpg"
},

{
id:49,
name:"مناقيش لحم",
description:"مناقيش باللحم",
price:100,
category:"مخبوزات",
image:"images/item49.jpg"
},

{
id:50,
name:"بيتزا صغيرة",
description:"بيتزا صغيرة",
price:120,
category:"مخبوزات",
image:"images/item50.jpg"
},

/* ===== الأصناف 51 - 100 ===== */

{
id:51,
name:"كوكيز شوكولاتة",
description:"كوكيز بالشوكولاتة",
price:70,
category:"حلويات",
image:"images/item51.jpg"
},

{
id:52,
name:"كوكيز فستق",
description:"كوكيز بالفستق",
price:80,
category:"حلويات",
image:"images/item52.jpg"
},

{
id:53,
name:"دونات",
description:"دونات طازجة",
price:60,
category:"حلويات",
image:"images/item53.jpg"
},

{
id:54,
name:"مافن",
description:"مافن طازج",
price:60,
category:"حلويات",
image:"images/item54.jpg"
},

{
id:55,
name:"تارت فواكه",
description:"تارت بالفواكه",
price:130,
category:"حلويات",
image:"images/item55.jpg"
},

{
id:56,
name:"تارت شوكولاتة",
description:"تارت بالشوكولاتة",
price:140,
category:"حلويات",
image:"images/item56.jpg"
},

{
id:57,
name:"إكلير",
description:"إكلير بالكريمة",
price:90,
category:"حلويات",
image:"images/item57.jpg"
},

{
id:58,
name:"موس شوكولاتة",
description:"موس شوكولاتة",
price:100,
category:"حلويات",
image:"images/item58.jpg"
},

{
id:59,
name:"موس فستق",
description:"موس بالفستق",
price:120,
category:"حلويات",
image:"images/item59.jpg"
},

{
id:60,
name:"بان كيك",
description:"بان كيك مع صوص",
price:120,
category:"حلويات",
image:"images/item60.jpg"
},

{
id:61,
name:"وافل",
description:"وافل طازج",
price:120,
category:"حلويات",
image:"images/item61.jpg"
},

{
id:62,
name:"كريب شوكولاتة",
description:"كريب بالشوكولاتة",
price:110,
category:"حلويات",
image:"images/item62.jpg"
},

{
id:63,
name:"كريب فستق",
description:"كريب بالفستق",
price:130,
category:"حلويات",
image:"images/item63.jpg"
},

{
id:64,
name:"كوب فواكه",
description:"فواكه مشكلة",
price:100,
category:"حلويات",
image:"images/item64.jpg"
},

{
id:65,
name:"سلطة فواكه",
description:"سلطة فواكه طازجة",
price:100,
category:"حلويات",
image:"images/item65.jpg"
},

{
id:66,
name:"موهيتو كلاسيك",
description:"موهيتو منعش",
price:80,
category:"مشروبات",
image:"images/item66.jpg"
},

{
id:67,
name:"موهيتو فراولة",
description:"موهيتو بالفراولة",
price:90,
category:"مشروبات",
image:"images/item67.jpg"
},

{
id:68,
name:"موهيتو مانجو",
description:"موهيتو بالمانجو",
price:90,
category:"مشروبات",
image:"images/item68.jpg"
},

{
id:69,
name:"سموثي فراولة",
description:"سموثي فراولة",
price:100,
category:"مشروبات",
image:"images/item69.jpg"
},

{
id:70,
name:"سموثي مانجو",
description:"سموثي مانجو",
price:100,
category:"مشروبات",
image:"images/item70.jpg"
},

{
id:71,
name:"سموثي فستق",
description:"سموثي بالفستق",
price:120,
category:"مشروبات",
image:"images/item71.jpg"
},

{
id:72,
name:"ميلك شيك فانيلا",
description:"ميلك شيك فانيلا",
price:100,
category:"مشروبات",
image:"images/item72.jpg"
},

{
id:73,
name:"ميلك شيك شوكولاتة",
description:"ميلك شيك شوكولاتة",
price:110,
category:"مشروبات",
image:"images/item73.jpg"
},

{
id:74,
name:"ميلك شيك فراولة",
description:"ميلك شيك فراولة",
price:110,
category:"مشروبات",
image:"images/item74.jpg"
},

{
id:75,
name:"ميلك شيك فستق",
description:"ميلك شيك فستق",
price:130,
category:"مشروبات",
image:"images/item75.jpg"
},

{
id:76,
name:"أمريكانو",
description:"قهوة أمريكانو",
price:70,
category:"مشروبات",
image:"images/item76.jpg"
},

{
id:77,
name:"نسكافيه",
description:"نسكافيه",
price:60,
category:"مشروبات",
image:"images/item77.jpg"
},

{
id:78,
name:"مياه معدنية",
description:"مياه معدنية",
price:25,
category:"مشروبات",
image:"images/item78.jpg"
},

{
id:79,
name:"مشروب غازي",
description:"مشروب غازي",
price:40,
category:"مشروبات",
image:"images/item79.jpg"
},

{
id:80,
name:"بطاطا مقلية",
description:"بطاطا مقلية",
price:70,
category:"مقبلات",
image:"images/item80.jpg"
},

{
id:81,
name:"بطاطا بالجبنة",
description:"بطاطا مع الجبنة",
price:90,
category:"مقبلات",
image:"images/item81.jpg"
},

{
id:82,
name:"سلطة خضراء",
description:"سلطة خضراء طازجة",
price:80,
category:"مقبلات",
image:"images/item82.jpg"
},

{
id:83,
name:"سلطة فتوش",
description:"فتوش طازج",
price:90,
category:"مقبلات",
image:"images/item83.jpg"
},

{
id:84,
name:"حمص",
description:"حمص بطحينة",
price:70,
category:"مقبلات",
image:"images/item84.jpg"
},

{
id:85,
name:"متبل",
description:"متبل باذنجان",
price:70,
category:"مقبلات",
image:"images/item85.jpg"
},

{
id:86,
name:"ورق عنب",
description:"ورق عنب",
price:90,
category:"مقبلات",
image:"images/item86.jpg"
},

{
id:87,
name:"مناقيش مشكلة",
description:"تشكيلة مناقيش",
price:120,
category:"مخبوزات",
image:"images/item87.jpg"
},

{
id:88,
name:"كرواسون شوكولاتة",
description:"كرواسون بالشوكولاتة",
price:80,
category:"مخبوزات",
image:"images/item88.jpg"
},

{
id:89,
name:"كرواسون سادة",
description:"كرواسون طازج",
price:60,
category:"مخبوزات",
image:"images/item89.jpg"
},

{
id:90,
name:"توست جبنة",
description:"توست بالجبنة",
price:70,
category:"ساندويتشات",
image:"images/item90.jpg"
},

{
id:91,
name:"توست دجاج",
description:"توست بالدجاج",
price:100,
category:"ساندويتشات",
image:"images/item91.jpg"
},

{
id:92,
name:"توست تونة",
description:"توست بالتونة",
price:95,
category:"ساندويتشات",
image:"images/item92.jpg"
},

{
id:93,
name:"رول دجاج",
description:"رول بالدجاج",
price:110,
category:"ساندويتشات",
image:"images/item93.jpg"
},

{
id:94,
name:"رول جبنة",
description:"رول بالجبنة",
price:90,
category:"ساندويتشات",
image:"images/item94.jpg"
},

{
id:95,
name:"طبق حلويات مشكلة",
description:"تشكيلة حلويات",
price:250,
category:"حلويات",
image:"images/item95.jpg"
},

{
id:96,
name:"طبق فستق مشكلة",
description:"تشكيلة بالفستق",
price:280,
category:"حلويات",
image:"images/item96.jpg"
},

{
id:97,
name:"بوكس حلويات صغير",
description:"بوكس حلويات",
price:300,
category:"حلويات",
image:"images/item97.jpg"
},

{
id:98,
name:"بوكس حلويات كبير",
description:"بوكس حلويات كبير",
price:500,
category:"حلويات",
image:"images/item98.jpg"
},

{
id:99,
name:"بوكس فستق فاخر",
description:"بوكس فستق فاخر",
price:600,
category:"حلويات",
image:"images/item99.jpg"
},

{
id:100,
name:"بوكس بيستاش دي ألب",
description:"بوكس فاخر من بيستاش دي ألب",
price:700,
category:"حلويات",
image:"images/item100.jpg"
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

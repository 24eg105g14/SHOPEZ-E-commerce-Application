[shopEZ2.html](https://github.com/user-attachments/files/30194783/shopEZ2.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>ShopEZ Online Store</title>

<style>
body{
    margin:0;
    font-family:Arial;
    background:#f2f4f8;
}

header{
    background:linear-gradient(90deg,#ff6f00,#ff9800);
    color:white;
    text-align:center;
    padding:15px;
    font-size:22px;
    font-weight:bold;
}

nav{
    background:#222;
    display:flex;
    justify-content:center;
    gap:10px;
    flex-wrap:wrap;
    padding:10px;
}

nav button{
    background:none;
    border:none;
    color:white;
    cursor:pointer;
}

.page{display:none;padding:20px;}
.active{display:block}

/* LOGIN */
.box{
    width:300px;
    margin:40px auto;
    background:white;
    padding:20px;
    border-radius:10px;
}

input,select{
    width:90%;
    padding:10px;
    margin:8px 0;
}

.btn{
    width:100%;
    padding:10px;
    background:#ff6f00;
    border:none;
    color:white;
    cursor:pointer;
}

/* SEARCH */
.search{
    width:60%;
    padding:10px;
    margin:10px auto;
    display:block;
}

/* PRODUCTS */
.section-title{
    text-align:center;
    margin:20px 0;
}

.products{
    display:flex;
    flex-wrap:wrap;
    justify-content:center;
    gap:15px;
}

.card{
    width:200px;
    background:white;
    padding:12px;
    border-radius:10px;
    text-align:center;
    box-shadow:0 3px 10px rgba(0,0,0,0.1);
    position:relative;
}

/* NO IMAGES — CLEAN BLOCK STYLE */
.img{
    width:100%;
    height:120px;
    background:linear-gradient(135deg,#dfe6e9,#b2bec3);
    border-radius:10px;
    display:flex;
    align-items:center;
    justify-content:center;
    font-weight:bold;
    color:#2d3436;
}

.badge{
    position:absolute;
    top:8px;
    right:8px;
    background:#4caf50;
    color:white;
    font-size:10px;
    padding:3px 6px;
    border-radius:10px;
}

.price{
    font-weight:bold;
    color:green;
}

.cart-item{
    background:white;
    width:320px;
    margin:10px auto;
    padding:10px;
    border-radius:8px;
}

.total{
    text-align:center;
    font-size:20px;
    font-weight:bold;
    color:green;
    background:white;
    width:320px;
    margin:20px auto;
    padding:10px;
    border-radius:10px;
}

.success{
    text-align:center;
    font-size:22px;
    color:green;
}
</style>
</head>

<body>

<header>🛒 ShopEZ ONLINE STORE</header>

<nav>
<button onclick="show('login')">Login</button>
<button onclick="show('signup')">Signup</button>
<button onclick="show('home')">Home</button>
<button onclick="show('cart')">Cart (<span id="count">0</span>)</button>
</nav>

<!-- LOGIN -->
<div id="login" class="page active">
<div class="box">
<h2>Login</h2>
<input placeholder="Username">
<input type="password" placeholder="Password">
<button class="btn" onclick="show('home')">Login</button>
</div>
</div>

<!-- SIGNUP -->
<div id="signup" class="page">
<div class="box">
<h2>Signup</h2>
<input placeholder="Username">
<input placeholder="Email">
<input type="password">
<button class="btn" onclick="show('login')">Create Account</button>
</div>
</div>

<!-- SEARCH -->
<input class="search" id="search" onkeyup="filter()" placeholder="🔍 Search products...">

<!-- HOME -->
<div id="home" class="page active">

<h2 class="section-title">👗 Clothing</h2>
<div class="products">

<div class="card product"><div class="img">T-SHIRT</div><h3>T-Shirt</h3><p class="price">499</p><button class="btn" onclick="add('T-Shirt',499)">Add</button></div>
<div class="card product"><div class="img">JEANS</div><h3>Jeans</h3><p class="price">1299</p><button class="btn" onclick="add('Jeans',1299)">Add</button></div>
<div class="card product"><div class="img">JACKET</div><h3>Jacket</h3><p class="price">2499</p><button class="btn" onclick="add('Jacket',2499)">Add</button></div>

</div>

<h2 class="section-title">💄 Makeup</h2>
<div class="products">

<div class="card product"><div class="img">LIPSTICK</div><h3>Lipstick</h3><p class="price">299</p><button class="btn" onclick="add('Lipstick',299)">Add</button></div>
<div class="card product"><div class="img">FOUNDATION</div><h3>Foundation</h3><p class="price">599</p><button class="btn" onclick="add('Foundation',599)">Add</button></div>

</div>

<h2 class="section-title">🧴 Skincare</h2>
<div class="products">

<div class="card product"><div class="img">FACE WASH</div><h3>Face Wash</h3><p class="price">199</p><button class="btn" onclick="add('Face Wash',199)">Add</button></div>
<div class="card product"><div class="img">SUNSCREEN</div><h3>Sunscreen</h3><p class="price">299</p><button class="btn" onclick="add('Sunscreen',299)">Add</button></div>

</div>

<h2 class="section-title">👟 Footwear</h2>
<div class="products">

<div class="card product"><div class="img">SHOES</div><h3>Shoes</h3><p class="price">1999</p><button class="btn" onclick="add('Shoes',1999)">Add</button></div>
<div class="card product"><div class="img">SANDALS</div><h3>Sandals</h3><p class="price">999</p><button class="btn" onclick="add('Sandals',999)">Add</button></div>

</div>

</div>

<!-- CART -->
<div id="cart" class="page">
<h2 style="text-align:center;">🛒 Cart</h2>
<div id="cartBox"></div>

<div class="total">
Total: ₹<span id="total">0</span><br>
<span style="color:red">10% Discount Applied</span>
</div>

<button class="btn" onclick="show('checkout')">Checkout</button>
</div>

<!-- CHECKOUT -->
<div id="checkout" class="page">
<div class="box">
<h2>Checkout</h2>
<input placeholder="Address">
<input placeholder="Phone">
<select>
<option>UPI</option>
<option>Card</option>
</select>
<button class="btn" onclick="place()">Place Order</button>
</div>
</div>

<!-- SUCCESS -->
<div id="success" class="page">
<h2 class="success">🎉 Order Placed Successfully!</h2>
</div>

<script>

let cart=[];
let total=0;

function show(id){
    document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
    document.getElementById(id).classList.add('active');
}

function add(name,price){
    cart.push({name,price});
    total+=price;
    document.getElementById('count').innerText=cart.length;
    update();
}

function update(){
    let box=document.getElementById("cartBox");
    box.innerHTML="";

    cart.forEach((c,i)=>{
        box.innerHTML+=`
        <div class="cart-item">
        ${c.name} - ₹${c.price}
        <button onclick="remove(${i})">X</button>
        </div>`;
    });

    document.getElementById('total').innerText=Math.round(total*0.9);
}

function remove(i){
    total-=cart[i].price;
    cart.splice(i,1);
    document.getElementById('count').innerText=cart.length;
    update();
}

function place(){
    cart=[];
    total=0;
    document.getElementById('count').innerText=0;
    show('success');
}

function filter(){
    let val=document.getElementById("search").value.toLowerCase();
    document.querySelectorAll(".product").forEach(p=>{
        p.style.display=p.innerText.toLowerCase().includes(val)?"block":"none";
    });
}

</script>

</body>
</html>

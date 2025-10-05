# 8-e-commerce<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>JKS Group of Business</title>
<style>
  body {
    font-family: Arial, sans-serif;
    margin:0; padding:0; background: #fff;
    color:#556b2f;
  }
  header, nav, main, footer {
    padding:10px 20px;
  }
  header {
    background: #556b2f;
    color: white;
    text-align:center;
    font-size: 1.8em;
    font-weight: bold;
  }
  nav {
    background: #f0f5e6;
    display:flex;
    justify-content: space-around;
  }
  nav button {
    background: transparent;
    border:none;
    font-size: 1em;
    padding: 10px;
    cursor:pointer;
    color:#556b2f;
    font-weight: 600;
  }
  nav button:hover, nav button.active {
    color: #364d00;
    font-weight:bold;
  }
  main {
    min-height: 70vh;
    padding: 20px;
    background: white;
    position:relative;
  }
  .hidden { display:none; }
  .category-list, .product-list, .cart-list {
    list-style:none;
    padding: 0;
  }
  .category-list li, .product-list li {
    border: 1px solid #cdd9b9;
    margin: 5px 0px;
    padding: 8px;
    cursor: pointer;
    border-radius: 5px;
    color:#556b2f;
  }
  .category-list li:hover, .product-list li:hover {
    background: #e6f0b3;
  }
  .cart-list li {
    border-bottom: 1px dotted #a6b180;
    padding: 5px 0;
  }
  .btn-primary {
    background-color: #556b2f;
    border: none;
    color: white;
    padding: 8px 15px;
    margin: 10px 0;
    cursor: pointer;
    border-radius: 5px;
  }
  .main-folder-list {
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
  }
  .folder-card {
    border: 2px solid #556b2f;
    border-radius: 8px;
    padding: 20px;
    width: 180px;
    margin: 15px;
    text-align: center;
    cursor: pointer;
    font-weight: bold;
    background: #f7f9e8;
    transition: background-color 0.3s;
  }
  .folder-card:hover {
    background-color: #e6f0b3;
  }
  input[type="number"] {
    width: 60px;
    margin-left: 10px;
    padding: 4px;
  }
  label {
    font-weight: bold;
    color:#556b2f;
  }
  form > div {
    margin: 5px 0;
  }
  #order-summary {
    margin-top: 20px;
    background: #f5f9d8;
    padding: 10px;
    border-radius: 5px;
    color:#556b2f;
  }
  .camera-container video, .camera-container canvas {
    width: 100%;
    max-width: 400px;
    border-radius: 5px;
  }
  .map-container {
    width: 100%;
    height: 300px;
    border-radius: 5px;
  }
  #back-to-home-btn {
    position: absolute;
    top: 10px;
    left: 20px;
    background: #556b2f;
    color: white;
    border: none;
    padding: 6px 12px;
    border-radius: 5px;
    cursor: pointer;
    font-weight: bold;
    z-index: 10;
  }
  #home-folders-label {
    font-weight: bold;
    font-size: 1.4em;
    text-align: center;
    margin-bottom: 15px;
    color:#556b2f;
  }
</style>
</head>
<body>

<header>JKS Group of Business</header>

<nav>
  <button id="nav-home" class="active">Home</button>
  <button id="nav-camera">Camera</button>
  <button id="nav-maps">Google Maps</button>
  <button id="nav-profile">Profile</button>
  <button id="nav-wallet">Wallet</button>
</nav>

<main>
  <!-- Home with 4 folders -->
  <section id="home-section">
    <h2>Welcome to JKS Group of Business</h2>
    <p>Select a service below:</p>
    <div id="home-folders-label">Main Service Folders</div>
    <div class="main-folder-list">
      <div class="folder-card" id="folder-ecommerce">E-commerce</div>
      <div class="folder-card" id="folder-food">Food</div>
      <div class="folder-card" id="folder-pharmacy">Pharmacy</div>
      <div class="folder-card" id="folder-others">Others</div>
    </div>
  </section>

  <!-- E-commerce (Provision, Milk, Meat, Fruits, Vegetables, Flowers, Snacks, Drinks) -->
  <section id="ecommerce-section" class="hidden">
    <button id="back-to-home-btn-ecom" title="Back to Home">Back</button>
    <h2>E-commerce</h2>
    <div>
      <label><strong>Categories:</strong></label>
      <ul id="ecom-main-category-list" class="category-list"></ul>
    </div>
    <div id="ecom-subcategory-container" style="margin-top: 15px;"></div>
    <div id="ecom-product-container" style="margin-top:20px;"></div>
    <div id="ecom-cart-container" style="margin-top:30px;">
      <h3>Cart</h3>
      <ul id="ecom-cart-list" class="cart-list"></ul>
      <button id="ecom-submit-order" class="btn-primary" disabled>Submit Order via WhatsApp</button>
    </div>
    <div id="ecom-customer-details-container" class="hidden" style="margin-top:20px;">
      <h3>Enter Your Details</h3>
      <form id="ecom-customer-details-form">
        <div><label>Name:</label><input type="text" id="ecom-cust-name" required /></div>
        <div><label>Mobile Number:</label><input type="tel" id="ecom-cust-mobile" required pattern="^\+?\d{10,15}$" placeholder="+919876543210" /></div>
        <div><label>Delivery Address:</label><textarea id="ecom-cust-address" required rows="3"></textarea></div>
        <button type="submit" class="btn-primary">Send Order</button>
      </form>
    </div>
  </section>

  <!-- Food -->
  <section id="food-section" class="hidden">
    <button id="back-to-home-btn-food" title="Back to Home">Back</button>
    <h2>Food</h2>
    <div>
      <label><strong>Categories:</strong></label>
      <ul id="food-main-category-list" class="category-list"></ul>
    </div>
    <div id="food-subcategory-container" style="margin-top: 15px;"></div>
    <div id="food-product-container" style="margin-top:20px;"></div>
    <div id="food-cart-container" style="margin-top:30px;">
      <h3>Cart</h3>
      <ul id="food-cart-list" class="cart-list"></ul>
      <button id="food-submit-order" class="btn-primary" disabled>Submit Order via WhatsApp</button>
    </div>
    <div id="food-customer-details-container" class="hidden" style="margin-top:20px;">
      <h3>Enter Your Details</h3>
      <form id="food-customer-details-form">
        <div><label>Name:</label><input type="text" id="food-cust-name" required /></div>
        <div><label>Mobile Number:</label><input type="tel" id="food-cust-mobile" required pattern="^\+?\d{10,15}$" placeholder="+919876543210" /></div>
        <div><label>Delivery Address:</label><textarea id="food-cust-address" required rows="3"></textarea></div>
        <button type="submit" class="btn-primary">Send Order</button>
      </form>
    </div>
  </section>

  <!-- Pharmacy -->
  <section id="pharmacy-section" class="hidden">
    <button id="back-to-home-btn-pharmacy" title="Back to Home">Back</button>
    <h2>Pharmacy</h2>
    <div>
      <label><strong>Categories:</strong></label>
      <ul id="pharmacy-main-category-list" class="category-list"></ul>
    </div>
    <div id="pharmacy-product-container" style="margin-top: 20px;"></div>
    <div id="pharmacy-cart-container" style="margin-top:30px;">
      <h3>Cart</h3>
      <ul id="pharmacy-cart-list" class="cart-list"></ul>
      <button id="pharmacy-submit-order" class="btn-primary" disabled>Submit Order via WhatsApp</button>
    </div>
    <div id="pharmacy-customer-details-container" class="hidden" style="margin-top:20px;">
      <h3>Enter Your Details</h3>
      <form id="pharmacy-customer-details-form">
        <div><label>Name:</label><input type="text" id="pharmacy-cust-name" required /></div>
        <div><label>Mobile Number:</label><input type="tel" id="pharmacy-cust-mobile" required pattern="^\+?\d{10,15}$" placeholder="+919876543210" /></div>
        <div><label>Delivery Address:</label><textarea id="pharmacy-cust-address" required rows="3"></textarea></div>
        <button type="submit" class="btn-primary">Send Order</button>
      </form>
    </div>
  </section>

  <!-- Others -->
  <section id="others-section" class="hidden">
    <button id="back-to-home-btn-others" title="Back to Home">Back</button>
    <h2>Others - Order Details</h2>
    <form id="others-order-form">
      <div><label>Name:</label><input type="text" id="others-name" required></div>
      <div><label>Mobile Number:</label><input type="tel" id="others-mobile" required pattern="^\+?\d{10,15}$" placeholder="+919876543210"></div>
      <div><label>Order Details:</label><textarea id="others-order" required rows="3"></textarea></div>
      <div><label>Delivery Address:</label><textarea id="others-address" required rows="3"></textarea></div>
      <button type="submit" class="btn-primary">Send Order via WhatsApp</button>
    </form>
  </section>

  <!-- Camera Section (unchanged from before) -->
  <section id="camera-section" class="hidden">
    <button id="back-to-home-btn-camera" title="Back to Home">Back</button>
    <h2>Camera Access</h2>
    <div class="camera-container">
      <video id="camera-video" autoplay></video>
      <canvas id="camera-canvas" class="hidden"></canvas><br />
      <button id="capture-photo" class="btn-primary">Capture Photo</button>
      <button id="retake-photo" class="btn-primary hidden">Retake</button>
      <button id="switch-camera" class="btn-primary">Switch Camera</button>
      <button id="send-photo-whatsapp" class="btn-primary hidden">Send Photo via WhatsApp</button>
      <div id="photo-result"></div>
    </div>
  </section>

  <!-- Maps Section (unchanged) -->
  <section id="maps-section" class="hidden">
    <button id="back-to-home-btn-maps" title="Back to Home">Back</button>
    <h2>Google Maps</h2>
    <p>Your current location:</p>
    <div id="map" class="map-container"></div>
  </section>

  <!-- Profile Section -->
  <section id="profile-section" class="hidden">
    <button id="back-to-home-btn-profile" title="Back to Home">Back</button>
    <h2>Profile</h2>
    <p>This is your user profile.</p>
  </section>

  <!-- Wallet Section -->
  <section id="wallet-section" class="hidden">
    <button id="back-to-home-btn-wallet" title="Back to Home">Back</button>
    <h2>Wallet</h2>
    <p>Manage your wallet and transactions here.</p>
  </section>

</main>

<script>
  // E-commerce Data - Provision, Milk, Meat, Fruits, Vegetables, Flowers, Snacks, Drinks inside E-commerce
  const ecomData = {
    "Provision": {
      "categories": ["My Provisions", "All Provisions"],
      "items": {
        "My Provisions": {
          "categories": ["Rice", "Dal", "Spices & Powders", "Oil", "Batters"],
          "items": {
            "Rice": ["Sona Masoori", "Idli Rice", "Basmati Rice"],
            "Dal": ["Toor Dal", "Moong Dal", "Udad Dal"],
            "Spices & Powders": ["Chilli Powder", "Coriander Powder", "Garam Masala"],
            "Oil": ["Sunflower Oil", "Palm Oil", "Groundnut Oil"],
            "Batters": ["Idli Batter", "Dosa Batter", "Pesarattu Batter"]
          }
        },
        "All Provisions": {
          "categories": ["Rice", "Dal", "Atta & Masala Items", "Oil and Ghee", "Batters & Sauces"],
          "items": {
            "Rice": ["Sona Masoori", "Idli Rice", "Basmati Rice"],
            "Dal": ["Toor Dal", "Moong Dal", "Udad Dal"],
            "Atta & Masala Items": ["Wheat Atta", "Maida", "Chili Powder", "Curry Powder"],
            "Oil and Ghee": ["Sunflower Oil", "Mustard Oil", "Ghee"],
            "Batters & Sauces": ["Idli Batter", "Dosa Batter", "Tomato Sauce"]
          }
        }
      }
    },
    "Milk": {
      "items": ["Milk", "Curd", "Ghee", "Paneer", "Butter", "Buttermilk"]
    },
    "Meat": {
      "categories": ["Chicken", "Mutton", "Fishes", "Prawns", "Crabs", "Eggs"],
      "items": {
        "Chicken": ["Boiler Chicken", "Country Chicken", "Farm Chicken", "Black Chicken", "Layer Chicken"],
        "Mutton": ["Head", "Legs", "Bone", "Boneless", "Mixed", "Liver", "Dhomma", "Blood", "Intestines"],
        "Fishes": ["Jeelabi", "Koramenu", "Chenduva"],
        "Prawns": ["Prawns"],
        "Crabs": ["Crabs"],
        "Eggs": ["Boiler Eggs", "Country Eggs"]
      }
    },
    "Fruits & Vegetables": {
      "categories": ["Fruits", "Vegetables"],
      "items": {
        "Fruits": ["Mango", "Banana", "Apple", "Orange", "Grapes"],
        "Vegetables": ["Tomato", "Potato", "Onion", "Carrot", "Bitter Gourd"]
      }
    },
    "Flowers": {
      "items": ["Rose", "Jasmine", "Marigold", "Lotus"]
    },
    "Snacks": {
      "items": ["Samosa", "Sev", "Bhujia"]
    },
    "Drinks": {
      "items": ["Thumsup", "Mirinda", "Sprite", "Red Bull", "Monster", "Jil Jeera"]
    }
  };

  const foodData = {
    "categories": ["Tiffens", "Biriyani", "Fried Rices", "Starters", "Ice Cream", "Shakes", "Desserts", "Juices", "Rolls", "Fried Chicken", "Burgers", "Pizzas", "Kababs", "Chats", "Drinks", "Snacks"],
    "items": {
      "Tiffens": ["Idli", "Dosa", "Pesarattu"],
      "Biriyani": ["Chicken Biryani", "Mutton Biryani", "Veg Biryani"],
      "Fried Rices": ["Chicken Fried Rice", "Egg Fried Rice", "Veg Fried Rice"],
      "Starters": ["Spring Roll", "Paneer Tikka", "Chicken 65"],
      "Ice Cream": ["Vanilla", "Chocolate", "Strawberry"],
      "Shakes": ["Mango Shake", "Chocolate Shake", "Banana Shake"],
      "Desserts": ["Gulab Jamun", "Rasgulla", "Kheer"],
      "Juices": ["Orange Juice", "Sugarcane Juice", "Watermelon Juice"],
      "Rolls": ["Chicken Roll", "Egg Roll", "Paneer Roll"],
      "Fried Chicken": ["Chicken Nuggets", "Chicken Wings", "Chicken Popcorn"],
      "Burgers": ["Veg Burger", "Chicken Burger", "Cheese Burger"],
      "Pizzas": ["Margherita", "Farmhouse", "Pepperoni"],
      "Kababs": ["Chicken Kabab", "Veg Kabab", "Mutton Kabab"],
      "Chats": {
        "categories": ["Snacks", "Chats"],
        "items": {
          "Snacks": ["Bonda", "Bajji", "Vada", "Mirchi Bajji", "Cut Bajji", "Onion Bajji", "Vankaya Bajji", "Onion Pakoda", "Mixture"],
          "Chats": ["Masala Puri", "Pani Puri", "Gobi Chat", "Paneer Chat", "Pav Bajji", "Mushroom Chat", "Egg Chat", "Cutlet Chat", "Papad Chat"]
        }
      },
      "Drinks": ["Thumsup", "Mirinda", "Sprite", "Red Bull", "Monster", "Jil Jeera"],
      "Snacks": ["Samosa", "Sev", "Bhujia"]
    }
  };

  const pharmacyData = {
    "items": ["Paracetamol", "Cough Syrup", "Bandages", "Pain Relief Balm", "Vitamin Tablets"]
  };

  // General state variables
  let currentFolder = null;
  let currentSubFolder = null;
  let cart = [];

  // Navigation buttons
  const navHome = document.getElementById('nav-home');
  const navCamera = document.getElementById('nav-camera');
  const navMaps = document.getElementById('nav-maps');
  const navProfile = document.getElementById('nav-profile');
  const navWallet = document.getElementById('nav-wallet');

  // Sections
  const homeSection = document.getElementById('home-section');
  const ecommerceSection = document.getElementById('ecommerce-section');
  const foodSection = document.getElementById('food-section');
  const pharmacySection = document.getElementById('pharmacy-section');
  const othersSection = document.getElementById('others-section');
  const cameraSection = document.getElementById('camera-section');
  const mapsSection = document.getElementById('maps-section');
  const profileSection = document.getElementById('profile-section');
  const walletSection = document.getElementById('wallet-section');

  // E-commerce page elements
  const ecomMainCatList = document.getElementById('ecom-main-category-list');
  const ecomSubCatContainer = document.getElementById('ecom-subcategory-container');
  const ecomProductContainer = document.getElementById('ecom-product-container');
  const ecomCartList = document.getElementById('ecom-cart-list');
  const ecomSubmitOrderBtn = document.getElementById('ecom-submit-order');
  const ecomCustomerDetailsContainer = document.getElementById('ecom-customer-details-container');
  const ecomCustomerDetailsForm = document.getElementById('ecom-customer-details-form');

  // Food page elements
  const foodMainCatList = document.getElementById('food-main-category-list');
  const foodSubCatContainer = document.getElementById('food-subcategory-container');
  const foodProductContainer = document.getElementById('food-product-container');
  const foodCartList = document.getElementById('food-cart-list');
  const foodSubmitOrderBtn = document.getElementById('food-submit-order');
  const foodCustomerDetailsContainer = document.getElementById('food-customer-details-container');
  const foodCustomerDetailsForm = document.getElementById('food-customer-details-form');

  // Pharmacy elements
  const pharmacyMainCatList = document.getElementById('pharmacy-main-category-list');
  const pharmacyProductContainer = document.getElementById('pharmacy-product-container');
  const pharmacyCartList = document.getElementById('pharmacy-cart-list');
  const pharmacySubmitOrderBtn = document.getElementById('pharmacy-submit-order');
  const pharmacyCustomerDetailsContainer = document.getElementById('pharmacy-customer-details-container');
  const pharmacyCustomerDetailsForm = document.getElementById('pharmacy-customer-details-form');

  // Others elements
  const othersOrderForm = document.getElementById('others-order-form');

  // Camera Elements
  const videoElement = document.getElementById('camera-video');
  const canvasElement = document.getElementById('camera-canvas');
  const captureBtn = document.getElementById('capture-photo');
  const retakeBtn = document.getElementById('retake-photo');
  const switchCamBtn = document.getElementById('switch-camera');
  const sendPhotoBtn = document.getElementById('send-photo-whatsapp');
  const photoResult = document.getElementById('photo-result');

  // Back buttons
  document.getElementById('back-to-home-btn-ecom').onclick = ()=>showSection('home');
  document.getElementById('back-to-home-btn-food').onclick = ()=>showSection('home');
  document.getElementById('back-to-home-btn-pharmacy').onclick = ()=>showSection('home');
  document.getElementById('back-to-home-btn-others').onclick = ()=>showSection('home');
  document.getElementById('back-to-home-btn-camera').onclick = ()=>{
    stopCamera();
    showSection('home');
  };
  document.getElementById('back-to-home-btn-maps').onclick = ()=>showSection('home');
  document.getElementById('back-to-home-btn-profile').onclick = ()=>showSection('home');
  document.getElementById('back-to-home-btn-wallet').onclick = ()=>showSection('home');

  navHome.onclick = ()=>showSection('home');
  navCamera.onclick = ()=>showSection('camera');
  navMaps.onclick = ()=>showSection('maps');
  navProfile.onclick = ()=>showSection('profile');
  navWallet.onclick = ()=>showSection('wallet');

  // Home main folders buttons
  document.getElementById('folder-ecommerce').onclick = ()=>showEcommerce();
  document.getElementById('folder-food').onclick = ()=>showFood();
  document.getElementById('folder-pharmacy').onclick = ()=>showPharmacy();
  document.getElementById('folder-others').onclick = ()=>showOthers();

  // Functions to show respective sections
  function showSection(section) {
    // hide all
    homeSection.classList.add('hidden');
    ecommerceSection.classList.add('hidden');
    foodSection.classList.add('hidden');
    pharmacySection.classList.add('hidden');
    othersSection.classList.add('hidden');
    cameraSection.classList.add('hidden');
    mapsSection.classList.add('hidden');
    profileSection.classList.add('hidden');
    walletSection.classList.add('hidden');

    navHome.classList.remove('active');
    navCamera.classList.remove('active');
    navMaps.classList.remove('active');
    navProfile.classList.remove('active');
    navWallet.classList.remove('active');

    if(section === 'home') {
      homeSection.classList.remove('hidden');
      navHome.classList.add('active');
    } else if(section === 'ecommerce') {
      ecommerceSection.classList.remove('hidden');
    } else if(section === 'food') {
      foodSection.classList.remove('hidden');
    } else if(section === 'pharmacy') {
      pharmacySection.classList.remove('hidden');
    } else if(section === 'others') {
      othersSection.classList.remove('hidden');
    } else if(section === 'camera') {
      cameraSection.classList.remove('hidden');
      startCamera();
      navCamera.classList.add('active');
    } else if(section === 'maps') {
      mapsSection.classList.remove('hidden');
      navMaps.classList.add('active');
      initMap();
    } else if(section === 'profile') {
      profileSection.classList.remove('hidden');
      navProfile.classList.add('active');
    } else if(section === 'wallet') {
      walletSection.classList.remove('hidden');
      navWallet.classList.add('active');
    }
  }

  // E-commerce Section
  function showEcommerce() {
    showSection('ecommerce');
    clearEcomUI();
    populateEcomMainCategories();
  }
  function clearEcomUI() {
    ecomMainCatList.innerHTML='';
    ecomSubCatContainer.innerHTML='';
    ecomProductContainer.innerHTML='';
    ecomCartList.innerHTML='';
    ecomCustomerDetailsContainer.classList.add('hidden');
    ecomSubmitOrderBtn.disabled = true;
    cart=[];
  }
  function populateEcomMainCategories() {
    ecomMainCatList.innerHTML='';
    Object.keys(ecomData).forEach(cat=>{
      let li=document.createElement('li');
      li.textContent=cat;
      li.onclick=()=>loadEcomCategory(cat);
      ecomMainCatList.appendChild(li);
    });
  }
  function loadEcomCategory(catName) {
    ecomSubCatContainer.innerHTML='';
    ecomProductContainer.innerHTML='';
    currentFolder=catName;
    let data=ecomData[catName];
    if(!data) return;

    if(data.categories){
      let ul=document.createElement('ul');
      ul.className='category-list';
      data.categories.forEach(subcat=>{
        let li=document.createElement('li');
        li.textContent=subcat;
        li.onclick=()=>loadEcomSubCategory(catName, subcat);
        ul.appendChild(li);
      });
      ecomSubCatContainer.innerHTML=`<h3>Select subcategory under ${catName}</h3>`;
      ecomSubCatContainer.appendChild(ul);
    }else if(data.items){
      showEcomProducts(data.items, catName);
    }
  }
  function loadEcomSubCategory(mainCat, subcat){
    ecomProductContainer.innerHTML='';
    currentSubFolder=subcat;
    let data=ecomData[mainCat];
    if(!data) return;

    if(mainCat==="Provision" || mainCat==="Meat"){
      // These have deeper nesting e.g. items inside subcategories
      const subData=data.items[subcat];
      if(subData?.categories){
        let ul=document.createElement('ul');
        ul.className='category-list';
        subData.categories.forEach(sc=>{
          let li=document.createElement('li');
          li.textContent=sc;
          li.onclick=()=>showEcomProducts(subData.items[sc], sc);
          ul.appendChild(li);
        });
        ecomSubCatContainer.innerHTML=`<h3>Select nested category under ${subcat}</h3>`;
        ecomSubCatContainer.appendChild(ul);
      } else if(subData?.items){
        showEcomProducts(subData.items, subcat);
      } else {
        showEcomProducts(subData, subcat);
      }
    }
    else if(data.items && data.items[subcat]){
      showEcomProducts(data.items[subcat], subcat);
    }
  }
  function showEcomProducts(items, category){
    ecomProductContainer.innerHTML='';
    if(!items) return;
    if(Array.isArray(items)){
      showEcomProductList(items, category, ecomProductContainer, ecomCartList, ecomSubmitOrderBtn, ecomCustomerDetailsContainer, ecomCustomerDetailsForm);
    } else {
      // items is object with categories
      for(let key in items){
        let h4=document.createElement('h4');
        h4.textContent=key;
        ecomProductContainer.appendChild(h4);
        showEcomProductList(items[key], category, ecomProductContainer, ecomCartList, ecomSubmitOrderBtn, ecomCustomerDetailsContainer, ecomCustomerDetailsForm);
      }
    }
  }

  // Food Section
  function showFood() {
    showSection('food');
    clearFoodUI();
    populateFoodCategories();
  }
  function clearFoodUI() {
    foodMainCatList.innerHTML='';
    foodSubCatContainer.innerHTML='';
    foodProductContainer.innerHTML='';
    foodCartList.innerHTML='';
    foodCustomerDetailsContainer.classList.add('hidden');
    foodSubmitOrderBtn.disabled = true;
    cart=[];
  }
  function populateFoodCategories() {
    foodMainCatList.innerHTML='';
    foodData.categories.forEach(cat=>{
      let li=document.createElement('li');
      li.textContent=cat;
      li.onclick=()=>loadFoodSubCategory(cat);
      foodMainCatList.appendChild(li);
    });
  }
  function loadFoodSubCategory(subcat){
    foodProductContainer.innerHTML='';
    currentFolder=null; currentSubFolder=subcat;
    const itemList=foodData.items[subcat];
    if(!itemList) return;

    if(subcat==="Chats"){
      foodSubCatContainer.innerHTML='';
      let chats=foodData.items["Chats"];
      if(chats?.categories){
        let ul=document.createElement('ul');
        ul.className='category-list';
        chats.categories.forEach(cat=>{
          let li=document.createElement('li');
          li.textContent=cat;
          li.onclick=()=>showFoodProducts(chats.items[cat], cat);
          ul.appendChild(li);
        });
        foodSubCatContainer.innerHTML=`<h3>Select Snacks or Chats</h3>`;
        foodSubCatContainer.appendChild(ul);
        return;
      }
    }
    foodSubCatContainer.innerHTML='';
    showFoodProducts(itemList, subcat);
  }
  function showFoodProducts(items, category){
    foodProductContainer.innerHTML='';
    showEcomProductList(items, category, foodProductContainer, foodCartList, foodSubmitOrderBtn, foodCustomerDetailsContainer, foodCustomerDetailsForm, true);
  }

  // Pharmacy Section
  function showPharmacy() {
    showSection('pharmacy');
    clearPharmacyUI();
    populatePharmacyItems();
  }
  function clearPharmacyUI() {
    pharmacyMainCatList.innerHTML = '';
    pharmacyProductContainer.innerHTML = '';
    pharmacyCartList.innerHTML = '';
    pharmacyCustomerDetailsContainer.classList.add('hidden');
    pharmacySubmitOrderBtn.disabled = true;
    cart = [];
  }
  function populatePharmacyItems() {
    pharmacyProductContainer.innerHTML = '';
    showEcomProductList(pharmacyData.items, "Pharmacy", pharmacyProductContainer, pharmacyCartList, pharmacySubmitOrderBtn, pharmacyCustomerDetailsContainer, pharmacyCustomerDetailsForm, false, true);
  }

  // Others Section
  function showOthers() {
    showSection('others');
    othersOrderForm.onsubmit = function(e) {
      e.preventDefault();
      const name = document.getElementById('others-name').value.trim();
      const mobile = document.getElementById('others-mobile').value.trim();
      const order = document.getElementById('others-order').value.trim();
      const address = document.getElementById('others-address').value.trim();

      if(!name || !mobile || !order || !address){
        alert("Please fill all details");
        return;
      }

      let orderText = `Order from ${name}\nMobile: ${mobile}\nAddress: ${address}\n\nOrder Details:\n${order}`;

      const whatsappNumber = '8977143043';
      const whatsappURL = `https://wa.me/${whatsappNumber}?text=${encodeURIComponent(orderText)}`;
      window.open(whatsappURL, '_blank');
      alert("Order sent to WhatsApp. Thank you!");
      othersOrderForm.reset();
      showSection('home');
    };
  }

  // Common product listing and add to cart function used in ecom, food, pharmacy
  function showEcomProductList(items, category, productContainer, cartList, submitBtn, customerDetailsContainer, customerDetailsForm, isFood=false, isPharmacy=false) {
    if(!items) return;
    let ul = document.createElement('ul');
    ul.className = 'product-list';

    items.forEach(p=>{
      let li=document.createElement('li');
      li.textContent = p + ' ';

      // Define quantity input
      let input, label;
      if(isFood){
        ({input, label} = createQuantityInput(1, 1, "plates"));
      } else if(isPharmacy){
        ({input, label} = createQuantityInput(1, 1, "sheets"));
      } else {
        ({input, label} = createQuantityInput(100, 50, "grams")); // default grams
      }

      let btn = document.createElement('button');
      btn.textContent = 'Add to Cart';
      btn.style.marginLeft = '10px';
      btn.onclick = () => addToCart(p, parseFloat(input.value), label.textContent.trim(), cartList, submitBtn, customerDetailsContainer);

      li.appendChild(input);
      li.appendChild(label);
      li.appendChild(btn);
      ul.appendChild(li);
    });

    productContainer.appendChild(ul);

    customerDetailsForm.onsubmit = (e) => {
      e.preventDefault();
      handleOrderSubmit(cartList, customerDetailsContainer, submitBtn);
    };
  }

  function createQuantityInput(min, step, unit){
    let input = document.createElement('input');
    input.type = 'number';
    input.min = min;
    input.step = step;
    input.value = min;
    input.style.width = '60px';
    input.style.marginLeft = '10px';

    let label = document.createElement('span');
    label.textContent = ` ${unit}`;
    label.style.marginLeft = '5px';

    return {input, label};
  }

  function addToCart(name, quantity, unit, cartList, submitBtn, customerDetailsContainer){
    if(quantity < 1){
      alert("Quantity must be at least 1");
      return;
    }
    let foundIndex = cart.findIndex(item => item.name === name && item.unit === unit);
    if(foundIndex >= 0){
      cart[foundIndex].quantity += quantity;
    } else {
      cart.push({name, quantity, unit});
    }
    refreshCartUI(cartList, submitBtn, customerDetailsContainer);
  }

  function refreshCartUI(cartList, submitBtn, customerDetailsContainer){
    cartList.innerHTML = '';
    cart.forEach(item => {
      let li = document.createElement('li');
      li.textContent = `${item.name} - ${item.quantity} ${item.unit}`;
      cartList.appendChild(li);
    });
    submitBtn.disabled = cart.length === 0;
    if(cart.length > 0){
      customerDetailsContainer.classList.remove('hidden');
    } else {
      customerDetailsContainer.classList.add('hidden');
    }
  }

  // Submit order handler generic for forms
  function handleOrderSubmit(cartList, customerDetailsContainer, submitBtn){
    if(cart.length === 0) {
      alert("Cart is empty");
      return;
    }
    const form = customerDetailsContainer.querySelector('form');
    const name = form.querySelector('input[type=text]').value.trim();
    const mobile = form.querySelector('input[type=tel]').value.trim();
    const address = form.querySelector('textarea').value.trim();

    if(!name || !mobile || !address){
      alert("Please fill all details");
      return;
    }

    let orderText = `Order from: ${name}\nMobile: ${mobile}\nAddress: ${address}\n\nItems:\n`;
    cart.forEach(item => {
      orderText += `- ${item.name}, Qty: ${item.quantity} ${item.unit}\n`;
    });

    const whatsappNumber = '8977143043';
    const whatsappURL = `https://wa.me/${whatsappNumber}?text=${encodeURIComponent(orderText)}`;

    window.open(whatsappURL, '_blank');
    alert("Order sent to WhatsApp successfully!");

    cart.length = 0;
    cartList.innerHTML = '';
    submitBtn.disabled = true;
    customerDetailsContainer.classList.add('hidden');

    showSection('home');
  }

  // Camera & others remains largely unchanged, per previous full code

  async function startCamera() {
    photoResult.innerHTML = '';
    retakeBtn.classList.add('hidden');
    captureBtn.classList.remove('hidden');
    sendPhotoBtn.classList.add('hidden');
    canvasElement.classList.add('hidden');
    videoElement.classList.remove('hidden');

    try {
      if(currentStream){
        currentStream.getTracks().forEach(track => track.stop());
      }
      const constraints = {video: {facingMode: useFrontCamera?"user":"environment"}};
      currentStream = await navigator.mediaDevices.getUserMedia(constraints);
      videoElement.srcObject = currentStream;
    } catch(e) {
      alert("Camera not accessible: " + e.message);
    }
  }

  function switchCamera() {
    useFrontCamera = !useFrontCamera;
    startCamera();
  }

  function capturePhoto() {
    canvasElement.width = videoElement.videoWidth;
    canvasElement.height = videoElement.videoHeight;
    canvasElement.getContext('2d').drawImage(videoElement,0,0);
    videoElement.classList.add('hidden');
    canvasElement.classList.remove('hidden');
    captureBtn.classList.add('hidden');
    retakeBtn.classList.remove('hidden');
    sendPhotoBtn.classList.remove('hidden');
    if(currentStream){
      currentStream.getTracks().forEach(track => track.stop());
      currentStream = null;
    }
  }

  function retakePhoto() {
    startCamera();
  }

  function sendPhotoWhatsApp() {
    alert("WhatsApp web cannot send photos directly through URL. Please share manually.");
  }

  function stopCamera() {
    if(currentStream){
      currentStream.getTracks().forEach(track => track.stop());
      currentStream = null;
    }
  }

  window.initMap = function() {
    const mapDiv = document.getElementById('map');
    mapDiv.textContent = "Loading map...";
    if(!navigator.geolocation){
      mapDiv.textContent = "Geolocation is not supported by your browser.";
      return;
    }
    navigator.geolocation.getCurrentPosition(
      (pos) => {
        const loc = {lat: pos.coords.latitude, lng: pos.coords.longitude};
        const map = new google.maps.Map(mapDiv, {zoom: 15, center: loc});
        new google.maps.Marker({position: loc, map: map, title: "You are here"});
      },
      () => {
        mapDiv.textContent = "Unable to retrieve location.";
      }
    );
  }

  init();
</script>

<script async defer src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&callback=initMap"></script>

</body>
</html>

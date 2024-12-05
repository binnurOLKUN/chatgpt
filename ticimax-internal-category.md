
css


/* Ana slider konteyner */
.button-group {
display: flex;
justify-content: center; /* Masaüstünde ortalamayı sağlar */
align-items: center;
overflow-x: auto; /* Yatay kaydırmayı etkinleştir */
scroll-snap-type: x mandatory; /* Scroll snapping özelliği */
gap: 10px; /* Butonlar arasındaki boşluk */
padding: 10px;
background-color: #f9f9f9;
border-bottom: 1px solid #ddd;
scrollbar-width: none; /* Firefox için scrollbar gizle */
touch-action: pan-x; /* Mobil cihazlarda yatay kaydırmayı etkinleştirir */
}

.button-group::-webkit-scrollbar {
display: none; /* Chrome, Safari için scrollbar gizle */
}

/* Slider butonları */
.button-group a {
flex: 0 0 auto; /* Sabit genişlikte butonlar */
padding: 10px 20px;
font-size: 16px;
text-decoration: none;
color: #000;
border: 1px solid #ccc;
border-radius: 5px;
background-color: #fff;
scroll-snap-align: start; /* Scroll snapping noktası */
transition: all 0.3s ease;
}

.button-group a:hover {
background-color: #f0f0f0;
border-color: #000;
}

/* Mobil uyumluluk */
@media screen and (max-width: 768px) {
.button-group {
justify-content: flex-start; /* Mobilde butonlar sola yaslanır */
}

.button-group a {
font-size: 14px; /* Daha küçük yazı boyutu */
padding: 8px 16px; /* Daha kompakt buton boyutu */
}
}

javascript

<script>
// Her sayfa için sabit 4 kategori eşlemesi
const categoryMapping = {
"erkek-spor-ayakkabi": [
{ name: "Erkek Ayakkabı", link: "/erkek-ayakkabi" },
{ name: "Erkek Bot", link: "/erkek-bot-ayakkabi-modelleri" },
{ name: "Erkek Sandalet & Terlik", link: "/erkek-sandalet-terlik-modelleri" },
{ name: "Sneaker Erkek Ayakkabı", link: "/sneaker-erkek-ayakkabi-modelleri" }
],
"erkek-ayakkabi": [
{ name: "Erkek Spor Ayakkabı", link: "/erkek-spor-ayakkabi" },
{ name: "Erkek Bot", link: "/erkek-bot-ayakkabi-modelleri" },
{ name: "Erkek Klasik Ayakkabı", link: "/erkek-klasik-ayakkabi" },
{ name: "Yazlık Erkek Ayakkabı", link: "/yazlik-erkek-ayakkabi" }
],
"erkek-bot-ayakkabi-modelleri": [
{ name: "Erkek Klasik Ayakkabı", link: "/erkek-klasik-ayakkabi" },
{ name: "Erkek Spor Ayakkabı", link: "/erkek-spor-ayakkabi" },
{ name: "Erkek Ayakkabı", link: "/erkek-ayakkabi" },
{ name: "Erkek Casual Ayakkabı", link: "/erkek-casual-ayakkabi" }
],
"sneaker-erkek-ayakkabi-modelleri": [
{ name: "Erkek Günlük Ayakkabı", link: "/erkek-gunluk-ayakkabi" },
{ name: "Yüksek Taban Erkek Ayakkabı", link: "/yuksek-taban-erkek-ayakkabi" },
{ name: "Erkek Spor Ayakkabı", link: "/erkek-spor-ayakkabi" },
{ name: "Erkek Ayakkabı", link: "/erkek-ayakkabi" }
]
};

// Bulunduğunuz sayfayı algıla
function getCurrentPage() {
// URL'deki son parçayı al ve kategori adına dönüştür
const path = window.location.pathname;
const pageName = path.split("/").filter(part => part).pop();
return pageName;
}

// İlgili kategorileri al ve render et
function renderCategories() {
const currentPage = getCurrentPage();
const relatedCategories = categoryMapping[currentPage];

if (!relatedCategories) return; // Eğer sayfa eşlemesi yoksa hiçbir şey yapma

const container = document.getElementById("category-buttons");
relatedCategories.forEach(category => {
const link = document.createElement("a");
link.href = category.link;
link.textContent = category.name;
container.appendChild(link);
});
}

// Sayfa yüklendiğinde çalıştır
document.addEventListener("DOMContentLoaded", renderCategories);


</script>

html

<div class="button-group" id="category-buttons">
<!-- Dinamik butonlar buraya eklenecek -->
</div>

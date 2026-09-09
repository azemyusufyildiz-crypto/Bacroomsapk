# BACKROOMS — Meridyen Lojistik

Tek bir HTML dosyasından ibaret, tarayıcıda ve telefonda çalışan 3B korku oyunu.
Hiç hazır model, doku veya ses dosyası kullanılmıyor: dünyanın tamamı, bütün
sesler ve bütün dokular kodun içinde üretiliyor.

> Meridyen Lojistik'te gece vardiyasındasın. Envanter çizelgesinde bir satır
> fazla: **DEPO B**. Böyle bir alan yok ama kapı orada duruyor.

---

## Hikaye

Sekiz aydır aynı depoda çalışıyorsun. Bu gece sayım var ve listede olmayan bir
alan var. Kapıyı açıyorsun, arkasında depo yerine sarı odalar çıkıyor.

Altı kat aşağı inerken hikayeyi dört ayrı ses anlatıyor:

| Ses | Kim | Ne anlatıyor |
|---|---|---|
| Kasetler | **Kerem** | Senden önceki vardiya. 35 kayıt, indikçe çözülüyor. |
| Evraklar | **Şirket** | Kimse cahil değil. Herkes biliyor ve formu dolduruyor. |
| El yazısı defter | **M. Aydın** | 1986'da burayı bulan adam. Şirketi neden kurduğunu anlatıyor. |
| Etiketsiz bantlar | **Sen** | Kaydettiğini hatırlamadığın, kendi sesinle kayıtlar. |

Toplam **23 belge** var, hiçbiri zorunlu değil. Kaç tanesini bulduğuna göre
**üç farklı son** açılıyor: Sessiz Son, Döngü Sonu, Gerçek Son.

---

## Seviyeler

Her katın kendi harita üreticisi, dokuları, aydınlatması, akustiği, prop'ları
ve canavarı var.

| # | Kat | Yapı | Tehdit |
|---|---|---|---|
| — | **Prolog: Depo** | Raflar, forklift, zincirler | Yok — sadece yürüyorsun |
| 0 | Sarı Odalar | Döngülü labirent | Sırıtan |
| 1 | Yaşanabilir Bölge | Devasa depo salonları | Tazı (sürü) |
| 2 | Boru Rüyaları | Dallanan dar tüneller | Sürüngen (pusucu) |
| 3 | Elektrik İstasyonu | Servis ızgarası | Deri Hırsızı |
| 4 | Terk Edilmiş Ofis | Koridor + kapılı odalar | Deri Hırsızı (tek) |
| 5 | Dehşet Oteli | Koridorlar + sıra odalar | Fare sürüsü |

---

## Kontroller

**Telefon**
- Sol yarı: yürüme çubuğu · Sağ yarı: bakış
- **KOŞ** / **ÇÖMEL** · **AL** (bağlama göre AÇ / SAKLAN / ÇALIŞTIR)
- Alt kısımdaki **kemer**: yuvaya dokun, **KULLAN**'a bas
- Dolaptayken **ÇÖMEL** basılı = nefes tut

**Bilgisayar**
| Tuş | İşlev |
|---|---|
| WASD / ok | Hareket |
| Fare | Bakış |
| Shift / Ctrl | Koş / Çömel |
| E | Al · Aç · Saklan |
| 1-7 | Kemer yuvası seç |
| Boşluk | Seçili eşyayı kullan |
| F / Q / R / G | Fener · Cıvata · Su · Tebeşir |
| ESC | Duraklat |

---

## Bilmen gerekenler

Oyun bunları sana ilk seviyede kendisi öğretiyor, ama özet:

- **Sadece seni GÖRÜRSE kovalar.** Ses duyunca koşarak gelmez, yürüyerek bakmaya gelir.
- **Koşmak 13 metre öteden duyulur.** Çömelmek neredeyse sessizdir.
- **Fener seni %70 daha uzaktan görünür yapar.** Kibrit sadece %25 — karanlıkta kalmak güvenlidir.
- **Dolaba görülmeden gir.** Kovalarken girersen kapıyı açar. İçerideyken nefesini tut.
- **Ona baktıkça hızlanır.** Arkana bakmak istersin ama bakmak onu hızlandırır.
- **Saldırmadan önce tüm sesler kesilir.** O sessizlik uyarıdır.
- **Diğerlerinden koyu duran duvarlar incedir**, içinden geçilir ve bir alt kata düşersin.
- Envanter **boş başlar**. El feneri dahil her şeyi bulman gerekir.

---

## Çalıştırma

### Tarayıcıda
`backrooms.html` dosyasını çift tıkla. İlk açılışta Three.js internetten
iniyor ve **telefonda saklanıyor**; sonraki açılışlarda internet gerekmiyor.

### Tamamen çevrimdışı
1. `https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js` adresini aç
2. `three.min.js` adıyla kaydet
3. HTML dosyasıyla **aynı klasöre** koy

Kod önce yanındaki dosyaya bakar, hiçbir siteye bağlanmaz.

### APK (htmltoapk)
`backrooms-mini.html` kullan. Yapıştırma kutusunun 100.000 karakter sınırına
sığması için sıkıştırılmış sürüm budur — **içerik birebir aynıdır**, kırpılmış
değildir.

### APK (Termux)
`backrooms.html` kullan, `assets/` klasörüne olduğu gibi koy. Orada karakter
sınırı yok ve okunabilir sürüm daha uygun.

---

## Dosyalar

| Dosya | Ne işe yarar |
|---|---|
| `backrooms.html` | Tam sürüm, okunabilir kod (~240 KB) |
| `backrooms-mini.html` | Aynı oyun, gzip'lenip gömülmüş (~95 KB) |
| `logo/icon-*.png` | Android başlatıcı ikonları (48-512 px) |
| `logo/store-banner-1024x500.png` | Mağaza öne çıkan görseli |

Mini sürüm çalışırken kendini açıyor; bunun için `DecompressionStream`
gerekiyor (Chrome 80 ve sonrası, 2020'den beri var).

---

## Teknik

Three.js r128 dışında hiçbir bağımlılık yok.

**Dünya** — Altı ayrı prosedürel harita üreticisi. Duvar kağıdı, halı, beton,
tavan plakası, ahşap, karton: hepsi `<canvas>` üstünde çiziliyor ve
albedo'dan **normal haritası** üretiliyor. Duvarlar tek instanced çizim
çağrısında basılıyor, her bloğa rastgele UV kaydırması veriliyor.

**Işık** — Fiziksel ışık sönümü (ters-kare), tavandan aşağı gölge haritalı
spot ışıklar, gökyüzü/zemin ışığı, göz uyumu (pupil karanlıkta yavaş açılıyor),
gerçek ampul renkleri, floresan titremesi ve ölü lambalar.

**Post-process** — Elle yazılmış çok geçişli hat: parlak-geçiş → ayrılmış
gauss bulanıklığı → birleştirme. Bloom, renk derecelendirme, kromatik sapma,
objektif bombeleşmesi, keskinleştirme, film greni, bant kırıcı dither.

**Yapay zekâ** — Dört durumlu makine (devriye / araştır / av / tarama).
Görüş konisi, farkındalık birikimi, ses olayları, sürü haberleşmesi, BFS yol
bulma ve kesişim tahmini. Her tür farklı davranıyor: Tazı iz kokluyor,
Sürüngen pusu kuruyor, Fare ışıktan kaçıyor, Deri Hırsızı sen bakınca donuyor
ve senin seslerini taklit ediyor, Sırıtan gözünü ayırdığında yaklaşıyor.

**Ses** — Tek bir dosya bile yok. Floresan uğultusu, tüp tıslaması, ayak
sesleri, çığlıklar, nefes, damlayan su ve müzik WebAudio ile sentezleniyor.
Yönlü ses (stereo panner + mesafe), seviyeye özel yankı (kodla üretilmiş
darbe yanıtı) ve kovalanırken susan müzik var.

**Çok oyunculu** — PeerJS ile eş-eşe, kurucu otoriter. Harita tohumlu
rastgelelikle üretildiği için iki cihazda birebir aynı çıkıyor. Düşen oyuncuyu
takım arkadaşı kaldırabiliyor.

**Performans** — Dinamik çözünürlük, iki karede bir gölge tazeleme, ışık
havuzu, instanced çizim, otomatik kalite düşürme.

---

## Geliştirici kısayolu

Sol üst köşeye **2,5 saniye içinde 5 kez** dokun → seviye seçme paneli açılır.

Yayınlamadan önce kaldırmak istersen `devZone` ile ilgili satırları sil.

---

## Bilinen sınırlar

- Seslendirme yok; kasetler metin ve sentezlenmiş konuşma efektiyle veriliyor.
- Çok oyunculu, PeerJS'in ücretsiz aracı sunucusunu kullanıyor. Bazı mobil
  ağlarda NAT yüzünden bağlantı kurulamayabilir. Kurucu çıkarsa oda dağılır.
- Dokular prosedürel; yakından bakınca fotoğraf tabanlı olmadıkları belli olur.
- Oyun Türkçe. Başka dil desteği yok.

---

## Not

Bu oyun bir telefonda, tek dosyada, hazır varlık kullanılmadan yazıldı.
Kodun tamamı `backrooms.html` içinde ve okunabilir halde duruyor.

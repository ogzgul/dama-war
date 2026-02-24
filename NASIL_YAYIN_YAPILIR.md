# 🎮 Dama Oyununu Paylaşma & Canlı Yayın Rehberi

> Bu rehber; oyunu Netlify'a nasıl yükleyeceğinizi, arkadaşlarınızla nasıl oynayacağınızı
> ve OBS Studio ile nasıl canlı yayın yapacağınızı adım adım açıklamaktadır.

---

## 1. Netlify'a Deploy Etme (Yayına Alma)

### Yöntem A — Sürükle & Bırak (En Kolay, 2 Dakika)

1. Tarayıcınızda **[app.netlify.com/drop](https://app.netlify.com/drop)** adresini açın.
2. `dama` klasörünüzü (içinde `index.html` olan klasör) sayfaya **sürükleyip bırakın**.
3. Netlify otomatik olarak sitenizi yayına alır ve size şöyle bir URL verir:
   ```
   https://ilginc-isim-123456.netlify.app
   ```
4. Bu URL'yi kopyalayıp arkadaşlarınızla paylaşın — **kurulum gerekmez, tıklamaları yeterli!**

> **Not:** Ücretsiz Netlify hesabınız olmadan da çalışır, ancak hesap açarsanız
> URL'yi özelleştirebilirsiniz (ör. `https://damaoyunum.netlify.app`).

---

### Yöntem B — GitHub + Netlify (Kalıcı & Otomatik Güncelleme)

1. **GitHub'da yeni bir repo açın** (ör. `dama-game`).
2. `dama` klasörünün içindekilerini bu repoya push edin:
   ```bash
   git init
   git add .
   git commit -m "Dama oyunu ilk sürüm"
   git remote add origin https://github.com/KULLANICI/dama-game.git
   git push -u origin main
   ```
3. **[app.netlify.com](https://app.netlify.com)** → *Add new site* → *Import an existing project* → GitHub'ı seçin.
4. Reponuzu seçin, **Build command** ve **Publish directory** alanlarını **boş bırakın** (saf HTML dosyası).
5. *Deploy site* butonuna tıklayın.

✅ Artık her `git push` yaptığınızda Netlify otomatik günceller.

---

### Netlify'da Özel Alan Adı (Opsiyonel)

- Netlify panonuzda *Domain settings* → *Add custom domain* bölümünden kendi alan adınızı bağlayabilirsiniz.
- Ücretsiz subdomain değiştirmek için: *Site settings* → *Site name* → istediğiniz ismi yazın.

---

## 2. Online Çok Oyunculu Nasıl Kullanılır

Oyun, **PeerJS** teknolojisi sayesinde herhangi bir sunucu kurmadan direkt tarayıcı-tarayıcı (P2P) bağlantı kurar.

### Oda Oluşturma (Ev Sahibi)

1. Oyunu açın → **🌐 Online Multiplayer** butonuna tıklayın.
2. **Create Room** sekmesinde **Generate Room** butonuna basın.
3. Size 6 karakterlik bir **oda kodu** gösterilir (ör. `ABCD12`).
4. **Copy Link** butonuyla tam URL'yi kopyalayıp arkadaşınıza gönderin:
   ```
   https://damaoyunum.netlify.app/#ABCD12
   ```
5. Arkadaşınız bağlandığında yeşil "Connected" mesajı çıkar, oyun başlar.
6. Siz **Beyaz** (White) oynarsınız, rakibiniz **Siyah** (Black) oynamaya başlar.

### Odaya Katılma (Misafir)

**Seçenek 1 — Direkt Link:**
Arkadaşınızın paylaştığı URL'ye tıklayın → sayfa otomatik olarak Join ekranını açar → **Join Room** butonuna basın.

**Seçenek 2 — Manuel Kod:**
1. Oyunu açın → **🌐 Online Multiplayer** → **Join Room** sekmesi.
2. 6 karakterlik kodu girin (ör. `ABCD12`).
3. **Join Room** butonuna basın.

> 💡 **İpucu:** Farklı cihazlar (telefon + bilgisayar) aynı ağda olmak **zorunda değildir**.
> İnternet bağlantısı olan her yerden oynanabilir.

---

## 3. OBS Studio ile Canlı Yayın

### OBS Studio Kurulumu

1. **[obsproject.com](https://obsproject.com)** adresinden OBS Studio'yu indirin ve kurun.
2. OBS'yi açın → sihirbazda *Sadece kayıt* veya *Yayın için optimize et* seçeneğini seçin.

### Tarayıcı Kaydı (En İyi Kalite)

**Yöntem 1 — Pencere Yakalama:**
1. OBS ana ekranında *Sources (Kaynaklar)* panelinde **+** → **Window Capture** seçin.
2. Oyununun açık olduğu tarayıcı penceresini listeden seçin.
3. Oyun tam ekranda görünür.

**Yöntem 2 — Browser Source (Önerilen):**
1. *Sources* → **+** → **Browser Source**.
2. URL alanına Netlify adresinizi girin:
   ```
   https://damaoyunum.netlify.app
   ```
3. Genişlik `1920`, Yükseklik `1080` ayarlayın.
4. OBS içinde oyunu doğrudan görüntüler — başka bir pencereye gerek kalmaz.

### Ses Ayarları

- Yorum yapmak için: *Sources* → **+** → **Audio Input Capture** → mikrofonunuzu seçin.
- Arka plan müziği için ayrı bir *Media Source* ekleyebilirsiniz.

---

## 4. Twitch'e Canlı Yayın

1. **[twitch.tv](https://twitch.tv)** adresinde hesap açın.
2. Twitch Panonuzda: **Ayarlar → Yayın → Stream Key** → anahtarı kopyalayın.
3. OBS'de: *Settings → Stream*:
   - Service: **Twitch**
   - Stream Key: yapıştırın
4. OBS ana ekranında **Start Streaming** butonuna basın.
5. Twitch profilinize giderek yayınınızı izleyebilirsiniz.

---

## 5. YouTube'a Canlı Yayın

1. **[studio.youtube.com](https://studio.youtube.com)** → *Create → Go Live*.
2. *Stream* sekmesinde **Stream Key**'i kopyalayın.
3. OBS'de: *Settings → Stream*:
   - Service: **YouTube - RTMPS**
   - Stream Key: yapıştırın
4. **Start Streaming** → YouTube'da canlı yayına geçin.

---

## 6. Oyun Linki Paylaşımı (Özet)

| Nereden Paylaş | Nasıl |
|----------------|-------|
| WhatsApp / Telegram | Netlify URL'sini yapıştır |
| Oda linki (online oyun) | `Copy Link` butonu → URL'yi gönder |
| Twitch/YouTube yayını | Stream Key ile OBS bağlantısı |
| QR Kod | [qr-code-generator.com](https://www.qr-code-generator.com) sitesine URL'yi yapıştır |

---

## 7. Sık Sorulan Sorular

**Netlify'a yükleme ücretsiz mi?**
Evet. Kişisel projeler için Netlify tamamen ücretsizdir. Aylık 100 GB bant genişliği ve 300 dakika build süresi içerir — bu oyun için fazlasıyla yeterli.

**Online oyun için sunucu gerekiyor mu?**
Hayır. Oyun **WebRTC / PeerJS** teknolojisiyle direkt cihazlar arası bağlantı kurar. Herhangi bir ücretli sunucu gerekmez.

**Oda kodu ne kadar süre geçerli?**
Ev sahibi tarayıcı sekmesini kapatana kadar geçerlidir. Sekme kapanırsa yeni bir oda oluşturmanız gerekir.

**Telefonda çalışır mı?**
Evet. Oyun mobil uyumludur. iOS Safari ve Android Chrome'da sorunsuz çalışır.

**OBS ile yayın yaparken kalite düşüyor, ne yapmalıyım?**
OBS Ayarları → Output → Video Bitrate'i `4000-6000 Kbps` olarak ayarlayın. İnternet hızınız yeterliyse bu kaliteyi artırır.

---

*Dama oyununun tadını çıkarın! Herhangi bir sorun için oyunun kaynak kodunu inceleyebilirsiniz.*

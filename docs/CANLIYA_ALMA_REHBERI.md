# Dama War — App Store Canlıya Alma Rehberi

## 1. GitHub Pages Kurulumu (Privacy Policy için)

### Adım 1: GitHub'da repo oluştur
1. github.com → **New repository**
2. Repository name: `dama-war` (veya istediğin bir isim)
3. **Public** seç
4. **Create repository** tıkla

### Adım 2: `docs/` klasörünü yükle
```bash
cd /Users/oguzgul/Desktop/Project/dama
git init
git add docs/
git commit -m "Add privacy policy and support pages"
git remote add origin https://github.com/KULLANICI_ADIN/dama-war.git
git push -u origin main
```

### Adım 3: GitHub Pages'i etkinleştir
1. GitHub'da repo → **Settings** → **Pages**
2. Source: **Deploy from a branch**
3. Branch: `main` / `docs` klasörünü seç → **Save**
4. Birkaç dakika sonra URL aktif olur:
   `https://KULLANICI_ADIN.github.io/dama-war/`

### Adım 4: URL'leri güncelle
- **Privacy Policy:** `https://KULLANICI_ADIN.github.io/dama-war/`
- **Support:** `https://KULLANICI_ADIN.github.io/dama-war/support.html`

---

## 2. App Store Connect — Tüm Alanları Doldur

### appstoreconnect.apple.com → Dama War → App Information

| Alan | Değer |
|------|-------|
| Name | Dama War |
| Subtitle | Turkish Checkers Online |
| Category | Games → Board |
| Content Rights | No third-party content |

### App Store → Turkish (opsiyonel, İngilizce zorunlu)

**Açıklama (Description):**
```
Challenge your friends or test your skills against AI in this authentic Turkish Dama (Checkers) game!

GAME MODES
• Two Players — Play locally on the same device
• vs Computer (Easy) — Relaxed practice for beginners
• vs Computer (Hard) — Challenging computer opponent
• Online Multiplayer — Play with anyone, anywhere in real time

HOW TO PLAY ONLINE
Create a room and share the 6-character code with your friend. They enter the code to connect — no account needed, no registration, just play!

TURKISH DAMA RULES
• Pieces move forward and sideways
• Captures are mandatory in all 4 directions
• Chain captures required — longest chain wins
• Kings slide any distance
• Classic Turkish board game rules

FEATURES
• Beautiful dark theme with gold accents
• Smooth piece animations
• Real-time P2P online multiplayer
• No account or login required
• No ads, no in-app purchases — completely free
• Offline play for local and computer opponent modes
```

**Keywords (100 karakter):**
```
dama,checkers,turkish checkers,board game,strategy,multiplayer,online,2 player,classic,turn based
```

**Promotional Text (170 karakter — review gerektirmez, istediğin zaman değiştirebilirsin):**
```
Play Turkish Dama online with friends! Create a room, share the code, and start playing instantly.
```

**Support URL:**
```
https://KULLANICI_ADIN.github.io/dama-war/support.html
```

**Marketing URL (opsiyonel):**
```
https://KULLANICI_ADIN.github.io/dama-war/
```

---

## 3. App Privacy (App Store Connect → App Privacy)

**Data Collection:** NO — "We do not collect data from this app"

Tüm sorulara **No** de:
- [ ] Contact Info → No
- [ ] Health & Fitness → No
- [ ] Financial Info → No
- [ ] Location → No
- [ ] Sensitive Info → No
- [ ] Contacts → No
- [ ] User Content → No
- [ ] Browsing History → No
- [ ] Search History → No
- [ ] Identifiers → No
- [ ] Usage Data → No
- [ ] Diagnostics → No

---

## 4. Screenshots Yükleme

**Hazır screenshot'lar (1320×2868 — iPhone 17 Pro Max):**
```
/Users/oguzgul/Desktop/Project/dama/docs/screenshots/
├── SS2_game.png      ← Oyun ekranı
├── SS3_ingame.png    ← Oyun içi
├── SS4_ai.png        ← AI modu
└── SS5_online.png    ← Online mod
```

App Store Connect → Dama War → **iOS App** → **1.0 Prepare for Submission**:
1. **App Previews and Screenshots** bölümü
2. **iPhone 6.9"** (1320 × 2868) → 4 screenshot'ı sürükle bırak
3. **Save** tıkla

> Not: Daha iyi screenshot için Simulator'ı aç, ekranın ilginç bir yerindeyken
> Cmd+S ile Mac'e kaydet veya:
> ```bash
> xcrun simctl io booted screenshot ~/Desktop/screenshot.png
> ```

---

## 5. Age Rating

App Store Connect → **Age Rating** → **Edit**:

| Soru | Cevap |
|------|-------|
| Cartoon Violence | None |
| Realistic Violence | None |
| Sexual Content | None |
| Profanity | None |
| Gambling | None |
| (diğer hepsi) | None |

**Sonuç: 4+** ✅

---

## 6. Pricing & Availability

- Price: **Free**
- Availability: **All countries** (veya istediğin ülkeler)

---

## 7. Review Bilgileri (App Review Information)

| Alan | Değer |
|------|-------|
| Contact First Name | Oğuz |
| Contact Last Name | GÜL |
| Phone Number | +90 5XX XXX XXXX |
| Email | oguz_gul216@hotmail.com |
| Notes | "Dama War is a free Turkish Checkers game. Online multiplayer uses P2P (PeerJS/WebRTC). No server-side data is stored. To test online: create a room on one device, join with the code on another." |

---

## 8. Submit for Review

1. Tüm alanlar yeşil tik mi? ✅
2. Screenshots yüklendi mi? ✅
3. Privacy Policy URL dolu mu? ✅
4. **Add to Review** → **Submit to App Review**

Apple genellikle **24-48 saat** içinde inceler.

---

## Checklist — Canlıya Alma

- [ ] GitHub Pages URL aktif: `https://KULLANICI_ADIN.github.io/dama-war/`
- [ ] Privacy Policy URL App Store Connect'te girildi
- [ ] Support URL girildi
- [ ] Description (EN) dolduruldu
- [ ] Keywords girildi
- [ ] Screenshots yüklendi (en az 1 adet, 1320×2868)
- [ ] App icon 1024×1024 yüklendi (zaten var)
- [ ] Age Rating tamamlandı (4+)
- [ ] App Privacy → No data collected
- [ ] Price: Free seçildi
- [ ] Review bilgileri dolduruldu
- [ ] **Submit for Review** tıklandı 🚀

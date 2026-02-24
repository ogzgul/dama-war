# Dama War — TestFlight'a Yükleme Rehberi

## Ön Koşullar

| Gereksinim | Durum |
|------------|-------|
| Apple Developer hesabı ($99/yıl) | ✅ Var |
| Fastlane kurulu (`fastlane --version`) | ✅ Var |
| App Store Connect'te "Dama War" uygulaması | ✅ Oluşturuldu |
| ASC API Key (.p8 dosyası) | ✅ `fastlane/keys/AuthKey.p8` |
| `.env` dosyası dolu | ✅ `fastlane/.env` |

---

## Her Güncelleme İçin Adımlar

### 1. Web kodunu güncelle
```bash
# Oyun dosyasını düzenlediysen www/ klasörüne kopyala
# (zaten www/index.html üzerinde çalışılıyor)
```

### 2. iOS projesini senkronize et
```bash
cd /Users/oguzgul/Desktop/Project/dama/mobile
npx cap sync ios
```

### 3. TestFlight'a yükle
```bash
cd /Users/oguzgul/Desktop/Project/dama/mobile/ios/App
fastlane beta
```

**Bu kadar.** Fastlane otomatik olarak:
- Build numarasını artırır
- Distribution sertifikasını kontrol eder
- IPA derler ve imzalar
- TestFlight'a yükler

---

## `fastlane beta` Adım Adım Ne Yapar?

```
1. app_store_connect_api_key  → ASC API Key ile kimlik doğrular
2. latest_testflight_build_number → Mevcut build numarasını alır
3. increment_build_number     → Build numarasını 1 artırır
4. cert                       → Distribution sertifikasını kontrol/indirir
5. sigh                       → App Store provisioning profile indirir
6. update_code_signing_settings → Projeye manuel imza ayarlar
7. gym                        → IPA derler (Release, App Store imzalı)
8. upload_to_testflight        → App Store Connect'e yükler
```

Toplam süre: ~2-4 dakika (bağlantı hızına göre)

---

## Dosya Yapısı

```
dama/mobile/ios/App/fastlane/
├── Fastfile          # Lane tanımları (beta, unsigned, simulator)
├── Appfile           # Bundle ID ve hesap bilgileri
├── .env              # Gizli anahtarlar (git'e ekleme!)
└── keys/
    ├── AuthKey.p8              # ASC API Key (git'e ekleme!)
    └── AuthKey_MUTS7Q624T.p8   # Yedek kopya
```

---

## `.env` Dosyası

```
# /Users/oguzgul/Desktop/Project/dama/mobile/ios/App/fastlane/.env
ASC_KEY_ID=MUTS7Q624T
ASC_ISSUER_ID=9143a885-6573-40d4-bd12-8c286503b517
ASC_KEY_FILEPATH=.../fastlane/keys/AuthKey.p8
TEAM_ID=5PY8Q784PU
APPLE_ID=oguz_gul216@hotmail.com
```

> ⚠️ Bu dosyayı asla git'e ekleme! `.gitignore`'da zaten var.

---

## Diğer Lane'ler

```bash
# İmzasız IPA (AltStore / Sideloadly için)
fastlane unsigned
# → build/Dama_unsigned.ipa

# Simulator'da çalıştır
fastlane simulator

# Geliştirici cihazına yükle (ücretsiz Apple ID)
fastlane dev
```

---

## TestFlight'ta Tester Davet Etme

1. **appstoreconnect.apple.com** → Dama War → TestFlight
2. **Internal Testing** (sadece ekip üyeleri, max 100 kişi, anında kullanılabilir)
3. **External Testing** (herkese açık, Apple onayı ~24 saat)
   - Groups → New Group → isim ver
   - Add Testers → e-posta ile davet gönder
   - Public Link oluşturabilirsin (link paylaşımıyla katılım)

---

## Sık Karşılaşılan Hatalar

| Hata | Çözüm |
|------|-------|
| `Couldn't find app` | App Store Connect'te uygulama kaydı oluştur |
| `Invalid bundle` orientation hatası | Info.plist'te iPad için 4 orientation gerekli |
| `No profiles found` | `fastlane sigh` veya `fastlane beta` yeniden çalıştır |
| `Your team has no devices` | iPhone'u Mac'e bağla veya `fastlane beta` (cert+sigh otomatik çözer) |
| API Key hatası | `.env` dosyasında değerleri kontrol et |

---

## Version vs Build Numarası

| Alan | Değer | Nerede |
|------|-------|--------|
| **Version** (pazarlama) | `1.0`, `1.1`, `2.0` | App Store'da görünür |
| **Build** (teknik) | `1`, `2`, `3`... | TestFlight'ta görünür |

Build numarası Fastlane tarafından otomatik artırılır.
Version'ı güncellemek için:
```bash
cd /Users/oguzgul/Desktop/Project/dama/mobile/ios/App
agvtool new-marketing-version 1.1
```

---

## Önemli Dosya Yolları

```
Proje kökü:
/Users/oguzgul/Desktop/Project/dama/

Web oyunu:
/Users/oguzgul/Desktop/Project/dama/mobile/www/index.html

iOS projesi:
/Users/oguzgul/Desktop/Project/dama/mobile/ios/App/

Build çıktıları:
/Users/oguzgul/Desktop/Project/dama/mobile/build/
  ├── Dama_appstore.ipa    ← TestFlight için
  ├── Dama_unsigned.ipa    ← AltStore için
  └── Dama_appstore.app.dSYM.zip
```

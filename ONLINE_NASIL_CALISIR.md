# Dama War — Online Çok Oyunculu Nasıl Çalışır?

## Kısaca: P2P (Eşten Eşe) Bağlantı

Dama War, iki telefon arasında **doğrudan** iletişim kurar. Bir sunucu üzerinde oyun verisi saklanmaz.

```
Telefon A  ←──── PeerJS Cloud (aracı) ────→  Telefon B
                  (sadece bağlantı kurar)
           ←═══════ Oyun verisi (P2P) ════════→
```

**PeerJS Cloud** sadece iki telefonu birbirine tanıştırır. Bağlantı kurulduktan sonra hamleler doğrudan telefondan telefona gider.

---

## Oyun Nasıl Başlatılır?

### Oda Oluşturan (Davet Eden) — Telefon A
1. Uygulamayı aç → **Online Multiplayer** seç
2. **Create Room** → **Generate Room** tıkla
3. 6 karakterlik bir **oda kodu** oluşur (örn: `KX7MNA`)
4. Bu kodu arkadaşına ilet (mesaj, WhatsApp, sesli söyle)
5. Arkadaşın bağlanınca oyun başlar — **sen Beyaz** oynar

### Katılan Kişi (Arkadaş) — Telefon B
1. Uygulamayı aç → **Online Multiplayer** seç
2. **Join Room** sekmesine geç
3. 6 haneli kodu yaz → **Join Room** tıkla
4. Bağlantı kurulur — **sen Siyah** oynar

---

## İnternet Şartı

| Durum | Sonuç |
|-------|-------|
| İki telefon da internete bağlı | ✅ Çalışır |
| Farklı ağlar (biri WiFi, biri 4G) | ✅ Çalışır |
| Aynı WiFi ağında | ✅ Çalışır |
| İnternet yoksa | ❌ Çalışmaz |

> Oda kodu **6 haneli** ve **büyük harf/rakam** karışımıdır.
> Kod yalnızca o an için geçerlidir; uygulama kapanınca kaybolur.

---

## Teknik Detay (Merak Edenler İçin)

- **PeerJS** kütüphanesi WebRTC P2P bağlantısı kullanır
- Broker sunucusu: `0.peerjs.com` (ücretsiz, herkese açık)
- Peer ID formatı: `damav2-xxxxxx` (küçük harfe çevrilmiş kod)
- Oyun verisi: JSON formatında, her hamlede karşı tarafa iletilir
- Veri şifrelenmez — rekabetçi değil, eğlencelik bir oyun

---

## Sorun Giderme

| Sorun | Çözüm |
|-------|-------|
| "Timed out" hatası | Oda kodunu kontrol et, oluşturan hâlâ bekliyor mu? |
| Bağlantı kurulamıyor | İki telefon da internete bağlı mı? |
| Rakip çıktı | "Disconnected" ekranı çıkar, menüye dön |
| Kod çalışmıyor | "Generate Room" ile yeni kod oluştur |

---

## Sıkça Sorulan Sorular

**S: Oda kodu neden localhost gösteriyor?**
C: Bu uygulama içi teknik URL'dir, önemsemezsin. Sadece 6 haneli kodu arkadaşına gönder — o kod çalışır.

**S: Kaç kişi aynı anda oynayabilir?**
C: Her oda 2 kişiliktir. Birden fazla oyun için farklı odalar kurulabilir.

**S: Oyun kaydediliyor mu?**
C: Hayır. Uygulama kapanınca oyun biter.

**S: Rakip bağlantıyı keserse ne olur?**
C: "Disconnected" ekranı çıkar ve menüye dönebilirsin.

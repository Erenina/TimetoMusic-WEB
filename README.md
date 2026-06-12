# Time to Music — Tanıtım Sitesi

[Time to Music](https://testflight.apple.com/join/SKZj7DAN) iOS uygulamasının tanıtım sitesi.
Saf HTML/CSS — build adımı yok, her statik hosting'de çalışır.

## Sayfalar

| Dosya | İçerik |
|---|---|
| `index.html` | Ana tanıtım sayfası (hero, özellikler, SSS, TestFlight CTA) |
| `gizlilik.html` | Gizlilik Politikası (App Store zorunluluğu) |
| `kosullar.html` | Kullanım Koşulları |
| `destek.html` | Destek / SSS (App Store "Support URL" için) |

## Yerelde önizleme

```bash
cd timetomusic-website
python3 -m http.server 8000
# http://localhost:8000
```

## Yayınlama (timetomusic.com — GitHub Pages)

Domain GoDaddy'den alındı, site GitHub Pages'te barındırılacak. `CNAME` dosyası
zaten `timetomusic.com` içeriyor — repo'yu push'layınca GitHub Pages bunu okur.

1. Bu klasörü bir GitHub reposu olarak push'la (repo public olmalı veya GitHub Pro)
2. Repo → **Settings → Pages** → Source: `main` branch, `/ (root)`
3. Aynı sayfada **Custom domain** kutusuna `timetomusic.com` yaz, kaydet
4. Aşağıdaki DNS kayıtlarını GoDaddy'de ekle (adım adım altta)
5. DNS yayıldıktan sonra (10 dk – birkaç saat) Pages sayfasında **Enforce HTTPS**'i işaretle

### GoDaddy DNS ayarları

GoDaddy → My Products → `timetomusic.com` → **DNS** → **Manage DNS**'e gir.

**Apex domain (`timetomusic.com`) için — mevcut `A` kaydını sil, şu 4 `A` kaydını ekle:**

| Tip | Ad | Değer | TTL |
|---|---|---|---|
| A | @ | 185.199.108.153 | 600 |
| A | @ | 185.199.109.153 | 600 |
| A | @ | 185.199.110.153 | 600 |
| A | @ | 185.199.111.153 | 600 |

**`www` yönlendirmesi için — mevcut `CNAME` (www) kaydını şuna güncelle:**

| Tip | Ad | Değer | TTL |
|---|---|---|---|
| CNAME | www | `erenina.github.io` | 600 |

> GoDaddy'nin varsayılan "Parked"/forwarding kayıtlarını (genelde `@` için A kaydı
> `Park` veya GoDaddy IP'sine işaret eder) sil — aksi halde site açılmaz.

## Vercel / Netlify (alternatif)
Repoyu bağlaman yeterli — framework preset "Other/Static", build komutu yok, output `.` (kök).
Bu durumda `CNAME` dosyasını sil (GitHub Pages'e özeldir) ve domain'i o platformun
panelinden ekleyip GoDaddy DNS'ini onların verdiği kayıtlara göre güncelle.

## App Store Connect'e girilecek adresler

- **Privacy Policy URL:** `https://timetomusic.com/gizlilik.html`
- **Support URL:** `https://timetomusic.com/destek.html`
- **Marketing URL (opsiyonel):** `https://timetomusic.com/`

## Güncellenecek yerler

- TestFlight linki yayın sonrası App Store linkiyle değiştirilecek
  (tüm sayfalarda `testflight.apple.com/join/SKZj7DAN` ara-değiştir)
- İletişim e-postası şu an `timetomusic@hotmail.com` — değişirse ara-değiştir

# alisadikoglu-website

Kişisel danışmanlık web sitesi — [alisadikoglu.com](https://alisadikoglu.com)

## Genel Bakış

Ali Sadıkoğlu Global Education'ın kurumsal web sitesi. Yurt dışı üniversite danışmanlığı ve STARup programı için başvuru, içerik ve iletişim altyapısını barındırır.

## Teknoloji

- **Statik HTML/CSS/JS** — framework yok, saf vanilla
- **Cloudflare Pages** — otomatik deploy (main branch push = canlı)
- **Web3Forms** — form backend (email bildirimi, her iki form için)
- **Domain** — alisadikoglu.com (Cloudflare DNS, Hover kayıt)

## Klasör Yapısı

```
/
├── index.html          # Ana sayfa (tüm section'lar dahil)
├── starup/
│   └── index.html      # STARup program sayfası + başvuru formu
├── blog/
│   ├── index.html      # Blog listesi
│   ├── 9-sinif-yurt-disi-universite/index.html
│   ├── amerika-universite-proje-onemi/index.html
│   ├── hollanda-universite-kabul-sartlari-2026/index.html
│   ├── ingiltere-universite-basvuru-sistemi/index.html
│   ├── italyada-ingilizce-universite-bocconi-politecnico/index.html
│   ├── yaz-okullari-gercekten-ise-yariyor-mu/index.html
│   ├── universite-essay-yaziminda-5-kritik-hata/index.html
│   ├── ivy-league-basvurularinda-fark-yaratan-aktiviteler/index.html
│   ├── universiteler-liderlikten-ne-anliyor/index.html
│   └── 12-sinifta-gec-kaldi-mi/index.html
└── README.md
```

## Deploy

`main` branch'e push edildiğinde Cloudflare Pages otomatik deploy eder. Ek bir işlem gerekmez.

```bash
git add .
git commit -m "değişiklik açıklaması"
git push origin main
```

## Formlar

İki adet başvuru formu var, ikisi de Web3Forms üzerinden çalışır.

| Form | Sayfa | Handler |
|------|-------|---------|
| Ön Görüşme | `index.html` → `#iletisim` | `submitForm()` |
| STARup Başvuru | `starup/index.html` → `#basvuru` | `submitSTARup()` |

Her iki form da veriyi toplayıp `api.web3forms.com/submit` endpoint'ine POST atar. Form bildirimleri Web3Forms dashboard üzerinden yönetilir.

## Dil Desteği

Site TR/EN çift dil içerir. Dil geçişi `lang-tr` / `lang-en` class'ları ile CSS display toggle ile çalışır. JS aracılığıyla `<html lang="">` attribute'u güncellenir.

## DNS

| Kayıt | Değer |
|-------|-------|
| A `@` | `76.76.21.21` (Cloudflare Pages) |
| CNAME `www` | `alisadikoglu-website.pages.dev` |
| Nameservers | `bonnie.ns.cloudflare.com`, `eric.ns.cloudflare.com` |

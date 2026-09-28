# Ödev Defteri — web sitesi

[Ödev Defteri](https://github.com/nodabasi/odev-defteri) mobil uygulamasının tanıtım
ve destek sitesi. Mağaza başvurusunun istediği **destek** ve **gizlilik politikası**
bağlantıları buradan verilir.

Statik HTML ve tek bir CSS dosyası. Derleme adımı, bağımlılık ve JavaScript yok.

## Sayfalar

| Yol | İçerik | Nerede kullanılır |
| --- | --- | --- |
| `/` | Tanıtım — uygulamanın ne yaptığı | Mağaza listesindeki pazarlama adresi |
| `/destek/` | SSS ve iletişim | App Store Connect → Destek adresi |
| `/gizlilik/` | Gizlilik politikası | App Store Connect ve Play Console → Gizlilik politikası adresi |
| `/hesap-silme/` | Hesap silme adımları | App Store Connect → Hesap silme adresi |

## Yerelde bakmak

```bash
python3 -m http.server 8000
```

Sonra `http://localhost:8000` adresini açın. Bağlantılar göreli olduğu için site hangi
alt dizine konursa konsun çalışır.

## Yayına almak

GitHub Pages: depo ayarlarında **Settings → Pages → Source** kısmını `main` dalının kök
dizinine ayarlayın. Site birkaç dakika içinde yayına girer.

## Güncellenmesi gerekenler

- **İletişim adresi.** Dört sayfada da `odabasi.developer@gmail.com` geçiyor.
- **Yürürlük tarihi.** `gizlilik/index.html` içindeki `.meta` satırı; uygulama
  yayımlandığı gün güncellenmeli.
- **Mağaza bağlantıları.** `index.html` içinde yerini gösteren bir HTML yorumu var;
  uygulama yayımlanınca indirme düğmeleri oraya eklenir.
- **Telif yılı.** Dört sayfanın alt bilgisinde.

## Site ile uygulama arasındaki bağ

Gizlilik ve hesap silme sayfaları uygulamanın bugünkü davranışını anlatır. Uygulamada
şu konular değişirse sayfaların da güncellenmesi gerekir:

- toplanan alanlar (`src/services/users.ts`, `students.ts`)
- kimin neyi görebildiği (`firestore.rules`)
- hesap silmenin kapsamı (`functions/src/account.ts`)
- verinin tutulduğu bölge (Firestore `eur3`, Functions `europe-west1`)

Uygulamadaki **Profil → Gizlilik & KVKK** ekranı henüz boş; `/gizlilik/` sayfasına
bağlanması bekleniyor.

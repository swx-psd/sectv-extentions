# DiziLife SecTV Plus Eklentisi (Dağıtım Paketi)

Bu klasör, **SecTV Plus** uygulaması için bağımsız olarak hazırlanmış ve derlenmiş **DiziLife (dizi76.life)** eklentisini barındırır.

---

## 📦 Paket İçeriği

1. **`dizilife.jar`**: Android `DexClassLoader` ile çalışan, `dizi76.life` üzerindeki trend dizileri, filmleri, bölümleri ve HLS akışlarını (`master.m3u8`) çözen eklenti motoru.
2. **`catalog.json`**: Uygulamanın eklentiyi tanıması, SHA-256 bütünlüğünü doğrulaması ve kurması için gerekli katalog dosyası.

---

## 🚀 GitHub'a Yükleme ve Kullanma Adımları

### 1. Dosyaları GitHub'a Yükleyin
1. GitHub üzerinde **Public** bir repo oluşturun (örneğin: `sectv-plugins`).
2. Bu klasördeki `dizilife.jar` ve `catalog.json` dosyalarını reponuza yükleyin (commit/push).

### 2. `catalog.json` Linkini Güncelleyin
GitHub'a yükledikten sonra `catalog.json` dosyasındaki `"downloadUrl"` kısmını kendi reponuzdaki `dizilife.jar` dosyasının **Raw (doğrudan indirme)** linki ile eşleştirin:

```json
{
    "schemaVersion": 1,
    "plugins": [
        {
            "pluginId": "com.sectv.plus.plugin.dizilife",
            "name": "DiziLife",
            "version": 1,
            "author": "SecTV",
            "description": "DiziLife dizi ve film eklentisi (dizi76.life)",
            "apiVersion": 1,
            "mainClass": "com.sectv.plus.plugin.sample.dizilife.DiziLifeExtractor",
            "siteUrl": "https://dizi76.life",
            "iconUrl": "",
            "sha256": "485287f848ad3f5dd6794c6b5e14656c7ff24369497ed2392ab61877f26435b7",
            "downloadUrl": "https://raw.githubusercontent.com/swx-psd/sectv-extentions/main/dizilife.jar"
        }
    ]
}
```

---

## ⚠️ Güncelleme Notu (FAZ 34.5 — 10.10.2026)

Bu klasördeki `dizilife.jar` **yeniden üretildi** ve eskisinden farklıdır:

| | Eski | Yeni |
|---|---|---|
| Boyut | 25.006 bayt | **9.985 bayt** |
| Sınıf sayısı | 17 (kanit + örnek + dizilife hepsi) | **5** (yalnızca dizilife) |
| SHA-256 | `946d9030…` | `485287f8…` |

**Neden:** Her jar artık yalnızca kendi eklenti paketini taşıyor ve kaynak dosya
adlarını içermiyor (bkz. `AGENTS.md` K23).

> ⛔ **`catalog.json` ve `dizilife.jar` BİRLİKTE yüklenmelidir.** SHA-256
> değiştiği için yalnız jar'ı yüklerseniz uygulama "Eklenti dosyası
> doğrulanamadı" diyerek kurulumu reddeder.

---

## 📱 SecTV Plus Uygulamasına Kurulum

1. SecTV Plus uygulamasını açın.
2. **Ayarlar → Eklentiler** ekranına gidin.
3. Katalog Kutucuğuna şu linki yapıştırın:
   ```text
   https://raw.githubusercontent.com/swx-psd/sectv-extentions/main/catalog.json
   ```
4. **"Aç"** / **"Yenile"** butonuna basın.
5. Listede **"DiziLife"** eklentisi görünecektir, **"Kur"** butonuna basın.
6. Kurulum tamamlandıktan sonra **Dizi & Film** sekmesine geçin.
7. Üstteki kaynak seçici çubuğunda **"DiziLife"** kaynağını görebilir ve içerikleri doğrudan izleyebilirsiniz!

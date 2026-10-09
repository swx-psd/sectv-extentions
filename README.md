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
            "sha256": "946d9030cf8dcf7ae0b95abf8bd6a3f535d1aee6f1692a37dd7b5241c1e01319",
            "downloadUrl": "https://raw.githubusercontent.com/<KULLANICI_ADINIZ>/<REPO_ADINIZ>/main/dizilife.jar"
        }
    ]
}
```

> **İpucu:** Gradle komutu ile kendi GitHub adresinize göre otomatik de üretebilirsiniz:
> ```powershell
> cd C:\Users\taha\Documents\SecTVPlus\Android\SecTVPlus
> .\gradlew.bat :plugin-sample:publishDiziLifeCatalog "-Pplugin.katalog.temelAdres=https://raw.githubusercontent.com/<KULLANICI>/<REPO>/main"
> ```

---

## 📱 SecTV Plus Uygulamasına Kurulum

1. SecTV Plus uygulamasını açın.
2. **Ayarlar → Eklentiler** ekranına gidin.
3. Katalog Kutucuğuna GitHub'daki `catalog.json` dosyanızın **Raw bağlantısını** yapıştırın:
   - Örnek: `https://raw.githubusercontent.com/<KULLANICI>/<REPO>/main/catalog.json`
4. **"Aç"** butonuna basın.
5. Listede **"DiziLife"** eklentisi görünecektir, **"Kur"** butonuna basın.
6. Kurulum tamamlandıktan sonra **Dizi & Film** sekmesine geçin.
7. Üstteki kaynak seçici çubuğunda **"DiziLife"** kaynağını görebilir ve içerikleri doğrudan izleyebilirsiniz!

# Yemek Tarifi Uygulaması

Java Swing tabanlı, **MySQL** veritabanı destekli bir yemek tarifi ve malzeme yönetim uygulaması. Kullanıcılar tarif ekleyebilir, malzeme stoğu tutabilir, hazır tarifleri görüntüleyebilir ve her tarifin **toplam maliyetini** otomatik olarak hesaplatabilir.

## Özellikler

- **Tarif yönetimi**: ad, kategori, hazırlama süresi, talimatlar, fotoğraf yolu
- **Malzeme stoğu**: malzeme adı, toplam miktar, birim (kg / adet vb.), birim fiyat
- **Tarif–malzeme ilişkisi**: her tarif için kullanılan malzeme ve miktar
- **Otomatik maliyet hesaplama**: tarifte kullanılan malzeme miktarları × birim fiyat üzerinden toplam maliyet (adet birimi için /10 ölçeklemesi)
- **Tarif detay ekranı**: malzeme listesi, fotoğraf, maliyet
- **Özelleştirilmiş JTable görünümü** (`CustomTableCellRenderer`)

## Teknolojiler

- **Java SE** + **Swing** (NetBeans projesi)
- **MySQL** (JDBC, `mysql-connector-j 9.0.0`)

## Veritabanı

Varsayılan bağlantı (`DbHelper.java`):

```
jdbc:mysql://localhost:3306/yemek
user: root
pass: 1234
```

### Tablolar
- `tarifler` — `tarif_id`, `tarif_adi`, `kategori`, `hazirlama_suresi`, `talimatlar`, `foto_path`
- `malzeme` — `malzeme_id`, `malzeme_adi`, `toplam_miktar`, `malzeme_birimi`, `birim_fiyat`
- `tarif_malzeme` — `tarif_id`, `malzeme_id`, `malzeme_miktar` (köprü tablo)

## Çalıştırma

1. MySQL'i kurun ve `yemek` veritabanını yukarıdaki tablolarla oluşturun
2. NetBeans'te `JavaApplication2` projesini açın
3. **mysql-connector-j** kütüphanesinin projeye eklendiğinden emin olun
4. `ana_ekran.java` üzerinden başlatın

## Ekranlar

| Sınıf | İşlev |
|-------|-------|
| `ana_ekran` | Ana menü |
| `ekleme_ekrani_2` | Yeni tarif ekleme (malzeme seçimi ile) |
| `malzeme_ekle` | Yeni malzeme ve fiyat girişi |
| `Tarif_Listesi_3` / `TarifListeleme` | Tarif listesi + arama |
| `tarif_detayi` | Tarif detay görüntüleme/güncelleme |
| `CustomTableCellRenderer` | Tablo hücresi özel görünüm |
| `DbHelper` | MySQL bağlantı sınıfı |

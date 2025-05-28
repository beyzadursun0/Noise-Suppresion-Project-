# Noise Suppression with Deep Learning

Bu proje, farklı derin öğrenme mimarilerini kullanarak ses sinyallerinden gürültüyü temizlemeye (noise suppression) odaklanmaktadır. Model girişleri zaman-frekans spektrumuna çevrilmiş ses verileri olup, çıkış olarak temizlenmiş spektrumlar üretilmektedir.

## 🔍 Amaç

Gürültülü ses sinyallerinden temiz sesin tahmin edilmesi. Bunun için çeşitli CNN tabanlı modeller kullanılmıştır:

- U-Net
- VGG-style CNN
- CNN + LSTM (CRN benzeri)
- ResNet + U-Net

---

## 📁 Proje Yapısı
project_root/
│
├── train/
│ ├── train/ -> Gürültülü eğitim sesleri (.wav)
│ └── y_train/ -> Temiz eğitim sesleri (.wav)
│
├── test/
│ ├── test/ -> Gürültülü test sesleri (.wav)
│ └── y_test/ -> Temiz test sesleri (.wav)


> Tüm ses dosyalarının `.wav` formatında ve 16 kHz örnekleme oranında olması beklenir.



## 🧠 Kullanılan Modeller

### 1. U-Net
Geleneksel encoder-decoder yapısında, düşük seviyeli özellikleri korumak için skip-connection kullanır.

### 2. VGG-style CNN
VGG tarzında ardışık konvolüsyon katmanları ve max-pooling kullanılarak ses özellikleri öğrenilir.

### 3. CNN + LSTM (CRN benzeri)
Zaman boyutunu öğrenmek için CNN + LSTM kombinasyonu kullanılır. Özellikle zamansal bağlamın önemli olduğu senaryolarda başarılıdır.

### 4. ResNet + U-Net
Residual bloklarla zenginleştirilmiş encoder, U-Net’in decoder kısmı ile birleştirilmiştir.

---

## 🛠 Eğitim Detayları

- Giriş boyutu: `(64, 64, 1)` (log-spektrum görüntüleri)
- Kayıp Fonksiyonu: `RMSE` (Karekök Ortalama Hata)
- Optimizasyon: `Adam`, öğrenme oranı = `1e-3`
- Epoch: `50`
- Batch Size: `64`

---

## 📊 Sonuçlar

Eğitim tamamlandıktan sonra her modelin `% RMSE` hatası grafik üzerinde karşılaştırılır:

- Düşük hata oranı, modelin temiz sesi daha doğru tahmin ettiğini gösterir.
- Aşağıdaki grafik çizilir:

```python
plt.title('Kayıp (Loss) Grafiği - % RMSE Hata')
plt.xlabel('Epochs')
plt.ylabel('Yüzde Hata (%)')
plt.legend()
plt.show()


## Bu proje şu anda geliştirme aşamasındadır. Eksik veya hatalı yerleri mevcut olabilir. Düzenlendikçe paylaşılacaktır.

## Lisans

Bu proje MIT lisansı ile lisanslanmıştır. Dilediğiniz gibi kullanabilir, değiştirebilir ve dağıtabilirsiniz. Ancak kaynak belirtilmelidir. Ayrıntılar için [LICENSE](LICENSE) dosyasına bakınız.


---

## ✉️ İletişim

📧 beyzadursun2002@gmail.com  
📍 GitHub: [@beyzadursun0](https://github.com/beyzadursun0)




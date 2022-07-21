---
description: Alım Satım Ödülleri programına genel bakış.
---

# Alım Satım Ödülleri

İlk token arzının (`250.000.000 DYDX`) `%25,00`'i dYdX Katman 2 Protokolü üzerinde alım satım yapan kullanıcılara, ödenen ücretlerin ve açık faizin bir kombinasyonuna dayalı olarak dağıtılacaktır.

**Hedefler**

* Tüm yatırımcıları dYdX Katman 2 Protokolünü kullanmaya teşvik etmek.
* Piyasa likiditesini ve toplamda ürün kullanımını artırmak.

## **Genel bakış**

![dYdX Katman 2 Protokolü'nde işlem yaparak ödüller kazanın](<../.gitbook/assets/image (17) (1).png>)

DYDX, dYdX Katman 2 Protokolü üzerinde ödenen ücretlerin ve açık faizin bir kombinasyonunu ödüllendiren bir formüle dayalı olarak yatırımcılara dağıtılacaktır. DYDX, beş yıl boyunca 28 günlük dönemler esasında dağıtılacak ve herhangi bir vesting veya kilitleme sürecine tabi tutulmayacaktır. Her dönemde 3.835.616 DYDX dağıtılacaktır.

Her bir dönem boyunca her yatırımcıya ne kadar DYDX verileceğini hesaplamak için Cobb-Douglas fonksiyonu kullanılır:

![](<../.gitbook/assets/math-20211221 (1).png>)

$$ r=R\times \frac{w}{\sum\limits _{n} w_{n}} \ \ ,n=1,2...k $$

| Süre | Tanım |
| ---------------------------- | ------------------------------------------------------------------------------------------ |
| r | Belirli bir yatırımcının ödülü. |
| R | Dönem için havuzdaki tüm yatırımcılar arasında bölünecek toplam ödül. |
| f | Bu dönemde bir yatırımcı tarafından ödenen toplam ücret. |
| w | Bireysel yatırımcı puanı. |
| $${\toplam\limitler _{n} w_{n}}$$ | Tüm yatırımcı puanlarının toplamı. |
| d | Bir yatırımcının bu dönemde tüm piyasalardaki ortalama açık faizi (her dakika ölçülür). |
| k | Bu dönemdeki toplam yatırımcı sayısı. |
| g | Bir yatırımcının dönem boyunca tuttuğu ortalama stkDYDX (her dakika rastgele ölçülür) |
| a | 0,80 |
| b | 0,15 |
| c | 0,05 |

[DIP-10](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-10.md)'da, dYdX Topluluğu ücret parametresini `a=0,67`'den `a=0,8`'e değiştirme ve açık pozisyon hacmi parametresini `b=0,28`'den `b=0,15`'e düşürme yönünde oy kullanmıştır.

## SSS

### Alım satım ödüllerini kimler alabilir?

dYdX Katman 2 protokolündeki tüm yatırımcılar alım satım ödülleri olarak DYDX alabilir.

dYdX Katman 2 Protokolü, dYdX Trading Inc.'in [Kullanım Şartları](https://dydx.exchange/terms)'nda tanımlandığı üzere Amerika Birleşik Devletleri ve Kısıtlanmış Bölgelerdeki yatırımcılar tarafından kullanılamaz.

### Alım Satım Ödülleri programında ne kadar DYDX kazandım?

Kullanıcılar, mevcut dönemde kullanıcıların alım satım verilerinin yer aldığı [**trade.dydx.exchange/portfolio/rewards**](https://trade.dydx.exchange/portfolio/rewards) sayfasında ödenen ücretleri, ortalama açık faizi ve tahmini alım satım ödüllerini görebilir.

![Mevcut dönem için ödüller ile ilgili bilgi](<../.gitbook/assets/image (18).png>)

Geçmiş dönemlerde alınan ödüller, [**dydx.community/history/rewards**](https://dydx.community/history/rewards) sayfasında görüntülenebilir \*\*\*\* (yakında eklenecek).

### Alım Satım Ödüllerimi nasıl alabilirim? Kazandığım DYDX'leri ne zaman çekebilir ve transfer edebilirim?

Alım Satım Ödülleri aracılığıyla kazanılan DYDX token'ları her dönemin sonunda transfer edilebilir. DYDX token sahiplerinin dönem sona erdikten sonra token'larını almak için yaklaşık `7 gün` (**Bekleme Süresi**) beklemeleri gerekir. Token'lar talep edildikten sonra dYdX yönetişimi için kullanılabilir.

Yatırımcılar her dönem sonunda, **Bekleme Süresi** sona erdikten sonra alım satım ödüllerini [buradan](https://dydx.community/dashboard) talep edebilir.

Kullanıcılar DYDX'lerini alabilmek için "Talep Et" seçeneğine tıklamalı, bir işlemi imzalamalı ve gas ücretlerini ödemelidir.

![Ödüller için portföye genel bakış](<../.gitbook/assets/image (20).png>)

### Açık Faiz nedir?

Toplam açık faiz, belirli bir piyasadaki tüm uzun veya kısa açık pozisyonların USD değeridir (uzun pozisyonların toplam birimi her zaman kısa pozisyonların toplam birimine eşittir) Açık faizin artması piyasaya yeni veya ek para geldiğini, düşmesi ise piyasadan para çıktığını gösterir.

Aşağıdaki tabloda yatırımcılar A, B, C, D ve E'nin alım satım faaliyetleri gösterilmektedir. Her günün alım satım faaliyetlerini takiben açık faiz USDC cinsinden hesaplanmaktadır:

| Zaman | Alım Satım Etkinliği | Toplam Net Açık Faiz (USDC) |
| ------- | -------------------------------------------------------------------------- | ------------------------------ |
| 1 Temmuz | **A Yatırımcısı** 30.000 $ fiyatla 1 BTC alıyor ve **B Yatırımcısı** 30.000 $ fiyatla 1 BTC satıyor | 30.000 $ |
| 3 Temmuz | **C Yatırımcısı** 30.000 $ fiyatla 5 BTC alıyor ve **D Yatırımcısı** 30.000 $ fiyatla 5 BTC satıyor | 180.000 $ |
| 5 Temmuz | **A Yatırımcısı** 30.000 $ fiyatla 1 BTC satıyor ve **D Yatırımcısı** 30.000 $ fiyatla 1 BTC alıyor | 150.000 $ |
| 10 Temmuz | **E Yatırımcısı** 30.000 $ fiyatla 5 BTC alıyor ve **C Yatırımcısı** 30.000 $ fiyatla 5 BTC satıyor | 150.000 $ |

**Alım Satım Ödülleri** formülü bağlamında, ödülleri hesaplamak için açık faiz tüm piyasalarda her dakika (her dakika içinde rastgele bir zamanda) ölçülür ve söz konusu dönemdeki ortalaması alınır.

Bir yatırımcının kendi açık faizi, o yatırımcının tüm açık pozisyonlarının USD değeridir. **Alım Satım Ödüllerinin** amaçları doğrultusunda, bir yatırımcının açık faizi tüm piyasalarda her dakika (her dakika içinde rastgele bir zamanda) ölçülür ve söz konusu dönemdeki ortalaması alınır.

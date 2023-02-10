---
description: Likidite Sağlayıcı Ödülleri Programına genel bakış.
---

# Likidite Sağlayıcı Ödülleri

İlk token arzının %7,5'i (`75.000.000 $DYDX`) piyasa yapıcı hacmi (maker volume), çalışma süresi (uptime), iki taraflı derinlik (two-sided depth), alış satış farkları (bid-ask spreads) ve desteklenen piyasaların sayısı parametrelerinden oluşan bir kombinasyonu ödüllendirecek şekilde belirlenen formüllere göre likidite sağlayıcılara dağıtılacaktır.

**Hedefler**

* İki taraflı likiditeyi iyileştirmek ve programlı bir şekilde likidite sağlayıcıları ödüllendirmek.

## **Genel bakış**

Piyasa likiditesini teşvik etmek amacıyla, likidite sağlayıcılara piyasalara katılımı, piyasa yapıcı hacmini, iki taraflı derinliği, (orta piyasaya kıyasla) fiyat farkını (spread) ve dYdX Katman 2 Protokolü üzerinde çalışma süresini (uptime) ödüllendiren formüllere göre $DYDX dağıtılacaktır. Herhangi bir Ethereum adresi bu ödülleri kazanabilir ve önceki dönemdeki piyasa yapıcı hacminin %0,25'i kadar bir minimum piyasa yapıcı eşiğine tabidir. $DYDX beş yıl boyunca 28 günlük dönemler bazında dağıtılacak ve herhangi bir hakediş (vesting) veya kilitleme sürecine tabi tutulmayacaktır. Dönem başına 1.150.685 $DYDX dağıtılacaktır.

Her bir likidite sağlayıcıya dönem başına ne kadar $DYDX'in ödül olarak verileceğini hesaplamak için aşağıdaki fonksiyonlar kullanılır. [DIP 15](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-15.md)'te, dYdX topluluğu Likidite Sağlayıcı (LP) ödülleri formülünün, fonksiyonların BTC/ETH piyasaları ve BTC/EHT dışı piyasalar olarak ikiye ayrılması suretiyle revize edilmesi yönünde oy kullandı. [DIP 19](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-19.md)'da, dYdX topluluğu, MakerVolume'a 0,05 $stkDYDX ağırlığının tekrar tahsis edilmesi yönünde oy kullandı.

Genel olarak, fonksiyonlarda hacmin ağırlığı tüm piyasalarda arttırıldı. Kazanılan $DYDX miktarı her bir katılımcının $$Q_{FINAL}$$ ($$Q_{BTC}$$+​$$Q_{ETH}$$+$$Q_{non BTC/ETH}$$​) miktarındaki payına göre belirlenir.

<figure><img src="../.gitbook/assets/Updated LP Rewards Formulas.png" alt=""><figcaption></figcaption></figure>

Piyasa başına belirli bir **minimum derinliğin** (boyut) ($$MinDepth$$) altındaki emirler hariç tutulur ve piyasa başına belirli bir **maksimum teklif-talep farkı** (orta piyasa teklif-talep farkı) ($$MaxSpread$$) üzerindeki emirler de hariç tutulur.

Likidite sağlayıcı performansı belli bir piyasa için dakika dakika izlenerek hesaplanır (rastgele örnekleme kullanılarak) ve bir $$Q_{SCORE}$$ içine toplaştırılır. Dakika dakika örnekleme söz konusu olduğunda, her dönemde 28 günlük \* 24 saatlik \* 60 dakikalık veri noktaları bulunur ve her dönemde toplam 40.320 veri noktası bulunur.

Likidite sağlayıcılar dönem başına göreli $ $ Q_{FINAL}$ paylarına dayalı olarak aylık ödüller kazanır.

Yukarıdaki formül ayrıntılı bilgi için aşağıda adım adım hesaplamalara bölünmüştür:

| _Piyasa Yapıcı Hacmi_ | Dönem için toplam piyasa yapıcı hacmi. |
| --------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <img src="../.gitbook/assets/1-qbid-formula.png" alt="" data-size="original"> | <p></p>Bir likidite sağlayıcının BTC-USD emir defterinde birden fazla açık teklif emri (29.900 $ fiyatla 1 BTC, 29.850 $ fiyatla 5 BTC, 29.500 $ fiyatla 10 BTC) olduğunu ve güncel BTC fiyatının ise 30.000 ${orta piyasaya dayalı olarak) olduğunu varsayalım. MinDepth'in 5.000 $ ve orta piyasada MaxSpread'in 200 $ veya 67 Baz Puanı (200/30.000 $) olduğunu varsayalım. Bir BP, yüzde birin yüzde biridir.<br><p></p><span class="math">Q_{BID} = (1\ \times \left(\frac{$29,900}{$100/30000}\right)) + (5\ \times \left(\frac{$29,850}{$150/30000}\right))</span><p></p><br><span class="math">Q_{BID}</span> rastgele örnekleme kullanılarak her dakika hesaplanır.<br> |
| <img src="../.gitbook/assets/1-qask-formula.png" alt="" data-size="original"> | <p></p>Bir likidite sağlayıcının BTC-USD emir defterinde birden fazla açık teklif emri (30.100 $ fiyatla 0,1 BTC, 30.150 $ fiyatla 5 BTC, 30.175 $ fiyatla 10 BTC) olduğunu ve BTC'nin şu anda 30.000 $ fiyatla (orta piyasaya dayalı olarak) işlem gördüğünü varsayalım. MinDepth'in 5.000 $ ve orta piyasada MaxSpread'in 200 $ veya 67 Baz Puanı (200/30.000 $) olduğunu varsayalım. Bir BP, yüzde birin yüzde biridir.<p></p><span class="math">Q_{ASK} = (5\ \times \left(\frac{$30,150}{$150/30000}\right)) + (10\ \times \left(\frac{$30,175}{$175/30000}\right))</span><p></p><br><span class="math">Q_{ASK}</span> her dakika rastgele bir aralıkla hesaplanır. |
| <img src="../.gitbook/assets/1-qmin-formula.png" alt="" data-size="original"> | <p></p><span class="math">Q_{BID}</span> ve <span class="math">Q_{ASK}</span>'in minimumunu alarak 2 taraflı likiditeyi ödüllendirir.<br><p></p>Her dakika hesaplanır. |
| <img src="../.gitbook/assets/1-qpoech-formula.png" alt="" data-size="original"> | $$Q_{EPOCH}$$, belirli bir dönemdeki tüm $$Q_{MIN}$$ değerlerinin toplamıdır. |
| <img src="../.gitbook/assets/1-q-uptime-epoch-formula.png" alt="" data-size="original"> | $Uptime_{EPOCH}$$, belli bir piyasa yapıcının faal olduğu ve hem alış, hem satış tarafında belirtilen minimum talimattan büyük talimat boyutlarıyla (aşağıda piyasa bazında belirtilmiştir) ve maksimum alış satış farkından daha küçük farklarla (aşağıda piyasa bazında belirtilmiştir) teklif verdiği, bir dönem içerisindeki zamandır. |
| <img src="../.gitbook/assets/1-qfinal-epoch-formula.png" alt="" data-size="original"> | $$Q_{FINAL}$$, çalışma süresini hesaplamak için $$Q_{EPOCH}$$'u normalleştirir |

Her piyasa, farklı bir ağırlık verilecek kendi ödül havuzuna sahip olacaktır. [DIP 15](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-15.md)'te dYdX topluluğu, BTC-USD ve ETH-USDC toplam ödüllerinin tahsisinin her birinin %10'a düşürülmesi yönünde oy kullandı. Her bir piyasaya uygulanan ağırlıklar seti aşağıdaki gibidir:

| Piyasa | Toplam Ödül Havuzu Tahsis %'si |
| ----------------------- | ---------------------------------------------------------------- |
| BTC-USD | %10 |
| ETH-USD | %10 |
| Diğer sürekli varlık piyasaları | ![](../.gitbook/assets/1-other-perpetual-markets-lp-weights.png) |

## SSS

### Likidite sağlayıcı ödüllerini kimler alabilir?

Önceki dönemde dYdX Katman 2 Protokolü üzerindeki piyasa yapıcı hacminin en az %0,25 kadarına ulaşan tüm likidite sağlayıcıları söz konusu dönemde $DYDX ödüllerini almaya hak kazanır.

dYdX Katman 2 Protokolü, dYdX Trading Inc.'in [Kullanım Şartları](https://dydx.exchange/terms)'nda tanımlandığı üzere Amerika Birleşik Devletleri ve Kısıtlanmış Bölgelerdeki likidite sağlayıcılar tarafından kullanılamaz.

### Likidite Sağlayıcı Ödülleri programında ne kadar $DYDX kazandım?

Belirli bir dönemde, likidite sağlayıcıları belirli bir işlem çifti piyasasındaki göreli $$Q_{SCORE}$$ değerlerine dayalı olarak getiri kazanır. Her bir işlem çifti, yönetişim tarafından belirlenen kendi göreli ödül miktarına sahiptir. Beklenen kazanılmış DYDX miktarı [LP Ödülleri Panosu](https://p.datadoghq.com/sb/dc160ddf0-b32271920202875868dc46be6b66cf87?tpl\_var\_Market=btc\&from\_ts=1661805073576\&to\_ts=1661891473576\&live=true) üzerinde görüntülenir ve ilgili likidite sağlayıcıların sayısına, göreceli $$Q_{SCORE}$$ düzeyine ve söz konusu çift için geçerli uygun ödül miktarına göre belirlenebilir.

### Likidite Sağlayıcı Ödüllerimi nasıl alabilirim?

Likidite Sağlayıcı Ödülleri [dYdX API](https://docs.dydx.exchange/)'sinde açıklanır. Her ne kadar yönetişim kullanıcı arayüzünde açıklanmasa da her dönemin [sonunda](https://dydx.community/dashboard) yine de yönetişim yoluyla buradan alınabilirler.

### Aldığım $DYDX Likidite Sağlayıcı Ödüllerimi ne zaman çekebilir ve transfer edebilirim?

Likidite Sağlayıcı Ödülleri aracılığıyla ödül olarak verilen $DYDX token'ları ilk baştaki transfer kısıtlama süresi kaldırıldığında alınabilir ve transfer edilebilir.

1. Dönemden başlayarak, Likidite Sağlayıcı Ödülleri aracılığıyla ödül olarak verilen $DYDX token'ları, her dönem sona erdikten `7 gün` (**Bekleme Süresi**) sonra alınabilir.

### İki taraflı derinlik, teklif-talep farkı ve çalışma süresi nasıl tanımlanıyor ve ölçülüyor?

**İki taraflı derinlik**

İki taraflı likidite sağlayıcısı, dYdX Katman 2 Protokolü üzerindeki iki taraflı piyasalarda aktif olarak teklif veren ve söz konusu piyasada teklif ve talep sağlayan bir firma veya bireydir. Protokole genel anlamda likidite sağlar.

Örneğin, BTC-USD piyasasındaki bir likidite sağlayıcı, 30.000 $-30.100 $, 10x50 şeklinde bir teklif verebilir. Bu da 30.000 $ fiyatla 10 BTC için teklif verdiği (satın alacağı) ve ayrıca 50 BTC için 30.100 $ fiyat talep ettiği (satacağı) anlamına gelir. Bunun ardından diğer piyasa katılımcıları likidite sağlayıcıdan 30.100 $ fiyatla satın alabilir (teklifi kaldırabilir) veya likidite sağlayıcıya 30.000 $ fiyatla satabilir (talebi karşılayabilir).

Likidite sağlayıcılar, belirli bir piyasadaki hem teklifleri hem de talepleri sağlama yetenekleri üzerinden değerlendirilir. Sadece tek bir tarafta (sadece teklif ya da sadece talep) teklif veren likidite sağlayıcılar, min() fonksiyonu nedeniyle ödül alamaz.

**Orta piyasada makas farkı**

Yaygın bir likidite ölçüsü de teklif-talep farkıdır. Bu, bir piyasadaki en yüksek teklif (satın alma emri) fiyatı ile en düşük talep (satış emri) fiyatı arasındaki farktır. Teklif ve talep arasındaki fark, yani makas farkı, alım satımda ana işlem maliyetidir (komisyonlar dışında) ve emirleri talep ve talep fiyatları üzerinden işleyerek likidite sağlayıcı tarafından alınır. Makas farkı, bir kullanıcının anında işlem yapma maliyetini ölçer.

Orta piyasadaki teklif-talep farkı özellikle piyasanın orta noktasını alır. Bu formül ile her bir piyasadaki MinDepth miktarının altındaki emirler de hariç tutulur.

Örneğin, bir likidite sağlayıcının BTC-USD için teklif fiyatı 30.000 $ ve talep fiyatı da 30.100 $ ise, teklif-talep farkı 100 $ olur. Orta piyasa fiyatı 30.050 $ ve orta piyasa makas farkı da 50 $'dır.

**Çalışma süresi**

Likidite sağlayıcı çalışma süresi özellikle yüksek oynaklık dönemlerinde piyasalar için çok önemlidir. $$Q_{FINAL}$$ hesaplamasında bir girdi olarak $$Uptime_{epoch}$$ değerinin beşinci kuvvetini kullanarak ödüller sürekli olarak 2 taraflı likiditeyi sürdüren likidite sağlayıcılara verilir. Diğer bir deyişle, %99'luk bir çalışma süresine sahip bir likidite sağlayıcı %90'lık bir çalışma süresine sahip bir likidite sağlayıcıdan daha değerlidir.

Çalışma süresi, belirli bir piyasadaki likidite sağlayan emirlerin dakika dakika (rastgeleleştirilmiş örnekleme ile) var olduğu zaman yüzdesi şeklinde tanımlanır. Çalışma süresinde, dYdX Katman 2 Protokolü üzerinde kesinti yaşanan süreler hariç tutulur. Borsanın yavaş olduğu veya emirleri kabul etmediği (ancak bir kesinti yaşanmayan) bazı aşırı durumlar görülebilir ve bu durumda yukarıdakiler geçerli olmaz (ancak bu bir hata olarak kabul edilir ve tüm likidite sağlayıcılar tıpkı kesintilerde olduğu gibi benzer şekilde etkilenir).

### Bir piyasadaki maksimum teklif-talep farkı nasıl tanımlanır?

Bir piyasadaki makas farkı $$MaxSpread$$ değerinden yüksek olduğunda hiçbir $$Q_{BID}$$ ve $$Q_{ASK}$$ değeri üretilmez.

İlk baştaki Maksimum Teklif-Talep Farkı değerleri aşağıdaki gibidir:

| Piyasa | Orta Piyasadaki Maksimum Makas Farkı (Teklif ve Talep) |
| ----------------------- | -------------------------------------- |
| BTC-USD | 20 bps |
| ETH-USD | 20 bps |
| Diğer sürekli varlık piyasaları | 40 bps |

### Bir piyasadaki minimum derinlik (boyut) nasıl tanımlanır?

Bir piyasadaki büyüklük $$MinDepth$$ değerinin altında olduğunda hiçbir $$Q_{BID}$$ veya $Q_{ASK}$$$ değeri üretilmez.

İlk baştaki Minimum Derinlik değerleri aşağıdaki gibidir:

| **Piyasa** | **Minimum Derinlik (Teklif ve Talep)** |
| ----------------------- | --------------------------- |
| BTC-USD | 5.000 $ |
| ETH-USD | 5.000 $ |
| Diğer sürekli varlık piyasaları | 1.000 $ |

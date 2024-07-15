---
description: Likidite Sağlayıcı Ödülleri Programına genel bakış.
---

#

Başlangıçta, token arzının **%7,5** (`75.000.000 $ethDYDX`) tutarındaki kısmı, LS ödülleri için tahsis edilmişti.

* [DIP 24](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md)'te dYdX topluluğu, Likidite Sağlayıcı Ödüllerini dönem başına `1.150.685 $ethDYDX`'ten dönem başına `575.343 $ethDYDX`'e %50 oranında azaltma yönünde [oy kullandı](https://dydx.community/dashboard/proposal/14). Sonuç olarak, LP ödülleri için ayrılan miktar `%7,5’tan` `%5,2'ye` düşmüştür.
*   [DIP 29](https://dydx.community/dashboard/proposal/16)'da dYdX topluluğu LP ödüllerini dYdX v3'teki 30.-32. Dönemdekinden ⅓ oranında azaltarak aşağıdaki değerlere düşürme yönünde [oy kullandı](https://dydx.community/dashboard/proposal/16):

    * Dönem 30: 383.562 $ethDYDX
    * Dönem 31: 191.781 $ethDYDX
    * Dönem 32: 0 $ethDYDX

    31. Dönem sonrasında dYdX v3 üzerinde herhangi bir LP ödülü olmayacaktır. Sonuç olarak, LP ödülleri için ayrılan miktar `%5,2’den` `%3,2'ye` düşmüştür.

dYdX Zinciri üzerinde Likidite Sağlayıcı ödüllerinin dağıtımı olmadığı için, dYdX topluluğu DIP 29'da Likidite Sağlayıcı ödülleri için kalan tahsisin dYdX Zinciri Topluluk Hazinesi'ne taşınması yönünde oy kullandı.

**Hedefler**

* İki taraflı likiditeyi iyileştirmek ve programlı bir şekilde likidite sağlayıcıları ödüllendirmek.

## **Genel bakış**

Piyasa likiditesini teşvik etmek amacıyla, piyasalara katılımı, piyasa yapıcı hacmini, iki taraflı derinliği, (orta piyasaya kıyasla) fiyat farkını ve dYdX v3 üzerinde çalışma süresini ödüllendiren formüllere göre likidite sağlayıcılara $ethDYDX dağıtılacaktır.

[DIP 15](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-15.md)'te, dYdX topluluğu Likidite Sağlayıcı (LP) ödülleri formülünün, fonksiyonların BTC/ETH piyasaları ve BTC/EHT dışı piyasalar olarak ikiye ayrılması suretiyle revize edilmesi yönünde oy kullandı. [DIP 19](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-19.md)'da dYdX topluluğu, 0.05 stkDYDX ağırlığının tekrar MakerVolume'a tahsis edilmesi yönünde oy kullandı.

Kazanılan ethDYDX miktarı, her bir katılımcının $$Q_{FINAL}$$ ($$Q_{BTC}$$+​$$Q_{ETH}$$+$$Q_{non BTC/ETH}$$​) miktarındaki göreceli payıyla belirlenir.

<figure><img src="../.gitbook/assets/Updated LP Rewards Formulas.png" alt=""><figcaption></figcaption></figure>

Piyasa başına belirli bir **minimum derinliğin** (boyut) ($$MinDepth$$) altındaki emirler hariç tutulur ve piyasa başına belirli bir **maksimum teklif-talep farkı** (orta piyasa teklif-talep farkı) ($$MaxSpread$$) üzerindeki emirler de hariç tutulur.

Dakika dakika örnekleme söz konusu olduğunda, her dönemde 28 günlük \* 24 saatlik \* 60 dakikalık veri noktaları bulunur ve her dönemde toplam 40.320 veri noktası bulunur.

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

<details>

<summary>Likidite sağlayıcı ödüllerini kimler alabilir?</summary>

Önceki dönemde dYdX v3 üzerindeki piyasa yapıcı hacminin en az %0,25 kadarına ulaşan tüm likidite sağlayıcıları, söz konusu dönemde ethDYDX ödüllerini almaya hak kazanır.

dYdX Trading Inc.'in [Kullanım Şartlarında](https://dydx.exchange/terms) belirtildiği üzere, dYdX v3, Birleşik Devletler'deki veya Kısıtlı Bölgeler'deki likidite sağlayıcıları tarafından kullanılamaz.

</details>

<details>

<summary>Likidite Sağlayıcı Ödülleri programında ne kadar $ethDYDX kazandım?</summary>

Belirli bir dönemde, likidite sağlayıcıları belirli bir işlem çifti piyasasındaki göreli $$Q_{SCORE}$$ değerlerine dayalı olarak getiri kazanır. Her bir işlem çifti, yönetişim tarafından belirlenen kendi göreli ödül miktarına sahiptir. Kazanılması beklenen ethDYDX miktarı [LS Ödülleri Panosu](https://p.datadoghq.com/sb/dc160ddf0-b32271920202875868dc46be6b66cf87?tpl\_var\_Market=btc\&from\_ts=1661805073576\&to\_ts=1661891473576\&live=true) üzerinde görüntülenir ve ilgili likidite sağlayıcıların sayısına, göreceli $$Q_{SCORE}$$ düzeyine ve belirli bir çift için alınabilecek ödül miktarına göre belirlenebilir.

</details>

<details>

<summary>Likidite Sağlayıcı Ödüllerimi nasıl alabilirim?</summary>

Likidite Sağlayıcı Ödülleri [dYdX API](https://docs.dydx.exchange/)'sinde açıklanır. Her ne kadar yönetişim kullanıcı arayüzünde açıklanmasa da her dönemin [sonunda](https://dydx.community/dashboard) yine de yönetişim yoluyla buradan alınabilirler.

</details>

<details>

<summary>Aldığım $ethDYDX Likidite Sağlayıcı Ödüllerimi ne zaman çekebilir ve transfer edebilirim?</summary>

Likidite Sağlayıcı Ödülleri aracılığıyla ödül olarak verilen $ethDYDX token'ları ilk baştaki transfer kısıtlama süresi geçtikten sonra teslim alınabilir ve transfer edilebilir.

1. Dönemden başlayarak, Likidite Sağlayıcı Ödülleri aracılığıyla ödül olarak verilen $ethDYDX token'ları, her dönem sona erdikten `7 gün` (**Bekleme Süresi**) sonra teslim alınabilir.

</details>

<details>

<summary>İki taraflı derinlik, teklif-talep farkı ve çalışma süresi nasıl tanımlanıyor ve ölçülüyor?</summary>

* **İki taraflı derinlik**



* **Orta piyasada makas farkı**



* **Çalışma süresi**

Likidite sağlayıcı çalışma süresi özellikle yüksek oynaklık dönemlerinde piyasalar için çok önemlidir. $$Q_{FINAL}$$ hesaplamasında bir girdi olarak $$Uptime_{epoch}$$ değerinin beşinci kuvvetini kullanarak ödüller sürekli olarak 2 taraflı likiditeyi sürdüren likidite sağlayıcılara verilir. Diğer bir deyişle, %99'luk bir çalışma süresine sahip bir likidite sağlayıcı %90'lık bir çalışma süresine sahip bir likidite sağlayıcıdan daha değerlidir.



</details>

<details>

<summary>Bir piyasadaki maksimum teklif-talep farkı nasıl tanımlanır?</summary>

Bir piyasadaki makas farkı $$MaxSpread$$ değerinden yüksek olduğunda hiçbir $$Q_{BID}$$ ve $$Q_{ASK}$$ değeri üretilmez.

İlk baştaki Maksimum Teklif-Talep Farkı değerleri aşağıdaki gibidir:

*
*
*

</details>

<details>

<summary>Bir piyasadaki minimum derinlik (boyut) nasıl tanımlanır?</summary>

Bir piyasadaki büyüklük $$MinDepth$$ değerinin altında olduğunda hiçbir $$Q_{BID}$$ veya $Q_{ASK}$$$ değeri üretilmez.

İlk baştaki Minimum Derinlik değerleri aşağıdaki gibidir:

*
*
*

</details>


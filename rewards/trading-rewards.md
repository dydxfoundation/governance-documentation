---
description: Alım Satım Ödülleri programına genel bakış.
---

# Alım Satım Ödülleri

Token arzının %`20,2'si` (`201.883.560 $ethDYDX`), dYdX v3 üzerinde işlem yapan kullanıcılara, ödenen ücretler baz alınarak dağıtılmak üzere tahsis edilir. **``**Başlangıçta, token arzının `%25'i` (`250.000.000 $ethDYDX`) trading ödülleri için ayrılmıştı.

* [DIP 16](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-16.md)'da, dYdX topluluğu trading ödüllerinin %25,0 oranında azaltılması yönünde [oy kullanmıştır](https://dydx.community/dashboard/proposal/8). Sonuç olarak, trading ödülleri için ayrılan miktar `%25,0`'ten `%20,2`'ye düşmüştür.
* [DIP 20](https://dydx.community/dashboard/proposal/11)'de, dYdX topluluğu, trading ödüllerinin %45,0 oranında daha azaltılması yönünde [oy kullanmıştır](https://dydx.community/dashboard/proposal/11). Sonuç olarak, trading ödülleri için ayrılan miktar `%20,2’den` `%14,5'e` düşmüştür.
*   [DIP 29](https://dydx.community/dashboard/proposal/16)'da dYdX topluluğu alım satım ödüllerini dYdX v3'teki 30.-32. Dönemdekinden ⅓ oranında azaltarak aşağıdaki değerlere düşürme yönünde [oy kullandı](https://dydx.community/dashboard/proposal/16):

    * Dönem 30: 1.054.795 $ethDYDX
    * Dönem 31: 527.398 $ethDYDX
    * Dönem 32: 0 $ethDYDX

    Not olarak, DIP 29'da dYdX topluluğu kalan Alım Satım Ödülleri tahsisini dYdX Zinciri üzerine Alım Satım Ödülleri için taşıma yönünde oy kullandı.

Belirlenen dönemlerde dağıtılan alım satım ödülleri 3.835.616 miktarından şu şekilde düşürülmüştür/düşürülecektir:

* Dönem 15'te 2.876.712 $ethDYDX,
* Dönem 21'de 1.582.192 $ethDYDX,
* Dönem 30'da 1.054.795 $ethDYDX,
* Dönem 31'de 527.398 $ethDYDX,
* Dönem 32 ve devamında 0 $ethDYDX.

Dönem 31'den sonra, dYdX v3 üzerinde herhangi bir alım satım ödülü olmayacaktır. dYdX v3 [Ödül Hazinesi Vester](https://etherscan.io/address/0xb9431e19b29b952d9358025f680077c3fd37292f)'i üzerinde kalan miktar, dYdX Zinciri Ödül Hazinesi Vester'ine (`dydx1wxje320an3karyc6mjw4zghs300dmrjkwn7xtk`) yatırılabilir ve daha sonra dYdX Zinciri üzerindeki yönetişim onayına tabi olarak dYdX Zinciri üzerinde alım satım ödülleri olarak dağıtılabilir.

**Hedefler**

* Tüm yatırımcıları dYdX v3 kullanmaya teşvik etmek.
* Piyasa likiditesini ve toplamda ürün kullanımını artırmak.

## **Genel bakış**

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Belirli bir dönemde ödenen ücretler ve tahmini ödüller</p></figcaption></figure>

$ethDYDX miktarı dYdX v3'te ödenen ücretler temel alınarak yatırımcılara dağıtılacaktır. $ethDYDX, beş yıl boyunca 28 günlük dönemler esas alınarak dağıtılacak ve herhangi bir hakediş veya kilitleme sürecine tabi olmayacaktır.

[DIP 29](https://dydx.community/dashboard/proposal/16)'da dYdX topluluğu alım satım ödüllerini dYdX v3'teki 30.-32. Dönemdekinden ⅓ oranında azaltarak aşağıdaki değerlere düşürme yönünde [oy kullandı](https://dydx.community/dashboard/proposal/16):

* Dönem 30: 1.054.795 $ethDYDX
* Dönem 31: 527.398 $ethDYDX
* Dönem 32 ve kalan tüm dönemler: 0 $ethDYDX



<figure><img src="../.gitbook/assets/1-trading-rewards-formula-new.png" alt=""><figcaption></figcaption></figure>

$$ r=R\times \frac{w}{\sum\limits _{n} w_{n}} \ \, n=1,2...k $$

| Süre | Tanım |
| ---------------------------- | ----------------------------------------------------------------------- |
| r | Belirli bir yatırımcının ödülü. |
| R | Dönem için havuzdaki tüm yatırımcılar arasında bölünecek toplam ödül. |
| f | Bu dönemde bir yatırımcı tarafından ödenen toplam ücret. |
| w | Bireysel yatırımcı puanı. |
| $${\sum\limits _{n} w_{n}}$$ | Tüm yatırımcı puanlarının toplamı. |
| k | Bu dönemdeki toplam yatırımcı sayısı. |

[DIP-13](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-13.md)'te, dYdX Topluluğu formülün belirli bir dönemde yatırımcı tarafından ödenen toplam ücretlere dayalı olacak şekilde basitleştirilmesi yönünde oy kullandı.

## SSS

### Alım satım ödüllerini kimler alabilir?

dYdX v3 üzerindeki tüm yatırımcılar, alım satım (trading) ödülü olarak $ethDYDX alma hakkına sahiptir.

dYdX Trading Inc.'in [Kullanım Şartlarında](https://dydx.exchange/terms) belirtildiği üzere, dYdX v3, Birleşik Devletler'deki veya Kısıtlı Bölgeler'deki yatırımcılar tarafından kullanılamaz.

### Trading Ödülleri programında ne kadar $ethDYDX kazandım?

Mevcut dönemde kullanıcılar, kullanıcıların işlem verilerinin bulunduğu [**trade.dydx.exchange/portfolio/readers**](https://trade.dydx.exchange/portfolio/rewards) adresi üzerinde ödenen ücretleri ve tahmini yatırım ödüllerini görebilirler.

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Belirli bir dönemde ödenen ücretler ve tahmini ödüller</p></figcaption></figure>

Geçmiş dönemlerdeki ödüller [**dydx.community/history/reward**](https://dydx.community/history/rewards) adresinde görüntülenebilir**.**

### Alım Satım Ödüllerimi nasıl alabilirim? Kazandığım ethDYDX'leri ne zaman çekebilir ve transfer edebilirim?

Alım Satım Ödülleri aracılığıyla kazanılan $ethDYDX token'ları her dönemin sonunda devredilebilir olacaktır. $ethDYDX token sahiplerinin $ethDYDX token'larını talep etmek için dönemin sona ermesinden sonra yaklaşık `7 gün` (**Bekleme Süresi**) beklemeleri gerekir.

7 günlük bekleme süresi sonunda, herhangi bir topluluk üyesi $ethDYDX ödüllerini talep edilebilir hale getirmek için [Merkle Distributor sözleşmesindeki](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) `updateRoot` parametresinde `Write` işlevini çağırabilir.

Adımlar:

1. Etherscan'deki [Merkle Distributor sözleşme](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) sayfasında, `Contract` sekmesine tıklayın ve `Write as Proxy` tercihini seçin.
2. `Connect to Web3` düğmesine tıklayın ve Web3 Cüzdanınızı bağlayın.

<figure><img src="../.gitbook/assets/merkle-distributor-contract.jpeg" alt=""><figcaption></figcaption></figure>

3\. `updateRoot` parametresi için aşağı kaydırın ve `Write` düğmesine tıklayın.

<figure><img src="../.gitbook/assets/updateRoot-claiming.jpeg" alt=""><figcaption></figcaption></figure>

**Bu işlem gaz ücreti olarak bir miktar ETH gerektirecektir ve işlem şu durumlarda başarısız olacaktır:**

* 7 günlük bekleme süresi hala tamamlanmamıştır veya
* Bir topluluk üyesi [Merkle Distributor sözleşmesindeki](https://etherscan.io/address/0x01d3348601968ab85b4bb028979006eac235a588#writeProxyContract) `updateRoot` parametresini zaten başarıyla çağırmıştır.

İşlem tamamlandıktan sonra, yatırımcılar Alım Satım Ödüllerini [buradan](https://dydx.community/dashboard) talep edebilirler. Kullanıcıların $ethDYDX talep etmek için `Claim` (Talep Et) üzerine tıklaması, bir işlem imzalaması ve gas ücretlerini ödemesi gerekir.

![Ödüller için portföye genel bakış](../.gitbook/assets/1-portfolio-overview-rewards.png)

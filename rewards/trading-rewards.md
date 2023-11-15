---
description: Alım Satım Ödülleri programına genel bakış.
---

# Alım Satım Ödülleri

Token arzının %`20,2'si` (`201.883.560 $ethDYDX`), dYdX v3 üzerinde işlem yapan kullanıcılara, ödenen ücretler baz alınarak dağıtılmak üzere tahsis edilir. **``**Başlangıçta, token arzının `%25'i` (`250.000.000 $ethDYDX`) trading ödülleri için ayrılmıştı.

* [DIP 16](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-16.md)'da, dYdX topluluğu trading ödüllerinin %25,0 oranında azaltılması yönünde [oy kullanmıştır](https://dydx.community/dashboard/proposal/8). Sonuç olarak, trading ödülleri için ayrılan miktar `%25,0`'ten `%20,2`'ye düşmüştür.
* [DIP20](https://dydx.community/dashboard/proposal/11)'de, dYdX topluluğu, trading ödüllerinin %45,0 oranında daha azaltılması yönünde [oy kullanmıştır](https://dydx.community/dashboard/proposal/11). Sonuç olarak, trading ödülleri için ayrılan miktar `%20,2’den` `%14,5'e` düşmüştür.

Belirli bir dönemde dağıtılan alım satım ödülleri, Dönem 15'te 3.835.616 $ethDYDX'ten 2.876.712 $ethDYDX'e ve Dönem 21'de 2.876.712 $ethDYDX'ten 1.582.192 $ethDYDX'e düşürülmüştür.

**Hedefler**

* Tüm yatırımcıları dYdX v3 kullanmaya teşvik etmek.
* Piyasa likiditesini ve toplamda ürün kullanımını artırmak.

## **Genel bakış**

<figure><img src="../.gitbook/assets/1-fees-paid-estimated-rewards.png" alt=""><figcaption><p>Belirli bir dönemde ödenen ücretler ve tahmini ödüller</p></figcaption></figure>

$ethDYDX, dYdX v3 üzerinde ödenen ücretler temel alınarak yatırımcılara dağıtılacaktır.  $ethDYDX beş yıl boyunca 28 günlük dönemler bazında dağıtılacak ve herhangi bir hakediş (vesting) veya kilitleme sürecine tabi tutulmayacaktır. Dönem başına 1.582.192 ethDYDX dağıtılacaktır.

Topluluğun [DIP16](https://dydx.community/dashboard/proposal/8)'da trading ödüllerinin %25 azalmayla 958.904 $ethDYDX‘e ve daha sonra [DIP20](https://dydx.community/dashboard/proposal/11)’de %45 oranında azalmayla 1.294,520 $ethDYDX‘e inmesini onaylamasıyla, Ödül Hazinesi'ne tahakkuk eden 2.253.424 $ethDYDX, dYdX topluluğu tarafından [yönetişim oylaması](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters) ile kullanılabilecektir/yönetebilecektir.

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

Alım Satım (Trading) Ödülleri aracılığıyla kazanılan $ethDYDX token'ları her dönemin sonunda transfer edilebilir.  $ethDYDX token sahiplerinin dönem sona erdikten sonra $ethDYDX token'larını almak için yaklaşık `7 gün` (**Bekleme Süresi**) beklemeleri gerekir.

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

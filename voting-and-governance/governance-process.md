---
description: Yönetişim mimarisine üst düzey bir bakış.
---

#

## Genel bakış

$ethDYDX, $stkDYDX ve $wethDYDX ("Yönetişim Tokenları"), sahiplerine dYdX v3 üzerinde değişiklikler teklif etme ve bu değişiklikler hakkında oy verme hakkı verir. dYdX yönetişimi AAVE yönetişim sözleşmelerine dayanır ve Yönetişim Token'larının sahipliğine dayalı oylamayı destekler.

Teklifler, teklif türüne bağlı olarak evet oylarında belirli bir eşiği ve yüzdeyi geçmelidir.



dYdX Yönetişiminin merkezinde 8 akıllı sözleşme vardır:

* **`$ethDYDX, $stkDYDX ve $wethDYDX Token` sözleşmeleri**: Zaman içinde farklı bloklarda her bir adresin oy verme yetkisinin anlık görüntülerine sahiptir.
* **`Governance Strategy V2` sözleşmesi**: Kullanıcıların teklif verme ve oy verme yetkisini ölçen mantığı içerir. dYdX Topluluğu, $wethDYDX'e dYdX v3 yönetişiminde oy verme ve teklif verme konusunda ethDYDX ile aynı yönetişim işlevselliğini kazandırmak için `Governance Strategy` (Yönetişim Stratejisi) sözleşmesini `Governance Strategy V2`'ye yükseltme yönünde [oy kullanmıştır](https://dydx.community/dashboard/proposal/15).
*
* **`Governor` sözleşmesi**: Teklifleri izler ve Timelock akıllı sözleşmesi aracılığıyla teklifleri yürütür.
* **`Timelock` sözleşmeleri**: Yönetişim tarafından oylanan işlemleri sıraya koyar, iptal eder veya yürütür. Bir teklifteki işlevler Timelock sözleşmesi tarafından başlatılır. Kuyruğa alınan işlemler, gecikmeden sonra ve ödemesiz sürenin bitiminden önce gerçekleştirilebilir.
* **`Priority Timelock` contract** Timelock sözleşmesi ile aynıdır ancak bir öncelik denetleyicisinin timelock bekleme süresi sona ermeden önce **Öncelik Süresi** (7 gün) içinde işlemleri gerçekleştirmesine olanak tanır.

![Akıllı sözleşme mimarisi](../.gitbook/assets/1-smart-contract-architectue.png)

Zincir içi dYdX yönetişimi şunlara olanak tanır:

* Yetkili herhangi bir executor sözleşmesi tarafından yürütülecek tekliflere oy verme
* Bir teklifin başlangıcında token bakiyelerinin anlık görüntülerini alma
* Oy verme ve teklif verme yetkilerini ayrı ayrı delege etme
* Teklifler, karar yeter sayıları ve oy farkı yetkileri de dâhil olmak üzere yönetişim eşiklerini belirleme
* Oyların nasıl sayıldığını değiştirme (Governor sözleşmesi üzerindeki "Governance Strategy" akıllı sözleşme adresini değiştirerek)

## Teklif Türleri

Bir executor her tür teklifi doğrulamalıdır.

#### **Short timelock executor**

Short timelock executor şunları kontrol eder:

* Liquidity Module, Safety Module ve Merkle Distributor Module da dâhil olmak üzere teşvik sözleşmeleri
* Ödül ve Topluluk Hazinelerindeki fonlar
* yeni token'ların basılması
* Safety Module hariç tüm proxy sözleşmeleri
* stark proxy sözleşmelerindeki koruyucu rolleri

**Starkware öncelik timelock** yürütücüsü



#### **Uzun timelock** yürütücüsü

Uzun timelock yürütücüsü (uygulayıcısı), genellikle dYdX v3'ün yönetişim mutabakatını (konsensüs) etkileyen kısımlarını değiştiren teklifleri uygulayabilir.

#### **Merkle-pauser executor**

Merkle-pauser executor, her bir kullanıcının toplam ödül bakiyesi ile düzenli aralıklarla güncellenen Merkle kökünü donduran teklifleri yürütür ve önerilen kökün yanlış veya kötü amaçlı olması durumunda kullanıcılara yeni ödüllerin zamanla dağıtılmasına olanak verir. Ayrıca stark proxy sözleşmelerinden herhangi biri tarafından zorlanan alım satım taleplerini de veto edebilir.

İlk baştaki timelock parametreleri aşağıdaki gibidir:

![Başlangıç timelock parametreleri](../.gitbook/assets/1-initial-timelock-parameters.png)

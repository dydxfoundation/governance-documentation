---
description: Yönetişim mimarisine üst düzey bir bakış.
---

# Mimari

## Genel bakış

DYDX, sahiplerine Protokol üzerinde yapılacak değişiklikler için teklif verme ve oy verme hakkı verir. DYDX yönetişimi, AAVE yönetişim sözleşmelerine dayalıdır ve DYDX token bakiyelerine dayalı olarak oy vermeyi destekler.

Teklifler, teklif türüne bağlı olarak evet oylarında belirli bir eşiği ve yüzdeyi geçmelidir.

Bu DYDX token'ları teklif vermek veya yönetişim teklifleri üzerinde oy vermek için kullanılabilir veya başka Ethereum adreslerine delege edilebilir.

dYdX Yönetişiminin merkezinde 6 akıllı sözleşme vardır:

* **`DYDX Token` sözleşmesi**: Her bir adresin oy verme yetkisinin zaman içinde farklı bloklardaki anlık görüntülerine sahiptir.
* **`Governance Strategy` sözleşmesi**: Kullanıcıların teklif verme ve oy verme yetkisini ölçen mantığı içerir.
* **`Safety Module` sözleşmesi**: DYDX token'larının stake edilmesini, pozisyonun tokene dönüştürülmesini ve ödüllerin alınmasını sağlayan mantıkları içerir. Güvenlik modülünde stake edilen token'lar tüm yönetişim haklarını muhafaza eder.
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

Bir teklifin süresini ve yürütülmesini etkileyen farklı parametrelere sahip dört tür teklif vardır, yani yönetişim mutabakatını etkileyen önemli teklifler daha uzun bir oylama süresi ve daha yüksek bir oy farkı gerektirirken sadece protokol parametrelerini etkileyen teklifler ise daha kısa bir oylama süresi gerektirir ve hızlı bir şekilde uygulamaya koyulabilir. Bir executor her tür teklifi doğrulamalıdır.

#### **Kısa timelock** yürütücüsü

Short timelock executor şunları kontrol eder:

* Liquidity Module, Safety Module ve Merkle Distributor Module da dâhil olmak üzere teşvik sözleşmeleri
* Ödül ve Topluluk Hazinelerindeki fonlar
* yeni token'ların basılması
* Safety Module hariç tüm proxy sözleşmeleri
* stark proxy sözleşmelerindeki koruyucu rolleri

**Starkware öncelik timelock** yürütücüsü

Starkware priority timelock executor, StarkEx Perpetual Exchange sözleşmesinin sahibidir. dYdX Katman 2 Borsasının yapılandırmasını kontrol eden teklifleri yürütebilir.

Alınacak eyleme bağlı olarak, borsa üzerindeki değişikliği doğru bir şekilde uygulamaya koymak için Starkware ekibinin sürece dâhil olması gerekebilir. Bu nedenle, bir teklifin yürütülmesini tetikleme imkânına sahip olduğu 7 günlük (**Öncelik Süresi**) bir süreyi Starkware'e sağlayan bir "priority controller" rolü bu executor'a verilir.

Starkware, _hangi_ protokol değişikliklerinin yapılacağı üzerinde kontrole sahip değildir. Yalnızca DYDX token sahipleri, dYdX yönetişimi aracılığıyla borsa protokolündeki değişiklikleri onaylama veya reddetme imkânına sahiptir.

#### **Uzun timelock** yürütücüsü

Long timelock executor, genellikle Protokol'ün yönetişim mutabakatını etkileyen bölümlerini değiştiren teklifleri yürütür.

#### **Merkle-pauser executor**

Merkle-pauser executor, her bir kullanıcının toplam ödül bakiyesi ile düzenli aralıklarla güncellenen Merkle kökünü donduran teklifleri yürütür ve önerilen kökün yanlış veya kötü amaçlı olması durumunda kullanıcılara yeni ödüllerin zamanla dağıtılmasına olanak verir. Ayrıca stark proxy sözleşmelerinden herhangi biri tarafından zorlanan alım satım taleplerini de veto edebilir.

İlk baştaki timelock parametreleri aşağıdaki gibidir:

![Başlangıç timelock parametreleri](../.gitbook/assets/1-initial-timelock-parameters.png)

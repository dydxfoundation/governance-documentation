---
description: dYdX İyileştirme Teklifi (DIP) yaşam döngüsüne genel bakış.
---

# Teklif Yaşam Döngüsü

## **Teklif Aşamaları**

dYdX Yönetişim Süreci, [**forums.dydx.community**](https://forums.dydx.community) adresindeki yönetişim forumları tarafından desteklenir ve dYdX İyileştirme Teklifi ("DIP") aracılığıyla onaylanır.

Aşağıda konseptin başlangıcından ve tanımlanmasından fiilen uygulanmasına kadar dYdX yönetişim sürecinin nasıl aktığını açıklayan bir ön taslağı özetliyoruz. Bu süreçler DYDX topluluğundan gelen geri bildirimlere göre değişebilir.

Aşağıdaki akış şeması bir teklifin geçmesi için başlangıçta önerilen aşamalardır:

![Stages of a DIP](<.. /.gitbook/assets/image (81).png>)

## 0. Forum Tartışması

Herkes [**forums.dydx.community**](https://forums.dydx.community) adresinde barındırılan dYdX'in Yönetişim forumlarında kayıt olup herhangi bir konuda bir ileti dizisi oluşturabilir. Topluluk üyelerinin bir e-posta adresi veya bir Ethereum cüzdanı kullanarak kaydolması gerekir.

## 1. (Zincir Dışı) DRC Oluşturma

Zincir dışı **dYdX Yorum Talebi** (DRC) oluşturulması yönetişimi iyileştirme sürecindeki ilk adımdır. Herkes Yönetişim Forumu'na katılabilir, zincir dışı DRC'ler oluşturabilir ve iyileştirmeleri tartışabilir.

Bir DRC oluşturmak için [bu şablonu](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md) (Github'ımızda mevcuttur) kullanın. DRC, potansiyel olarak nihai DIP'nin tüm bilgilerini kapsamalıdır.

DRC'ler en azından şunları içermelidir:

* Kısa ve öz DRC başlıkları
* Teklifin kısa ve öz bir açıklaması
* DRC'nin gerekçesi, örneğin neden?
* Forum gönderisinin başlığında DRC: DRC'nin kısa başlığı yer almalıdır. Örneğin, DRC: Yeni Piyasa Talebi
* Topluluk üyelerinin zincir dışı iyileştirmeleri oylamak için kullanabileceği bir topluluk anketi

## 2. DRC Tartışması ve Geri Bildirim

Yönetişim forumunda yayınlandıktan sonra, DRC'yi daha da iyileştirmek için tüm sorular ve yorumlar ele alınıp yanıtlanmalı ve dikkate alınmalıdır.

## 3. DRC Snapshot Anketi

Snapshot anketleri iki amaca hizmet eder: Gelecekteki zincir içi DIP'ler için duyarlılık gösterilmesi ve zincir dışında kontrol edilen değişkenler için bağlayıcı oylamalar.

Zincir dışı bir DRC üzerinde çok açık bir mutabakat sağlandığında, `10.000'den` fazla DYDX tutan bir topluluk üyesi DRC için **Snapshot** üzerinde **zincir dışı bir oylama** oluşturabilir. Normal çalışma haftası boyunca görünürlüğü artırmak için dYdX Topluluğu'nun Snapshot anketlerini Pazartesi günleri oluşturmasını öneririz.

Snapshot, kullanıcıların duyarlılığı zincir dışında göstermesini sağlayan basit bir oylama arayüzüdür. Snapshot üzerindeki oylamalarda, oy vermek için kullanılan adresin oy verme yetkisine göre ağırlık verilir.

Duyarlılık gösterilmesine ilişkin Snapshot anketleri için, teklifi verenin şunları sağlaması gerekir:

* DRC hakkındaki ayrıntılı bilgiler,
* bir oylama sistemi,
* bir oylama süresi; oylama başlangıç tarihi ve oylama bitiş tarihi arasında 4 günlük bir oylama süresi olmalıdır ve
* bir oylama bekleme süresi; 6.570 blok (yaklaşık 1 gün) ileride olan bir Snapshot blok numarası. Snapshot blok numarası, oy kullanabilen topluluk üyelerinin durumunu kilitler. Snapshot blok numarası öncesinde token tutan token sahipleri oy verme hakkına sahiptir. Her bir adresin ilgili oylama yetkisinin anlık görüntüsünü almadan önce, oylama için bekleme süresi DYDX/stkDYDY sahiplerine token edinmek, oylama yetkisini delege etmek ve token'ları cüzdanlar arasında taşımak (token'ların cüzdanlar arasındaki taşınması yalnızca DYDX sahipleri için geçerlidir) için zaman verir.

Zincir içi bir akıllı sözleşmenin çağrılmasını gerektirmeyen kararlar, özellikle de Alım Satım ve Likidite Sağlayıcı ödüllerinin formüllerinde yapılacak değişiklikler için Snapshot oylamaları bağlayıcı ve kesin oylama olarak kabul edilir. Teklif verenin yukarıdaki gereksinimleri karşılaması ve şunları sağlaması gerekir:

* iki oylama seçeneği; açıkça belirtmek gerekirse, bir adres bir teklifin lehine veya aleyhine oy verir.

Teklif edilen değişiklik/değişiklikler, Snapshot anketinin sonuçları şunları karşılarsa dYdX Trading Inc. tarafından uygulamaya koyulur:

* karar yeter sayısı - en az 1 milyon DYDX/stkDYDX. Karar yeter sayısı karar alma sürecinin merkeziyetsizleştirilmesine katkıda bulunur ve tek taraflı karar alınmasına karşı korur ve
* minimum oy farkı - verilen oyların en az %67'si teklifin lehine olmalıdır. Minimum oy farkı, son derece tartışmalı ve daha fazla tartışılması gereken tekliflerin filtrelenmesini sağlar.

dYdX Trading Inc.'in başarılı bir Snapshot anketinde kabul edilen değişiklikleri uygulamak için uygulamaya koyma mühleti olarak 1 Döneme varan bir süreye (28 gün) sahip olacaktır.

Teklifler ve oyların IPFS'de depolanan ve Commonwealth portalında mevcut olan yalnızca imzalanmış mesajlar olduğunu unutmayın.

## 4. (Zincir içi) DIP Oluşturma

Açık bir mutabakata varıldığında, teklifin türü için yeterli teklif yetkisine sahip bir topluluk üyesi tarafından zincir içi bir DIP verilebilir. Zincir içi bir DIP bir akıllı sözleşme çağrısı aracılığıyla başlatılır. Teklif, Snapshot üzerindeki zincir dışı DIP oylamasının kazanan sonucuna dayalı olmalıdır ve teklif başına en fazla 10 eylem olmak kaydıyla bir veya birden fazla eylemden oluşabilir.

Bir DIP'nin oluşturulabilmesi için, bir hesap için gerekli olan minimum sayıda token'ın tutulması/delege edilmesi gerekir. Bir teklif oluşturulduğunda bir Timelock executor belirtilmelidir. Başlangıç parametreleri aşağıdaki gibidir (ve yönetişim tarafından değiştirilebilir):

| Parametre | Açıklama | Short Timelock Executor | Merkle-Pauser Executor | Long Timelock Executor | Starkware Executor |
| ------------------ | ------------------------------------------------ | ----------------------- | ---------------------- | ---------------------- | -------------------- |
| Teklif Eşiği | Teklif oluşturmak için tutulması/delege edilmiş olması gereken minimum token miktarı | Toplam arzın %0,5'i | Toplam arzın %0,5'i | Toplam arzın %2'si | Toplam arzın %0,5'i |

## 5. (Zincir içi) DIP Oylaması

Bir Zincir içi DIP oluşturulduktan sonra, teklif şu anda `6570` blok veya yaklaşık 1 gün (blok başına yaklaşık 13 saniye gerektiğini varsayarak) olarak yapılandırılan **Oylama Bekleme Süresi** ile tanımlanan bir `bekleme` durumuna geçer. Diğer bir deyişle, kullanıcı anlık görüntüleri DIP oluşturulduktan 1 gün sonra kaydedilir ve bu noktada teklif `aktif` duruma geçer.

Oylama Bekleme Süresi dolduktan sonra Oylama Süresi etkinleştirilir. Oylama süresinin uzunluğu teklifin türüne bağlıdır.

Aşağıdaki grafik bir DIP durumu akış şemasını göstermektedir:

![Lifecycle of a DIP](<.. /.gitbook/assets/image (63).png>)

Zincir içi bir DIP oluşturulduktan sonra, bir **Oylama Bekleme Süresi**, **Oylama Süresi**, **Karar Yeter Sayısı** ve bir minimum **Oy Farkına** tabi olur. Başlangıç parametreleri aşağıdaki gibidir:

| Parametre | Açıklama | Short Timelock Executor | Merkle-Pauser Executor | Long Timelock Executor | Starkware Executor |
| ----------------- | ----------------------------------------------------------------------------------------------------- | ----------------------- | ---------------------- | ---------------------- | -------------------- |
| Oylama Bekleme Süresi | Bir teklifi oylamadan önce beklenmesi gereken Ethereum blok sayısı, teklif sunulduktan sonra başlayabilir | 6.570 blok | 6.570 blok | 6.570 blok | 6.570 blok |
| Oylama Süresi | Tekliflerin oylanmaya açık olduğu süre | 4 gün | 2 gün | 10 gün | 4 gün |
| Karar Yeter Sayısı | Bir DIP teklifinin geçmesi için gereken minimum evet oyu | Toplam arzın %2'si | Toplam arzın %1'i | Toplam arzın %10'u | Toplam arzın %2'si |
| Oy Farkı | Bir DIP teklifinin geçmesi için gereken evet-hayır oyları arasındaki fark | Toplam arzın %0,5'i | Toplam arzın %0,5'i | Toplam arzın %10'u | Toplam arzın %0,5'i |

Yalnızca oylama bekleme süresi yönetişim tarafından değiştirilebilir ve yalnızca minimum ve maksimum bekleme süreleri (dâhil olarak) arasındaki değerlere değiştirilebilir. Oylama süresi, karar yeter sayısı ve oy farkı değiştirilemez.

## 6. Teklifin Kuyruğa ve Uygulamaya Konulması

Bir DIP geçtikten sonra, herhangi bir adres teklifi timelock kuyruğuna taşımak için kuyruk metodunu çağırabilir. Bir DIP sadece geçmişse kuyruğa koyulabilir.

| Parametre | Açıklama | Short Timelock Executor | Merkle-Pauser Executor | Long Timelock Executor | Starkware Executor |
| ---------------------- | ------------------------------------------------------------------------------------- | ----------------------- | ---------------------- | ---------------------- | ------------------ |
| Timelock Bekleme Süresi | Bir teklif geçtikten ve kuyruğa koyulduktan sonra, teklif uygulamaya koyulmadan önce beklenen süre | 2 gün | 0 gün | 7 gün | 2-9 gün |
| Uygulamaya Koyma Mühleti | Bir teklifin, uygulamaya konulabilir hale geldikten sonra uygulamaya konması gereken süre. | 7 gün | 7 gün | 7 gün | 7 gün |
| Minimum Timelock Bekleme Süresi | Bir teklif uygulamaya koyulmadan önce beklenen minimum süre (kuyruğa koyulduktan sonra) | 1 gün | 0 gün | 5 gün | 4 gün |
| Maksimum Timelock Bekleme Süresi | Bir teklif uygulamaya koyulmadan önce beklenen maksimum süre (kuyruğa koyulduktan sonra) | 7 gün | 1 gün | 21 gün | 21 gün |

Oylama süresi bitip bir teklif başarılı olur olmaz timelock bekleme süresini başlatmak için herkes kuyruk metodunu çağırabilir.

Starkware priority timelock executor söz konusu olduğunda, 9 günlük timelock bekleme süresi boyunca 7 günlük bir öncelik süresi vardır. Bu da 9 gün sonra bir teklifi herkesin uygulamaya koyabileceği anlamına gelir ancak Starkware 2-9 gün (öncelik süresi) içinde teklifi uygulamaya koyma seçeneğine sahiptir.

Pratikte:

* 0.-2. Günler: Hiç kimse uygulamaya koyamaz
* 2.-9. Günler: Yalnızca Starkware uygulamaya koyabilir
* 9. Gün: Herkes uygulamaya koyabilir

## 7. (İsteğe Bağlı) Teklif İptali

Bir DIP'in yaşam döngüsündeki herhangi bir noktada, teklif veren DIP'yi iptal edebilir. Teklif veren mevcut blokta yeterli teklif yetkisine sahip değilse, bir teklif uygulamaya koyulmadan önce herkes tarafından iptal edilebilir.



## SSS

### Oylama Bekleme Süresinin amacı nedir?

**Oylama Bekleme Süresi**, bir teklif sunulduktan sonra oylama yapılmadan önce beklenmesi gereken Ethereum bloklarının sayısıdır.

DYDX oylama yetkisi, bir teklif henüz sunulmadan önce veya teklifin **Oylama Bekleme Süresi** sırasında bir adrese delege edilmelidir.

Şu an için, **Oylama Bekleme Süresi** `6.570 blok` olarak belirlenmiştir ve bu da yaklaşık 1 gündür. Bu değer, bir teklif oluşturulduğunda mevcut blok sayısına eklenir.

İleride, dYdX Yönetişimi **Oylama Bekleme Süresinin** artırılmasını veya azaltılmasını oylayabilir. **Oylama Bekleme Süresinin** artırılmasının bariz faydaları vardır. Bununla birlikte, aşırı durumlardan fırsatçı bir şekilde yararlanma gibi bazı olası olumsuz sonuçlara da yol açabilir.

### Teklif Eşiğinin amacı nedir?

DYDX serbestçe alınıp satılabilen bir varlık olduğundan, piyasa alımı yoluyla herkes yönetişimi ele geçirmeyi deneyebilir. Bununla birlikte, kötü niyetli bir oylamayı geçmeye zorlamak, bir short timelock durumunda minimum 5 milyon DYDX ve bir long timelock durumunda ise 20 milyon DYDX gerektirir. Her ne kadar kesinlikle imkânsız olmasa da bu miktar son derece pahalı olacak ve fiyat dalgalanması da hesaba katıldığında saldırıdan elde edilecek net kazançtan çok daha maliyetli olacaktır.

Bir grup bir şekilde kötü niyetli bir şekilde yönetişimi ele geçirmeyi başaracak olsa, timelock bekleme süresi etkilenen kişilere varlıklarını protokolden çekmeleri için zaman verecektir. Bu, geri kalan iyi niyetli oyuncular tarafından muhtemelen tutulacak bir yol olarak protokolü çatallamak için bir fırsat da olabilir.

###

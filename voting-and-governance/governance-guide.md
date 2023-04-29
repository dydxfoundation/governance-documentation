---
description: >-
  DRC oluşturma, Snapshot anketinin oluşturulması, DIP oluşturma, bir Snapshot anketinin oylanması, bir DIP'nin oylanması, bir DIP'nin kuyruğa koyulması ve bir DIP'nin uygulamaya koyulmasına ilişkin yönetişim sürecine adım adım bir genel bakış.
---

# Yönetişim Rehberi

dYdX Vakfı, dYdX topluluğunun dYdX yönetişim sürecini anlamasına yardımcı olmak için bu kılavuzu oluşturmuştur. Kılavuzda şu konulara adım adım bir genel bakış sağlanmaktadır:

* [Forum Tartışmaları (zincir dışı)](governance-guide.md#step-1-forum-discussions-drc-creation-off-chain-and-drc-feedback)
* [DRC oluşturma (zincir dışı)](governance-guide.md#step-1-forum-discussions-drc-creation-off-chain-and-drc-feedback)
* [Snapshot anketi oluşturma (zincir dışı)](governance-guide.md#step-2-drc-snapshot-polling-off-chain)
* [Bir Snapshot anketinin oylanması](governance-guide.md#how-to-vote-on-a-snapshot-poll)
* [DIP oluşturma (zincir dışı)](governance-guide.md#step-3-dip-creation-off-chain-proposal)
* [DIP oluşturma (zincir içi)](governance-guide.md#step-1-on-chain-dip-drafting)
* [Bir DIP'nin oylanması (zincir içi)](governance-guide.md#how-to-vote-on-a-dip)
* [Bir DIP'nin kuyruğa koyulması (zincir içi)](governance-guide.md#how-to-queue-a-proposal)
* [Bir DIP'nin uygulamaya koyulması (zincir içi)](governance-guide.md#how-to-execute-a-proposal)

Kılavuzda yer alan iki örnek _DIP 2 (zincir dışı teklif) - Likidite Sağlayıcı Ödülleri Eşiğinin Düşürülmesi_ ve _DIP 3 (zincir içi teklif) Safety Module'un Restorasyonu'dur_.

## DIP 2 (Zincir Dışı Teklif) - Likidite Sağlayıcı Ödülleri Eşiğinin Düşürülmesi

_**Özet:**_

Dönem 6'da dYdX topluluğu, piyasa yapıcılar için LP ödülleri hacmi eşiğinin %1'den %0,25'e düşürülmesini [Snapshot](https://commonwealth.im/dydx/snapshot/dydxgov.eth/0x785066561be1e5d170eb28960da5ef2643ee0d0c3d590fd797c028512cc6be43)'ta oylamıştır. LP ödülleri eşiğinin Dönem 2'de %5'den %1'e düşürülmesinde, Dönem 6'daki düşürme (%1'den %0,25'e) ile aynı süreç izlenmiştir. LP ödülleri hacmi eşiğinin %5'den %1'e düşürülmesi sürecine adım adım genel bakış aşağıda yer almaktadır.

Topluluğun çoğunluğu (399 oy veren ve [DYDX](https://forums.dydx.community/snapshot/dydxgov.eth/QmXtS7CGVX7C5v2JdcJpsqWAeZrStQcogSQpP6zzhzwLmN)'in %86'sı) Likidite Sağlayıcı ödüllerinin alınması için hacim eşiğinin %5'den %1'e düşürülmesi yönünde oy kullanmıştır. Piyasa yapıcılar için Likidite Sağlayıcı ödülleri hacmi eşiğinin %5'den %1'e düşürülmesi için [zincir dışı bir DIP](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-2.md) DeFiance Capital'da Jacob Goh (jweam0x) tarafından sunulmuştur. Dönem 2'de %1'lik eşiği karşılayan piyasa yapıcılar Dönem 3'te Likidite Sağlayıcı ödülleri kazanmaya hak kazanmışlardır. Teklif, hiçbir zincir içi akıllı sözleşme değişikliği gerektirmemiştir.

_**Geçmiş:**_

Likidite Sağlayıcı [ödülleri programı](https://docs.dydx.community/dydx-governance/rewards/liquidity-provider-rewards) kapsamında, protokol için piyasa yapan Likidite Sağlayıcılara her dönem (28 gün) 1.150.685 DYDX dağıtılmaktadır. Ödüller çalışma süresi, iki taraflı derinlik, teklif-talep farkları ve desteklenen piyasaların sayısının bir kombinasyonunu ödüllendiren bir formül esasında dağıtılmaktadır. Bu ödül programına hak kazanmak için, likidite sağlayıcıların bir önceki dönem boyunca toplam piyasa yapıcı hacminin minimum bir yüzdesini sağlaması gerekmektedir.

dYdX topluluğu, Likidite Sağlayıcı ödülleri eşiğinin üzerinde "anında ve gayri kabili rücu kontrol" sahibidir. Topluluğun kontrol ettiği parametrelerin tam listesini [burada](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters) bulabilirsiniz.

Topluluk Likidite Sağlayıcı ödülleri eşiğinin düşürülmesini istemektedir çünkü bu yeni Piyasa Yapıcıları ve küçük ila orta ölçekli Piyasa Yapıcıları dYdX platformundaki likiditeyi artırmaya teşvik edecektir. Dahası, platformdaki Piyasa Yapıcıların sayısının artırılması dYdX protokolünün daha merkeziyetsiz bir hale gelmesini sağlar.

Bunun ardından, dYdX yönetişiminin pratikte nasıl işlediğine dair adım adım bir genel bakış sunuyoruz. dYdX yönetişim süreci hakkında daha fazla bilgiyi [burada](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle) bulabilirsiniz.

### **1. ADIM - Forum Tartışmaları, DRC Oluşturma (Zincir Dışı) ve DRC Geri Bildirimi**

_**Açıklama:**_

dYdX Yönetişim Süreci, [yönetişim forumları](https://dydx.forum/) tarafından desteklenir. Topluluk üyeleri zincir dışı bir açık mutabakat sağlamak için tartışma ileti dizilerinde gönderi oluşturur ve yorum yapar. Forum tartışmaları ve DRC Oluşturma hakkında daha fazla bilgiyi [burada bulabilirsiniz](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle). \
\
Not - Operasyonlar alt-DAO'su, [topluluk oylamalarının Commonwealth'ten Discourse'a geçişinin](https://snapshot.org/#/dydxgov.eth/proposal/0xa5e77732dd24edd26bd41b089969b3662c29eb41c3bacd35cb2931ca55882a8f) akabinde yeni forum konumu olarak [**https://dydx.forum/**](https://dydx.forum/) adresini devreye almıştır. Bu kılavuzda yer alan ve önceki DRC tartışmalarına yapılan bazı atıflar hala Commonwealth'e işaret edecektir; ancak yeni başlatılan tüm tartışmalar, yeni başlatılan [**Discourse**](https://dydx.forum/) forumunda gerçekleşmelidir. \


_**DIP 2 başvurusu:**_

Three Arrows Capital'dan Su Zhu (zhusu) Likidite Sağlayıcı Ödülleri Eşiğinin düşürülmesi için [zincir dışı bir Forum Tartışması](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives/) oluşturmuştur. Wintermute'tan Evgeny, Kronos'dan Ben, Sixtant'tan Josh ve daha birçok topluluk üyesi tartışmaya katılmış ve değerli geri bildirimler sağlamıştır.

![https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives/](../.gitbook/assets/2-reduce-mm-incentives.png)

![https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives/](../.gitbook/assets/2-reduce-mm-incentives-2.png)

#### _Discourse Üzerinde Nasıl Gönderi ve Yorum Yapılır:_

* E-posta hesabınızla Discourse'a kaydolun ve dYdX topluluğuna [buradan](https://dydx.forum/) katılın.

<figure><img src="../.gitbook/assets/Screenshot 2023-04-19 at 10.59.27 AM.png" alt=""><figcaption></figcaption></figure>

* Bir ileti dizisi seçin, yorumlar arasında gezinin ve yorumları beğenin veya yanıtlayın.
* "**Yeni Konu**" üzerine tıklayarak ve konu kategorisini seçerek yeni bir tartışma dizisi oluşturun veya bir DRC gönderin.

<figure><img src="../.gitbook/assets/Screenshot 2023-04-19 at 11.03.33 AM.png" alt=""><figcaption></figcaption></figure>

* Eğer bir DRC oluşturuyorsanız lütfen [buradaki](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md) şablonu izleyin. [Teklif Yaşam Döngüsü](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle) bölümünde _DRC Oluşturma_ başlığı altında belirtildiği üzere DRC'ler en az şunları içermelidir:
  * DRC'nin kısa ve öz bir başlığı.
  * Teklifin kısa ve öz bir açıklaması.
  * DRC'nin gerekçesi (örneğin neden?).
  * Forum gönderisinin başlığı DRC: \[DRC'nin kısa başlığını ekleyin] şeklinde olmalıdır (Örneğin, DRC: Yeni Piyasa Talebi).
  * Topluluk üyelerinin zincir dışı iyileştirmeleri oylamak için kullanabileceği bir topluluk anketi.

### **2. ADIM - DRC Snapshot Anketi (Zincir Dışı)**

_**Açıklama:**_

Topluluk açıkça bir mutabakat sağladıktan sonra, 10.000 teklif verme yetkisine sahip bir topluluk üyesi [Snapshot](https://snapshot.org/#/) üzerinde DRC için zincir dışı bir oylama oluşturabilir. [Teklif verme yetkisi](https://docs.dydx.community/dydx-governance/voting-and-governance/voting) bir teklif oluşturma ve sürdürme erişimi sağlar. Snapshot, kullanıcıların duyarlılığı zincir dışında göstermesini sağlayan basit bir oylama arayüzüdür. Snapshot üzerindeki oylamalarda, oylama yapmak için kullanılan adrese ait veya bu adrese delege edilmiş DYDX sayısına göre ağırlık verilir. Snapshot anketini oluşturan topluluk üyesi DRC hakkında ayrıntılı bilgi, bir oylama sistemi, oylamanın başlangıç tarihi, oylamanın sona erme tarihi ve snapshot blok numarasını sağlamalıdır. Oylama süresi 5 gün olmalı ve oylama 1 günlük oylama bekleme süresi sonrasında başlamalıdır. Oylama bekleme süresi dYdX topluluk üyelerinin DRC hakkında daha fazla bilgi edinmesi, DYDX satın alması veya DYDX'lerinin oylama yetkisini delege etmesi için zaman sağlar. Snapshot blok numarası öncesinde DYDX tutan veya oylama yetkisi kendisine delege edilen topluluk üyeleri oy verme hakkına sahiptir. Snapshot anketleri hakkında daha fazla bilgiyi [burada](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle) bulabilirsiniz.

_**DIP 2 başvurusu:**_

Topluluk üyeleri Su Zhu'nun gönderisi hakkında geri bildirim sağlamıştır. Topluluk tarafından aşağıdaki ödül eşikleri önerilmiştir:

* [%0,5](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=body) - Three Arrows Capital'dan Su Zhu,
* [%1](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=4972) - BitTrading'den Sam,
* [%2,5](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=4855) - Kronos / WOO Network'ten Bin ve
* [%5](https://forums.dydx.community/proposal/discussion/1805-reduce-market-maker-incentives?comment=4872) - Wintermute'tan Evgeny.

Bunun ardından, Su Zhu aşağıdaki seçeneklerle bir Snapshot anketi oluşturmuştur:

* MM eşiğinin %1'e düşürülmesi
* MM eşiğinin %2,5'e düşürülmesi
* MM eşiğinin %5 olarak bırakılması

![https://snapshot.org/#/dydxgov.eth/proposal/QmXtS7CGVX7C5v2JdcJpsqWAeZrStQcogSQpP6zzhzwLmN](../.gitbook/assets/2-create-snapshot.png)

#### _Bir Snapshot Anketi Üzerinde Oylama Yapma:_

* Ethereum cüzdanınız ile Snapshot'a kaydolun ve [buradaki](https://snapshot.org/#/dydxgov.eth) dYdX tekliflerini izleyin.

![https://snapshot.org/#/dydxgov.eth](../.gitbook/assets/2-register-snapshot.png)

* Aktif Snapshot anketlerinde oy vermek için, Snapshot anketinin aktif hale geldiği Snapshot blok numarası öncesinde adresinizde DYDX tutmanız veya adresinize oylama yetkisi delege edilmiş olması gerekir.
* Oy vermek için, teklife tıklayıp "Evet" veya "Hayır" seçeneğini belirleyin ve ardından "Oy Ver" seçeneğine tıklayın.

#### _Snapshot Üzerinde Bir Anket Nasıl Oluşturulur:_

* Bir Snapshot anketi oluşturabilmek için, teklifi oluşturmakta **kullandığınız adreste en az 10.000 DYDX bulundurmanız ve/veya bu adrese oylama yetkisi delege edilmiş olması** gerekir.
* Snapshot teklifi, teklif başına en fazla 10 eylem olmak üzere bir veya birden fazla eylemden oluşabilir. Eylemler, bir teklifte belirtilen değişikliklerdir.
* Minimum 10.000'lik teklif verme yetkisi gereksinimini karşılıyorsanız "**Yeni Teklif**" seçeneğine tıklayın ve aşağıdaki içerik gereksinimleri uyarınca açık alanları doldurun.

<figure><img src="../.gitbook/assets/Screenshot 2023-04-19 at 11.08.42 AM.png" alt=""><figcaption><p>dYdX Snapshot sayfası - "Yeni Teklif Oluştur" düğmesi</p></figcaption></figure>

<figure><img src="../.gitbook/assets/Screenshot 2023-04-19 at 11.09.33 AM.png" alt=""><figcaption><p>Snapshot ayrıntılarını burada belirtin ve DRC için bir bağlantı eklediğinizden emin olun</p></figcaption></figure>

DRC Snapshot Anketi İçerik Gereksinimleri:

* Forum tartışmasına bir bağlantı ile beraber DRC hakkında ayrıntılı bilgi,
* bir oylama sistemi,
* toplam oylama süresi 4 gün olacak şekilde oylama başlangıç tarihi ve oylama sona erme tarihi ve
* Snapshot anketi oylama başlamadan 1 gün (\~6.570 blok) önce yayınlanır.

Bağlayıcı Snapshot Anketleri için gereksinim:

Bir Snapshot anketi çoğu karar için yalnızca görüşlerin yansıtılmasını sağlarken, akıllı sözleşmeleri değiştiren bağlayıcı bir sonuç için zincir içi bir oylama gereklidir. Zincir içi bir akıllı sözleşmenin çağrılmasını gerektirmeyen kararlar, özellikle de Alım Satım ve Likidite Sağlayıcı ödüllerinin formüllerinde yapılacak değişiklikler için, Snapshot oylamaları bağlayıcı ve kesin oylama olarak kabul edilir. Yukarıdaki içerik gereksinimlerine ek olarak, zincir dışı kontrol edilen değişkenler için bağlayıcı bir oylama niteliğindeki Snapshot anketleri şunları içermelidir:

* İki ayrı oylama seçeneği. Açıkça belirtmek gerekirse, bir adres bir teklifin lehine veya aleyhine oy verir.

![](../.gitbook/assets/2-snapshot-binary-voting.png)

* Oylama sonrasında ilgili bilgiler IPFS üzerinde saklanacak ve bir rapor otomatik olarak oluşturulup indirilmeye hazır hale getirilecektir.

![https://snapshot.org/#/dydxgov.eth/proposal/QmXtS7CGVX7C5v2JdcJpsqWAeZrStQcogSQpP6zzhzwLmN](../.gitbook/assets/2-snapshot-ipfs.png)

### **3. ADIM - DIP Oluşturma (Zincir Dışı Teklif)**

_**Açıklama**:_

(1) Bir Snapshot anketi zincir dışı bir parametrenin (Alım Satım Ödülleri veya LP Ödülleri formüllerinde yapılan değişiklikler gibi) güncellenmesi sonucunu doğurduğunda ve (2) bir topluluk üyesi zincir içi akıllı sözleşmeleri değiştirme teklifinde bulunmak istediğinde bir DIP oluşturulması gerekir. Herhangi bir zincir içi akıllı sözleşme güncellemesi gerektirmeyen oylamalarda Snapshot anketi bir zincir dışı DIP ile resmileştirilmeli dYdX Vakfı'nın Github'ının Beklemedeki DIP dalına bir Çekme Talebi aracılığıyla gönderilmelidir. DIP, Snapshot oylamasının kazanan sonucunu yansıtmalıdır. DIP'te, [buradaki](https://github.com/dydxfoundation/dip/blob/master/DIP-X.md) şablonda yer alan bilgiler belirtilmelidir.

_**DIP 2 başvurusu:**_

Bu örnekte, [DIP](https://github.com/jteamdc/dip/blob/master/content/dips/DIP-2.md) @Jteamdc. tarafından yazılmıştır.

![https://github.com/jteamdc/dip/blob/master/content/dips/DIP-2.md](../.gitbook/assets/2-dip-example.png)

@Jteamdc; DIP 2 için taslak teklif tamamlandığında, dYdX Vakfı'nın Beklemedeki DIP'ler bölümüne karşı çalışma bölümünden bir \*\*\*\* [Çekme Talebi](https://github.com/dydxfoundation/dip/pull/8) oluşturmuştur. dYdX Vakfı teklifi gözden geçirdikten ve onayladıktan sonra, Beklemedeki DIP'lerdeki değişiklikler Ana Dal ile birleştirilmiştir.

![https://github.com/dydxfoundation/dip/pulls](../.gitbook/assets/2-dip-pending-merge.png)

Likidite sağlayıcıların ödül eşiğinin düşürülmesi herhangi bir zincir içi akıllı sözleşme değişikliği gerektirmediği için süreç artık tamamlanmıştır ve değişiklikler bir sonraki dönemde yürürlüğe girecektir.

#### _Bir DIP Nasıl Oluşturulur:_

* DIP, Snapshot üzerindeki zincir dışı DIP oylamasının kazanan sonucuna dayalı olmalıdır ve teklif başına en fazla 10 eylem olmak kaydıyla bir veya birden fazla eylemden oluşabilir. Eylemler, bir teklifte belirtilen değişikliklerdir. Daha fazla bilgiyi [DIP Oluşturma](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle#6.-proposal-queuing-and-execution) başlığı altında bulabilirsiniz.
* Bir Github hesabı açmak için kaydolun: [https://github.com/signup](https://github.com/signup).
* [Buradaki](https://github.com/dydxfoundation/dip) dYdX repo sayfasına gidin ve Github hesabınızın altındaki repo'yu çatallayın.

![https://github.com/dydxfoundation/dip](../.gitbook/assets/2-dip-create-1.png)

* Çatallanan DIP repo'sunda DIP'lerin içeriğinin yer aldığı dizine gidin: [https://github.com/\[user\_name\]/dip/tree/master/content/dips](https://github.com/yt8073/dip/tree/master/content/dips).

![](../.gitbook/assets/2-dip-create-2.png)

* Dips klasörünü seçin: [https://github.com/\[user\_name\]/dip/tree/master/content](https://github.com/Jwatts15/dip/tree/master/content).

![](../.gitbook/assets/2-dip-create-3.png)

Dips klasörü, [buradaki](https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md) DIP şablonunu izleyen önceki tekliflerin bir dizinini içerir.

![https://github.com/dydxfoundation/dip/tree/master/content/dips](../.gitbook/assets/2-dip-create-4.png)

* Bir teklif taslağına başlamadan önce, çatalladığınız dalın ana dalın en son sürümü ile güncellenmiş olduğundan emin olun. DIP repo'sunun eski bir sürümünü kullanıyorsanız, çatallanmış sürümünüzün en son değişiklikleri içeren bir şekilde güncel olduğunu lütfen doğrulayın. Çatallanmış sürümünüzü yeniden temellendirme konusunda yardım almak için şuradaki adımları izleyebilirsiniz: [https://stackoverflow.com/quotions/7929369/how-to-repase-local-branch-onto-remote-master](https://stackoverflow.com/questions/7929369/how-to-rebase-local-branch-onto-remote-master).
* [DIP şablonunu](https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md) teklifinizin bilgileri ile düzenleyin. Eğer DIP repo'sunu çatallamadıysanız, düzenle simgesini seçtiğinizde, yönetici olmadığınız için repo ana daldan otomatik olarak çatallanacaktır.

![https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md](../.gitbook/assets/2-dip-create-5.png)

* [Şablonu](https://github.com/dydxfoundation/DIP/blob/master/DIP-X.md) izleyin ve DIP'inizi `content/dips/` dizinindeki depo çatalınıza ekleyin. Lütfen aşağıda verilen DIP Durumları adlandırma ilkelerini izleyin.

![](../.gitbook/assets/2-dip-create-6.png)

DIP Durumları:

* WIP - hâlâ geliştirilmeye devam eden bir DIP.
* Teklif Edildi - zincir içinde teklif edilmeye hazır bir DIP.
* Onaylandı - uygulamaya koyulması dYdX topluluğu tarafından kabul edilen bir DIP.
* Uygulamaya Koyuldu - ana ağda yayınlanan bir DIP.
* Reddedildi - reddedilen bir DIP.
* Tüm içeriğin doğru olduğunu kontrol ettikten sonra, çalışma dalınızdan dYdX Vakfı'nın Beklemedeki DIP'ler dalına bir Çekme Talebi oluşturun. Bu Çekme Talebini dYdX Vakfı'nın ana dalına lütfen **göndermeyin** çünkü herhangi bir dış taraf ana dalla birleştirmek isterse IPFS işi başarısız olacaktır. Lütfen [burada](https://github.com/dydxfoundation/dip/pull/8) örnek olarak verilen Çekme Talebini kullanın.

![](../.gitbook/assets/2-dip-status-1.png)

* İnceleme sonrasında, dYdX Vakfı, Beklemedeki DIP'ler dalındaki değişiklikleri Ana şube ile birleştirecektir.

![https://github.com/dydxfoundation/dip/pull/9](../.gitbook/assets/2-dip-status-2.png)

* **Birleşme** öncesinde, DIP'yi IPFS'ye yüklemek için bir iş otomatik olarak çalışacaktır. DIP'nin IPFS'ye yüklendiğini buradan doğrulayabilirsiniz: [https://github.com/dydxfoundation/dip/pull/9/check](https://github.com/dydxfoundation/dip/pull/9/checks).
* DIP, [**`dip`**](https://github.com/dydxfoundation/dip)`/`[`content`](https://github.com/dydxfoundation/dip/tree/master/content)`/`**`dips`**`/` altında eklenir.

![](../.gitbook/assets/2-dip-status-3.png)

Teklif herhangi bir zincir içi akıllı sözleşme değişikliği gerektirmediği için, süreç artık tamamlanmıştır ve değişiklikler bir sonraki dönemde yürürlüğe girecektir

## DIP 3 (Zincir İçi Teklif) - Safety Module Restorasyonu

_**Özet:**_

1 Kasım günü, Safety Module staking havuzunun işlevlerini restore etmek için Paradigm'den Dan Robinson tarafından zincir içi bir [DIP](https://dydx.community/dashboard/proposal/3) oluşturulmuştur. Topluluğun çoğunluğu (251 oy veren ve yaklaşık 142 milyon DYDX) Safety Module'un işlevlerini restore etme lehine oy vermiştir. 10 günlük bir Oylama Süresinin ardından, bir topluluk üyesinin kuyruğu çağırması ve teklifin 7 günlük timelock bekleme süresine taşınması yaklaşık 3 gün sürmüştür. 20 Kasım günü, Safety Module eski durumuna getirilmiş ve temiz bir duruma sıfırlanmıştır.

_**Geçmiş:**_

dYdX Safety Module, dYdX protokolünü desteklemek için kullanılabilecek merkeziyetsiz bir fon havuzuna kaynak sağlamak için tasarlanmış bir staking sözleşmesidir. Kullanıcılar güvenlik havuzunda DYDX stake eder ve stkDYDX (1:1) alır. stkDYDX, DYDX ile aynı oy verme ve teklif verme haklarına sahip bir ERC-20 olarak transfer edilen, token'a dönüştürülmüş bir pozisyondur. Eksi bakiyeye düşme durumunda, kayıpları azaltmak için stake edilen DYDX'leri slash etmek için bir yönetişim oylaması gerekir. DYDX token arzının %2,5'i (25.000.000 DYDX) güvenlik staking havuzunda DYDX stake eden kullanıcılara dağıtılacaktır. Güvenlik staking havuzu hakkında daha fazla bilgiyi [burada](https://dydx.foundation/blog/en/safety-staking) bulabilirsiniz.

[Güvenlik staking havuzu ödülleri](https://docs.dydx.community/dydx-governance/staking-pools/safety-staking-pool) kapsamında, stake edenlere her dönem (28 gün) 383.562 DYDX dağıtılacaktır. Ödüller, stake edenlere her saniye orantılı olarak dağıtılır.

dYdX topluluğu, safety module akıllı sözleşmesinin parametreleri üzerinde "anında ve gayri kabili rücu" kontrol sahibidir. Topluluğun kontrol ettiği parametrelerin tam listesini [burada](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters) bulabilirsiniz.

8 Eylül günü TSİ saat 18.00'de, DYDX token'ları üzerindeki transfer kısıtlaması kaldırılmış ve dYdX Safety Module üzerinde staking fiilen açılmıştır. 50'den fazla farklı adres 1 saate yakın bir süre boyunca yaklaşık 157.000 DYDX stake etmiştir. Bir yazılım hatası konuşlandırma sürecinde bir hataya neden olmuş ve Safety Module'da stake eden adreslere hiçbir stkDYDX verilmemiştir. Bunun sonucunda da her bir stake edenin fonları sözleşmede takılmış ve dYdX ekibi dYdX yönetişim arayüzünde staking'i devre dışı bırakmıştır.

[DIP 1](https://dydx.community/dashboard/proposal/0)'de, Safety Module'un işlevlerinin eski durumuna getirilmesi ve etkilenen adreslerin fonlarını kurtarmalarına ve bunları bir bütün haline getirmek için stake ettikleri token'ların %10'u kadar bir ek tazminat almalarına izin verilmesi önerilmiştir. Topluluk [DIP 1 - Safety Module Restorasyonu ve Stake Edenlerin](https://dydx.community/dashboard/proposal/0) Kurtarılması teklifini desteklemiş olsa da teklif bir Long Timelock oylamasının geçmesi için gereken 100 milyon DYDX karar yeter sayısına ulaşamadığı için başarısız olmuştur. Bunun sonucunda da DeFiance Capital'dan Jacob Goh (jteam0x), kaçırdıkları ödüller ve kendilerine verilen rahatsızlıktan dolayı etkilenen adreslere geri ödeme yapılması ve tazminat verilmesi için [DIP 4 - Safety Module'da Stake Edenlere Geri Ödeme Yapılması ve Tazminat Verilmesi](https://dydx.community/dashboard/proposal/2) teklifini oluşturmuştur. [DIP 4](https://dydx.community/dashboard/proposal/2), kullanıcıların stake ettiği token'lar için kurtarma sözleşmesinin konuşlandırılmasını ve etkilenen adreslere Ödül Hazinesi'nden %10 oranında ek bir tazminat ödenmesini içermektedir. DIP, Short Timelock'ın daha az katı olan yönetişim parametreleri tarafından yönetilmiştir.

Bir DIP'nin teklif yaşam döngüsü DIP'in oluşturulmasına kadar genellikle tutarlıdır. DIP 3 (zincir içi) ve DIP 2 (zincir dışı) arasındaki en büyük fark, DIP 3'ün zincir içi bir oylama ve bir akıllı sözleşmenin konuşlandırılmasını gerektirmesidir. Forum tartışmaları, DRC oluşturma ve DIP taslağının oluşturulması süreci aynı olduğundan, adım adım açıklamamıza zincir içi DIP taslağı için içerik gereksinimleri ile başlıyoruz.. Daha fazla bilgi için lütfen aşağıdaki bağlantıları izleyin:

* dYdX'in yönetişim süreci - [https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle).
* Safety Module Olay Raporu - [https://dydx.foundation/blog/en/outage-1](https://dydx.foundation/blog/en/outage-1).
* Zincir Dışı Forum tartışması **-** [https://commonwealth.im/dydx/proposal/discussion/1743-safety-staking-pool-on-pause](https://commonwealth.im/dydx/proposal/discussion/1743-safety-staking-pool-on-pause).
* Zincir Dışı DRC **-** [https://commonwealth.im/dydx/proposal/discussion/1770-drc-incident-report-of-the-safety-module-outage-proposed-solution](https://commonwealth.im/dydx/proposal/discussion/1770-drc-incident-report-of-the-safety-module-outage-proposed-solution)
* Zincir Dışı DRC Snapshot Anketi **-** [https://snapshot.org/#/dydxgov.eth/proposal/QmbJ5QxHr1pyShKTDaF5DjAr6vxQn8DVxshH2fyWgzDCBn](https://snapshot.org/#/dydxgov.eth/proposal/QmbJ5QxHr1pyShKTDaF5DjAr6vxQn8DVxshH2fyWgzDCBn)
* Github'da teklif edilen DIP **-** [https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md)

### **1. ADIM - Zincir İçi DIP Taslağı**

_**Açıklama:**_

dYdX protokolünde yönetişim mutabakatını etkileyen zincir içi bir DIP taslağında akıllı sözleşme değişikliklerinin uygulanması için atılacak adımlar özetlenmelidir. Topluluğun Snapshot'ta veya daha önce başarısız olmuş bir DIP'te açık bir mutabakat sağlamasının ardından, yeterli teklif verme yetkisine sahip bir topluluk üyesi yeni DIP'yi zincir içinde gönderebilir. Teklif verme yetki eşiği, timelock executor ve diğer yönetişim parametreleri hakkında daha fazla bilgiyi [burada](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters) bulabilirsiniz.

_**DIP 3 başvurusu:**_

Bu örnekte [DIP](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md), Paradigm'den Dan Robinson tarafından yazılmıştır. Teklif zincir içi akıllı sözleşme değişiklikleri içerdiğinden, teklifte belirli akıllı sözleşme uygulamalarına bir bağlantı da yer almıştır.

![https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-3.md](../.gitbook/assets/2-dip3-example-1.png)

SafetyModuleV2.sol konuşlandırma sözleşmesinden Safety klasörüne gezinti yolu teklifin nasıl uygulanacağına dair belirli ayrıntıları içeren README dosyasını gösterir.

![](../.gitbook/assets/2-dip3-example-1a.png)

Teklifin uygulanmasına ilişkin olarak README dosyasında yer alan adımları şurada bulabilirsiniz: [https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety).

![https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](../.gitbook/assets/2-dip3-example-2.png)

![https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](../.gitbook/assets/2-dip3-example-3.png)

![https://github.com/dydxfoundation/governance-contracts/tree/master/contracts/safety](../.gitbook/assets/2-dip3-example-4.png)

#### _Bir Zincir İçi DIP (WIP) taslağı nasıl oluşturulur:_

* DIP'yi oluşturmak için yeni bir cüzdan oluşturun. Konuşlandırma süreci bir çevre değişkeni olarak kurtarma cümlenizi girmenizi gerektirecektir; bu yüzden zincir içi DIP oluşturmak için tek kullanımlık bir cüzdan kullanmanızı öneririz.
* DIP'yi oluşturmak için tek kullanımlık cüzdana yeterli teklif verme yetkisi delege edin. Teklif verme yetkisini [burada](https://dydx.community/dashboard) delege edebilirsiniz. Farklı teklif verme gücü eşikleri aşağıda verilmiştir ve eşikleri [burada](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters) da bulabilirsiniz.
  * Short Timelock: toplam arzın %0,5'i (teklif verme yetkili 5 milyon).
  * Starkware Executor: toplam arzın %0,5'i (teklif verme yetkili 5 milyon).
  * Long Timelock Executor: toplam arzın %2,0'si (teklif verme yetkili 20 milyon).
  * Merkle Pauser Executor: toplam arzın %0,5'i (teklif verme yetkili 5 milyon).
* Bir Alchemy Anahtarı oluşturun. Alchemy Anahtarı sayesinde Ethereum ile etkileşim kurmak ve akıllı sözleşmeyi konuşlandırmak için bir Ethereum Düğümü çalıştırmanıza gerek yoktur. Bir Alchemy Anahtarı oluşturma kılavuzunu [burada](https://docs.alchemy.com/alchemy/introduction/getting-started) bulabilirsiniz.

![https://docs.alchemy.com/alchemy/introduction/getting-started](../.gitbook/assets/2-draft-dip-example-1.png)

Ethereum'u seçin ve "Başla" seçeneğine tıklayın.

![](../.gitbook/assets/2-draft-dip-example-2.png)

Gerekli bilgileri doldurun, Goerli Ağını seçin ve "uygulama oluştur" seçeneğine tıklayın.

<figure><img src="../.gitbook/assets/2-draft-dip-example-3.png" alt=""><figcaption></figcaption></figure>

Hesabınızı oluşturduktan sonra, [buradaki](https://docs.alchemy.com/alchemy/introduction/getting-started) kurulum talimatlarını izleyin.

"4. Oluşturmaya Başla" başlığının altında, "ilk akıllı sözleşmenizi konuşlandırmayı deneyin" seçeneğine tıklayın ve kılavuzu izleyin.

![https://docs.alchemy.com/alchemy/introduction/getting-started](../.gitbook/assets/2-draft-dip-example-4.png)

* Windows komut satırını ve varsayılan Terminal Uygulamasını açın veya iTerm'i indirin: [https://iterm2.com/](https://iterm2.com/).
* Daha önce yapmadıysanız, Node.js ve npm'yi indirin ve kurun: [https://docs.npmjs.com/downloading-and-installing-node-js-and-npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm).
* Hardhat, Ethereum yazılımlarını derlemek ve test etmek için bir geliştirme aracıdır. Daha önce yapmadıysanız, Hardhat'i kurun: [https://hardhat.org/tutorial/setting-up-the-environment.html](https://hardhat.org/tutorial/setting-up-the-environment.html).
* Teklif ettiğiniz akıllı sözleşme uygulamalarınızın taslağını oluşturun.
* IPFS hash'i otomatik olarak oluşturulur ve [buradan](https://github.com/dydxfoundation/dip/tree/master/content/ipfs-dips) edinilebilir. IPFS hash'i, `DIP-[New DIP #]-ipfs-hashes.json` dosya adı altında dYdX Vakfı'nın dizininde olacaktır.

![https://github.com/dydxfoundation/dip/tree/master/content/ipfs-dips](../.gitbook/assets/2-draft-dip-example-5.png)

* Yeni dosyayı (`DIP-[New DIP #]-ipfs-hashes.jso`) seçtikten sonra, encodedHash kullandığınızdan emin olun.

![https://github.com/dydxfoundation/dip/blob/master/content/ipfs-dips/DIP-3-Ipfs-hashes.json](../.gitbook/assets/2-draft-dip-example-6.png)

### **2. ADIM - Zincir içinde bir DIP gönderin**

_**Açıklama:**_

Bir topluluk üyesi teklif edilen akıllı sözleşme uygulamalarının doğru olduğunu ve DIP'nin kesinleştiğini onayladıktan sonra, DIP zincir içinde gönderilebilir. Bir zincir içi DIP oluşturulduğunda, teklif yaklaşık 1 gün (yaklaşık 6.570 blok) sürecek Oylama Bekleme Süresi için "Beklemede" durumuna geçer. Kullanıcı anlık görüntüleri, DYDX bakiyelerini ve delege edilmiş oylama yetkisini hesaplamak için Oylama Bekleme Süresinin ardından kaydedilir. Bunun ardından, teklif "Aktif" duruma geçer ve oylama süresi teklif türüne bağlı olarak 2-10 gün arasında değişir. Bir teklifin uygulanması için, oylama, teklifin türüne bağlı olarak değişen karar yeter sayısını ve minimum oy farkını geçmelidir. DIP karar yeter sayısını ve minimum oy farkını geçer ve oy veren topluluk üyelerinin çoğunluğu DIP lehine oy verirse, teklifin timelock kuyruğuna taşınması için herhangi bir adres kuyruğu çağırabilir. Timelock sözleşmeleri, dYdX topluluğu tarafından oylanan işlemleri kuyruğa koyabilir, iptal edebilir veya uygulamaya koyabilir. Timelock kuyruğunun uzunluğu teklifin türüne bağlı olarak değişir.

_**DIP 3 başvurusu:**_

Paradigm ekibi, `SafetyModuleV2.sol`'un solidity kodunu tamamlamış ve kesinleştirmiştir.

![https://github.com/dydxfoundation/governance-contracts/blob/master/contracts/safety/v2/SafetyModuleV2.sol](../.gitbook/assets/2-draft-dip-example-7.png)

Paradigm ekibi, güncellemeleri hem yerel hem de çatallanmış bir ana ağ ortamında simüle etmiştir. Bunun ardından, yönetişim teklifinin ana ağda uygulamaya koyulmasının ardından tüm işlevlerin restore edilmesini sağlamak için test paketi çalıştırılmıştır.

Paradigm ekibi, aşağıdaki betikleri çalıştırarak akıllı sözleşme güncellemelerini konuşlandırmıştır.

**Safety Module Kurtarma Konuşlandırması**

`export ALCHEMY_KEY=<... >`

`export MNEMONIC=<... >`

`npx hardhat --network mainnet deploy:safety-module-recovery`\
`--dydx-token-address 0x92D6C1e31e14520e676a687F0a93788B716BEff5`\
`--short-timelock-address 0x64c7d40c07EFAbec2AafdC243bF59eaF2195c6dc`\
`--rewards-treasury-address 0x639192D54431F8c816368D3FB4107Bc168d0E871`

**Yönetişim Teklifi: Safety Module Düzeltmesi**

`export ALCHEMY_KEY=<... >`

`export MNEMONIC=<... >`

`npx hardhat --network mainnet deploy:safety-module-fix-proposal`\
`--proposal-ipfs-hash-hex 0x...`\
`--governor-address 0x7E9B1672616FF6D6629Ef2879419aaE79A9018D2`\
`--long-timelock-address 0xEcaE9BF44A21d00E2350a42127A377Bf5856d84B`\
`--safety-module-address 0x65f7BA4Ec257AF7c55fd5854E5f6356bBd0fb8EC`\
`--safety-module-proxy-admin-address 0x6aaD0BCfbD91963Cf2c8FB042091fd411FB05b3C`\
`--safety-module-new-impl-address 0x...`

**Yönetişim Teklifi: Safety Module Tazminatı**

`export ALCHEMY_KEY=<... >`

`export MNEMONIC=<... >`

`npx hardhat --network mainnet deploy:safety-module-compensation-proposal`\
`--proposal-ipfs-hash-hex 0x...`\
`--dydx-token-address 0x92D6C1e31e14520e676a687F0a93788B716BEff5`\
`--governor-address 0x7E9B1672616FF6D6629Ef2879419aaE79A9018D2`\
`--short-timelock-address 0x64c7d40c07EFAbec2AafdC243bF59eaF2195c6dc`\
`--rewards-treasury-address 0x639192D54431F8c816368D3FB4107Bc168d0E871`\
`--safety-module-recovery-address 0x...`

Aynı anda DIP, [https://dydx.community/dashboard](https://dydx.community/dashboard) üzerinde yayınlanmıştır.

![https://dydx.community/dashboard](../.gitbook/assets/2-draft-dip-example-8.png)

![https://dydx.community/dashboard](../.gitbook/assets/2-draft-dip-example-9.png)

dYdX Yönetişim sözleşmesi [0x7e9b1672616ff6d629ef2879419aae79ae79a9018d2'dir: https://etherscan.io/txs?a=0x7e9b1672616ff6629ef2879419aae79ae79a9018d2\&p=10](https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aae79a9018d2\&p=10).

DIP konuşlandırması Etherscan üzerinde doğrulanabilir: [https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad).

DIP, 1 Kasım 2021 tarihinde 13.532.376 numaralı blokta oluşturulmuştur. Sıradaki 6.570 blok boyunca DIP durumu "Beklemede" olur.

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/2-draft-dip-example-10.png)

DIP 13.538.946 numaralı blokta "Aktif" duruma geçtiğinde DYDX sahipleri DIP'yi oylamıştır.

İlk oy 2 Kasım 2021 tarihinde TSİ saat 08.51.22'de (13538959 numaralı blokta), DIP'nin zincir içinde oluşturulduğu andan 6583 blok sonra verilmiştir.

![https://etherscan.io/tx/0xc3d0ace92be4ac3da40dc17f45a573d4dbd83d31f7a95733071de883ded67a4f](../.gitbook/assets/2-draft-dip-example-11.png)

Long Timelock kapsamındaki 10 günlük oylama süresi sonrasında, herhangi bir topluluk üyesi kuyruğu çağırabilir ve teklifi 7 günlük timelock bekleme süresine taşıyabilir. DIP 3 söz konusu olduğunda, bir topluluk üyesinin kuyruğu çağırması neredeyse 3 gün sürmüştür.

![https://etherscan.io/tx/0x3402372a549d2270a6b5d4f84884ae2bfec6922fc808703b47d53b27d288c81](../.gitbook/assets/2-draft-dip-example-12.png)

7 günlük timelock bekleme süresi dolduğunda DIP zincir üzerinde uygulamaya koyulmuştur.

![https://etherscan.io/tx/0xfd332147899fd3ef1db62f262ffae92bbd7d18a5ed4e142eb0407a173dbf0453](../.gitbook/assets/2-draft-dip-example-13.png)

DIP'nin zincir üzerinde uygulamaya koyulduğu anda [https://dydx.community/dashboard/provention/3](https://dydx.community/dashboard/proposal/3) adresindeki DIP durumu "Uygulamaya Koyuldu" şeklinde güncellenmiştir.

![](../.gitbook/assets/2-draft-dip-example-14.png)

(1) Tekliflerin timelock bekleme süresinden hemen sonra başlayan 7 günlük Uygulama Mühleti sona ermeden uygulamaya koyulması ve (2) teklifi veren adresin DIP uygulamaya koyulana kadar ilgili timelock sözleşmesi tarafından gerekli kılınan minimum teklif verme yetkisini (teklif verme yetkili 5 milyon veya 20 milyon) muhafaza etmesi gerektiğini unutmayın.

#### _Bir DIP Zincir İçinde Nasıl Gönderilir:_

* DIP'yi oluşturmak için yeterli teklif verme yetkisine sahip olduğunuzdan emin olun. Daha fazla bilgiyi [DIP Oluşturma](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle) başlığı altında bulabilirsiniz.
  * Short Timelock Executor: toplam arzın %0,5'i (teklif verme yetkili 5 milyon).
  * Starkware Executor: toplam arzın %0,5'i (teklif verme yetkili 5 milyon).
  * Long Timelock Executor: toplam arzın %2,0'si (teklif verme yetkili 20 milyon).
  * Merkle Pauser Executor: toplam arzın %0,5'i (teklif verme yetkili 5 milyon).
* Gas ücretini ödemek için cüzdanda ETH olduğundan emin olun.
* Ethereum Mainnet ağı için Alchemy üzerinde bir uygulama oluşturun.

![https://dashboard.alchemyapi.io/](../.gitbook/assets/2-draft-dip-example-15.png)

* Uygulama oluşturulduktan sonra, Alchemy Anahtarınızı (7LOaQtguSm2kSEcFXQH88B) almak için "Anahtarı Görüntüle" seçeneğine tıklayın: [https://eth-mainnet.alchemyapi.io/v2/7LOaQtguSm2kSEcFXQH88B-EN\_K7t\_ul](https://eth-mainnet.alchemyapi.io/v2/7LOaQtguSm2kSEcFXQH88B-EN\_K7t\_ul).

![https://dashboard.alchemyapi.io/apps/xogmjmlex8tlmr95](../.gitbook/assets/2-draft-dip-example-16.png)

* Node.js ve npm'yi indirin ve kurun: [https://docs.npmjs.com/downloading-and-installing-node-js-and-npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm).
* Hardhat'i kurun: [https://hardhat.org/tutorial/setting-up-the-environment.html](https://hardhat.org/tutorial/setting-up-the-environment.html).
* Taslağını hazırladığınız komut dizisini çalıştırın.
* Teklifin zincir içinde oluşturulduğunu doğrulamak için Yönetişim Sözleşmesini kontrol edin: [https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aae79a9018d2\&p=10](https://etherscan.io/txs?a=0x7e9b1672616ff6d6629ef2879419aae79a9018d2\&p=10).
* Teklifi gönderen adreste, ilgili timelock sözleşmesi tarafından gerekli kılınan minimum teklif verme yetkisini teklif uygulamaya koyulana kadar muhafaza etmeniz gerekir.

#### _Bir DIP için nasıl oy verilir:_

* Gas ücretini ödemek için cüzdanda ETH olduğundan emin olun.
* Aktif bir DIP için [https://dydx.community/dashboard](https://dydx.community/dashboard) adresinde DIP'yi seçerek oy verebilirsiniz.

![](../.gitbook/assets/2-draft-dip-example-17.png)

Oylama süresi teklifin türüne bağlıdır. Daha fazla bilgiyi [DIP Oluşturma](https://docs.dydx.community/dydx-governance/voting-and-governance/dip-proposal-lifecycle) başlığı altında bulabilirsiniz.

* Short Timelock Executor: 4 gün.
* Starkware Executor: 4 gün.
* Long Timelock Executor: 10 gün.
* Merkle Pauser Executor: 2 gün.

#### _Bir Teklif Nasıl Kuyruğa Koyulur:_

Başarılı bir teklif, Timelock Bekleme Süresini başlatmak için kuyruğa koyulabilir.

* Eth içeren uyumlu bir cüzdan kullandığınızdan emin olun.
* Etherscan üzerinde "Sözleşme" Sekmesine gidin ve "Sözleşme Yaz" seçeneğine tıklayın. Yönetişim Sözleşmesini [burada](https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract) bulabilirsiniz.

![https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract](../.gitbook/assets/2-draft-dip-example-queue-1.png)

* Kuyruk seçeneğine tıklayın ve "proposalId" bilgisini girip gönderin.

![](../.gitbook/assets/2-draft-dip-example-queue-2.png)

DIP oluşturulduğunda, "proposalId" bilgisini Etherscan üzerinde bulabilirsiniz: [https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad).

* "Daha fazlasını görmek için tıklayın" seçeneğine tıklayın.

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/2-draft-dip-example-queue-3.png)

* "Girdi Verilerinin Kodunu Çöz" seçeneğine tıklayın.

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/2-draft-dip-example-queue-4.png)

![https://etherscan.io/tx/0x5f2472e7dfcbf50628d29c94f97a072f3c19177f66cde4cca9f376c7934af5ad](../.gitbook/assets/2-draft-dip-example-queue-5.png)

#### _Bir Teklif Nasıl Uygulamaya Koyulur:_

Timelock Bekleme Süresi dolduğunda, başarılı bir teklif uygulamaya koyulabilir.

* Etherscan üzerinde "Sözleşme" Sekmesine gidin ve "Sözleşme Yaz" seçeneğine tıklayın. Yönetişim Sözleşmesini [burada](https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract) bulabilirsiniz.

![https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract](../.gitbook/assets/2-draft-dip-example-execute-1.png)

* "Uygulamaya koy" seçeneğine tıklayın ve "proposalId" bilgisini girip gönderin.

![https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2#writeContract](../.gitbook/assets/2-draft-dip-example-execute-2.png)

* "proposalId" bilgisini bulmak için yukarıdaki adımları (_Bir Teklif Nasıl Kuyruğa Koyulur_ başlığı altındaki) izleyin.
* "payableAmount (ether)" altında "0" girin.

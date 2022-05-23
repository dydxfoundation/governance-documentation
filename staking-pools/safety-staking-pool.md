---
description: Güvenlik Staking Havuzuna genel bir bakış
---

# Safety Module

İlk baştaki token arzının (`25.000.000 DYDX`) `%2,50'si` sistemi desteklemek için bir Güvenlik havuzunda DYDX stake eden kullanıcılara dağıtılacaktır.

**Hedefler**

* Ödeme aczi veya protokolle ilgili diğer sorunlar yaşanması durumunda kullanılacak merkezsizleştirilmiş bir fona kaynak sağlamak.
* DYDX sahiplerini doğru bir şekilde yönetişime teşvik etmek: DYDX sahipleri temel destekleyiciler olarak sulandırıcı olayların riskini üstlenir ve sistemde riskleri yönetenler olarak hareket ederler.

Safety Module'da stake edilen DYDX teklif verme ve oy kullanma haklarının yanı sıra delegasyon imkânını da sürdürür.

[**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety) sayfasında staking yapmaya başlayın****

## Genel bakış

Kullanıcı güvenliği ve koruması Protokol'ün kullanıma sunulmasından bu yana kilit bir odak noktası olmuştur. Bu nedenle, Protokol'ün kullanıcıları için ek bir güvenlik ağı oluşturmak amacıyla, güvenlik havuzunda DYDX stake eden kullanıcılara DYDX dağıtılacaktır. Stake edenler havuzdaki toplam DYDX içindeki paylarıyla orantılı olarak sürekli DYDX alacaktır.

Güvenlik havuzu, 8 Eylül 2021 günü saat 18.00'de (TSİ) DYDX transfer edilebilir hale geldiğinde kullanıma açılacaktır.

## Fon Çekme

Stake edenler dönemin sona ermesinden sonra fon çekebilmek için dönemin sona ermesinden en az `14 gün` **(Karartma Süresi)** önce fon çekme talebinde bulunmalıdır. Stake edenler fon çekme talebinde bulunmazsa, stake ettikleri DYDX'ler bir sonraki döneme devredilir.

## Riskler

Stake edilen DYDX'ler bir eksi bakiyeye düşme olayı yaşanması durumunda slashing sürecine maruz kalır. Slashing DYDX yönetişiminin takdirine bağlı olarak uygulanır ve yürürlüğe konması için bir yönetişim oylaması gerektirir.

Tıpkı tüm diğer DeFi protokollerindeki katılımcılar gibi, Safety Module üzerinde stake edenler de dayanak akıllı sözleşme kodunda bir güvenlik açığı olması durumunda akıllı sözleşme riskine maruz kalır. Tüm DYDX ve yönetişim akıllı sözleşmeleri denetlenmiş ve titizlikle test edilmiştir.

## Eksi Bakiyeye Düşme Olayları

Bir Eksi Bakiyeye Düşme Olayının meydana gelmesinin yorumlanması bir dYdX yönetişim oylamasına tabidir ancak şunları içerebilir:

* Borsanın Ödeme Kabiliyeti (örneğin, borsanın kâr sağlamayan likidasyonlar nedeniyle eksik teminatlandırılmış bir hale gelmesi)
* Akıllı sözleşme saldırıları
* dYdX yönetişiminin eksi bakiyeye düşme sonucunda yaşandığını düşündüğü diğer olaylar

Bir Eksi Bakiyeye Düşme Olayında, token sahiplerinin bakiyeleri slashing sürecine tabi tutulabilir ve başka bir adrese veya sözleşmeye transfer edilebilir (vaka bazında dYdX yönetişimi tarafından belirlenir). dYdX yönetişimi, stake edilen token'ları slash etmek için bir short timelock teklifini oylamadan geçirmelidir. Stake edilmiş DYDX token'larını slash etme konusunda bir yönetişim oylaması sonrasında, slash edilen DYDX'ler ortaya çıkan açığı kapatmak için ihtiyaç duyulan varlıklara karşılık piyasada açık artırmaya çıkarılabilir.

## SSS

### Staking ödüllerini nasıl kazanabilirim?

Stake edenler diledikleri zaman güvenlik staking havuzuna DYDX yatırabilir ve hemen ödül kazanmaya başlayabilirler. DYDX ödülleri her bir stake edenin toplam havuzdaki payına göre saniye bazında sürekli olarak kazanılır. Ödüller istendiği zaman talep edilebilir ve çekilebilir.

Aktif fonlar aktif kaldıkları süre boyunca ödül kazanır. Bu da bazı fonların çekilmesi talep edildikten sonra o fonların dönem sonuna kadar ödül kazanmaya devam edeceği anlamına gelir. Bu durum, [Likidite staking havuzundan](https://docs.dydx.community/dydx-governance/staking-pools/liquidity-staking-pool) aşağıdaki örnekte gösterilmektedir:

![](<.. /.gitbook/assets/image (59).png>)

Yukarıdaki senaryoda, kullanıcı **Zaman0'dan** **Zaman2**'ye kadar olan süre için ödül kazanır ve ödül de o dönemde stake edilen toplam bakiyeye göre değişir. Kullanıcı bakiyesinin yalnızca bir kısmını çekmeyi talep ederse geriye kalan bakiye **Zaman2'nin** ötesinde de ödül kazanmaya devam eder.

### Güvenlik Havuzuna nasıl DYDX yatırabilir ve stake edebilirim?

Güvenlik Havuzunda DYDX stake etmek için şu adımları izleyin:

* [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety) adresine gidin****
* "**Stake Et**" seçeneğine tıklayın
* İlk yatırma işleminizde DYDX'i etkinleştirmeniz gerekir. Bunu sadece bir kez yapmanız ve gas ücretlerini de yalnızca bir kez ödemeniz gerekecektir.
* Havuzda stake etmek istediğiniz DYDX miktarını girin.
* "**Fonları Stake Et**" seçeneğine tıklayın. Fonları stake etmek ve staking'den çıkarmak için gas ücretleri ödemeniz gerekecektir.

Stake edilen fonlar artık aktiftir ve hemen ödül kazanmaya başlar.

Doğrudan akıllı sözleşme üzerinde fon yatırmak ve stake etmek için, kullanıcılar \'stake\' [fonksiyonunu](https://github.com/dydxprotocol/governance-private/blob/2645927b44f517f51c84e35a00a1ee810300c13f/contracts/liquidity/v1/impl/LS1Staking.sol#L59) çağırır. Kullanıcılar ayrıca \'stakeFor\' [fonksiyonunu](https://github.com/dydxprotocol/governance-private/blob/2645927b44f517f51c84e35a00a1ee810300c13f/contracts/liquidity/v1/impl/LS1Staking.sol#L64) çağırarak başka bir adres adına da fon yatırabilir ve stake edebilirler.

### stkDYDX nedir?

Protokolün güvenliğine katkıda bulunmak ve teşvik almak için, DYDX sahipleri token'larını Safety Module'a yatırır. Buna karşılık da bir ERC-20 olarak çekilebilen veya transfer edilebilen token'a dönüştürülmüş bir pozisyon (**stkDYDX**) alırlar. **stkDYDX** token'ı dYdX yönetişimi üzerinde DYDX ile aynı teklif verme ve oy verme haklarına sahiptir.

### Karartma süresi nedir?

Karartma süresi kullanıcıların stake edilen fonlarını çekmeyi talep edemediği bir zaman dilimidir. Havuzdaki fonların kullanılabilirliği için öngörülebilirlik ve düzenli bir tempo sağlamak amacıyla çekim işlemleri için bir dönem takvimi uygulanmaktadır. Stake eden bir kişi, fonlarını o dönem sona erdikten sonra çekebilmek için karartma süresi başlamadan önce fonlarını staking'den çıkarma talebinde bulunmalıdır. Stake eden bir kişi eğer çekim talebinde bulunmazsa, kendisinin stake edilen fonları bir sonraki döneme devredilir.

Güvenlik Havuzu için önerilen karartma süresi `14 gündür`.

### Stake edilen bakiyelerin muhasebesi nasıl yapılır?

Stake edilen bir bakiye şu iki durumdan birinde olur:

* **Aktif**: Borç almak için kullanılabilir; staking ödülleri kazanır; stake eden kişi tarafından çekilemez.
* **Aktif Değil**: Borç almak için kullanılamaz; ödül kazanmaz; stake eden kişi tarafından çekilebilir.

Stake eden bir kişi hem aktif hem de aktif olmayan bakiyelere sahip olabilir. Fonlar aşağıdaki örnekte gösterilen şekilde dönem bazında hesaplanır:

![](<.. /.gitbook/assets/image (36).png>)

Aşağıdaki işlemler stake edilen bakiyeleri aşağıda belirtilen şekilde etkiler:

* **Fon Yatırma**: Aktif bakiyeyi artırır.
* **Fon Çekme** **Talebi**: Mevcut dönemin sonunda, bazı aktif fonları aktif olmayan bir konuma taşır.
* **Fon Çekme**: Aktif olmayan bakiyeyi azaltır.
* **Transfer**: Bazı aktif fonları stake eden başka bir kişiye aktarır.

Belirli bir dönemin sonunda bir bakiyenin değişmesinin planlanmış olabileceğini kodlamak için her bakiyeyi üç alandan oluşan bir yapı halinde saklarız: currentEpoch, currentEpochBalance ve nextEpochBalance.

### Stake havuzundan nasıl fon çekebilirim? Ne kadar sürer?

Havuzdaki fonların kullanılabilirliği için öngörülebilirlik ve düzenli bir tempo sağlamak amacıyla çekim işlemleri için bir dönem takvimi uygulanmaktadır. Stake eden bir kişi, fonlarını o dönem sona erdikten sonra çekebilmek için bir dönemin sona ermesinden en az `14 gün` önce fon çekme talebinde bulunmalıdır. Stake edenler fon çekme talebinde bulunmazsa, stake ettikleri DYDX'ler bir sonraki döneme devredilir.

Fonlarını çekebilmek amacıyla, kullanıcılar bir sonraki dönemde fon çekme talebinde bulunmak için \`requestWithdrawal\` fonksiyonunu çağırır. Kullanıcı fonları stake edilmeye devam edecektir ve mevcut dönem boyunca çekilemez. Bir sonraki dönemden başlayarak, fonlar "aktif değil" olacak ve çekilebilecektir.

Bir sonraki dönemde, kullanıcılar aktif olmayan fonlarını belirli bir adrese çekmek için \`withdrawStake\` fonksiyonunu çağırır. Kullanıcılar çekmek istedikleri aktif olmayan fon miktarını seçebilir veya aktif olmayan tüm fonlarını çekmek için \`withdrawMaxStake\` fonksiyonunu çağırabilir. \`withdrawMaxStake\` fonksiyonunu çağırmanın, eth\_call aracılığıyla maksimum değeri sorgulayıp \`withdrawStake()\` fonksiyonunu çağırmaktan daha fazla gas ücreti ödemenize neden olacağını unutmayın.

Likidite Havuzundan DYDX çekmek için şu adımları izleyin:

* [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety) adresine gidin****
* "**Talep Et**" seçeneğine tıklayın ve havuzdan çekmeyi talep etmek istediğiniz DYDX miktarını girin.
* "**Fon çekmeyi talep et**" seçeneğine tıklayın. Fon çekmek için gas ücretleri ödemeniz gerekecektir.
* Mevcut dönemin sona ermesinden en az 14 gün önce DYDX çekme talebinde bulunan stake edenler bir sonraki dönemin başında DYDX'lerini çekebilirler.

### Güvenlik staking havuzunda stake edenler için riskler nelerdir? Eksi Bakiyeye Düşme Olayı durumunda ne olur?

Stake eden bir kişinin Güvenlik Havuzu'nda DYDX kilitleme kararı bu kişiyi bir eksi bakiyeye düşme riski ile karşı karşıya bırakır ve bu da DYDX yönetişiminin takdirine bağlı olarak stake edilen DYDX fonlarının slashing sürecine tabi tutulmasına yol açabilir.

Sözleşmedeki aktif veya aktif olmayan tüm fonlar slash edilebilir. Sözleşme kapsamında, slashing süreci DYDX ve stkDYDX arasındaki kurun güncellenmesi yoluyla gerçekleştirilir. Bu da slashing süreci sırasında DYDX ve stkDYDX arasındaki kurun ilk baştaki 1:1 değerinden sapacağı anlamına gelir. Staking ödüllerinin kazanılmasının slashing sürecinden etkilenmediğini unutmayın.

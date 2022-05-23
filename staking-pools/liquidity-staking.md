---
description: Likidite Staking Havuzlarına genel bakış.
---

# Likidite Staking Havuzu

Bir likidite staking havuzunda USDC stake eden kullanıcılara %2,5 \(`25.000.000 DYDX`\) dağıtılacaktır.

### Hedefler

* dYdX likidite ağının etkilerini artırmak

## Genel bakış

Likidite, özellikle de doğru kullanıldığında başarılı bir borsanın temel bileşenlerinden biridir. Likidite ağının etkilerini artırmak ve profesyonel piyasa yapıcıları teşvik etmek için likidite staking havuzunda USDC stake eden kullanıcılara DYDX dağıtılacaktır. Bilinen ve onaylanmış piyasa yapıcılar, Protokol'de piyasalar oluşturmak için stake edilen USDC'leri kullanarak piyasalarda mevcut olan likiditeyi artıracaktır. Piyasa yapıcılar Protokol'den USDC çekemeyecek ve USDC'leri sadece Protokol'de kullanmaları gerekecektir. Bununla birlikte, bir piyasa yapıcı fon kaybederse \(kâr sağlamayan alım satım işlemleri sonucunda\) ve likidite staking havuzunu besleyemezse stake eden USDC'lerin bir kısmı kaybedilebilir. Stake edenler, stake eden her bir kişinin havuzdaki toplam USDC miktarı içindeki payıyla orantılı olarak sürekli dağıtılacak bir şekilde DYDX alacaktır. Stake eden bir kişi, o dönem sona erdikten sonra **USDC**'lerini çekebilmek için dönem sona ermeden en az `14 gün` önce USDC'lerini stakingden çıkarma talebinde bulunmalıdır. Stake edenler fon çekme talebinde bulunmazsa, stake ettikleri USDC'ler bir sonraki döneme devredilir.

## Onaylanmış Borç Alanlar

Likidite Staking Havuzu sözleşmesi iki taraflı, eksik teminatlandırılmış bir borç verme sistemi şeklinde çalışır.

Çekilebilecek miktar, bir borç alanın tahsis yüzdesine ve havuzda stake edilen kullanılabilir fonların toplamına bağlıdır. Hem tahsis yüzdesi hem de kullanılabilir fonlar `LS1EpochSchedule` tarafından belirlenen önceden tanımlanmış zamanlarda değişebilir. Borç alınan fonlar sadece dYdX'in Katman 2 borsasında kullanılabilir. Bu zorunluluk, L2 borsa sözleşmesi \(`StarkPerpetual`\) ile etkileşime giren `TrustedBorrowerL2Proxy` sözleşmesi aracılığıyla gözetilir.

Onaylanan ilk likidite sağlayıcılar arasında açılış tarihinden bu yana Protokol'de aktif olarak piyasa yapan `Wintermute`, `Sixtant`, `Kronos`, `Amber` ve `MGNR` yer almaktadır.

| Önceden Onaylanmış Borç Alanlar | İlk Tahsis Yüzdesi | Likidite Sağlayıcılar hakkındaki bilgiler |
| :--- | :--- | :--- |
| Wintermute | `%X` TBD | [https://dydx.exchange/blog/ama-recap-wintermute](https://dydx.exchange/blog/ama-recap-wintermute) |
| Sixtant | %Y TBD | [https://dydx.exchange/blog/ama-recap-sixtant](https://dydx.exchange/blog/ama-recap-sixtant) |
| Kronos \(Wootrade\) | %Z TBD | [https://dydx.exchange/blog/ama-recap-wootrade](https://dydx.exchange/blog/ama-recap-wootrade) |
| Amber | %Z TBD |  |
| MGNR | %Z TBD |  |

Kullanıcılar fonları staking'den çıkarma talebinde bulunduğunda, bir borç alanın bir sonraki dönem için tahsis edilen bakiyesi an itibarıyla borç almış olduğu miktarın altına düşebilir. Bu durumda, borç alan kişi dönem sona ermeden önce borç aldığı ve kendisine tahsis edilen bakiyeler arasındaki farkı ödemekle yükümlüdür. Bir borç alanın borç bakiyesi bir sonraki dönemin başında kendisine tahsis edilenden büyükse, o dönemin başlangıcından önce farkı iade etmesi beklenir ve bunu yapacağına güvenilir.

Borç alanlar fon borç alırken ve geri ödeme yaparken net borç bakiyeleri kaydedilir. Tüm borç alanların toplam borç bakiyesi de izlenir. Sözleşme tarafından tutulan kalan bakiyeye ise borç alınmamış bakiye denir.

Sözleşmeyi bir bütün olarak düşünürken aşağıdaki denklem her zaman doğrudur:

toplam aktif + toplam aktif olmayan = toplam borç alınan + toplam borç alınmamış

### Yönetişim

dYdX Yönetişimi şunlardan sorumludur:

* Mevcut borç alanları kapsamlı bir incelemeye tabi tutmak
* Staking havuzuna yeni borç alanlar eklemek
* Onaylanmış borç alanların borç alınmış fon tahsislerini değiştirmek
   * Belirli borç alanların tahsislerini değiştirmek için \`setBorrowerAllocations\` ve \`setBorrowingRestriction\` fonksiyonları çağrılır. Bu fonksiyonlar borç alanlar eklemek ve borç alanları kaldırmak için kullanılabilir. Artışlar bir sonraki dönemde yürürlüğe girer ancak düşüşler borç almayı hemen kısıtlar. Bu fonksiyonlar karartma süresi boyunca çağrılamaz.
* Dönem uzunluğu ve karartma süresi sözleşme oluşturulduğunda belirlenir ancak dYdX yönetişimi tarafından değiştirilebilir

### Stake Edilen Bakiyelerin Muhasebesi

Stake edilen bir bakiye şu iki durumdan birinde olur:

* Aktif: Borç almak için kullanılabilir; staking ödülleri kazanır; stake eden kişi tarafından çekilemez.
* Aktif Değil: Borç almak için kullanılamaz; ödül kazanmaz; stake eden kişi tarafından çekilebilir.

Stake eden bir kişi, hem aktif hem de aktif olmayan bakiyelere sahip olabilir. Fonlar aşağıdaki örnekte gösterilen şekilde dönem bazında hesaplanır:

Aşağıdaki işlemler stake edilen bakiyeleri belirtilen şekilde etkiler:

* Fon Yatırma: Aktif bakiyeyi artırır.
* Fon Çekme Talebi: Mevcut dönemin sonunda, bazı aktif fonları aktif olmayan bir konuma taşır.
* Fon Çekme: Aktif olmayan bakiyeyi azaltır.
* Transfer: Bazı aktif fonları stake eden başka bir kişiye aktarır.

Belirli bir dönemin sonunda bir bakiyenin değişmesinin planlanmış olabileceğini kodlamak için her bakiyeyi üç alandan oluşan bir yapı halinde saklarız: currentEpoch, currentEpochBalance ve nextEpochBalance. Aktif olmayan kullanıcı bakiyeleri de shortfallCounter alanını kullanır.

## SSS

### Staking ödüllerini nasıl kazanabilirim?

Stake edenler diledikleri zaman likidite staking havuzuna USDC yatırabilir ve hemen ödül kazanmaya başlayabilir. DYDX ödülleri, her bir stake eden kişinin toplam havuzdaki payına göre sürekli olarak kazanılır. Ödüller istendiği zaman alınabilir ve çekilebilir.

### Likidite Havuzuna nasıl USDC yatırabilir ve stake edebilirim?

Kullanıcılar fon yatırmak ve stake etmek için \'stake\' [fonksiyonunu](https://github.com/dydxprotocol/governance-private/blob/2645927b44f517f51c84e35a00a1ee810300c13f/contracts/liquidity/v1/impl/LS1Staking.sol#L59) çağırır. Kullanıcılar ayrıca \'stakeFor\' [fonksiyonunu](https://github.com/dydxprotocol/governance-private/blob/2645927b44f517f51c84e35a00a1ee810300c13f/contracts/liquidity/v1/impl/LS1Staking.sol#L64) çağırarak başka bir adres adına da fon yatırabilir ve stake edebilirler.

Likidite Havuzunda USDC stake etmek için aşağıdaki adımları izleyin:

* "Stake Et" seçeneğine tıklayın
* İlk yatırma işleminizde USDC'yi etkinleştirmeniz gerekir. Bunu sadece bir kez yapmanız gerekecektir.
* Havuzda stake etmek istediğiniz USDC miktarını girin
* "Fonları Stake Et" seçeneğine tıklayın. Fonları stake etmek ve staking'den çıkarmak için gas ücretleri ödemeniz gerekecektir

![](https://lh4.googleusercontent.com/caSDz783Gi-asRNYP8Gm8L5qv_yAuJZwEmUAfl8I1MfHecIF2In10IQCqZBCIpxeXl90eT28GGLbZyts8-x9U5w4Y6LBC4kyehMEalsZu_-aI11S6V7nwPrwtcc75m2M8847jFvv)

Stake edilen fonlar aktiftir ve hemen ödül kazanmaya başlar.

### Ödül Muhasebesi

Aktif fonlar, aktif kaldıkları süre boyunca ödül kazanır. Bu da bazı fonların çekilmesi talep edildikten sonra o fonların dönem sonuna kadar ödül kazanmaya devam edeceği anlamına gelir. Örneğin:

Yukarıdaki senaryoda, kullanıcı t\_0'dan t\_2'ye kadar olan süre için ödül kazanır ve ödül de o dönemde stake edilen toplam bakiyeye göre değişir. Kullanıcı bakiyesinin yalnızca bir kısmını çekmeyi talep ederse, geriye kalan bakiye t\_2'nin ötesinde de ödül kazanmaya devam eder.

### Karartma Süresi nedir?

Karartma süresi, kullanıcıların stake edilen fonlarını çekmeyi talep edemediği bir zaman dilimidir. \'requestWithdrawal\' fonksiyonu, ilk başta bir dönemin son 14 günü olarak yapılandırılan karartma süresi boyunca çağrılamaz. Yeni dönemler 28 günde bir başlar. Diğer bir deyişle, kullanıcılar belirli bir dönemin sona ermesinden 7 gün öncesine kadar bir sonraki dönemde fon çekmeyi talep edebilir.

### Stake havuzundan nasıl fon çekebilirim? Ne kadar sürer?

Havuzdaki fonların kullanılabilirliği için öngörülebilirlik ve düzenli bir tempo sağlamak amacıyla çekim işlemleri için bir dönem takvimi uygulanmaktadır. Stake eden bir kişi, fonlarını o dönem sona erdikten sonra çekebilmek için bir dönemin sona ermesinden en az 14 gün önce fonları staking'den çıkarma talebinde bulunmalıdır. Stake edenler hiçbir fon çekme talebinde bulunmazsa, stake ettikleri USDC'ler bir sonraki döneme devredilir

Fonlarını çekebilmek amacıyla, kullanıcılar bir sonraki dönemde fon çekme talebinde bulunmak için \`requestWithdrawal\` [fonksiyonunu](https://github.com/dydxprotocol/governance-private/blob/master/contracts/liquidity/v1/impl/LS1Staking.sol#L73-L83) çağırır. Kullanıcı fonları stake edilmeye devam edecektir ve mevcut dönem boyunca çekilemez. Bir sonraki dönemden başlayarak, fonlar "aktif değil" olacak ve çekilebilecektir.

Bir sonraki dönemde, kullanıcılar aktif olmayan fonlarını belirli bir adrese çekmek için \`[withdrawStake](https://github.com/dydxprotocol/governance-private/blob/master/contracts/liquidity/v1/impl/LS1Staking.sol#L91)\` fonksiyonunu çağırır. Kullanıcılar çekmek istedikleri aktif olmayan fon miktarını seçebilir veya aktif olmayan tüm fonlarını çekmek için \`withdrawMaxStake\` fonksiyonunu çağırabilir. \`withdrawMaxStake\` fonksiyonunu çağırmak, eth\_call aracılığıyla maksimum değeri sorgulayıp \`withdrawStake\()\` fonksiyonunu çağırmaktan daha fazla gas ücreti ödemenize neden olur.

### Likidite staking havuzunda stake etmenin riskleri nelerdir? Borç alan bir kişi borcunu geri ödeyemezse ne olur?

Teminatlandırılmamış borçlar, borç alan kişi tarafından karşılanması gereken çok daha yüksek bir güven standardı içerir. Likidite sağlayıcılar stake edilen USDC'leri Protokol'den çekemez ve bunları sadece Protokol'de kullanmaları gerekir. Bununla birlikte, bir likidite sağlayıcısı alım satım işlemlerinde fon kaybederse, stake edilen USDC'lerini kaybedebilir ve borç tahsisini dış finansman kaynakları aracılığıyla yenileyemeyebilir.

Bu durumda, borç alanın fon çekme talebinde bulunulan fonları geri ödemekte gecikmesi durumunda eksi bakiyeye düşmesi halinde aktif olmayan fonlara kayıplar için orantılı olarak el koyulabilir. Teminatlandırılmamış bir borçta temerrüde düşmesi durumunda, kabahatli bir borç alanın itibarı önemli ölçüde zedelenir.

Sözleşmenin ödeme kabiliyeti:

Herhangi bir zamanda, sözleşme stake edilen ve borç alınan bakiyeler arasındaki ilişkiye bağlı olarak aşağıdaki durumlardan birinde olacaktır:

| ![](https://lh3.googleusercontent.com/nTJuAC4WSmhOiAGkM6r-YWzy6z2MIHQnydr8U0n-TReAh_gfqD6ZyalxQpYv9RNBsJzrlw78QB_wp9utqBc-PQZipwzWpxDifD1_zEtyVBhYXRl_f8V-iDMwLBO70LQsftDlXrsr) | ![](https://lh3.googleusercontent.com/x_Yev8ZJrYYm8FTDSdoj0jDXEBY_b9xOC69lpQudQdoALQ_tuQFEbFc5hAU6TbpGNCB6J2BsjMwHb59GrCqR52747j45jSC_BmyzyiY72gTRk4oamv35gO8PPZalA43COZF1pgtP) |
| :--- | :--- |
| ![](https://lh6.googleusercontent.com/wX37DQoW9oR4OhJzb4hc5ZxPE1X05OPfyETbUv7WTY0b__WH2PydjJoBuQIREHgeWL18GDn7E1ORgGmcre0R6iYPmwSsdFNzBZ7DBPs0wkajjoDBjxDYDPHcet_-dPPAyS1GWL0v) |  |

Şu durumlarda sözleşmenin ödeme aczine düştüğü söylenir:

* toplam borç bakiyesi toplam aktif bakiyeden fazla ise
* benzer şekilde, toplam aktif olmayan bakiye toplam borç alınmamış bakiyeden fazla ise
* benzer şekilde, toplam çekilebilir bakiye sözleşmenin USDC bakiyesinden fazla ise

Aksi takdirde, sözleşmenin borcunu ödeyebilecek durumda olduğu söylenir.

Borç alma, bir borç alana tahsis edilen aktif fon oranı ile sınırlı olduğu ve aktif olmayan bakiyenin sadece dönemler arasında yükselebileceği için \(sözleşmeye "çıplak" USDC transferleri hariç\), sözleşme genellikle sadece dönemler arasındaki geçişler sırasında borcunu ödeyebilecek durumdan ödeme aczine düşmüş duruma geçebilir.

Bireysel bir borç alanın kendisine tahsis edilen bakiyesi ödenmemiş borç bakiyesinin altına düşmeden önce, her zaman en az bir hafta öncesinden bu durum kendisine bildirilir. Böyle bir geçiş sadece dönemler arasında gerçekleşebilir.

Sözleşme ödeme aczine düşmüş durumdayken, kullanıcılar alacaklı oldukları tüm fonları çekemeyebilir. Dahası, eksi bakiyenin giderilip giderilemeyeceği ve ne kadar hızlı giderilebileceği konusunda herhangi bir belirsizlik varsa durum ek riskler de içerir:

1. Kullanıcılar daha fazla fon stake etmek istemeyebilir çünkü bunu yapmak onları fonlarını geri alamayacakları bir konuma sokabilir.
2. Hâlihazırda stake eden kullanıcılar, fonlarını geri alma ihtimallerini en üst düzeye çıkarmak için "çıkışa koşmak" ve mümkün olan en kısa sürede fonlarını çekmek isteyebilir.

Kayıplar, bir eksi bakiyeye düşme olayı sırasında borca dönüştürülmüş aktif olmayan fonların oranını temsil eden endeksler aracılığıyla takip edilir. Stake eden her bir kişinin bakiyesinde önbelleğe alınmış bir eksi bakiye sayacı bulunur ve bu sayaç bakiyenin en son ne zaman güncellendiğine göre geçmişte meydana gelen eksi bakiyelerin sayısını temsil eder. Aktif olmayan bir bakiyenin maruz kaldığı tüm kayıplar, stake eden o kişinin borç bakiyesine aynı oranda yansıtılır. Endeksin nasıl hesaplandığına dair daha fazla bilgi için LS1DebtAccounting'e bakın.

Sözleşme ödeme aczine düşmüşse, tahsisini aşmış bir borç alan hedeflenerek \(herkes tarafından\) markDebt\(\) fonksiyonu çağrılabilir. Borç alanın borç alınmış bakiyesinin tahsis bakiyesini aşan miktarı borç bakiyesi olarak adlandırılır. Borç bakiyesinin miktarı borç alınan bakiyeden düşülür ve ödenmemiş eksi bakiye borcunu hesaplamak için kullanılan özel bir bakiyeye taşınır.

Stake edilen fonların hesaplanmasında da buna eşit bir ayarlama yapılır. Borç miktarına eşit bir miktar aktif olmayan bakiyelerden düşülür ve stake edenlere borçlu olunan eksi bakiye borcunu hesaplamak için özel bir bakiyeye eklenir. Her bir stake eden kişinin aktif olmayan bakiyesinden bir kesinti yapılacak ve bu kişi borç şeklinde eş değer bir miktar alacaktır. Bu şekilde, ödeme aczine düşünce yaşanan kayıplar, aktif olmayan bakiyelere sahip tüm stake edenlerden tahsil edilir \(orantılı olarak\).

Bu süreç aşağıda gösterilmektedir:

![](https://lh5.googleusercontent.com/2b2e67wVF3DL32NU0ykTVV0PJWaJ_bdmRQRKgx-5c3_qr_nWNYsuE77JviLtbBxXzASEfIp2Fw4hvzRPeM1a7TAIxq0NYUfo3dZLUhChilDpa5Ygq-YugSvNXKmyf2ul3GQM22SZ)

Borçlu olan borç alan borcunu geri öderse \(veya yönetişim gibi başka bir taraf onun adına geri öderse\), borcun alacaklısı olan stake edenler ilk gelen alır esasında fonları alabilir.

### Borç neyi temsil eder?

Borç

### Borç alan bir kişi temerrüde düştüğü takdirde stake edenler için herhangi bir yasal çözüm var mı?

Bir borç alan için markDebt\(\) çağrıldığında, borç alan sözleşmeden daha fazla fon borç alma hakkını kaybeder. Bu hak yönetişim tarafından yeniden verilebilir.

Potansiyel olarak Vakıf ile piyasa yapıcı sözleşmesi hakkında içerik ekleyebilirsiniz


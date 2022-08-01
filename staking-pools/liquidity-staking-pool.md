---
description: Likidite Staking Havuzuna genel bir bakış
---

# Likidite Modülü

İlk token arzının `%2,50'si` (`25.000.000 DYDX`) likidite staking havuzunda USDC stake eden kullanıcılara dağıtılacaktır.

### Hedefler

* dYdX Katman 2 protokolü üzerinde piyasa yapma amaçları için USDC tahsisini teşvik etmek.
* dYdX üzerinde makas farkı, derinlik ve çalışma süresini artırmak için en yüksek performansı sergileyen likidite sağlayıcılara sermaye tahsis etmek.

[**dydx.community/dashboard/pools/liquidity**](https://dydx.community/dashboard/pools/liquidity) sayfasında staking yapmaya başlayın**.**

## **Staking**'e Genel Bakış

Likidite, tüm başarılı borsaların temel bir bileşenidir. Likidite ağının etkilerini artırmak ve profesyonel likidite sağlayıcıları teşvik etmek için, likidite staking havuzunda USDC stake eden kullanıcılara DYDX dağıtılacaktır. Topluluk tarafından onaylanmış likidite sağlayıcılar, dYdX Katman 2 Protokolü üzerinde piyasalar oluşturmak için stake edilen USDC'leri kullanarak piyasalarda mevcut likiditeyi artıracaktır. Likidite sağlayıcıları, dYdX Katman 2 Protokolü dışında borç alınan fonları kullanamaz.

Stake edenler, USDC staking için DYDX ödülleri kazanacaktır. DYDX ödülleri, stake eden her bir kişinin havuzdaki toplam USDC miktarı içindeki payıyla orantılı olarak sürekli dağıtılacaktır.

Her bir stake eden ve likidite sağlayıcının Döner Kredi Sözleşmesine (bağlantı [buradadır](https://dydx.foundation/revolving-credit-agreement)) taraf olması gerekmektedir. Sözleşme, borç alınan USDC'yi geri ödemeyen herhangi bir likidite sağlayıcısına karşı her bir stake edene uygulanabilir bir hak vermek için likidite stake havuzunun koşullarını doğal bir dille belirtir. Sözleşme, yalnızca her bir stake eden ve her bir likidite sağlayıcı arasındadır. dYdX Vakfı sözleşmeye taraf değildir ve sözleşme çerçevesinde dYdX Vakfı'nın hiçbir hak ve yükümlülüğü yoktur.

## USDC'yi Staking'den Çıkarma ve Çekme İşlemleri

Stake eden bir kişi, o [**dönem**](../start-here/epochs.md) sona erdikten sonra USDC'lerini çekebilmek için dönem sona ermeden en az `14 gün` (**Karartma Süresi**) önce USDC'lerini çekme talebinde bulunmalıdır. Stake edenler fon çekme talebinde bulunmazsa, stake ettikleri USDC'ler bir sonraki döneme devredilir.

**Karartma Süresi** boyunca fon çekme talebinde bulunulamaz.

## Staking Riskleri

Havuzdan borç alanların bir teminatı kilitlemesi gerekli değildir. Tüm borç alanlar profesyonel ve saygın likidite sağlayıcılardır. İzin verilen borç alanların ve havuz tahsislerinin listesi yönetişim tarafından güncellenebilir.

Kullanıcılar USDC çekme talebinde bulunduğunda, bir borç alanın bir sonraki dönem için tahsis edilen bakiyesi borç alanın o an itibarıyla borç almış olduğu miktarın altına düşebilir. Bu durumda, borç alan kişi, dönem sona ermeden önce borç aldığı ve kendisine tahsis edilen bakiyeler arasındaki farkı ödemekle yükümlüdür.

Borç alan bir kişi borçlu olduğu bir bakiyeyi dönem sonunda havuza geri ödemezse, temerrüde düşmüş olarak kabul edilir ve borç geri ödenene kadar daha fazla USDC borç almasına izin verilmez. Bir borç alan bir borcu hiç geri ödemediği takdirde stake edenler USDC kaybedebilir. Bir piyasa yapıcı USDC kaybederse ve likidite staking havuzunu besleyemezse, stake edenler USDC'lerinin bir kısmını kaybedebilir.

Stake edenler ayrıca dayanak akıllı sözleşme kodunda bir güvenlik açığı olması durumunda akıllı sözleşme riskine de maruz kalır. Tüm DYDX ve yönetişim akıllı sözleşmeleri denetlenmiş ve titizlikle test edilmiştir.

Stake edenlerin riskini azaltmak için, her bir stake eden ve likidite sağlayıcının Döner Kredi Sözleşmesine (bağlantı [buradadır](https://dydx.foundation/revolving-credit-agreement)) taraf olması gerekir ancak sözleşmenin akdedilmesi, bir stake edenin sözleşme çerçevesindeki hakları infaz edilse bile likidite sağlayıcının borç aldığı tüm miktarları geri ödeyeceğini garanti etmez.

## Onaylanmış Borç Alanlar

Likidite Staking Havuzu sözleşmesi iki taraflı, eksik teminatlandırılmış ve faizsiz bir likidite sistemi olarak işler.

Çekilebilecek miktar, bir borç alanın tahsis yüzdesine ve havuzda stake edilen kullanılabilir USDC toplamına bağlıdır. Hem tahsis yüzdesi hem de toplam kullanılabilir USDC, `LS1EpochSchedule` tarafından belirlenen önceden tanımlanmış zamanlarda değişebilir. Borç alınan USDC'ler yalnızca dYdX'in Katman 2 Protokolünde kullanılabilir. Bu gereklilik, `StarkEx Perpetual Exchange` sözleşmesi ile etkileşime giren `StarkProxy` sözleşmesi aracılığıyla gözetilir.

Onaylanan ilk likidite sağlayıcılar arasında, dYdX Katman 2 Protokolünde aktif olarak piyasa yapan `Wintermute`, `Amber Group`, `Wootrade (Kronos)`, `Sixtant` ve `DAT Trading` yer almaktadır.

| Önceden Onaylanmış Borç Alanlar | İlk Tahsis Yüzdesi | Ethereum Adresi | StarkProxy | Likidite Sağlayıcılar hakkındaki bilgiler |
| ---------------------- | ----------------------------- | --------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Wintermute | %25 | [0x4f3a120E72C76c22ae802D129F599BFDbc31cb81](https://etherscan.io/address/0x4f3a120E72C76c22ae802D129F599BFDbc31cb81) | [0x0b2B08AC98a1568A34208121c26F4F41a9e0FbB6](https://etherscan.io/address/0x0b2B08AC98a1568A34208121c26F4F41a9e0FbB6) | [https://forums.dydx.community/provention/community/1486-borrower-wintermute/](https://forums.dydx.community/proposal/discussion/1486-borrower-wintermute/) |
| Amber Group | %25 | [0x39Ad99E33ab7E85818741dD6076112188bc2611](https://etherscan.io/address/0x39Ad99E33ab7Ee85818741dD6076112188bc2611) | [0x3e6E9EFb0A677a24F47093a22044dc5451A028cF](https://etherscan.io/address/0x3e6E9EFb0A677a24F47093a22044dc5451A028cF) | [https://forums.dydx.community/provention/1487-borrower-amber-group/](https://forums.dydx.community/proposal/discussion/1487-borrower-amber-group/) |
| WOO Network (Kronos) | %20 | [0x38d981c3c42b2ec8e9572f560552407d0f1279fb](https://etherscan.io/address/0x38d981c3c42b2ec8e9572f560552407d0f1279fb) | [0x16BEC2D9A010e7D8b2D576d17893C52Dbfe4C06](https://etherscan.io/address/0x16BEC2D9A010e7D8b2D576d17893C52Ddbfe4C06) | [https://forums.dydx.community/provention/1485-borrower-wootra-kronos-research/](https://forums.dydx.community/proposal/discussion/1485-borrower-wootrade-kronos-research/) |
| Sixtant | %20 | [0x89ded350b2be3dc2014c71f1e49cdfad17ccaf7c](https://etherscan.io/address/0x89ded350b2be3dc2014c71f1e49cdfad17ccaf7c) | [0xCB7fa3a2F47b62293Cc2E1a4C7752fC72E49FCe2](https://etherscan.io/address/0xCB7fa3a2F47b62293Cc2E1a4C7752fC72E49FCe2) | [https://forums.dydx.community/provention/1484-borrower-sixtant/](https://forums.dydx.community/proposal/discussion/1484-borrower-sixtant/) |
| DAT Trading | %10 | [0x83E8f8f4DAE0f42d68FdbBf85d4191a5e6f92F8](https://etherscan.io/address/0x83e8fb8f4dae0f42d68fdbbf85d4191a5e6f92f8) | [0x531F3BE462F10386D01FBeD7fAD1d20A61Ce7874](https://etherscan.io/address/0x531F3BE462F10386D01FBeD7fAD1d20A61Ce7874) | [https://forums.dydx.community/provention/1483-borrower-dat-trading/](https://forums.dydx.community/proposal/discussion/1483-borrower-dat-trading/) |

## Stake Edilen Bakiyelerin Muhasebesi

Stake edilen bir bakiye şu iki durumdan birinde olur:

* **Aktif**: Borç almak için kullanılabilir; staking ödülleri kazanır; stake eden kişi tarafından çekilemez.
* **Aktif Değil**: Borç almak için kullanılamaz; ödül kazanmaz; stake eden kişi tarafından çekilebilir.

Stake eden bir kişi, hem aktif hem de aktif olmayan bakiyelere sahip olabilir. USDC, aşağıdaki örnekte gösterilen şekilde dönem bazında hesaplanır:

![Stake edilen bakiyenin muhasebesi](<../.gitbook/assets/image (34) (1).png>)

Aşağıdaki işlemler stake edilen bakiyeleri aşağıda belirtilen şekilde etkiler:

* **Fon Yatırma**: Aktif bakiyeyi artırır.
* Fon **çekme talebi**: Mevcut dönemin sonunda, bazı aktif USDC'leri inaktif hale getirir.
* **Fon Çekme**: Aktif olmayan bakiyeyi azaltır.
* **Transfer**: Bazı aktif USDC'leri başka bir stake eden kişiye aktarır.

Belirli bir dönemin sonunda bir bakiyenin değişmesinin planlanmış olabileceğini kodlamak için, her bakiye üç alandan oluşan bir yapı halinde saklanır: currentEpoch, currentEpochBalance ve nextEpochBalance. Aktif olmayan kullanıcı bakiyeleri de shortfallCounter alanını kullanır.

### stkUSDC nedir?

Likidite Staking Havuzu'na USDC yatıran ve stake eden USDC sahipleri, token'a dönüştürülmüş bir pozisyon (**stkUSDC**) alacaktır. stkUSDC, bir kullanıcı USDC stake ettiğinde basılır ve bir kullanıcı `withdrawStake` fonksiyonunu çağırdığında yakılır. USDC'nin bir stake edenin cüzdanını terk ettiği aynı işlemde, stake edenin cüzdanına stkUSDC girer ve staking'den çıkarma işleminde de bunun tam tersi gerçekleşir.

Bir stkUSDC bakiyesi aktif olabilir veya olmayabilir. Aktif stkUSDC'ler bir ERC-20 olarak transfer edilebilir ancak çekilemez. Aktif olmayan stkUSDC'ler ise çekilebilir ancak transfer edilemez. Örneğin, bir kullanıcının cüzdanında 100 aktif ve 100 aktif olmayan stkUSDC olabilir ve kullanıcının bakiyesi 200 stkUSDC görünecektir ancak kullanıcı 100 stkUSDC'den fazlasını transfer etmeye çalışırsa transfer işlemi geri dönecektir.

Stake edenin dönem sona ermeden önce çekme talebinde bulunduğu bir stake edilen bakiye, aktif değil addedilir ve dolayısıyla da transfer edilemez.

## **Stake edenler** SSS

### Staking ödüllerini nasıl kazanabilirim?

Stake edenler diledikleri zaman likidite staking havuzuna USDC yatırabilir ve hemen ödül kazanmaya başlayabilir. DYDX ödülleri, her bir stake edenin toplam havuzdaki payına göre saniye bazında sürekli olarak kazanılır. Ödüller istendiği zaman alınabilir ve çekilebilir.

Stake edilen USDC'ler aktif kaldığı süre için ödül kazanır. Bu da bir miktar USDC çekme talebinde bulunulduktan sonra, o USDC'lerin dönem sonuna kadar ödül kazanmaya devam edeceği anlamına gelir. Örneğin:

![Ödül muhasebesi](<../.gitbook/assets/image (65) (1).png>)

Yukarıdaki senaryoda, kullanıcı **Zaman0'dan** **Zaman2**'ye kadar olan süre için ödül kazanır ve ödül de o dönemde stake edilen toplam bakiyeye göre değişir. Kullanıcı bakiyesinin sadece bir kısmını çekme talebinde bulunursa, kalan bakiye **Zaman2**'nin ötesinde ödül kazanmaya devam eder.

### Likidite Havuzuna nasıl USDC yatırabilir ve stake edebilirim?

Likidite Havuzunda USDC stake etmek için şu adımları izleyin:

* [https://dydx.community/dashboard/pools/likidite](https://dydx.community/dashboard/pools/liquidity) adresine gidin
* "Stake Et" seçeneğine tıklayın
* İlk yatırma işleminizde USDC'yi etkinleştirmeniz gerekir. Bunu sadece bir kez yapmanız ve gas ücretlerini de yalnızca bir kez ödemeniz gerekecektir.
* Havuzda stake etmek istediğiniz USDC miktarını girin.
* "Fonları Stake Et" seçeneğine tıklayın; stake etmek, fon çekme talebinde bulunmak ve USDC çekmek için gas ücretleri ödemeniz gerekecektir.

![](<../.gitbook/assets/image (57).png>)

Stake edilen USDC'ler artık aktiftir ve hemen ödül kazanmaya başlar.

Doğrudan akıllı sözleşmede USDC yatırmak ve stake etmek için, kullanıcılar `stake` fonksiyonunu çağırır. Kullanıcılar ayrıca `stakeFor` fonksiyonunu çağırarak başka bir adres adına da USDC yatırabilir ve stake edebilir. Doğrudan akıllı sözleşmede USDC stake etseniz bile Döner Kredi Sözleşmesini (bağlantı [buradadır](https://dydx.foundation/revolving-credit-agreement)) bildiğiniz ve gözden geçirmiş olduğunuz kabul edilir.

### Karartma Süresi nedir?

Karartma süresi, kullanıcıların stake edilen USDC'leri çekmeyi talep edemediği bir zaman dilimidir. İlk başta bir dönemin son `14 günü` olarak yapılandırılmış olan karartma süresi boyunca `requestWithdrawal` fonksiyonu çağrılamaz. Yeni dönemler 28 günde bir başlar. Diğer bir deyişle, kullanıcılar belirli bir dönemin sona ermesinden `14 gün` öncesine kadar bir sonraki dönemde fon çekmeyi talep edebilir.

### Staking havuzundan nasıl USDC çekebilirim? Ne kadar sürer?

Havuzdaki USDC'lerin kullanılabilirliği için öngörülebilirlik ve düzenli bir tempo sağlamak amacıyla çekim işlemleri için bir dönem takvimi uygulanmaktadır. Stake eden bir kişi, o dönem sona erdikten sonra USDC'lerini çekebilmek için dönemin sona ermesinden en az `14 gün` önce USDC'leri staking'den çıkarma talebinde bulunmalıdır. Stake edenler fon çekme talebinde bulunmazsa, stake ettikleri USDC'ler bir sonraki döneme devredilir.

USDC çekebilmek için, kullanıcılar bir sonraki dönemde USDC çekme talebinde bulunmak amacıyla `requestWithdrawal` fonksiyonunu çağırır. Kullanıcı fonları stake edilmeye devam edecektir ve mevcut dönem boyunca çekilemez. Bir sonraki dönemden başlayarak, fonlar "aktif değil" olacak ve çekilebilecektir.

Bir sonraki dönemde, kullanıcılar aktif olmayan USDC'leri belirli bir adrese çekmek için `withdrawStake` fonksiyonunu çağırır. Kullanıcılar çekmek istedikleri aktif olmayan fon miktarını seçebilir veya aktif olmayan tüm fonlarını çekmek için \`withdrawMaxStake\` fonksiyonunu çağırabilir. `withdrawMaxStake` fonksiyonunu çağırmak, eth\_call aracılığıyla maksimum değeri sorgulayıp `withdrawStake()` fonksiyonunu çağırmaktan daha fazla gas ücreti ödemenize neden olur.

Likidite Havuzunda USDC'leri staking'den çıkarmak için aşağıdaki adımları izleyin:

* [**https://dydx.community/dashboard/staking-pool/liquidity**](https://dydx.community/dashboard/staking-pool/liquidity) adresine gidin\*\*\*\*
* Aşağıdaki ekranı açmak için "**Talep Et**" seçeneğine tıklayın:

![Çekme talebi](<../.gitbook/assets/image (68).png>)

* Havuzdan çekme talebinde bulunmak istediğiniz USDC miktarını girin ve "**Fon çekme talebinde bulun**" seçeneğine tıklayın. USDC'leri staking'den çıkarmak için gas ücretleri ödemeniz gerekecektir.
* Mevcut dönem sona ermeden en az 14 gün (**Karartma Süresi**) önce USDC'lerini staking'den çıkarma talebinde bulunan stake edenler USDC'lerini bir sonraki dönemin başında çekebilirler.

### Yönetişim hangi parametreleri değiştirebilir?

dYdX Yönetişimi şunlardan sorumludur:

* Mevcut borç alanları kapsamlı bir incelemeye tabi tutmak
* Staking Likidite Havuzuna yeni borç alanları eklemek ve/veya mevcut borç alanları havuzdan çıkarmak
* Onaylanmış borç alanlara tahsis edilen borç alınan USDC miktarını değiştirmek
   * Belirli borç alanların tahsislerini değiştirmek için `setBorrowerAllocations` ve `setBorrowingRestriction` fonksiyonları çağrılır. Bu fonksiyonlar borç alanlar eklemek ve borç alanları kaldırmak için kullanılabilir. Artışlar bir sonraki dönemde yürürlüğe girer ancak düşüşler borç almayı hemen kısıtlar. Bu fonksiyonlar karartma süresi boyunca çağrılamaz.
* Dönem uzunluğu ve karartma süresi sözleşme oluşturulduğunda belirlenir ama daha sonra değiştirilebilir

## **Borç alanlar SSS**

### **Borç Alma**

Stake Edilen USDC'ler, onaylanmış borç alanlara tahsis edilen bir havuza girer. Her borç alan yönetişim tarafından kontrol edilen bir tahsis yüzdesine sahiptir ve bu tahsise kadar borç alabilir. Staking'den çıkarma süreci bir "dönem takvimi"ne tabidir. Stake edilen USDC'ler sadece bir dönemin başında çekilebilir (yani "aktif değil"dir).

Çekilmesi talep edilen USDC'ler, dönem sona ermeden önce borç alanlar tarafından iade edilmelidir. Eksik ödeme durumunda, ödenmemiş tutar bir "borç bakiyesi" haline gelir ve staking sözleşmesi yeniden stabilize edilir. Hataya düşen borç alan, borç bakiyesini geri ödemelidir ve yönetişim tarafından bu kısıtlama kaldırılana dek borç alması kısıtlanır.

Borç alanlar Döner Kredi Sözleşmesinin tüm hükümlerine tabidir (bağlantı [buradadır](https://dydx.foundation/revolving-credit-agreement)).

### **StarkProxy Özellikleri**

#### **Auto-Pay**

Borç alanlar tahsis edilen USDC'leri azami oranda kullanabilmek ve talep edilen fon çekme işlemlerinin zamanında ödenmesini sağlamak için `autoPayOrBorrow()` kullanabilir. Bir borç alanın sorumluluklarını yerine getirdiğinden emin olması için, her dönemde bu fonksiyonun yalnızca bir kez başarıyla çağrılması yeterlidir.

Fonksiyon dönemin ilk yarısında çağrılırsa eski durumuna geri döner çünkü bu karartma süresinin dışındadır. `StarkProxy` sözleşmesi geri ödeme için yeterli USDC'ye sahip değilse fonksiyon eski durumuna geri döner. Böyle bir durumda, `autoPayOrBorrow()` fonksiyonu çağrılmadan önce USDC eklenmeli veya borsadan çekilmelidir.

#### **Borç Alanın Sahip Olduğu USDC'ler**

Borç alan kişi kendi USDC'lerini güvenle `StarkProxy` sözleşmesine yatırabilir ve bunları dYdX Katman 2 Protokolünde borç alınan USDC'ler ile aynı hesapta kullanabilir. USDC'ler aşağıdaki durumlardan herhangi birinde `StarkProxy` sözleşmesinden çekilebilir:

* `StarkProxy` sözleşmesinde tutulan ve borç alınan bakiyeyi aşan USDC tutarı herhangi bir zamanda çekilebilir.
* Yönetişim belirli bir tutarın çekilmesini onaylayabilir.
   * Not: Bu, borç alanın USDC'lerinin büyük bir kısmını dYdX Katman 2 Protokolünden dışarı çıkarmak zorunda kalmadan kârlarını çekmesine olanak vermek için kullanılabilir.

#### **Borç Alan Rolleri**

`StarkProxy` sözleşmesi borç alanın kontrolünde olan aşağıdaki rolleri destekler. Bunlar, borç alanın güvenlik ihtiyaçlarına bağlı olarak tek bir adres veya ayrı adresler tarafından tutulabilir. Her rol herhangi bir sayıda adres tarafından tutulabilir.

Sahip

* Delegasyon yöneticisi rolünü verir veya kaldırır.
* `StarkProxy` sözleşmesinden çekilen USDC'lerin izin verilen alıcılarını ekler veya kaldırır.
* dYdX Katman 2 Protokolünde kullanılmasına izin verilen STARK anahtarlarını ekler veya kaldırır.
* `LiquidityStakingV1` ve `StarkPerpetual` sözleşmelerinde ERC20 tahsislerini belirler.
* `StarkEx Perpetual Exchange` sözleşmesinde `forcedWithdrawalRequest()` veya `forcedTradeRequest()` fonksiyonunu çağırır.

Delegasyon Yöneticisi

* Borç alan, borsa operatörü ve fon çekme operatörü rollerini verir veya kaldırır.

Borç Alan

* Likidite Staking sözleşmesinde `autoPayOrBorrow()`, `borrow()`, `repay()` ve `repayDebt()` fonksiyonlarını çağırır.

Borsa Operatörü

* `StarkEx Perpetual Exchange` sözleşmesinde `registerUserOnExchange()`, `depositToExchange()` ve `withdrawFromExchange()` fonksiyonlarını çağırır.

Fon Çekme Operatörü

* `StarkProxy` sözleşmesinden izin verilen bir alıcıya geçerli bir harici fon çekme işlemi (yukarıya bakın) yapar.

#### **Sınırlamalar**

dYdX Katman 2 Protokolündeki Katman 2 transferleri `StarkProxy` tarafından kontrol edilen hesaplar için devre dışı bırakılmıştır.

#### **Koruyucu Yetkileri**

Koruyucu rolü dYdX yönetişimi tarafından kontrol edilir. Rolü, borç alınan USDC'lerin güvenliğini sağlamak ve borç alanın özel anahtarının kaybolması veya kötüye kullanılması durumunda stake edenlere iade edilmesine izin vermektir.

Koruyucu şu eylemleri herhangi bir zamanda alabilir (time-lock'a tabidir):

* Borç almayı ve borç alınan USDC'lerin borsaya yatırılmasını kısıtlamak.
* Borç alınan bir bakiyeyi `StarkProxy` sözleşmesinde USDC kullanarak geri ödemek.
* `StarkProxy` sözleşmesinde USDC kullanarak bir borç bakiyesini geri ödemek.
* StarkEx sözleşmesinden `StarkProxy` sözleşmesine fon çekmek (örneğin borsadan yavaş bir fon çekme işleminin ikinci adımı olarak).
* Borç alan tarafından başlatılan bir zorla alım satım talebini iptal etmek.
* Bakiye kontrolünü geçiştirerek borç alanın `StarkProxy` sözleşmesinden bir miktar fon çekmesini onaylamak.
* Akıllı sözleşmenin sürümünü yükseltmek.

**Borç alanın ödenmemiş bir borç bakiyesi varsa, koruyucu şu eylemleri alabilir (time-lock'a tabidir):**

* dYdX Katman 2 Protokolünden bir zorla fon çekme işlemi yapmak.
* dYdX Katman 2 Protokolünde bir zorla alım satım işlemi (yalnızca azalt) yapmak.

## Staking Riskleri SSS

### Likidite staking havuzunda stake etmenin riskleri nelerdir? Borç alan bir kişi, borç aldığı fonları geri ödeyemezse ne olur?

Teminatsız bir borç alma sistemi, borç alan kişi tarafından karşılanması gereken çok daha yüksek bir güven standardı gerektirir. Likidite staking havuzundan borç alan likidite sağlayıcılar, borç alınan fonları likidite staking sisteminin ve dYdX Katman 2 Protokolünün dışına çıkaramaz. Bununla birlikte, bir likidite sağlayıcısı alım satım işlemlerinde fon kaybederse, stake edilen USDC'lerini kaybedebilir ve borç tahsisini dış finansman kaynakları aracılığıyla yenileyemeyebilir.

Bu durumda, bir borç alanın çekilmesi talep edilen fonları geri ödemede gecikmesi ve eksi bakiyeye düşülmesi durumunda aktif olmayan fonlara aşağıda belirtilen şekilde el koyulabilir ve bu fonlar kaybedilebilir. Borç alınan fonlarda temerrüde düşmesi durumunda, kusurlu bir borç alanın itibarı önemli ölçüde zedelenir.

Her bir stake eden ve borç alan kişi her ne kadar Döner Kredi Sözleşmesine (bağlantı [burada](https://dydx.foundation/revolving-credit-agreement)) taraf olsa da bu sözleşme, borç alanların yükümlülüklerini geri ödeyeceğine dair bir garanti vermez.

### Sözleşme ödeme kabiliyetini nasıl korur?

Herhangi bir zamanda, sözleşme stake edilen ve borç alınan bakiyeler arasındaki ilişkiye bağlı olarak aşağıdaki durumlardan birinde olacaktır:

![Sözleşmenin Ödeme Kabiliyeti](<../.gitbook/assets/image (41).png>)

Şu durumlarda sözleşmenin **ödeme aczine** düştüğü söylenir:

* toplam borç bakiyesi toplam aktif bakiyeden fazlaysa;
* veya benzer şekilde, toplam aktif olmayan bakiye toplam borç alınmamış bakiyeden daha fazlaysa;
* veya benzer şekilde, toplam çekilebilir bakiye sözleşmenin USDC bakiyesinden daha fazlaysa.

Aksi takdirde, sözleşmenin **borcunu ödeyebilecek durumda** olduğu söylenir.

Borç alma imkânı bir borç alanın kendisine tahsis edilen aktif USDC oranıyla sınırlı olduğu ve aktif olmayan bakiye sadece dönemler arasında yükselebileceği için, sözleşme genellikle sadece dönemler arasındaki geçişler sırasında borcunu ödeyebilecek durumdan ödeme aczine düşmüş bir duruma geçebilir.

Eğer yeni bir dönemin başlangıcında sözleşme ödeme aczine düşmüş durumda ise mümkün olan en kısa sürede sözleşmeyi yeniden stabilize etmek önemlidir. Ödeme kabiliyeti "borç muhasebesi" adı verilen bir mekanizma aracılığıyla tekrar kazanılır. Sözleşme ödeme aczine düştüğünde, tahsislerini aşmış borç alanların bir listesini belirterek, `markDebt()` fonksiyonu herkes tarafından çağrılabilir. Borç alanın borç bakiyesinin borç alanın tahsisini aşan miktarına borç alanın eksi bakiye miktarı denir.

`markDebt()` fonksiyonu çağrıldığında, her borç alanın eksi bakiye miktarı borç alınan fon bakiyesinden düşülür ve borç bakiyesi adı verilen bir bakiyeye taşınır. Aynı anda, bu eksi bakiye miktarlarının toplamı stake edenlerin aktif olmayan bakiyelerinden düşülür ve stake edenlere borç dekontları olarak dağıtılır. Her bir stake eden kişinin aktif olmayan bakiyesinden bir kesinti yapılacak ve her bir stake eden borç şeklinde eş değer bir miktar alacaktır. Bu şekilde, ödeme aczine düşünce yaşanan kayıplar, aktif olmayan bakiyelere sahip tüm stake edenlerden tahsil edilir (orantılı olarak).

Bu süreç aşağıda gösterilmektedir:

![Temerrüt](<../.gitbook/assets/image (46).png>)

### Borç neyi temsil eder?

Bir borç alanın temerrüde düşmesi durumunda, eksi bakiye miktarı (aktif olmayan bakiyelerin %100'üne kadar) aktif olmayan bir bakiyeden bir borç bakiyesine dönüştürülür (aktif olmayan bakiye sahiplerine ait olup el koyulmuş olan ve kaybedilen fonlar). Stake eden bir kişinin borç bakiyesi, stake eden kişiye stake edilen USDC havuzundan fon çekme hakkını vermez; borç bakiyesi özellikle borç geri ödemeleri şeklinde ödenmelidir.

Borç, daha sonra Borç Alan bir borç geri ödemesi yaparken veya yönetişim tarafından belirlenen başka bir yolla ödeme yaparken kullanılabilecek USDC'ler için bir USDC dekontunu temsil eder.

### Borç alan bir kişi temerrüde düşerse stake edenler ne gibi yasal çözümlere başvurabilir?

Stake edenler ve borç alanlar Döner Kredi Sözleşmesinin (bağlantı [buradadır](https://dydx.foundation/revolving-credit-agreement)) taraflarıdır ve bu sözleşmenin her bir stake eden ve her bir borç alan kişi arasında yürütülebilir bir sözleşme oluşturması amaçlanmaktadır. Buna ek olarak, Likidite Staking Havuzu akıllı sözleşmesi stake edenlere borç alanlara karşı bir yasal çözüm sağlamak için tasarlanmıştır ancak geri ödemeyi garanti edemez.

Bir borç alan için `markDebt()` çağrıldığında, borç alan sözleşmeden daha fazla fon borç alma hakkını kaybeder. Bu hak yönetişim tarafından yeniden verilebilir.

Borç "mark" edildikten sonra, ana muhasebe sisteminden çıkarılır ve stake edenler tarafından birden fazla şekilde tahsil edilebilir. Borçlu olan borç alan borcunu geri öderse (veya yönetişim gibi bir başka taraf onun adına geri öderse), borcun alacaklısı olan stake edenler fonları ilk gelen alır esasında alabilir. Akıllı sözleşmedeki "borç operatörü" arayüzü aracılığıyla daha esnek çözümler uygulanabilir.

Stake edenler borç aldıktan sonra pratikte neler olacağı bağlama bağlı olacaktır. Eğer onaylanmış bir borç alan tarafından yapılmış dürüst bir hata ise stake edenler borcun hızla ve tam olarak ödenmesini bekleyebilir. USDC fonları kaybedilirse, yönetişim etkilenen stake edenlere kısmi bir geri ödeme yapabilir. Çözüm belirsizse, yönetişim etkilenen stake edenlere bir ERC20 dekontu düzenlemeyi seçebilir ve bir çözüm beklenirken stake edenlere anında likidite sağlayabilir. Uygun görülmesi halinde, bir çözüme varılana kadar yönetişim dekont sahiplerine faiz ödemeleri yapmayı seçebilir.

Tüm bu durumlar temelde staking sözleşmesi tarafından desteklenmektedir ancak alınacak uygun eylem dYdX yönetişimi tarafından kararlaştırılmalı ve yürütülmelidir. Duruma bağlı olarak, bu harici bir akıllı sözleşmenin yazılmasını ve konuşlandırılmasını gerektirebilir.

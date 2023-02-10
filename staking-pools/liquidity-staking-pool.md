---
description: Likidite Staking Havuzuna genel bir bakış
---

# Likidite Modülü

Token arzının `%0,6'sı` (`5.753.430 $DYDX),` Likidite Staking Havuzu'na USDC stake eden kullanıcılara dağıtılmıştır. Başlangıçta, token arzının `%2,50'si` (`25.000.000 DYDX`) Likidite Staking Havuzu'na $USDC stake eden kullanıcılara dağıtılmak üzere tahsis edilmiştir. Likidite Staking Havuzu 29 Eylül 2022 itibarıyla artık aktif değildir. [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md)'te, dYdX topluluğu, Likidite Staking Havuzu ödüllerinin saniyede 0 olarak ayarlanması suretiyle Likidite Staking Havuzu ve Borç Alma Havuzu'nun tasfiye edilmesi yönünde [oy kullanmıştır](https://dydx.community/dashboard/proposal/7).

.
Daha \\önceden, Likidite Staking Havuzu'na $USDC stake eden kullanıcılara $DYDX dağıtılmıştır. Topluluğun onayladığı likidite sağlayıcılar bu stake edilen $USDC'yi dYdX Katman 2 Protokolünde piyasalar yapmak ve piyasalarda mevcut likiditeyi daha da büyütmek için kullanmıştır. Likidite sağlayıcıların borç alınan fonları dYdX Katman 2 Protokolü dışında kullanmaları yasaktı.

## **Staking**'e Genel Bakış

Şu anda, Likidite Staking Havuzu'nda stake edilen $USDC ödül kazandırmamaktadır.

Daha önceden $USDC stake edenlere dağıtılmış olan 383.562 $DYDX Ödül Hazinesi'ne tahakkuk edecek ve dYdX topluluğu tarafından bir [yönetişim oylaması](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters) ile kullanılabilecektir.

## USDC'yi Staking'den Çıkarma ve Çekme İşlemleri

Stake eden bir kişi, ilgili [dönem](../start-here/epochs.md) sona erdikten sonra $USDC çekebilmek için dönem sona ermeden en az `****3 gün` (**Karartma Süresi**) önce $USDC çekme talebinde bulunmalıdır. Stake edenler fon çekme talebinde bulunmazsa stake ettikleri $DYDX bir sonraki döneme devredilir.

**Karartma Süresi** boyunca fon çekme talebinde bulunulamaz.

[DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md)'te, dYdX topluluğu Karartma Süresinin `14 günden` `3 güne` düşürülmesi yönünde [oy kullandı](https://dydx.community/dashboard/proposal/7).

## $stkUSDC nedir?

Likidite Staking Havuzu'na $USDC yatıran ve stake eden $USDC sahipleri, token'a dönüştürülmüş bir pozisyon ($**stkUSDC**) alacaktır. $stkUSDC, bir kullanıcı $USDC stake ettiğinde basılır ve bir kullanıcı `withdrawStake` fonksiyonunu çağırdığında yakılır. $USDC'nin bir stake edenin cüzdanını terk ettiği aynı işlemde, stake edenin cüzdanına $stkUSDC girer ve staking'den çıkarma işleminde de bunun tam tersi gerçekleşir.

Bir $stkUSDC bakiyesi aktif olabilir veya olmayabilir. Aktif $stkUSDC'ler bir ERC-20 olarak transfer edilebilir ancak çekilemez. Aktif olmayan $stkUSDC'ler ise çekilebilir ancak transfer edilemez. Örneğin, bir kullanıcının cüzdanında 100 aktif ve 100 aktif olmayan #stkUSDC olabilir; bu durumda kullanıcının bakiyesi 200 $stkUSDC görünecektir ancak kullanıcı 100 $stkUSDC'den fazlasını transfer etmeye çalışırsa transfer işlemi geri dönecektir.

Stake edenin dönem sona ermeden önce çekme talebinde bulunduğu bir stake edilen bakiye, aktif değil addedilir ve dolayısıyla da transfer edilemez.

## SSS

### Karartma Süresi nedir?

Karartma süresi kullanıcıların stake edilen fonlarını çekmeyi talep edemediği bir zaman dilimidir. `requestWithdrawal` fonksiyonu, bir dönemin son `3 günü` olarak yapılandırılan bir karartma süresi içinde çağrılamaz. Yeni dönemler 28 günde bir başlar. Diğer bir deyişle, kullanıcılar bir sonraki dönemde fon çekmeyi cari dönemin sona ermesinden `3 gün` öncesine kadar talep edebilirler.

### Stake havuzundan nasıl $USDC çekebilirim? Ne kadar sürer?

Stake eden biri, bir dönemin bitişinden sonra $USDC çekebilmek için o dönemin sona ermesinden en az `3 gün` önce $USDC bakiyesini stake'ten çıkarmalıdır. Stake edenler fon çekme talebinde bulunmazsa stake ettikleri $DYDX bir sonraki döneme devredilir.

$USDC çekebilmek için, kullanıcılar bir sonraki dönem için $USDC çekme talebinde bulunmak amacıyla `requestWithdrawal` fonksiyonunu çağırır. Kullanıcı fonları stake edilmeye devam edecektir ve mevcut dönem boyunca çekilemez. Bir sonraki dönemden başlayarak, fonlar "aktif değil" olacak ve çekilebilecektir.

Bir sonraki dönemde, kullanıcılar belirli bir adrese aktif olmayan $USDC çekmek için `withdrawStake` fonksiyonunu çağırır. Kullanıcılar çekmek istedikleri aktif olmayan fon miktarını seçebilir veya aktif olmayan tüm fonlarını çekmek için \`withdrawMaxStake\` fonksiyonunu çağırabilir. `withdrawMaxStake` fonksiyonunu çağırmak, eth\_call aracılığıyla maksimum değeri sorgulayıp `withdrawStake()` fonksiyonunu çağırmaktan daha fazla gas ücreti ödemenize neden olur.

Likidite Havuzu'na $USDC unstake etmek için aşağıdaki adımları izleyin:

* [**https://dydx.community/dashboard/staking-pool/liquidity**](https://dydx.community/dashboard/staking-pool/liquidity) adresine gidin\*\*\*\*
* Aşağıdaki ekranı açmak için "**Talep Et**" seçeneğine tıklayın:

![Çekme talebi](../.gitbook/assets/1-withdraw-from-liquidity-pool.png)

* Havuzdan çekme talebinde bulunmak istediğiniz USDC miktarını girin ve "**Fon çekme talebinde bulun**" seçeneğine tıklayın. USDC'leri staking'den çıkarmak için gas ücretleri ödemeniz gerekecektir.
* USDC'sinin stake'inin kaldırılmasını cari dönemin sona ermesinden en az `3 gün` (**Karartma Süresi**) önce talep eden kullanıcılar USDC'lerini bir sonraki dönemin başında çekebilirler.

### Yönetişim hangi parametreleri değiştirebilir?

dYdX Yönetişimi şunlardan sorumludur:

* Likidite Staking Havuzuna USDC stake edilmesi karşılığında saniye başına ödüller
* Staking Likidite Havuzuna yeni borç alanları eklemek ve/veya mevcut borç alanları havuzdan çıkarmak
* Onaylanmış borç alanlara tahsis edilen borç alınan USDC miktarını değiştirmek
  * Belirli borç alanların tahsislerini değiştirmek için `setBorrowerAllocations` ve `setBorrowingRestriction` fonksiyonları çağrılır. Bu fonksiyonlar borç alanlar eklemek ve borç alanları kaldırmak için kullanılabilir. Artışlar bir sonraki dönemde yürürlüğe girer ancak düşüşler borç almayı hemen kısıtlar. Bu fonksiyonlar karartma süresi boyunca çağrılamaz.
* Dönem uzunluğu ve karartma süresi sözleşme oluşturulduğunda belirlenir ama daha sonra değiştirilebilir

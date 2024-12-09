---
description: Likidite Staking Havuzuna genel bakış
---

# 🔋 Likidite Modülü

Likidite Staking Havuzu 29 Eylül 2022 itibarıyla artık aktif değildir. [DIP 14](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-14.md)'te dYdX topluluğu, Likidite Staking Havuzu ödüllerini saniye başına 0 olarak belirleyerek Likidite Staking Havuzu'nu ve Borç Alma Havuzu'nu fiilen kapatma yönünde [oy kullandı](https://dydx.community/dashboard/proposal/7).

Likidite Modülü Ödülleri tahsisinden kalan tüm ethDYDX, dYdX Zinciri Topluluk Hazinesine taşınmıştır.

dYdX Zinciri Topluluk Hazinesi hakkında daha fazla bilgi [burada](https://app.gitbook.com/s/7eKRye9zrZIr1Pp3Q3Mu/modules-and-parameters/community-treasury) mevcuttur.

## **Staking**'e Genel Bakış

Şu anda, Likidite Staking Havuzu'nda stake edilen $USDC ödül kazandırmamaktadır.

## USDC'yi Staking'den Çıkarma ve Çekme İşlemleri

Stake eden bir kişi, ilgili [dönem](../start-here/epochs.md) sona erdikten sonra $USDC çekebilmek için dönem sona ermeden en az `****3 gün` (**Karartma Süresi**) önce $USDC çekme talebinde bulunmalıdır. Stake edenler fon çekme talebinde bulunmazsa stake ettikleri $DYDX bir sonraki döneme devredilir.

**Karartma Süresi** boyunca fon çekme talebinde bulunulamaz.

## SSS

<details>

<summary>Karartma Süresi nedir?</summary>

Karartma süresi kullanıcıların stake edilen fonlarını çekmeyi talep edemediği bir zaman dilimidir. `requestWithdrawal` fonksiyonu, bir dönemin son `3 günü` olarak yapılandırılan bir karartma süresi içinde çağrılamaz. Yeni dönemler 28 günde bir başlar. Diğer bir deyişle, kullanıcılar bir sonraki dönemde fon çekmeyi cari dönemin sona ermesinden `3 gün` öncesine kadar talep edebilirler.

</details>

<details>

<summary>Stake havuzundan nasıl $USDC çekebilirim? Ne kadar sürer?</summary>

Stake eden biri, bir dönemin bitişinden sonra $USDC çekebilmek için o dönemin sona ermesinden en az `3 gün` önce $USDC bakiyesini stake'ten çıkarmalıdır. Stake edenler fon çekme talebinde bulunmazsa stake ettikleri $DYDX bir sonraki döneme devredilir.

$USDC çekebilmek için, kullanıcılar bir sonraki dönem için $USDC çekme talebinde bulunmak amacıyla `requestWithdrawal` fonksiyonunu çağırır. Kullanıcı fonları stake edilmeye devam edecektir ve mevcut dönem boyunca çekilemez. Bir sonraki dönemden başlayarak, fonlar "aktif değil" olacak ve çekilebilecektir.

Bir sonraki dönemde, kullanıcılar belirli bir adrese aktif olmayan $USDC çekmek için `withdrawStake` fonksiyonunu çağırır. Kullanıcılar çekmek istedikleri aktif olmayan fon miktarını seçebilir veya aktif olmayan tüm fonlarını çekmek için \`withdrawMaxStake\` fonksiyonunu çağırabilir. `withdrawMaxStake` fonksiyonunu çağırmak, eth\_call aracılığıyla maksimum değeri sorgulayıp `withdrawStake()` fonksiyonunu çağırmaktan daha fazla gas ücreti ödemenize neden olur.

Likidite Havuzu'na $USDC unstake etmek için aşağıdaki adımları izleyin:

* [**https://dydx.community/dashboard/staking-pool/liquidity**](https://dydx.community/dashboard/staking-pool/liquidity) adresine gidin\*\*\*\*
* “**Talep Et**" üzerine tıklayın
* Havuzdan çekme talebinde bulunmak istediğiniz $USDC miktarını girin ve "**Çekme talebinde bulun**" seçeneğine tıklayın. $USDC'leri staking'den çıkarmak için gaz ücretleri ödemeniz gerekecektir.
* Cari dönemin sona ermesinden en az `3 gün` (**Karartma Süresi**) önce $USDC'nin stake'inin kaldırılmasını talep eden kullanıcılar, $USDC'lerini bir sonraki dönemin başında çekebilirler.

</details>

###

---
description: Güvenlik Staking Havuzuna genel bakış
hidden: true
---

# 🔐 Güvenlik Modülü

Güvenlik Modülü, 28 Kasım 2022 itibarıyla artık aktif değildir. [DIP 17](https://dydx.community/dashboard/proposal/9)'de dYdX topluluğu, Güvenlik Modülü ödüllerini saniyede 0'a ayarlayarak Güvenlik Modülü'nü etkin bir şekilde kapatmak yönünde [oy kullandı](https://dydx.community/dashboard/proposal/7).

Likidite Modülü Ödülleri tahsisinden kalan tüm ethDYDX, dYdX Zinciri Topluluk Hazinesi'ne taşındı.

dYdX Zinciri Topluluk Hazinesi Ödülleri hakkında daha fazla bilgi [burada](https://app.gitbook.com/s/7eKRye9zrZIr1Pp3Q3Mu/modules/community-treasury) mevcuttur.



## DYDX'i Staking'den Çıkarma ve Çekme İşlemleri

Stake edenler, dönemin bitişinden sonra ethDYDX çekebilmek için dönemin sona ermesinden en az `3 gün` **(Karartma Süresi)** önce varlıklarını çekme talebinde bulunmalıdır. Stake edenler varlık çekme talebinde bulunmazsa, stake ettikleri $ethDYDX'ler bir sonraki döneme devredilir.

**Karartma Süresi** boyunca fon çekme talebinde bulunulamaz.

[DIP 17](https://dydx.community/dashboard/proposal/9)'de dYdX topluluğu, Karartma Süresi'ni `14 günden` `3 güne` düşürme yönünde [oy kullandı](https://dydx.community/dashboard/proposal/7).

## SSS

<details>

<summary>Karartma süresi nedir?</summary>

Karartma süresi kullanıcıların stake edilen $stkDYDX'i çekmeyi talep edemediği bir zaman dilimidir. `requestWithdrawal` fonksiyonu, bir dönemin son `3 günü` olarak yapılandırılan bir karartma süresi içinde çağrılamaz. Yeni dönemler 28 günde bir başlar. Diğer bir deyişle, kullanıcılar bir sonraki dönemde fon çekmeyi cari dönemin sona ermesinden `3 gün` öncesine kadar talep edebilirler.

</details>

<details>

<summary>Stake havuzundan nasıl fon çekebilirim? Ne kadar sürer?</summary>

Havuzdaki fonların kullanılabilirliği için öngörülebilirlik ve düzenli bir tempo sağlamak amacıyla çekim işlemleri için bir dönem takvimi uygulanmaktadır. Stake eden bir kişi, fonlarını o dönem sona erdikten sonra çekebilmek için bir dönemin sona ermesinden en az `3 gün` önce fon çekme talebinde bulunmalıdır. Stake edenler varlık çekme talebinde bulunmazsa, stake ettikleri $ethDYDX'ler bir sonraki döneme devredilir.

Varlıklarını çekebilmek için, kullanıcılar, bir sonraki dönemde varlık çekme talebinde bulunmak için `` `requestWithdrawal` `` fonksiyonunu çağırır. Kullanıcı fonları stake edilmeye devam edecektir ve mevcut dönem boyunca çekilemez. Bir sonraki dönemden başlayarak, fonlar "aktif değil" olacak ve çekilebilecektir.

Bir sonraki dönemde, kullanıcılar aktif olmayan varlıklarını belirli bir adrese çekmek için `` `withdrawStake` `` fonksiyonunu çağırır. Kullanıcılar çekmek istedikleri aktif olmayan varlık miktarını seçebilir veya aktif olmayan tüm varlıklarını çekmek için `` `withdrawMaxStake` `` fonksiyonunu çağırabilir. `` `withdrawMaxStake` `` fonksiyonunu çağırmanın, eth\_call aracılığıyla maksimum değeri sorgulayıp `` `withdrawStake()` `` fonksiyonunu çağırmaktan daha fazla gas ücreti ödemenize neden olacağı bilinmelidir.

Güvenlik Modülü'nden $ethDYDX çekmek için şu adımları izleyin:

* [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety) adresine gidin\*\*\*\*
* "**Talep Et**" seçeneğine tıklayın ve havuzdan çekmeyi talep etmek istediğiniz $ethDYDX miktarını girin.
* "**Fon çekmeyi talep et**" seçeneğine tıklayın. Fon çekmek için gas ücretleri ödemeniz gerekecektir.
* Mevcut dönemin sona ermesinden en az `3 gün` önce $ethDYDX çekme talebinde bulunan stake edenler, bir sonraki dönemin başında $ethDYDX'lerini çekebilirler.

</details>


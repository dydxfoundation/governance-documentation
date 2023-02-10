---
description: Güvenlik Staking Havuzuna genel bir bakış
---

# Güvenlik Modülü

Token arzının `%0,5'i` (`5.049.079 $DYDX),` sistemi desteklemek için bir Güvenlik havuzuna DYDX stake eden kullanıcılara dağıtılmıştır. Başlangıçta, token arzının `%2,50'si` (`25.000.000 DYDX`), Güvenlik Modülü'ne $DYDX stake eden kullanıcılara dağıtılmak üzere ayrılmıştır. Güvenlik Modülü, 28 Kasım 2022 itibarıyla artık aktif değildir. [DIP 17](https://dydx.community/dashboard/proposal/9)'de dYdX topluluğu, Güvenlik Modülü ödüllerini saniyede 0'a ayarlayarak Güvenlik Modülü'nü etkin bir şekilde kapatmak yönünde [oy kullandı](https://dydx.community/dashboard/proposal/7).\


Bundan önce, DYDX'i Güvenlik Modülü'ne stake eden kullanıcılara $DYDX dağıtılmıştı. Güvenlik modülü, iflas veya dYdX protokolüyle ilgili oluşacak başka sorunlar durumunda kullanılacak olan merkezsizleştirilmiş bir fondu.

Güvenlik Modülü'nde stake edilen $DYDX teklif verme ve oy kullanma haklarının yanı sıra delegasyon imkânlarını da sürdürür.

## Genel bakış

Şu anda, Güvenlik Modülü'nde stake edilen $DYDX ödül kazandırmamaktadır.

Daha önce $DYDX stake edenlere dağıtılan 383.562 $DYDX, Ödül Hazinesi'nde toplanacak ve [yönetişim oylamasıyla](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters) dYdX topluluğu tarafından kullanılabilecektir.

## DYDX'i Staking'den Çıkarma ve Çekme İşlemleri

Stake edenler, dönemin bitişinden sonra $DYDX çekebilmek için dönemin sona ermesinden en az `3 gün` **(Karartma Süresi)** önce fon çekme talebinde bulunmalıdır. Stake edenler fon çekme talebinde bulunmazsa stake ettikleri $DYDX bir sonraki döneme devredilir.

**Karartma Süresi** boyunca fon çekme talebinde bulunulamaz.

[DIP 17](https://dydx.community/dashboard/proposal/9)'de dYdX topluluğu, Karartma Süresi'ni `14 günden` `3 güne` düşürme yönünde [oy kullandı](https://dydx.community/dashboard/proposal/7).



## SSS

### Karartma süresi nedir?

Karartma süresi kullanıcıların stake edilen $stkDYDX'i çekmeyi talep edemediği bir zaman dilimidir. `requestWithdrawal` fonksiyonu, bir dönemin son `3 günü` olarak yapılandırılan bir karartma süresi içinde çağrılamaz. Yeni dönemler 28 günde bir başlar. Diğer bir deyişle, kullanıcılar bir sonraki dönemde fon çekmeyi cari dönemin sona ermesinden `3 gün` öncesine kadar talep edebilirler.

### Stake havuzundan nasıl fon çekebilirim? Ne kadar sürer?

Havuzdaki fonların kullanılabilirliği için öngörülebilirlik ve düzenli bir tempo sağlamak amacıyla çekim işlemleri için bir dönem takvimi uygulanmaktadır. Stake eden bir kişi, fonlarını o dönem sona erdikten sonra çekebilmek için bir dönemin sona ermesinden en az `3 gün` önce fon çekme talebinde bulunmalıdır. Stake edenler fon çekme talebinde bulunmazsa stake ettikleri $DYDX bir sonraki döneme devredilir.

Fonlarını çekebilmek amacıyla, kullanıcılar bir sonraki dönemde fon çekme talebinde bulunmak için \`requestWithdrawal\` fonksiyonunu çağırır. Kullanıcı fonları stake edilmeye devam edecektir ve mevcut dönem boyunca çekilemez. Bir sonraki dönemden başlayarak, fonlar "aktif değil" olacak ve çekilebilecektir.

Bir sonraki dönemde, kullanıcılar aktif olmayan fonlarını belirli bir adrese çekmek için \`withdrawStake\` fonksiyonunu çağırır. Kullanıcılar çekmek istedikleri aktif olmayan fon miktarını seçebilir veya aktif olmayan tüm fonlarını çekmek için \`withdrawMaxStake\` fonksiyonunu çağırabilir. \`withdrawMaxStake\` fonksiyonunu çağırmanın, eth\_call aracılığıyla maksimum değeri sorgulayıp \`withdrawStake()\` fonksiyonunu çağırmaktan daha fazla gas ücreti ödemenize neden olacağını unutmayın.

Güvenlik Modülü'nden $DYDX çekmek için aşağıdaki adımları izleyin:

* [**dydx.community/dashboard/pools/safety**](https://dydx.community/dashboard/pools/safety) adresine gidin\*\*\*\*
* "**Talep Et**" seçeneğine tıklayın ve havuzdan çekmeyi talep etmek istediğiniz DYDX miktarını girin.
* "**Fon çekmeyi talep et**" seçeneğine tıklayın. Fon çekmek için gas ücretleri ödemeniz gerekecektir.
* Mevcut dönemin sona ermesinden en az `3 gün` önce DYDX çekme talebinde bulunan stake edenler bir sonraki dönemin başında DYDX'lerini çekebilirler.


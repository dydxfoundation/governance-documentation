---
description: Topluluk hazinesine genel bir bakış.
---

# Topluluk Hazinesi

Token arzının **`%`**`16,2`'si (`162.004.734 $DYDX`) dYdX topluluğunun katkıda bulunanlar hibeler, topluluk girişimleri, likidite madenciliği ve diğer programlar için sürekli olarak kullanması amacıyla **** topluluk hazinesine tahsis edilmiştir. Başlangıçta, token arzının `%5,0'i` (`50.000.000 $DYDX`) topluluk hazinesine tahsis edilmiştir ve her dönemde topluluk hazinesine 766.703 $DYDX verilmiştir. Şu anda, topluluk hazinesinde 2.492.731 $DYDX bulunmaktadır çünkü üç yönetişim teklifi her bir dönemde dYdX topluluğuna sunulan $DYDX miktarında 1.726.028 $DYDX artışla sonuçlanmıştır:

* [DIP 14](https://dydx.community/dashboard/proposal/7) - USDC staking için ödülleri 0 olarak belirleme (dönem başına 383.562 $DYDX),
* [DIP 16](https://dydx.community/dashboard/proposal/8) - trading ödüllerini %25 düşürme (dönem başına 958.904 $DYDX) ve
* [DIP 17](https://dydx.community/dashboard/proposal/9) - $DYDX staking için ödülleri 0 olarak belirleme (dönem başına 383.562 $DYDX).



**Hedefler**

* dYdX'in büyümesini sağlayan programlar ve girişimleri finanse etmek.
* Topluluk NFT'leri, yazılım yarışmaları, analiz panoları, memler, promosyon ürünleri, üçüncü taraf araçları, çeviriler ve diğer projeleri finanse etmek için hibe programları geliştirmek.
* Sınıfının en iyisi bir yönetişim sistemi geliştirmek ve sağlam yönetişimi teşvik etmek.

## Genel bakış

Topluluk hazinesi $DYDX sahiplerinin hibeler, yeni likidite madenciliği havuzları veya başka bir program üzerinde alacağı kararlar doğrultusunda kullanılmak üzere $DYDX tutacaktır. $DYDX beş yıl boyunca sürekli olarak topluluk hazinesine tahsis edilecektir. Topluluk hazinesinden herhangi bir miktarda $DYDX harcamak için bir yönetişim oylaması gerekecektir.

Beş yıl dolduktan sonra yönetişimin sürekli enflasyon (yıllık maksimum `%2` enflasyon oranında) uygulamaya karar vermesi hâlinde, yeni basılan tüm $DYDX'ler topluluk hazinesi tarafından kullanılabilecektir.

## SSS

### $DYDX Topluluk Hazinesine nasıl devreder?

Her saniye, Topluluk Hazinesi Devredicisi (ayrıntılara [buradan](https://docs.dydx.community/dydx-governance/resources/technical-overview#governance-architecture-overview) göz atın) Topluluk Hazinesi'ne [`0,3169242627`](tel:03169242627) $DYDX devreder. $DYDX devredildikten sonra, Topluluk Hazinesi Devredicisi'nde `claim` (talep etme) fonksiyonunun çağırılması, devredilen $DYDX'in transferini gerçekleştirir. Herhangi bir dYdX topluluk üyesi [buradan](https://etherscan.io/address/0x08a90Fe0741B7DeF03fB290cc7B273F1855767D8#writeContract) Etherscan üzerinde `claim` işlevini çağırarak (bir miktar gaz ücreti gerektirecektir) devredilen $DYDX'i Topluluk Hazinesi Devredicisi'nden Topluluk Hazinesine taşıyabilir.

<figure><img src="../.gitbook/assets/claim-function-CT-vester.png" alt=""><figcaption></figcaption></figure>

### Topluluk Hazinesinin kazanılmış bakiyesi nedir?

dYdX topluluk üyeleri topluluk hazinesinin devredilen bakiyesini [buradan](https://dydx.shippooor.xyz/) görüntüleyebilirler. \
\
Dahası, dYdX Vakfı her dönemin sonunda [Dönem Raporu ile](https://dydx.foundation/blog) Topluluk Hazinesinin devredilmiş bakiyesini yayınlamaktadır. Topluluk Hazinesi'ne devredilmiş $DYDX'e ek olarak, dYdX topluluğu (1) trade ödüllerinin %25 oranında azaltılması (958.904 $DYDX), (2) USDC staking ödüllerinin 0'a ayarlanması (383.562 DYDX) ve (3) DYDX staking ödüllerinin 0'a ayarlanması (383.562 DYDX) yönündeki oyların sonucunda Ödül Hazinesi'ne tahakkuk eden $DYDX'e de erişebilir. Dönem 17'den başlayarak, her bir dönemde Ödül Hazinesi'ne 1.726.028 $DYDX tahakkuk edecektir ve bu meblağ bir [yönetişim oylaması](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters) ile dYdX topluluğu tarafından kullanılabilecektir.

### Ödül Hazinesi'nden $DYDX harcamak için kimler teklif verebilir?

Teklif vermek için yeterli yetkiye sahip her kullanıcı teklif verebilir. Topluluk hazinesinden herhangi bir miktarda $DYDX harcamak için bir yönetişim oylaması gerekecektir. Bir teklif vermek için, lütfen [DIP Teklifi Yaşam Döngüsü](../voting-and-governance/dip-proposal-lifecycle.md)'nde belirtilen şekilde bir dYdX İyileştirme Teklifi (DIP) verin.

### Topluluk Hazinesi'nden gelen varlıkları harcamak için bir teklif oluşturmaya nasıl başlarsınız?

Reverie, 5 milyondan fazla $DYDX (kısa zaman kilitli oylama ([short timelock vote](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-process#short-timelock-executor)) [için teklif eşiği](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters#timelock-parameters)) teklif gücüne sahip bir dYdX topluluğu üyesinin Topluluk Hazinesi'nden bir hedef adresine $DYDX aktarmak için bir teklifi nasıl oluşturabileceğine dair kapsamlı, teknik, adım adım bir kılavuz hazırlamıştır. Bu teknik kılavuza ulaşmak için [buraya](https://app.gitbook.com/o/-MeNgGQU0ucT2xo4s8-T/s/-MeNfSkgj48hU0q8Zbjn/\~/changes/EyisuFjLIyJ7K9RzaTfJ/technical-guide-on-building-a-dydx-community-treasury-spending-proposal) tıklayın.

### Topluluk Hazinesi'ne ne tür teklifler verilebilir?

Topluluk tarafından yönetilen hazine bir olasılıklar dünyasının kapısını açar. dYdX Katman 2 Protokolü ekosisteminin büyümesini destekleyebilecek ekosistem hibeleri de dâhil olmak üzere çeşitli deneyler ve girişimler görmeyi umuyoruz.

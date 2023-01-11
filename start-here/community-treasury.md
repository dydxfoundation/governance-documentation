---
description: Topluluk hazinesine genel bir bakış.
---

# Hazine

Başlangıçtaki token arzının (`50.000.000 DYDX`) `%5,00'i` katkıda bulunanlara hibeler, topluluk girişimleri, likidite madenciliği ve diğer programlar aracılığıyla sürekli bir şekilde tahsis edilecek bir topluluk hazinesine dağıtılacaktır.

**Hedefler**

* dYdX'in büyümesini sağlayan programlar ve girişimleri finanse etmek.
* Topluluk NFT'leri, yazılım yarışmaları, analiz panoları, memler, promosyon ürünleri, üçüncü taraf araçları, çeviriler ve diğer projeleri finanse etmek için hibe programları geliştirmek.
* Sınıfının en iyisi bir yönetişim sistemi geliştirmek ve sağlam yönetişimi teşvik etmek.

## Genel bakış

Topluluk hazinesi DYDX sahiplerinin hibeler, yeni likidite madenciliği havuzları veya başka bir program üzerinde alacağı kararlar doğrultusunda kullanılmak üzere DYDX tutacaktır. DYDX beş yıl boyunca sürekli olarak vesting kapsamında topluluk hazinesine tahsis edilecektir. Topluluk hazinesinden herhangi bir miktarda DYDX harcamak için bir yönetişim oylaması gerekecektir.

Beş yıl dolduktan sonra yönetişim sürekli enflasyon (yıllık maksimum `%2` enflasyon ile) uygulamaya karar verirse, yeni basılan tüm DYDX'ler topluluk hazinesi tarafından kullanılabilecektir.

## SSS

### DYDX Topluluk Hazinesine nasıl devreder?

Her saniye, Topluluk Hazinesi Devredicisi (ayrıntılara [buradan](https://docs.dydx.community/dydx-governance/resources/technical-overview#governance-architecture-overview) göz atın) Topluluk Hazinesine [`0.3169242627`](tel:03169242627) DYDX devreder. DYDX devredildikten sonra Topluluk Hazinesi Devredicisi üzerinde `claim` işlevini çağırmak, devredilen DYDX'i Topluluk Hazinesine aktaracaktır. Herhangi bir dYdX topluluk üyesi [buradan](https://etherscan.io/address/0x08a90Fe0741B7DeF03fB290cc7B273F1855767D8#writeContract) Etherscan üzerinde `claim` işlevini çağırarak (bir miktar gaz ücreti gerektirecektir) devredilen DYDX'i Topluluk Hazinesi Devredicisinden Topluluk Hazinesine taşıyabilir.

<figure><img src="../.gitbook/assets/claim-function-CT-vester.png" alt=""><figcaption></figcaption></figure>

### Topluluk Hazinesinin kazanılmış bakiyesi nedir?

dYdX topluluk üyeleri topluluk hazinesinin devredilen bakiyesini [buradan](https://dydx.shippooor.xyz/) görüntüleyebilirler. \
\
Dahası, dYdX Vakfı her dönemin sonunda [Dönem Raporu ile](https://dydx.foundation/blog) Topluluk Hazinesinin devredilmiş bakiyesini yayınlamaktadır. Topluluk Hazinesinde kazanılmış DYDX'e ek olarak, dYdX topluluğu (1) alım satım ödüllerinin %25 oranında (958.904 DYDX) azaltılması, (2) USDC staking ödüllerinin 0'a (383.562 DYDX) ayarlanması (3) DYDX staking ödüllerinin 0'a (383.562 DYDX) ayarlanması yönündeki oylarının bir sonucu olarak Ödül Hazinesinde tahakkuk eden DYDX'i kullanabilir. Dönem 17'den başlayarak her dönem Ödül Hazinesi'nde 1.726.028 DYDX tahakkuk edecek ve dYdX topluluğu tarafından [yönetişim oylamasıyla](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters) kullanılabilecektir.

### Topluluk Hazinesi'nden DYDX token'ları harcamak için kimler teklif verebilir?

Teklif vermek için yeterli yetkiye sahip her kullanıcı teklif verebilir. Topluluk hazinesinden herhangi bir miktarda DYDX harcamak için bir yönetişim oylaması gerekecektir. Bir teklif vermek için, lütfen [DIP Teklifi Yaşam Döngüsü](../voting-and-governance/dip-proposal-lifecycle.md)'nde belirtilen şekilde bir dYdX İyileştirme Teklifi (DIP) verin.

### Topluluk Hazinesi'nden gelen varlıkları harcamak için bir teklif oluşturmaya nasıl başlarsınız?

Reverie, 5 milyondan fazla DYDX ([kısa zaman kilitli oy (short timelock vote)](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-process#short-timelock-executor) için [teklif eşiği](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters#timelock-parameters)) teklif gücüne sahip bir dYdX topluluğu üyesinin Topluluk Hazinesinden bir hedef adresine DYDX aktarmak için bir teklifi nasıl oluşturabileceğine dair kapsamlı, teknik, adım adım bir kılavuz hazırladı. Bu teknik kılavuza ulaşmak için [buraya](https://app.gitbook.com/o/-MeNgGQU0ucT2xo4s8-T/s/-MeNfSkgj48hU0q8Zbjn/\~/changes/EyisuFjLIyJ7K9RzaTfJ/technical-guide-on-building-a-dydx-community-treasury-spending-proposal) tıklayın.

### Topluluk Hazinesi'ne ne tür teklifler verilebilir?

Topluluk tarafından yönetilen hazine bir olasılıklar dünyasının kapısını açar. dYdX Katman 2 Protokolü ekosisteminin büyümesini destekleyebilecek ekosistem hibeleri de dâhil olmak üzere çeşitli deneyler ve girişimler görmeyi umuyoruz.

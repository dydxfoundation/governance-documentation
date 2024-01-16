---
description: Topluluk hazinesine genel bir bakış.
---

# Topluluk Hazinesi

Token arzının **`%26,1'i`** (`261.133.225 $ethDYDX`) katılımcı hibeleri, topluluk girişimleri, likidite madenciliği ve diğer programlarda kullanılmak üzere düzenli olarak dYdX topluluğunun hazinesine hibe edilir. Başlangıçta, token arzının `%5'i` (`50.000.000 $ethDYDX`) topluluk hazinesine [tahsis edilmişti](https://docs.dydx.community/dydx-governance/start-here/dydx-allocations) ve her dönem topluluk hazinesinde 766.703 $ethDYDX birikmekteydi. Şu anda topluluk hazinesinde 3.787.251 $ethDYDX birikmektedir çünkü birçok yönetişim teklifi, her dönem dYdX topluluğunun kullanabileceği $ethDYDX miktarında 3.020.548 $ethDYDX artışla sonuçlanmıştır:

* [DIP 14](https://dydx.community/dashboard/proposal/7) - USDC staking için ödülleri 0 olarak belirleme (dönem başına 383.562 $ethDYDX),
* [DIP 16](https://dydx.community/dashboard/proposal/8) - trading ödüllerini %25 düşürme (dönem başına 958.904 $ethDYDX),
* [DIP 17](https://dydx.community/dashboard/proposal/9) - $DYDX staking için ödülleri 0 olarak belirleme (dönem başına 383.562 $ethDYDX),
* [DIP 20](https://dydx.community/dashboard/proposal/11) - trading ödüllerini tekrar %45 düşürme (dönem başına 1.294.520 $ethDYDX) ve
* [DIP 24](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md) - Likidite Sağlayıcı Ödüllerini %50 düşürme (dönem başına 575.342 $ethDYDX).
*   [DIP 29](https://dydx.community/dashboard/proposal/16) - dYdX v3'te Dönem 30-32'den itibaren Likidite Sağlayıcı Ödüllerini ⅓ oranında azaltarak aşağıdaki değerlere düşürme:

    * Dönem 30: 383.562 $ethDYDX
    * Dönem 31: 191.781 $ethDYDX
    * Dönem 32: 0 $ethDYDX

    Dönem 31'den sonra, dYdX v3 üzerinde herhangi bir Likidite Sağlayıcı Ödülü olmayacaktır. dYdX topluluğu DIP 29'da Alım Satım Ödüllerini dYdX v3'teki Dönem 30-32'den ⅓ oranında azaltma yönünde oy kullanmıştır; ancak Alım Satım Ödüllerinin kalan tahsisi dYdX Zinciri üzerine Alım Satım Ödülleri olarak taşınmıştır.

18 Kasım 2023 tarihinde dYdX topluluğu Topluluk Hazinesi'ne tahakkuk eden ethDYDX bakiyesini Ethereum'dan dYdX Zinciri'ne köprüleme yönünde [oy kullandı](https://dydx.community/dashboard/proposal/16). DYDX köprülendikten sonra dYdX Zinciri üzerinde yapılacak bir yönetişim oylaması ile dYdX topluluğu tarafından kullanılabilir.



**Hedefler**

* dYdX'in büyümesini sağlayan programlar ve girişimleri finanse etmek.
* Topluluk NFT'leri, yazılım yarışmaları, analiz panoları, memler, promosyon ürünleri, üçüncü taraf araçları, çeviriler ve diğer projeleri finanse etmek için hibe programları geliştirmek.
* Sınıfının en iyisi bir yönetişim sistemi geliştirmek ve sağlam yönetişimi teşvik etmek.

## Genel bakış

Topluluk hazinesi, $ethDYDX sahiplerinin karar verdiği şekilde hibeler, yeni likidite madenciliği havuzları veya başka herhangi bir program için kullanmak üzere $ethDYDX miktarını koruyacaktır. $ethDYDX, beş yıl boyunca sürekli olarak topluluk hazinesine vest edilecektir. Topluluk hazinesinden herhangi bir miktarda ethDYDX harcamak için bir yönetişim oylaması gerekecektir.

Beş yıl dolduktan sonra yönetim, (yıllık maksimum `%2` enflasyon ile) sürekli enflasyon uygulamaya karar verirse, yeni basılan tüm $ethDYDX'ler topluluk hazinesi tarafından kullanılabilecektir.

## SSS

### $ethDYDX Topluluk Hazinesine nasıl devreder (vesting)?

Her saniye, Topluluk Hazinesi Devredicisi (ayrıntılara [buradan](https://docs.dydx.community/dydx-governance/resources/technical-overview#governance-architecture-overview) göz atın) Topluluk Hazinesine [`0,3169242627`](tel:03169242627) $ethDYDX devreder. $ethDYDX devredildikten sonra Topluluk Hazinesi Devredicisi üzerinde `claim` (talep et) işlevini çağırmak, devredilen $ethDYDX'i Topluluk Hazinesine aktaracaktır. Herhangi bir dYdX topluluk üyesi [buradan](https://etherscan.io/address/0x08a90Fe0741B7DeF03fB290cc7B273F1855767D8#writeContract) Etherscan üzerinde `claim` işlevini çağırarak (gas ücreti olarak bir miktar ETH gerektirecektir), devredilen $ethDYDX'i Topluluk Hazinesi Devredicisi'nden Topluluk Hazinesine taşıyabilir.

Lütfen dYdX topluluğu tarafından topluluk hazinesinin kontrolü hakkında daha fazla bilgi edinmek için dYdX Foundation'ın [Kullanım Şartlarına](https://dydx.foundation/terms) göz atın.

<figure><img src="../.gitbook/assets/claim-function-CT-vester.png" alt=""><figcaption></figcaption></figure>

### Topluluk Hazinesinin kazanılmış bakiyesi nedir?

dYdX topluluk üyeleri topluluk hazinesinin devredilen bakiyesini [buradan](https://dydx.shippooor.xyz/) görüntüleyebilirler. \
\
Dahası, dYdX Foundation her dönemin sonunda [Dönem Raporu](https://dydx.foundation/blog) ile Topluluk Hazinesinin devredilmiş bakiyesini yalnızca bilgi amaçlı yayınlamaktadır. Topluluk Hazinesi'ne devredilen $ethDYDX'e ek olarak, dYdX topluluğu, şu oylamalar sonucunda Ödül Hazinesi'ne tahakkuk ettirilen ethDYDX'e de erişebilir:

* [DIP 14](https://dydx.community/dashboard/proposal/7) - USDC staking için ödülleri 0 olarak belirleme (dönem başına 383.562 $ethDYDX),
* [DIP 16](https://dydx.community/dashboard/proposal/8) - trading ödüllerini %25 düşürme (dönem başına 958.904 $ethDYDX),
* [DIP 17](https://dydx.community/dashboard/proposal/9) - ethDYDX staking için ödülleri 0 olarak belirleme (dönem başına 383.562 $ethDYDX),
* [DIP 20](https://dydx.community/dashboard/proposal/11) - trading ödüllerini tekrar %45 düşürme (dönem başına 1.294.520 $ethDYDX),
* [DIP 24](https://github.com/dydxfoundation/dip/blob/master/content/dips/DIP-24.md) - Likidite Sağlayıcı Ödüllerini %50 düşürme (dönem başına 575.342 $ethDYDX), ve
* [DIP 29](https://dydx.community/dashboard/proposal/16) - dYdX v3'te Dönem 30-32'den itibaren Likidite Sağlayıcı Ödüllerini ⅓ oranında azaltarak aşağıdaki değerlere düşürme:
  * Dönem 30: 383.562 $ethDYDX
  * Dönem 31: 191.781 $ethDYDX
  * Dönem 32: 0 $ethDYDX

### Topluluk Hazinesi'ndeki ethDYDX'i harcamak için kimler teklif verebilir?

Teklif vermek için yeterli yetkiye sahip her kullanıcı teklif verebilir. Topluluk hazinesinden herhangi bir miktarda ethDYDX harcamak için bir yönetişim oylaması gerekecektir. Bir teklif vermek için, lütfen [DIP Teklifi Yaşam Döngüsü](../voting-and-governance/dip-proposal-lifecycle.md)'nde belirtilen şekilde bir dYdX İyileştirme Teklifi (DIP) verin.

### Topluluk Hazinesi'nden gelen varlıkları harcamak için bir teklif oluşturmaya nasıl başlarsınız?

Reverie, 5 milyondan fazla $ethDYDX (kısa zaman kilitli oylama ([short timelock vote](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-process#short-timelock-executor)) için [teklif eşiği](https://docs.dydx.community/dydx-governance/voting-and-governance/governance-parameters#timelock-parameters)) teklif gücüne sahip bir dYdX topluluğu üyesinin Topluluk Hazinesi'nden bir hedef adresine $ethDYDX aktarmak için bir teklifi nasıl oluşturabileceğine dair kapsamlı, teknik, adım adım bir kılavuz hazırlamıştır. Bu teknik kılavuza ulaşmak için [buraya](https://app.gitbook.com/o/-MeNgGQU0ucT2xo4s8-T/s/-MeNfSkgj48hU0q8Zbjn/\~/changes/EyisuFjLIyJ7K9RzaTfJ/technical-guide-on-building-a-dydx-community-treasury-spending-proposal) tıklayın.

### Topluluk Hazinesi'ne ne tür teklifler verilebilir?

Topluluk tarafından yönetilen hazine bir olasılıklar dünyasının kapısını açar. dYdX v3'ün ekosisteminin büyümesini destekleyebilecek ekosistem hibeleri de dâhil olmak üzere çeşitli deneyler ve girişimler görmeyi umuyoruz.

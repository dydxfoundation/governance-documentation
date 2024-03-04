---
description: Topluluk hazinesine genel bir bakış.
---

# Topluluk Hazinesi

Token arzının **`%26,1'i`** (`261.133.225 $ethDYDX`) katılımcı hibeleri, topluluk girişimleri, likidite madenciliği ve diğer programlarda kullanılmak üzere düzenli olarak dYdX topluluğunun hazinesine hibe edilir. Başlangıçta, token arzının `%5'i` (`50.000.000 $ethDYDX`) topluluk hazinesine [tahsis](https://docs.dydx.community/dydx-governance/start-here/dydx-allocations) edilmişti ve her dönem topluluk hazinesinde 766.703 $ethDYDX birikmekteydi. Şu anda topluluk hazinesinde 3.787.251 $ethDYDX birikmektedir çünkü birçok yönetişim teklifi, her dönem dYdX topluluğunun kullanabileceği $ethDYDX miktarında 3.020.548 $ethDYDX artışla sonuçlanmıştır:

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

Daha önce, Topluluk Hazinesi Devredicisi (ayrıntılara [buradan](https://docs.dydx.community/dydx-governance/resources/technical-overview#governance-architecture-overview) bakabilirsiniz) her saniye Topluluk Hazinesi'ne [`0,3169242627`](tel:03169242627) $ethDYDX kazandırıyordu. $ethDYDX devredildikten sonra Topluluk Hazinesi Devredicisi üzerinde `claim` (talep et) işlevini çağırmak, devredilen $ethDYDX'i Topluluk Hazinesine aktarıyordu. Herhangi bir dYdX topluluk üyesi [buradan](https://etherscan.io/address/0x08a90Fe0741B7DeF03fB290cc7B273F1855767D8#writeContract) Etherscan üzerinde `claim` işlevini çağırarak (gas ücreti olarak bir miktar ETH gerektiriyordu), devredilen $ethDYDX'i Topluluk Hazinesi Devredicisi'nden Topluluk Hazinesine taşıyabiliyordu.

Lütfen dYdX topluluğu tarafından topluluk hazinesinin kontrolü hakkında daha fazla bilgi edinmek için dYdX Foundation'ın [Kullanım Şartlarına](https://dydx.foundation/terms) göz atın.

<figure><img src="../.gitbook/assets/claim-function-CT-vester.png" alt=""><figcaption></figcaption></figure>

###

###


---
description: Yönetişim mimarisi ve akıllı sözleşmelere genel bakış.
---

# Teknik Özet

## Yönetişim Mimarisine Genel Bakış

dYdX zincir içi yönetişimi şu özellikleri destekler:

* Teklif oluşturma ve oylama
* Bir teklifin başlangıcında token bakiyelerinin anlık görüntülerini alma
* Oy verme ve teklif verme yetkilerini ayrı ayrı devretme
* Teklif verme, karar yeter sayısı ve oy farkı eşikleri de dâhil olmak üzere yönetişim eşiklerini belirleme
* Oyların nasıl sayıldığını belirleyen “Governance Strategy” akıllı sözleşmesini değiştirme
* Şunlara olanak veren birden fazla executor sözleşmesini yapılandırma:
   * short time-lock executor'lar aracılığıyla hızlı protokol yükseltmeleri ve fon dağıtımı;
   * long time-lock executor'lar aracılığıyla yönetişim yükseltmeleri.

dYdX Yönetişimini destekleyen 6 akıllı sözleşme vardır:

* **`DydxToken` sözleşmesi**: Bir adresin herhangi bir blok numarasındaki oy verme veya teklif verme yetkisi için yapılan sorguları destekleyen anlık görüntüleri saklar. Oy verme ve teklif verme yetkilerinin ayrı ayrı devredilmesini destekler.
* **`DydxGovernor` sözleşmesi**: Teklifleri izler ve Executor akıllı sözleşmeleri aracılığıyla teklifleri yürütür.
* **`Executor` sözleşmeleri**: Yönetişim tarafından oylanan işlemleri sıraya koyar, iptal eder ve yürütür. Bir teklif geçerse, teklifteki işlev çağrıları teklifte belirtilen Executor sözleşmesi ile yürütülür. Sıraya koyulan işlemler belirli bir bekleme süresinin ardından gerçekleştirilir ve bu süre Executor sözleşmesi tarafından belirlenir.
* ******`Priority Timelock`** **sözleşmesi**: Timelock sözleşmesi ile aynıdır ancak bir öncelik denetleyicisinin timelock bekleme süresi sona ermeden önce **Öncelik Süresi** (7 gün) içinde işlemleri gerçekleştirmesine olanak tanır.
* **`Governance Strategy` sözleşmesi**: Oy sayma mantığını içerir. Şu anda, DYDX Token ve Safety Module'dan verilen oyları sayar. Long time-lock aracılığıyla yükseltilebilir.
* **`Safety Module` sözleşmesi**: DYDX token'larını stake etme, stake edilmiş bir pozisyonu token'a dönüştürme ve ödül kazanma mantıklarını içerir ve dayanak token'ların oy verme ve teklif verme haklarını ve yetki devri işlevlerini sürdürür.

{% tabs %}
 {% tab title="Mainnet" %}
 | Sözleşme                             | Adres                                    |
 | ------------------------------------ | ------------------------------------------ | | DydxToken                            | 0x92D6C1e31e14520e676a687F0a93788B716BEff5 |
 | DydxGovernor                         | 0x7E9B1672616FF6D6629Ef2879419aaE79A9018D2 |
 | Short Timelock Executor              | 0x64c7d40c07EFAbec2AafdC243bF59eaF2195c6dc |
 | Long Timelock Executor               | 0xEcaE9BF44A21d00E2350a42127A377Bf5856d84B |
 | Merkle-Pauser Timelock Executor      | 0xd98e7A71BacB6F11438A8271dDB2EFd7f9361F52 |
 | Starkware Priority Timelock Executor | 0xa306989BA6BcacdECCf3C0614FfF2B8C668e3CaE |
 | Rewards Treasury                     | 0x639192D54431F8c816368D3FB4107Bc168d0E871 |
 | Community Treasury                   | 0xE710CEd57456D3A16152c32835B5FB4E72D9eA5b |
 | Safety Module                        | 0x65f7BA4Ec257AF7c55fd5854E5f6356bBd0fb8EC |
 | GovernanceStrategy                   | 0x90Dfd35F4a0BB2d30CDf66508085e33C353475D9 |
 | Rewards Treasury Vester              | 0xb9431E19B29B952d9358025f680077C3Fd37292f |
 | Community Treasury Vester            | 0x08a90Fe0741B7DeF03fB290cc7B273F1855767D8 |
 | Merkle Distributor                   | 0x01d3348601968aB85b4bb028979006eac235a588 |
 | Chainlink Adapter                    | 0x99B0599952a4FD2d1A1561Fa4C010827EaD30354 |
 | Liquidity Staking                    | 0x5Aa653A076c1dbB47cec8C1B4d152444CAD91941 |
 | Claims Proxy                         | 0x0fd829C3365A225FB9226e75c97c3A114bD3199e |
 | StarkEx Helper Governor              | 0x0db9b3F7Dd83e29C9bece8E5e1089bA4369E694a |
 | StarkEx Remover Governor V2          | 0xFCAac0F14deA11eDe11Afcb875f29130e1ad5ec0 |
 | Rewards Treasury Proxy Admin         | 0x40D6992cbd03E0DC1c2DE9606D29Cb245E737a5d |
 | Community Treasury Proxy Admin       | 0x9d51599A6b10f562619D8ef2EFDcA1B68aE80D03 |
 | Safety Module Proxy Admin            | 0x6aaD0BCfbD91963Cf2c8FB042091fd411FB05b3C |
 | Merkle Distributor Proxy Admin       | 0x6C5cd3aD7A16Ae207D221908E6b997d9B0DcD7b0 |
 | Liquidity Staking Proxy Admin        | 0xAc5D8bCD13da463bea96c75f9085c4e40037F790 |
 | StarkProxy \[0]                      | 0x0b2B08AC98a1568A34208121c26F4F41a9e0FbB6 |
 | StarkProxy \[1]                      | 0x3e6E9EFb0A677a24F47093a22044dc5451A028cF |
 | StarkProxy \[2]                      | 0xCB7fa3a2F47b62293Cc2E1a4C7752fC72E49FCe2 |
 | StarkProxy \[3]                      | 0x16BEC2D9A010e7D8b2D576d17893C52Ddbfe4C06 |
 | StarkProxy \[4]                      | 0x531F3BE462F10386D01FBeD7fAD1d20A61Ce7874 |
 | StarkProxy Proxy Admin \[0]          | 0xE16718eace44e0CB06b9cd164490A69A6425D1e3 |
 | StarkProxy Proxy Admin \[1]          | 0x78e899e576C3565C3219dbC9Ea5042A9DBed36d3 |
 | StarkProxy Proxy Admin \[2]          | 0x15774D4555fEfD57C9Fc8b11C8beba993eafcc13 |
 | StarkProxy Proxy Admin \[3]          | 0x4d9460e5C958f46a1Fe129954A069a37972f16EA |
 | StarkProxy Proxy Admin \[4]          | 0xfa45DCDbEc82C94082d283B62506320DB8632054 |
 {% endtab %}
 {% endtabs %}

## Açık kaynak kodu ve denetlenmiş

Yönetişim sözleşmeleri ve staking havuzları için tüm akıllı sözleşme kaynak kodlarını [https://github.com/dydxfoundation/governance-contracts](https://github.com/dydxfoundation/governance-contracts) adresinde bulabilirsiniz.

dydx.community sitesinde barındırılan yönetişim ön ucu için kaynak kodunu [burada](https://github.com/dydxfoundation/pnyx) bulabilirsiniz.

Önemli tüm yeni akıllı sözleşmeler Peckshield tarafından denetlenmiştir. Hiçbir önemli veya yüksek öncelikli güvenlik sorunu bulunmamıştır. Çekirdek yönetişim ve token sözleşmeleri [CertiK](https://www.certik.io), [Certora](https://www.certora.com) ve [Peckshield](https://peckshield.com/en) tarafından denetlenen Aave yönetişim sözleşmelerinden fork'lanmıştır ve mainnet üzerinde aylarca saha testine tabi tutulmuştur.

## Ana Yönetişim Sözleşmeleri

![Red dashed lines indicate contract is upgradeable](<.. /.gitbook/assets/Screen Shot 2021-09-03 at 5.17.43 PM.png>)

### DydxToken

DydxToken sözleşmesinde Aave'den esinlenilmiştir. dYdX ekibi tarafından küçük değişiklikler yapılmıştır.

DYDX, Ethereum mainnet'te [0x92D6C1e31e14520e676a687F0a93788B716Beff5](https://etherscan.io/address/0x92d6c1e31e14520e676a687f0a93788b716beff5) adresinde konuşlandırılmıştır. Commit'ten oluşturulmuştur \[pek yakında].

**ABI**

\[pek yakında]

### DydxGovernor

DydxGovernor sözleşmesinde Aave'den esinlenilmiştir. dYdX tarafından küçük değişiklikler yapılmıştır.

Governor, Ethereum mainnet'te [0x7E9B1672616FF6629Ef2879419aE79A9018D2](https://etherscan.io/address/0x7e9b1672616ff6d6629ef2879419aae79a9018d2) adresinde konuşlandırılmıştır. Commit'ten oluşturulmuştur \[pek yakında].

### GovernanceStrategy

GovernanceStrategy sözleşmesinde Aave'den esinlenilmiştir.

Strategy, Ethereum mainnet'te [0x90Dfd35F4a0BB2d30CDf665085e33C353475D9](https://etherscan.io/address/0x90Dfd35F4a0BB2d30CDf66508085e33C353475D9) adresinde konuşlandırılmıştır. Commit'ten oluşturulmuştur \[pek yakında].

**ABI**

\[pek yakında]

### Executor'lar

Executor sözleşmesinde Aave'den esinlenilmiştir. dYdX tarafından küçük değişiklikler yapılmıştır.

**Long Timelock**, Ethereum mainnet'te [0xEcaE9BF44A21d00E2350a42127A377Bf5856d84B](https://etherscan.io/address/0xecae9bf44a21d00e2350a42127a377bf5856d84b) adresinde konuşlandırılmıştır. Commit'ten oluşturulmuştur \[pek yakında].

**ABI**

\[pek yakında]

**Short Timelock**, Ethereum mainnet'te [0xEcaE9BF44A21d00E2350a42127A377Bf5856d84B](https://etherscan.io/address/0xecae9bf44a21d00e2350a42127a377bf5856d84b) adresinde konuşlandırılmıştır. Commit'ten oluşturulmuştur \[pek yakında].

**ABI**

\[pek yakında]

**Merkle Timelock**, Ethereum mainnet'te [0xd98e7A71BacB6F11438A8271dDB2EFd7f9361F52](https://etherscan.io/address/0xd98e7a71bacb6f11438a8271ddb2efd7f9361f52) adresinde konuşlandırılmıştır. Commit'ten oluşturulmuştur \[pek yakında].

**ABI**

\[pek yakında]

**Starkware Priority Timelock**, Ethereum mainnet'te [0xa306989BA6BcacdECCf3C0614FfF2B8C668e3CaE](https://etherscan.io/address/0xa306989ba6bcacdeccf3c0614fff2b8c668e3cae) adresinde konuşlandırılmıştır. Commit'ten oluşturulmuştur \[pek yakında].

**ABI**

\[pek yakında]

## DYDX Teşvik Sözleşmeleri

### Merkle Distributor



![Red dashed lines indicate contract is upgradeable](<.. /.gitbook/assets/Screen Shot 2021-09-03 at 5.23.50 PM.png>)

Merkle Distributor akıllı sözleşmesi Merkle bakiyeler ağacına göre DYDX token ödüllerini dağıtır. Ağaç her kullanıcının toplam ödül bakiyesi ile belirli aralıklarla güncellenebilir ve böylece yeni ödüller zaman içerisinde kullanıcılara dağıtılabilir.

Bir güncelleme, teklif edilen Merkle kökünü oracle sözleşmesi tarafından döndürülen en son değere ayarlayarak gerçekleştirilir. Teklif edilen Merkle kökü, bekleme süresi geçtikten sonra aktif hale getirilebilir. Bekleme süresi zarfında, dYdX Yönetişimi teklif edilen kökün yanlış veya kötü amaçlı olması durumunda Merkle kökünü dondurma imkânına sahiptir. Kök güncellemelerinin duraklatması ShortTimelockExecutor tarafından kaldırılabilir.

Merkle Distributor akıllı sözleşmesinde Uniswap ve Badger tasarımlarından esinlenilmiştir. Akıllı sözleşme Ethereum mainnet'te 0x01d3348601968aB85b4bb028979006eac235a588 adresinde konuşlandırılmıştır. Commit'ten oluşturulmuştur \[pek yakında].

**ABI**

\[pek yakında]

### Safety Module



![Red dashed lines indicate contract is upgradeable](<.. /.gitbook/assets/Screen Shot 2021-09-03 at 5.24.45 PM.png>)

Safety Module, Protokol'ün güvenliği için DYDX stake eden kullanıcılara DYDX ödülleri sunan bir staking havuzudur.

**ABI**

\[pek yakında]



### Likidite Modülü



![Red dashed lines indicate contract is upgradeable](<.. /.gitbook/assets/Screen Shot 2021-09-03 at 5.25.30 PM.png>)

Liquidity Module, staking ve borç verme için bir akıllı sözleşme koleksiyonudur ve bu sözleşmeler USDC fonlarının dYdX katman 2 borsası üzerinde piyasa yapıcı amaçları doğrultusunda tahsis edilmesini teşvik eder.

Stake edenler, USDC staking için DYDX ödülleri kazanır. Stake edilen fonlar, belirli önceden onaylanmış ortaklar tarafından itibarlarına bağlı olarak teminatsız bir şekilde borç alınabilir. Bu fonlar sadece L2 borsası üzerinde kullanılabilir. Bu zorunluluk, StarkEx Perpetual Exchange sözleşmesi ile etkileşime giren StarkProxy sözleşmesi aracılığıyla gözetilir.

![A diagram of the Liquidity module](<.. /.gitbook/assets/image (66).png>)

### StarkProxy

Bu sözleşme token sahibinin LiquidityStaking'den fon borç almasına ve bu fonları StarkPerpetual'da kullanmasına olanak tanır. Token sahibi tarafından daha fazla fon yatırılabilir ve borç alınan tutarın üzerindeki fonlar serbestçe çekilebilir. Bu sözleşme, Starkware tarafından yazılmış ve daha önce denetlenmiş ve konuşlandırılmış olan [StarkPerpetual](https://github.com/starkware-libs/starkex-contracts/tree/master/scalable-dex/contracts/src/perpetual) sözleşmesi ile etkileşime girer.



### Hazine Sözleşmeleri



![Red dashed lines indicate contract is upgradeable](<.. /.gitbook/assets/Screen Shot 2021-09-03 at 5.26.09 PM.png>)

TreasuryVester sözleşmesinde [Uniswap](https://github.com/Uniswap/governance/blob/master/contracts/TreasuryVester.sol)'tan esinlenilmiştir.

Short Timelock yalnızca yönetişim tarafından onaylanmış eylemleri yürütebilir.

İki treasury vester ve hazine sözleşmesi vardır. Bunların ilki teşvik sözleşmesi ödülleri için, diğeri ise “genel amaçlı” hazine fonlarını tutmak içindir.

Her bir hazineyi yönetişim kontrol ettiğinden, her iki hazineden de fonları herhangi bir adrese aktarabilir ve/veya fonların harcanacağı herhangi bir adresi onaylayabilir. Örneğin, ödül programlarında yönetişim tarafından belirlenen token onay limitleri olması gerekir.

Her bir treasury vester, token'ları ilgili hazineye \~5 yıl (3 Ağustos 2021 - 3 Ağustos 2026) boyunca doğrusal bir şekilde vest edecektir.



## Harici Sözleşmeler

### Chainlink Oracle Tarafından Desteklenen Ödüller (Alım Satım ve Likidite Sağlayıcı Ödülleri)

Bu sistemin amacı, dYdX katman 2 borsasını kullanan yatırımcılar tarafından kazanılan DYDX token ödüllerini merkeziyetsiz bir oracle imzalayanları ağı aracılığıyla hesaplamak ve yayınlamaktır. Ödüller, dağıtım programının başlangıcından itibaren her kullanıcı tarafından kazanılan toplam ödülü içeren bir Merkle ağacında saklanır. Her bir dönemde, Merkle kökü son dönemde kazanılan ödülleri yansıtacak şekilde MerkleDistributorV1 akıllı sözleşmesinde güncellenir.

Ödül verilerini zincir içinde yayınlamak için Chainlink Oracle sistemi ile entegre olduk. Chainlink'in Merkle ağacını oluşturmak için kullandığı alım satım verilerini yayınlamak için IPNS kullanıyoruz. IPNS kullanmamız sayesinde, en son dönemin alım satım verilerini önceki dönemlerle aynı IPNS bağlantısı altında yayınlayabiliyoruz ve böylece verilerin konumu değişmiyor.

Chainlink, ham alım satım verilerinden uygun ödülleri hesapladıktan sonra Merkle ödül ağacını IPFS'ye gönderiyor. Merkle ağacı verilerini içeren IPFS CID, o dönemin ödülleri için Merkle kökü ile birlikte Merkle distributor sözleşmesinde saklanıyor.

Aşağıdaki akış grafiği Chainlink Oracle Tarafından Desteklenen Ödüller sistem mimarisini göstermektedir:

![](<.. /.gitbook/assets/Merkle Distributor.png>)

### Diğer Varlıklar

* dYdX Vakfı markalı varlıklar [**burada**](https://dydx.foundation/brand) mevcuttur****

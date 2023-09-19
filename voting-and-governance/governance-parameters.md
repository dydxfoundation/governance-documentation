---
description: Yönetişim parametrelerine genel bakış.
---

# Parametreler

Yönetişimin başladığı tarih itibarıyla, DYDX sahipleri şunlar üzerinde anında ve gayri kabili rücu kontrol sahibidir:

* Topluluk hazinesinin tahsisi
* Protokoldeki yeni token listelemeleri
* Protokolün risk parametreleri
* Likidite staking havuzunda piyasa yapıcılara sermaye tahsisleri
* Likidite staking havuzuna yeni piyasa yapıcıların eklenmesi
* Bir kayıp durumunda güvenlik staking havuzu ödemelerinin belirlenmesi
* Lansman anında mevcut ödüllerin ve havuzlardan herhangi birinin değiştirilmesi
* Yönetişim sözleşmeleri

dYdX Yönetişimi şu sözleşmelerin parametreleri üzerinde kontrol sahibidir:

* [Timelock](https://github.com/dydxfoundation/governance-docs/tree/28153eacbdaafb32078630fafa7ad64f111ac9ab/voting-and-governance-process/parameters.md#timelock-parameters)
* Priority Timelock
* Governor
* DYDX Token
* Hazine
* Merkle Distributor
* Likidite Staking
* Safety Module
* Stark Proxy
* Stark Perpetual

## Timelock Parametreleri

![](../.gitbook/assets/1-initial-timelock-parameters.png)

## Governor Parametreleri

| Parametre | Açıklama | Değer |
| ----------------- | ----------------------------------------------------------------------------- | -------------- |
| Oylama Bekleme Süresi | Teklifin oluşturulması ve oylanması arasındaki bekleme süresi (blok cinsinden) | 6.570 blok |
| Executor rolü ekleyin | Yeni executor ekleyebilen adres | Short Timelock |
| Sahip rolü | Stratejiyi / oylama bekleme süresini değiştirebilir / executor'ların yetkilerini iptal edebilir + diğer rollerin sahibidir | Long Timelock |

## DYDX Token

| Parametre | Açıklama | Değer |
| --------- | ------------------------------------------- | -------------- |
| Sahip | Token çıkarmanın kısıtlanmasının ardından DYDX token'ları çıkarabilir | Short Timelock |

## Ödül Hazinesi Parametreleri

| Parametre | Açıklama | Değer |
| ----------- | ------------------------------------------------------ | -------------- |
| Sahip | Hazine tarafından tutulan herhangi bir token'ı onaylayabilir veya transfer edebilir | Short Timelock |
| Proxy Yöneticisi | Sözleşmenin sürümünü yükseltebilir | Short Timelock |

##

## Topluluk Hazinesi Parametreleri

| Parametre | Açıklama | Değer |
| ----------- | ------------------------------------------------------ | -------------- |
| Sahip | Hazine tarafından tutulan herhangi bir token'ı onaylayabilir veya transfer edebilir | Short Timelock |
| Proxy Yöneticisi | Sözleşmenin sürümünü yükseltebilir | Short Timelock |

##

## Merkle Distributor

| Parametre | Açıklama | Değer |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------ | ---------------------------- |
| Sahip rolü | Ödüllerin oracle adresini güncelleyebilir, IPNS adını güncelleyebilir ve tüm rollerin yöneticisidir | Short Timelock |
| Config updater rolü | Ödül parametrelerini belirleyebilir, dönem takvimini değiştirebilir veya IPFS güncelleme süresini değiştirebilir | Short Timelock |
| Pauser rolü | Merkle kökü üzerindeki güncellemeleri duraklatabilir | Merkle-pauser Timelock |
| Unpauser rolü | Merkle kökü üzerindeki duraklatılmış güncellemeleri tekrar başlatabilir | Short Timelock |
| Claim operator rolü | Bir kullanıcı adına ödülleri alabilir | Claims Proxy |
| Aralık | Bir dönemin uzunluğu | 28 gün |
| Başlangıç noktası | Dönem sıfırın başlangıcı | 3 Ağustos 2021 18.00 (TSİ) |
| IPNS adı | Ödül verilerinin yayınlandığı IPNS adı | rewards-data.dydx.foundation |
| IPFS güncelleme süresi | Dönem sona erdikten sonra yeni dönemin borsa istatistiklerinin IPNS adı aracılığıyla IPFS üzerinde yayınlanmaya başlaması gereken süre | 3 dakika |
| Proxy Yöneticisi | Sözleşmenin sürümünü yükseltebilir | Short Timelock |

##

## Likidite Staking

| Parametre | Açıklama | Değer |
| --------------------- | --------------------------------------------------------------------------------- | ------------------------- |
| Sahip rolü | Tüm rollerin yöneticisi | Short Timelock |
| Dönem parametreleri rolü | Aralık, başlangıç noktası ve karartma süresi gibi dönem parametrelerini belirleyebilir | Short Timelock |
| Ödül oranı rolü | Ödüllerin verilme oranını belirleyebilir | Short Timelock |
| Borç alan yöneticisi rolü | Borç alanların tahsislerini belirleyebilir ve borç alanların borç almasına izin verebilir/almasını kısıtlayabilir | Short Timelock |
| Claim operator rolü | Bir kullanıcı adına ödülleri alabilir | Claims Proxy |
| Stake operator rolü | Kullanıcının stake edilen fonlarını bir kullanıcı adına idare edebilir (örneğin fon çekme işlemi gerçekleştirebilir) | Short Timelock |
| Debt operator rolü | Borç alanların borcunu azaltabilir ve stake edenlerin borcunu azaltabilir | Short Timelock |
| Aralık | Bir dönemin uzunluğu | 28 gün |
| Başlangıç noktası | Dönem sıfırın başlangıcı | 3 Ağustos 2021 18.00 (TSİ) |
| Karartma süresi | Karartma süresinin uzunluğu | 3 gün |
| Ödül verme oranı | Stake edenlere saniye başına ödül olarak tahsis edilen token'lar | 0 |
| Proxy Yöneticisi | Sözleşmenin sürümünü yükseltebilir | Short Timelock |

## Safety Module

| Parametre | Açıklama | Değer |
| --------------------- | --------------------------------------------------------------------------------- | ------------------------- |
| Sahip rolü | Tüm rollerin yöneticisi | Short Timelock |
| Slasher rolü | Stake edilen token bakiyelerini slash edebilir ve bu fonları çekebilir | Short Timelock |
| Dönem parametreleri rolü | Aralık, başlangıç noktası ve karartma süresi gibi dönem parametrelerini belirleyebilir | Short Timelock |
| Ödül oranı rolü | Ödüllerin verilme oranını belirleyebilir | Short Timelock |
| Claim operator rolü | Bir kullanıcı adına ödülleri alabilir | Claims Proxy |
| Stake operator rolü | Kullanıcının stake edilen fonlarını bir kullanıcı adına idare edebilir (örneğin fon çekme işlemi gerçekleştirebilir) | Short Timelock |
| Aralık | Bir dönemin uzunluğu | 28 gün |
| Başlangıç noktası | Dönem sıfırın başlangıcı | 3 Ağustos 2021 18.00 (TSİ) |
| Karartma süresi | Karartma süresinin uzunluğu | 3 gün |
| Ödül verme oranı | Stake edenlere saniye başına ödül olarak tahsis edilen token'lar | 0 |
| Proxy Yöneticisi | Sözleşmenin sürümünü yükseltebilir | Long Timelock |

## Stark Proxy

| Parametre | Açıklama | Değer |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------- |
| Sahip rolü | Fon alan alıcıları ve STARK anahtarlarını ekleyebilir/kaldırabilir, likidite staking ve stark perpetual sözleşmelerinde ERC20 tahsislerini belirleyebilir, zorlanan eylemleri çağırabilir ve sahip + delegasyon yöneticisi rollerinin yöneticisidir | Piyasa Yapıcı |
| Delegasyon yöneticisi rolü | Borç alan, exchange operator ve withdrawal operator rollerinin yöneticisidir | Piyasa Yapıcı |
| Borç alan rolü | Likidite staking sözleşmesinde borç alma fonksiyonlarını çağırabilir | Piyasa Yapıcı |
| Exchange operator rolü | Stark perpetual sözleşmesinde borsa fonksiyonlarını çağırabilir | Piyasa Yapıcı |
| Withdrawal operator rolü | Borç alınan bakiyeden fazla olan fonları izin verilen bir alıcıya çekebilir | Piyasa Yapıcı |
| Guardian rolü | Borç alanın vadesi dolduğu halde ödenmemiş borcu varsa kapatma eylemlerini ve zorlama eylemlerini gerçekleştirebilir, borç alınan fonlarla açma işlemlerini kısıtlayabilir ve withdrawal operator rolü tarafından harici olarak çekilecek bir token miktarını onaylayabilir. | Short Timelock |
| Veto guardian rolü | Sahip tarafından başlatılan zorla alım satım taleplerini bekleme süresi boyunca veto edebilir | Merkle-pauser Timelock |

## Stark Perpetual

| Parametre | Açıklama | Short Timelock Executor | Merkle-Pauser Executor | Long Timelock Executor | Starkware Executor |
| -------------------------------------- | ----------- | ----------------------- | ---------------------- | ---------------------- | ------------------ |
| Yeni varlık ekle |             | H | H | H | E |
| Mevcut varlığın yapılandırmasını değiştirin |             | H | H | H | E |
| Proxy Yöneticisi |             | H | H | H | E |
| Operator ekle |             | H | H | H | E |
| Operator kaldır |             | H | H | H | E |
| Doğrulayıcı ekle |             | H | H | H | E |
| Doğrulayıcı kaldır |             | H | H | H | E |

---
description: >-
  Bu kılavuz, piyasa yapıcı katılımını kolaylaştırmak için dYdX ekibi tarafından hazırlanmıştır. Entegrasyon adımlarına başlamadan önce lütfen bu belgeyi baştan sona okuyun.
---

# Piyasa Yapıcı Katılım Süreci

## dYdX Tarafından Önerilen Piyasa Yapıcı Katılım Süreci Akışı:

1. Tercih ettiğiniz Ethereum cüzdanını dYdX L2 Perpetual protokolüne bağlayın.
2. Perpetual hesabınıza USDC yatırın.
3. Katman 2 üzerindeki hesabınızı tanımlayan ve tarayıcınızda yerel olarak kaydedilen bir STARK Anahtarı oluşturmanız gerekecektir. Stark Anahtarı dYdX kullanıcılarını Ethereum hesap adresleri ile ilişkilendirir. Dolayısıyla, bir kullanıcı önce bir Ethereum anahtarının bir STARK Anahtarına bağlanmasını imzalamayı talep etmeli ve ardından da başka herhangi bir işlemin gerçekleşebilmesi için önce dYdX'in akıllı sözleşmesinde STARK Anahtarını kaydetmelidir. “Stark Anahtarı Oluştur”a tıklayın ve işlemi imzalayın. İmzalama ücretsizdir ve bir işlem göndermez. Stark Anahtarınızı cüzdanınızla dilediğiniz zaman geri yükleyebilirsiniz.

Alternatif olarak, programlamayı bilen yatırımcılar şu yöntemi kullanarak STARK anahtar çiftini türetebilir:

```
key_pair_with_y_coordinate = client.onboarding.derive_stark_key(
  # Optional if eth_private_key or web3.eth.defaultAccount was provided.
  ethereum_address='ethereumAddress',
)
```

STARK Anahtarları hakkında daha fazla bilgiyi burada bulabilirsiniz.

4\. Bunun ardından, Ethereum imzanızı gerektiren ve bir web3 sağlayıcısı aracılığıyla edinebileceğiniz bir API anahtarına ihtiyacınız olacaktır. Not: Eth imzalarına yalnızca katılım sağlamak ve API anahtarlarını yönetmek için ihtiyaç duyulur, alım satım için ise duyulmaz. Alım satım için STARK anahtarı imzaları gerekir. API Anahtarları aşağıdaki işlevleri kullanarak kaydedilebilir ve elde edilebilir:

_Kaydetme:_

```
api_key_response = client.api_keys.create_api_key(
# Optional if eth_private_key or web3.eth.defaultAccount was provided.
ethereum_address='0x0123...',
)
```

_Elde Etme:_

```
api_keys = client.private.get_api_keys()
```

_Alternatif olarak (3. Ve 4.)_, özel anahtarın çevrimiçi olmasını istemiyorsanız, gerekli kimlik bilgilerini almak için aşağıdaki adımlarla STARK anahtarını güvenli bir şekilde oluşturabilirsiniz.

a. dYdX Perpetuals borsasındayken web tarayıcınızda herhangi bir yere sağ tıklayın ve Geliştirici Araçlarını açmak için İncele ögesini seçin

Sırasıyla Application > Local Storage > https://trade.dydx.exchange ögelerine gidin

c. STARK\_KEY\_PAIRS ögesini seçin ve stark özel anahtarını almak için cüzdan adresinizin yanındaki açılır listeye tıklayın

d. API\_KEY\_PAIRS ögesini seçin ve API anahtarı, gizli anahtar ve parolayı almak için cüzdan adresinizin yanındaki açılır listeye tıklayın

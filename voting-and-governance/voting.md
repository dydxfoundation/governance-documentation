---
description: Oylama sürecine genel bir bakış.
---

# Oylama Süreci

Protokol, DYDX sahipleri ve delegeler tarafından yönetilir ve yükseltilir.

## **Öneri Verme ve Oy Verme Yetkileri**

Her DYDX token ile ilişkili iki yetki vardır:

* **Öneri Verme yetkisi **bir öneri oluşturma ve sürdürme erişimi sağlar.
* **Oy verme yetkisi** mevcut teklifler lehine veya aleyhine oy vermek için kullanılır.

DYDX sahipleri belirli bir blokta sahip oldukları ve kendilerine delege edilen token'ların toplamı ile orantılı yönetişim yetkileri alırlar.

**`Öneri Verme Yetkisi =`**`DYDX token'larından gelen Öneri Verme Yetkisi +`

`Stake Edilen DYDX token'larından gelen Öneri Verme Yetkisi +`

``Delege olarak alınan DYDX tokenlerinden gelen Öneri Verme Yetkisi +

`Delege olarak alınan stake edilmiş DYDX tokenlerinden gelen Öneri Verme Yetkisi -`

`Delege edilen DYDX'ten gelen Öneri Verme Yetkisi -`

`Stake edilen DYDX'ten gelen Öneri Verme Yetkisi`

\`\`

**`Oy Verme Yetkisi =`**`DYDX tokenlerinden gelen Oy Verme Yetkisi +`

`Stake Edilen DYDX token'larından gelen Oy Verme Yetkisi +`

`Delege edilen olarak alınan DYDX token'larından gelen Oy Verme Yetkisi +`

`Delege edilen olarak alınan stkDYDX token'larından gelen Oy Verme Yetkisi -`

`Delege edilen DYDX'ten gelen Oy Verme Yetkisi -`

`Stake Edilen ve delege edilen DYDX'ten gelen Oy Verme Yetkisi`

## SSS

### Nasıl oy veririm?

DYDX zincir içi yönetişimine katılmak için DYDX token'larına sahip olmanız veya DYDX token'larının size delege edilmiş olması gerekir. Ayrıca işlem maliyetlerini karşılamak için ETH'ye de ihtiyacınız olacaktır.

Token sahibi iseniz veya size delege edilmiş tokenleriniz varsa ve aktif bir teklif varsa, dYdX Yönetişiminde oy vermeye hazırsınız demektir.

![Oy verme yetkinizi kullanarak oyunuzu kullanın](../.gitbook/assets/1-voting-power.png)

Oyunuzu vermek için teklifler sayfasına gidin ve aktif bir teklifin üzerine tıklayın.

### **Nasıl delege edebilirim?**

DYDX, sahiplerinin oy verme haklarını kendi seçtikleri bir adrese delege etmelerine olanak tanır. İsteyen herkes, DYDX'e sahip olması gerekmeden, delegasyon alarak dYdX yönetişimine katılabilir. Kullanıcılar bir seferde tek bir adrese delege edebilir ve delegenin oy sayısına eklenen oyların sayısı kullanıcının hesabındaki DYDX bakiyesine eşittir. Oylar, gönderen tekrar delege edene veya DYDX'lerini transfer edene kadar mevcut bloktan ve sonraki bloklardan delege edilir.

![Oy kullanma ve teklif verme yetkilerinizi delege edin](../.gitbook/assets/1-delegate-power.png)

Token sahipleri, yönetişim portalından veya programlama yoluyla bir token ile ilişkili yönetişim yetkilerinden birini veya her ikisini birden delege etmeyi seçebilirler. Delege edilmiş bir yetki alan bir kullanıcı kendisine delege edilen bu yetkiyi başka bir delegeye iletemez.

Token sahipleri teklif verme yetkisini ve oy verme yetkisini farklı adreslere delege edebilir. Ancak kısmi delegasyon yoktur (yetkinin yalnızca %100'ü veya %0'ı).

Tokenlerinizi bir cüzdan adresine delege etmek için:

* [dydx.community/dashboard](https://dydx.community/dashboard) adresine gidin
* "Delege Et" seçeneğine tıklayın
* Delege etmek istediğiniz yetki türünü seçin
* Oy verme ve/veya teklif verme yetkinizi delege etmek istediğiniz üçüncü taraf için bir Cüzdan Adresi girin. Yetkilerin delege edilmesi ile tokenleriniz transfer edilmez

DYDX delege etmek ve delegasyonu iptal etmek kullanıcıların Ethereum gas ücretleri ödemelerini gerektirir.

### Oy verdikten sonra oyumu değiştirebilir miyim?

Zincir içi bir oy verdikten sonra oyunuzu değiştirmeniz mümkün değildir.

### Oy verme işlemi devam ederken DYDX'lerimi transfer edebilir miyim?

Evet.

### Oyuma daha fazla token ekleyebilir miyim?

Zincir içi bir DIP gönderildiğinde, mevcut token sahiplerinin bir anlık görüntüsü alınır. Kullanıcıların başlangıç bloku öncesinde DYDX token'larına sahip olması veya kendisine DYDX token'larının stake edilmiş olması gerekir.

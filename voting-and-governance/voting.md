---
description: Una visión general del proceso de votación.
hidden: true
---

# 🗳️ Proceso de Votación

dYdX v3 está gobernado y actualizado por los titulares y delegados de Tokens de Gobernanza.

## **Poderes de propuesta y votación**

Hay dos poderes asociados con cada uno de los Tokens de Gobernanza:

* El **poder de propuesta** da acceso a la creación y el mantenimiento de una propuesta.
* El **poder de votación** se utiliza para votar a favor o en contra de las propuestas existentes.

Los titulares de tokens de gobernanza reciben poderes de gobernanza proporcionalmente a su suma de tokens propios y delegados en un bloque determinado.

**`Poder de propuesta =`**`Poder de propuesta del token $ethDYDX +`

`Poder de Propuesta del token $wethDYDX +`

`Poder de Propuesta del token $stkDYDX +`

`Poder de propuesta de los tokens de $ethDYDX recibidos como delegados +`

`Poder de Propuesta de los tokens de $wethDYDX recibidos como delegados +`

`Poder de Propuesta de los tokens de $stkDYDX recibidos como delegados -`

`Poder de Propuesta de $ethDYDX delegado -`

`Poder de propuesta de $wethDYDX delegado -`

`Poder de propuesta de $stkDYDX apostado delegado`

\`\`

**`Poder de Voto =`**`Poder de Voto del token $ethDYDX +`

`Poder de voto del token $wethDYDX +`

`Poder de Voto del token $stkDYDX +`

`Poder de voto del token $ethDYDX recibido como delegado +`

`Poder de voto de los tokens de $wethDYDX recibidos como delegados +`

`Poder de voto de los tokens de $stkDYDX recibidos como delegados -`

`Poder de Voto de $ethDYDX delegado -`

`Poder de voto de $wethDYDX delegado -`

`Poder de votación de $stkDYDX delegados`

## Preguntas frecuentes

### ¿Cómo voto?

Para participar en la gobernanza de dYdX, deberás tener o delegar los Tokens de Gobernanza. También necesitarás ETH para cubrir los costos de transacción.

Si tienes tokens o te han delegado tokens y hay una propuesta activa, estás listo/a para votar en la Gobernanza de dYdX.

![Emitir votos usando tu poder de votación](../.gitbook/assets/1-voting-power.png)

Para emitir tu voto, ve a la página de propuestas y haz clic en una propuesta activa.

### **¿Cómo delegar?**

La gobernanza de dYdX permite a los titulares delegar los derechos de voto a la dirección de tu elección. Cualquiera puede participar en la gobernanza de dYdX al recibir una delegación, sin necesidad de ser propietario de Tokens de Gobernanza. Los usuarios pueden delegar a una dirección por vez, y la cantidad de votos agregados al conteo de votos del delegado es equivalente al saldo de Tokens de gobernanza de la cuenta del usuario. Los votos se delegan desde el bloque actual en adelante, hasta que el remitente vuelva a delegar, o transferir sus Tokens de Gobernanza.

![Delegar tus poderes de votación y de propuesta](../.gitbook/assets/1-delegate-power.png)

Los titulares de tokens pueden optar por delegar uno o los dos poderes de gobernanza asociados con un token, ya sea a través del portal de gobernanza o mediante programación. Un usuario que ha recibido un poder delegado no puede transferir este poder delegado a otro usuario.

Los titulares de tokens pueden delegar el poder de propuesta y el poder de voto a diferentes direcciones. Sin embargo, no hay una delegación parcial (solo el 100% o el 0% del poder).

Para delegar tus tokens a una dirección de billetera:

* Ve a [dydx.community/dashboard](https://dydx.community/dashboard)
* Haz clic en "Delegar"
* Selecciona el tipo de poder que deseas delegar
* Ingresa una Dirección de Billetera para un tercero a quien deseas delegar tu poder de voto y/o propuesta. Delegar poderes no transfiere tus tokens

Delegar y deseleccionar tokens de gobernanza requiere que los usuarios gasten tarifas de gas de Ethereum.

### ¿Puedo cambiar mi voto después de haber votado?

Una vez que se emite una votación en la cadena no es posible cambiar tu voto.

### ¿Puedo transferir mis Tokens de gobernanza mientras la votación está en curso?

Sí.

### ¿Puedo agregar más tokens a mi voto?

Cuando se envía un DIP en la cadena, se toma una instantánea de los titulares de tokens actuales. Los usuarios deberán poseer Tokens de gobernanza antes del bloque de inicio.

---
description: >-
  El equipo de dYdX ha creado esta guía para facilitar la incorporación de creadores de mercado. Lee el documento en su totalidad antes de comenzar cualquier paso de integración.
---

# Incorporación de creadores de mercado

## Flujo de incorporación de creador de mercado sugerido por dYdX:

1. Conecta tu billetera preferida de Ethereum al protocolo de perpetuals de dYdX L2.
2. Depositar USDC en tu cuenta de perpetuals.
3. Deberás generar una clave STARK que identifique tu cuenta en la Capa 2 y se guarde localmente en tu navegador. La clave Stark asocia a los usuarios de dYdX con las direcciones de cuenta de Ethereum, por lo que primero un usuario debe solicitar la vinculación de una clave Ethereum a una clave STARK y luego registrar la clave STARK en el contrato inteligente de dYdX antes de que pueda llevarse a cabo cualquier otra operación. Haz clic en "Generate Stark Key" y firma la transacción. La firma es gratuita y no enviará una transacción. Puedes recuperar tu clave de Stark en cualquier momento con tu billetera.

Alternativamente, los traders programáticos pueden obtener su par de claves STARK utilizando el siguiente método:

```
key_pair_with_y_coordinate = client.onboarding.derive_stark_key(
  # Optional if eth_private_key or web3.eth.defaultAccount was provided.
  ethereum_address='ethereumAddress',
)
```

Puedes encontrar más información sobre las claves STARK aquí.

4\. A continuación necesitarás una clave de API que requerirá tu firma de Ethereum o a través de un proveedor de web3. Nota, las firmas de Ethereum solo son necesarias para incorporar y administrar las claves de API pero no para la operación. Las firmas de clave STARK se requieren para realizar operaciones. Las claves de API se pueden registrar y obtener utilizando las siguientes funciones:

_Registro:_

```
api_key_response = client.api_keys.create_api_key(
# Optional if eth_private_key or web3.eth.defaultAccount was provided.
ethereum_address='0x0123...',
)
```

_Obtención:_

```
api_keys = client.private.get_api_keys()
```

_Alternativamente (3. y 4.)_, si no quieres que la clave privada esté en línea, puedes generar la clave STARK de forma segura con los siguientes pasos para obtener las credenciales requeridas.

a. Desde las operaciones de perpetuals de dYdX, haz clic con el botón derecho en cualquier lugar de tu navegador web y selecciona Inspeccionar para abrir las Herramientas de desarrollador

b. Ir a la aplicación > almacenamiento local > https://trade.dydx.exchange

c. Selecciona STARK\_KEY\_PAIRS y haz clic en el menú desplegable junto a tu dirección de billetera para obtener la clave privada de stark

d. Selecciona API\_KEY\_PAIRS y haz clic en el menú desplegable junto a tu dirección de billetera para obtener la clave de API, la clave secreta y la frase de contraseña

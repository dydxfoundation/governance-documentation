---
description: >-
  Um das Onboarding von Marktmachern zu erleichtern, hat das dYdX-Team diesen Leitfaden erstellt. Bitte lesen Sie das Dokument vollständig durch, bevor Sie mit den Integrationsschritten beginnen.
---

# Onboarding für Market Maker

## Von dYdX empfohlener Onboarding-Flow für Marktmacher:

1. Verbinden Sie Ihre bevorzugte Ethereum-Wallet mit dem dYdX L2 Perpetual-Protokoll.
2. Zahlen Sie $USDC auf Ihr Perpetual-Konto ein.
3. Sie müssen einen STARK-Schlüssel generieren, der Ihr Konto auf Ebene 2 identifiziert und lokal in Ihrem Browser gespeichert wird. Der Stark-Schlüssel verknüpft dYdX-Benutzer mit Ethereum-Kontoadressen, sodass ein Benutzer zuerst die Unterzeichnung der Verknüpfung eines Ethereum-Schlüssels mit einem STARK-Schlüssel anfordern und dann den STARK-Schlüssel auf dem Smart-Vertrag von dYdX registrieren muss, bevor eine andere Operation stattfinden kann. Klicken Sie auf „Stark-Schlüssel generieren“ und unterschreiben Sie die Transaktion. Die Signierung ist kostenlos und wird keine Transaktion senden. Sie können Ihren Stark-Schlüssel jederzeit mit Ihrer Wallet wiederherstellen.

Alternativ können programmatische Händler ihr STARK-Schlüsselpaar mit der folgenden Methode ableiten:

```
key_pair_with_y_coordinate = client.onboarding.derive_stark_key(
  # Optional if eth_private_key or web3.eth.defaultAccount was provided.
  ethereum_address='ethereumAddress',
)
```

Mehr über STARK-Schlüssel finden Sie hier.

4\. Als nächstes benötigen Sie einen API-Schlüssel, der Ihre Ethereum-Signatur erfordert, oder über einen Web3-Anbieter. Beachten Sie, dass Eth-Signaturen nur für das Onboarding und die Verwaltung von API-Schlüsseln benötigt werden, nicht jedoch für den Handel – STARK-Schlüsselsignaturen sind für den Handel erforderlich. API-Schlüssel können mit den folgenden Funktionen registriert und abgerufen werden:

_Registrierung:_

```
api_key_response = client.api_keys.create_api_key(
# Optional if eth_private_key or web3.eth.defaultAccount was provided.
ethereum_address='0x0123...',
)
```

_Erhalten:_

```
api_keys = client.private.get_api_keys()
```

_Alternativ (3. und 4.)_ Wenn Sie nicht möchten, dass der private Schlüssel online ist, können Sie den STARK-Schlüssel mit den folgenden Schritten sicher generieren, um die erforderlichen Anmeldeinformationen zu erhalten.

a. Klicken Sie im dYdX Perpetuals Exchange mit der rechten Maustaste auf eine beliebige Stelle in Ihrem Webbrowser und wählen Sie Inspect, um die Developer Tools zu öffnen

b. Gehen Sie zu Anwendung > Lokaler Speicher > https://trade.dydx.exchange

c. Wählen Sie STARK\_KEY\_PAIRS und klicken Sie auf das Dropdown-Menü neben Ihrer Wallet-Adresse, um den starken privaten Schlüssel zu erhalten

d. Wählen Sie API\_KEY\_PAIRS und klicken Sie auf das Dropdown-Menü neben Ihrer Wallet-Adresse, um den API-Schlüssel, den geheimen Schlüssel und die Passphrase abzurufen

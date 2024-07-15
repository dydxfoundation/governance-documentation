---
description: Una descripción general de alto nivel de la arquitectura de gobernanza.
---

#

## Visión general



Las propuestas deben pasar un umbral determinado y un porcentaje de votos positivos según el tipo de propuesta.





*
*
*
* **El contrato `de gobernanza`**: realiza un seguimiento de las propuestas y puede ejecutar propuestas a través del contrato inteligente de bloqueo de tiempo.
* **Los contratos `de bloqueo de tiempo`**: pueden poner en cola, cancelar o ejecutar transacciones votadas por la gobernanza. Las funciones de una propuesta son iniciadas por el contrato de bloqueo de tiempo. Las transacciones en cola se pueden ejecutar después de un retraso y antes de la expiración del período de gracia.
* **El contrato `de Bloqueo cronométrico de prioridad`**: Lo mismo que el contrato de bloqueo de tiempo, pero permite que un controlador de prioridad ejecute transacciones dentro del **período** prioritario (7 días) antes del final del retraso del bloqueo de tiempo.

![Arquitectura de contratos inteligente](../.gitbook/assets/1-smart-contract-architectue.png)

La gobernanza en la cadena de dYdX permite:

* Votar por las propuestas a ser ejecutadas por cualquier contrato ejecutor autorizado
* Participaciones de token instantáneas al comienzo de una propuesta
* Delegar por separado las facultades de voto y propuesta
* Establecer umbrales de gobernanza incluyendo propuestas, quórums y poderes diferenciales de voto
* Cambiar la forma en que se cuentan los votos (cambiando la dirección del contrato inteligente de “Estrategia de gobernanza” en el contrato de gobernanza)

## Tipos de propuestas

Cada tipo de propuesta debe ser validada por un ejecutor.

#### **Ejecutor de bloqueo de corto tiempo**

El ejecutor de bloqueo de corto tiempo controla lo siguiente:

* Los contratos de incentivos como: el módulo de liquidez, el módulo de seguridad y el módulo de distribuidor de Merkle
* Los fondos de las recompensas y tesorerías de la comunidad
* Acuñar nuevos tokens
* todos los contratos de proxy excepto el módulo de seguridad
* roles de custodio en los contratos de proxy de stark

**Ejecutor de bloqueo de tiempo de prioridad de Starkware**



#### **Ejecutor de bloqueo de largo tiempo**



#### **Ejecutor Merkle-pauser**

Ejecutor Merkle-pauser: el ejecutor Merkle-pauser puede ejecutar propuestas que congelan la raíz de Merkle, la cual se actualiza periódicamente con el saldo de recompensa acumulativo de cada usuario, lo que permite distribuir nuevas recompensas a los usuarios a lo largo del tiempo, en caso de que la raíz propuesta sea incorrecta o maliciosa. También puede vetar las solicitudes de operaciones forzadas de cualquiera de los contratos de proxy de stark.

Los parámetros de bloqueo de tiempo inicial son los siguientes:

![Parámetros de bloqueo de tiempo inicial](../.gitbook/assets/1-initial-timelock-parameters.png)

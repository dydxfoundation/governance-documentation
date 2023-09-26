---
description: Visión general de los parámetros de gobernanza.
---

# Parámetros

Al momento de lanzar la gobernanza, los titulares de DYDX tienen control inmediato e irrevocable sobre:

* Asignación de la tesorería de la comunidad
* Nuevos listados de tokens en el Protocolo
* Parámetros de riesgo para el Protocolo
* Asignaciones de capital a creadores de mercado en el fondo de participación de liquidez
* Adición de nuevos creadores de mercado al fondo de participación de liquidez
* Determinar los pagos del fondo de participación de seguridad en caso de una pérdida
* Cambiar cualquiera de las recompensas y fondos existentes en el lanzamiento
* Los propios contratos de gobernanza

La gobernanza dYdX control de los parámetros de los siguientes contratos:

* [Bloqueo de tiempo](https://github.com/dydxfoundation/governance-docs/tree/28153eacbdaafb32078630fafa7ad64f111ac9ab/voting-and-governance-process/parameters.md#timelock-parameters)
* Bloqueo de tiempo de prioridad
* Gobernador
* Tokens de DYDX
* Tesorería
* Distribuidor Merkle
* Participación de liquidez
* Módulo de seguridad
* Proxy de Stark
* Perpetuals de Stark

## Parámetros de bloqueo de tiempo

![](../.gitbook/assets/1-initial-timelock-parameters.png)

## Parámetros de gobernanza

| Parámetro | Descripción | Valor |
| ----------------- | ----------------------------------------------------------------------------- | -------------- |
| Retraso de votación | Retraso (en bloques) entre la creación de propuestas y la votación | 6,570 bloques |
| Agregar un rol de ejecutor | Dirección que puede agregar nuevos ejecutores | Bloqueo de corto tiempo |
| Función de propietario | Puede cambiar la estrategia / retraso de votación / desautorizar ejecutores y tiene otros roles | Bloqueo de largo tiempo |

## Tokens de DYDX

| Parámetro | Descripción | Valor |
| --------- | ------------------------------------------- | -------------- |
| Propietario | Puede acuñar tokens de DYDX después de la restricción de acuñación | Bloqueo de corto tiempo |

## Parámetros de tesorería de recompensas

| Parámetro | Descripción | Valor |
| ----------- | ------------------------------------------------------ | -------------- |
| Propietario | Puede aprobar o transferir cualquier token en poder de la tesorería | Bloqueo de corto tiempo |
| Administrador de proxy | Puede actualizar el contrato | Bloqueo de corto tiempo |

##

## Parámetros de tesorería de la comunidad

| Parámetro | Descripción | Valor |
| ----------- | ------------------------------------------------------ | -------------- |
| Propietario | Puede aprobar o transferir cualquier token en poder de la tesorería | Bloqueo de corto tiempo |
| Administrador de proxy | Puede actualizar el contrato | Bloqueo de corto tiempo |

##

## Distribuidor Merkle

| Parámetro | Descripción | Valor |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------ | ---------------------------- |
| Función de propietario | Puede actualizar la dirección del oráculo de recompensas, actualizar el nombre de IPNS y es administrador de todos los roles | Bloqueo de corto tiempo |
| Función de actualización de configuración | Puede establecer parámetros de recompensas, cambiar el cronograma de la etapa o cambiar el período de actualización de IPFS | Bloqueo de corto tiempo |
| Función de pauser | Puede detener las actualizaciones de la raíz de merkle | Bloqueo de tiempo de Merkle-pauser |
| Función de Unpauser | Puede reanudar las actualizaciones de la raíz de merkle | Bloqueo de corto tiempo |
| Función de operador de reclamos | Puede reclamar recompensas en nombre de un usuario | Proxy de reclamos |
| Intervalo | Duración de una etapa | 28 días |
| Compensación | Inicio de la etapa 0 | 3 de agosto de 2021, 15:00 UTC |
| Nombre de IPNS | Nombre de IPNS en el que se publican los datos de recompensas | rewards-data.dydx.foundation |
| Período de actualización de IPFS | Período de tiempo después del final de la etapa después de la cual las estadísticas de intercambio de la nueva etapa deberían estar disponibles en IPFS a través del nombre de IPNS | 3 minutos |
| Administrador de proxy | Puede actualizar el contrato | Bloqueo de corto tiempo |

##

## Participación de liquidez

| Parámetro | Descripción | Valor |
| --------------------- | --------------------------------------------------------------------------------- | ------------------------- |
| Función de propietario | Administración de todos los roles | Bloqueo de corto tiempo |
| Función de parámetros de etapa | Puede establecer parámetros de la etapa como el intervalo, el desplazamiento y la ventana de bloqueo | Bloqueo de corto tiempo |
| Función de tasa de recompensas | Puede establecer la tasa de emisión de recompensas | Bloqueo de corto tiempo |
| Función de administrador de prestatario | Puede establecer asignaciones de prestatarios y permitir o restringir a los prestatarios | Bloqueo de corto tiempo |
| Función de operador de reclamos | Puede reclamar recompensas en nombre de un usuario | Proxy de reclamos |
| Función de operador de participación | Puede manipular los fondos invertidos de un usuario (por ejemplo, realizar retiros de usuario) | Bloqueo de corto tiempo |
| Función de operador de deuda | Puede disminuir las deudas de préstamo y disminuir las deudas de los inversores | Bloqueo de corto tiempo |
| Intervalo | Duración de una etapa | 28 días |
| Compensación | Inicio de la etapa 0 | 3 de agosto de 2021, 15:00 UTC |
| Ventana de bloqueo | Duración de la ventana de bloqueo | 3 días |
| Tasa de emisión de recompensas | Tokens asignados a los inversores como recompensas por segundo | 0 |
| Administrador de proxy | Puede actualizar el contrato | Bloqueo de corto tiempo |

## Módulo de seguridad

| Parámetro | Descripción | Valor |
| --------------------- | --------------------------------------------------------------------------------- | ------------------------- |
| Función de propietario | Administración de todos los roles | Bloqueo de corto tiempo |
| Función de Slasher | Puede reducir los saldos de los tokens invertidos y retirar esos fondos | Bloqueo de corto tiempo |
| Función de parámetros de etapa | Puede establecer parámetros de la etapa como el intervalo, el desplazamiento y la ventana de bloqueo | Bloqueo de corto tiempo |
| Función de tasa de recompensas | Puede establecer la tasa de emisión de recompensas | Bloqueo de corto tiempo |
| Función de operador de reclamos | Puede reclamar recompensas en nombre de un usuario | Proxy de reclamos |
| Función de operador de participación | Puede manipular los fondos invertidos de un usuario (por ejemplo, realizar retiros de usuario) | Bloqueo de corto tiempo |
| Intervalo | Duración de una etapa | 28 días |
| Compensación | Inicio de la etapa 0 | 3 de agosto de 2021, 15:00 UTC |
| Ventana de bloqueo | Duración de la ventana de bloqueo | 3 días |
| Tasa de emisión de recompensas | Tokens asignados a los inversores como recompensas por segundo | 0 |
| Administrador de proxy | Puede actualizar el contrato | Bloqueo de largo tiempo |

## Proxy de Stark

| Parámetro | Descripción | Valor |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------- |
| Función de propietario | Puede agregar/eliminar destinatarios que reciben fondos + claves de STARK, establecer asignaciones de ERC20 en operaciones de liquidez y contratos de perpetuals estrictos, utilizar acciones forzadas y es administrador como propietario + roles de administrador de delegación | Creador de mercado |
| Función de administrador de delegación | Es el administrador de los prestatarios, operador de bolsa y ejerce los roles de operador de retiros | Creador de mercado |
| Función de prestatario | Puede utilizar funciones de préstamo en el contrato de participación de liquidez | Creador de mercado |
| Función de operador de bolsa | Puede usar funciones de bolsa en el contrato de perpetuals de stark | Creador de mercado |
| Función de operador de retiros | Puede retirar fondos en exceso del saldo prestado a un destinatario permitido | Creador de mercado |
| Función de custodio | Puede realizar acciones de cierre, acciones forzadas si el prestatario tiene una deuda vencida, restringir acciones abiertas con fondos prestados y aprobar un monto simbólico para ser retirado externamente por el rol de operador de retiros. | Bloqueo de corto tiempo |
| Función de custodio de veto | Puede vetar las solicitudes de operaciones forzadas iniciadas por el propietario, durante el período de espera | Bloqueo de tiempo de Merkle-pauser |

## Perpetuals de Stark

| Parámetro | Descripción | Ejecutor de bloqueo de corto tiempo | Ejecutor Merkle-pauser | Ejecutor de bloqueo de largo tiempo  | Ejecutor de Starkware |
| -------------------------------------- | ----------- | ----------------------- | ---------------------- | ---------------------- | ------------------ |
| Agrega un nuevo activo |             | N | N | N | Y |
| Cambia la configuración de los activos existentes |             | N | N | N | Y |
| Administrador de proxy |             | N | N | N | Y |
| Añadir operador |             | N | N | N | Y |
| Eliminar el operador |             | N | N | N | Y |
| Añadir verificador |             | N | N | N | Y |
| Eliminar el verificador |             | N | N | N | Y |

---
description: Descripción general de los términos clave relacionados con la gobernanza.
---

# Glosario

$**ethDYDX:** El activo nativo del ecosistema dYdX basado en Ethereum que constituye la base de la gobernanza y la seguridad de dYdX v3. $ethDYDX es un token ERC-20 que designa el peso del poder de voto o propuesta de un usuario.

**$wethDYDX:** La versión envuelta de $ethDYDX que se obtiene interactuando con el contrato inteligente $wethDYDX. $wethDYDX es un token ERC-20 que designa el peso del poder de voto o propuesta de un usuario.

**dYdX v3:** Protocolo perpetuo de la Capa 2 de dYdX.

**Fundación dYdX:** una fundación independiente, con sede en Zug, Suiza, creada para participar en el impulso del Protocolo dYdX a futuro.

**Contrato de Token $ethDYDX**: Contiene instantáneas del poder de voto de cada dirección en diferentes bloques en el tiempo.

**Contrato de Token $wethDYDX**: Contiene instantáneas del poder de voto de cada dirección en diferentes bloques en el tiempo.

**DIP:** las propuestas de mejoras de dYdX son propuestas en cadena.

**DRC**: las solicitudes de comentarios de dYdX son propuestas fuera de la cadena y el primer paso requerido en el proceso de mejora de la gobernanza.

**Quórum:** para que se apruebe una votación, debe lograr un quórum positivo mínimo de tokens DYDX. El propósito del quórum es asegurar que únicamente las medidas que se aprueben tengan la participación adecuada de los votantes.

**Etapa:** Todos los demás contratos funcionan en ciclos de 28 días, conocidos como etapas.

**Período de gracia de ejecución:** el período después de la votación cuando una propuesta de DIP se ejecuta, durante el cual debe ser ejecutada.

**Contrato de estrategia de gobernanza V2**: Contiene la lógica de medición del poder relativo de los usuarios para proponer y votar.

**Contrato de gobernanza**: realiza un seguimiento de las propuestas y puede ejecutar propuestas a través del contrato inteligente de bloqueo de tiempo.

**Ejecutor de bloqueo de tiempo largo**: el ejecutor de bloqueo de tiempo largo puede ejecutar propuestas que generalmente modifican partes del Protocolo que afectan el consenso de gobernanza.

**Ejecutor de Merkle-pauser:** el ejecutor de Merkle-pauser puede ejecutar propuestas que congelan la raíz de Merkle, la cual se actualiza periódicamente con el saldo de recompensa acumulativo de cada usuario, lo que permite distribuir nuevas recompensas a los usuarios a lo largo del tiempo, en caso de que la raíz propuesta sea incorrecta o maliciosa.

**Fondo de seguridad:** componente a cargo de proteger el protocolo de la insolvencia.

**Contrato de dYdX invertido:** contiene las dinámicas para invertir tokens DYDX, tokenizar la posición y obtener recompensas.

**Ejecutor de bloqueo de corto tiempo:** el ejecutor de bloqueo de corto tiempo puede ejecutar propuestas que generalmente cambian los contratos de recompensas e incentivos o la tesorería de la comunidad que requieren una intervención rápida.

**Ejecutor de Starkware:** el ejecutor de Starkware puede ejecutar propuestas generalmente que modifican partes del protocolo que actualmente requieren la intervención de Starkware.

**Contrato de bloqueo de tiempo**: puede poner en cola o cancelar o ejecutar las transacciones votadas por la gobernanza. Las funciones de una propuesta son iniciadas por el contrato de bloqueo de tiempo. Las transacciones en cola se pueden ejecutar después de un retraso y hasta la finalización del período de gracia.

**Retraso de bloqueo de tiempo:** el retraso antes de que una propuesta de DIP se ejecute después de que una propuesta pase e ingrese a la cola.

**Umbral** de propuesta: para evitar un sistema en el que se crean innumerables propuestas de spam, un umbral de propuesta requiere que una dirección tenga una cierta cantidad de votos antes de poder hacer una propuesta.

**Poder de** propuesta: la participación de tokens que da acceso a la creación y el mantenimiento de una propuesta.

**Poder de voto:** poder de voto que se utiliza para votar a favor o en contra de las propuestas existentes.

**Retraso de votación:** este es el período de tiempo durante el cual se puede crear una propuesta y estar disponible para ser votada. Al requerir que se apruebe al menos un bloque, la gobernanza está protegida de los ataques de Crédito Flash que pueden tomar prestado una gran cantidad de tokens, proponer una votación y votar todo en un mismo bloque.

**Período de votación:** una vez que se haya presentado una propuesta de DIP, los miembros de la comunidad de DYDX tendrán que emitir sus votos antes del final del período de votación. Este es el período de tiempo durante el cual las propuestas están disponibles para ser votadas, con tiempo en Bloques de Ethereum.

**Umbral de propuesta:** los tokens mínimos mantenidos/delegados necesarios para crear una propuesta de DIP.

**Diferencial de votación:** la brecha de sí o no que se requiere para que se apruebe la propuesta de DIP.

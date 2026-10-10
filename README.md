# Sucursal WebLogic

Monitor animado en pixel art (estilo juegos de 16 bits) que explica, y más adelante monitorea, la capa media de pagos sobre Oracle WebLogic.

La idea es que alguien que nunca ha visto WebLogic entienda, solo mirando la animación, qué es un hilo, una conexión del pool, el directorio JNDI, una cola JMS y por qué un problema en la base de datos se ve como un problema en el servidor de aplicaciones.

## Cómo verlo

Abre `index.html` en el navegador. No necesita instalación ni servidor. Se ve mejor en computador.

## Las dos vistas

**1 · La central (ambientes).** Cómo viajan las transacciones entre entidades genéricas (redes, bancos, cajeros, datáfonos), un balanceador SLB y dos nodos en clúster. Incluye la caída de un nodo y el failover.

**2 · Dentro de WebLogic.** Un Managed Server dibujado como un edificio en corte:

| En el edificio | En WebLogic |
|---|---|
| El edificio | Managed Server `ms1` |
| Empleados del lobby (H1, H2…) | Hilos del Work Manager |
| Directorio del lobby | Árbol JNDI |
| Conmutador del piso 1 (columnas) | Data Source y su pool de conexiones |
| Bóveda en el edificio de enfrente | Base de datos Oracle |
| Correspondencia del sótano | Cola JMS persistente |
| Archivo en disco | Persistent Store (File Store) |
| Back office (M1, M2) | MDB |
| Bandeja roja | Cola de error |

Escenarios incluidos: pool corto, fuga de conexiones, BD lenta e hilos stuck, MDB detenido, tablespace lleno (`ORA-01653`) y archivelogs llenos (`ORA-00257`).

Fallas graves con alarma: **BD caída**, **JMS Server caído** (File Store sin espacio) y **pool insuficiente**. Los personajes afectados quedan fuera de combate, suena la sirena y un tablero de alerta explica la causa, las métricas que la delatan y cómo recuperarse (en el caso del pool, con un Maximum Capacity recomendado).

Las métricas usan los nombres reales de los MBeans de runtime de WebLogic (`ActiveConnectionsCurrentCount`, `WaitingForConnectionCurrentCount`, `MessagesCurrentCount`, `StuckThreadCount`…).

## Personajes

- **Mandy**, la gerente: da las alertas. Es un homenaje a mi gata siamesa.
- **El ingeniero de mantenimiento**, con casco: va al sitio del problema y propone el paso del runbook.

## Estado

Fase 0: prototipo visual con **datos simulados**. El plan completo está en [`docs/PLAN.md`](docs/PLAN.md).

## Aviso

Modelo didáctico con entidades genéricas. No contiene IPs, puertos, nombres de clientes ni configuración real de ninguna empresa, y no representa la arquitectura interna de ninguna organización.

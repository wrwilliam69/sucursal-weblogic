# Plan del proyecto

## Fase 0 · Punto cero (hecho)

- [x] Prototipo en un solo `index.html` con datos simulados.
- [x] Vista 1 "La central": entidades, SLB, dos nodos, failover.
- [x] Vista 2 "Dentro de WebLogic" como edificio: hilos, JNDI, Data Source, BD, cola JMS, File Store, MDB, cola de error.
- [x] Escenarios: pool corto, fuga, BD lenta, MDB detenido, tablespace lleno, archivelogs llenos.
- [x] Placas H1/M1, letreros con conteo en vivo y leyenda.
- [x] Mandy (gerente) y el ingeniero de mantenimiento.

## Fase 1 · Conceptos según la documentación

- [ ] Verificar los textos del diccionario contra la documentación oficial de Oracle para la versión de WebLogic del laboratorio: valores por defecto, nombres de MBeans, rutas REST y WLST.

## Fase 2 · Analogías

- [ ] Documentar la tabla concepto → analogía → métrica → personaje como guion del proyecto.

## Fase 3 · Armado del proyecto

- [ ] Escribir `AGENTS.md` con las reglas para el agente de código.
- [ ] Separar la fuente de datos (simulada o real) de la escena gráfica.
- [ ] Decidir si se queda en canvas propio o se migra a Phaser.
- [ ] Estimar costos: EC2 del laboratorio, herramientas y horas.

## Fase 4 · Parte gráfica

- [ ] Sprites dibujados a mano (Piskel o Aseprite) para Mandy, el ingeniero y los personajes.
- [ ] Mejorar la vista en celular.
- [ ] Placas, letreros y leyenda también en la vista 1.

## Fase 5 · Conexión real (laboratorio EC2)

- [ ] Crear `jdbc/PagosDS` y la cadena JMS completa en `ms1`.
- [ ] App de prueba que genere carga, con escenarios de fuga y consulta lenta.
- [ ] Usuario con rol Monitor; probar llamadas REST y WLST.
- [ ] Backend que lea las métricas y alimente las vistas.
- [ ] Opcional: WebLogic Monitoring Exporter con Prometheus.

## Fase 6 · LinkedIn

- [ ] Grabar GIF o video de las dos vistas desde el computador.
- [ ] Publicar la serie de posts por hitos.

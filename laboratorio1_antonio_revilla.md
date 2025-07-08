# Análisis de Caso: Boeing 737 MAX

## Causa raíz del problema

El Boeing 737 MAX incorporó el sistema MCAS (Maneuvering Characteristics Augmentation System) para ajustar automáticamente la inclinación del avión durante ciertas maniobras. Este sistema dependía únicamente de un sensor de ángulo de ataque (AOA). Cuando ese sensor falló, el MCAS activó comandos erróneos que llevaron al avión a picar, sin que los pilotos tuvieran forma clara de corregirlo. Esto provocó los accidentes de Lion Air (2018) y Ethiopian Airlines (2019), con un total de 346 muertes.

La causa raíz fue la falta de mecanismos de **redundancia y verificación cruzada** en un sistema crítico. Además, hubo **falta de transparencia** hacia los pilotos y reguladores sobre el funcionamiento del MCAS, junto con **presiones comerciales** que empujaron a minimizar pruebas y tiempos de entrega.

## Principios de Ingeniería de Software violados

- **Validación y pruebas insuficientes:** No se realizaron pruebas exhaustivas para simular fallos del sensor AOA ni se validaron comportamientos en condiciones extremas.
- **Requisitos mal definidos:** El diseño del MCAS no contempló la necesidad de sensores múltiples, lógica de validación, ni la interacción con los pilotos ante fallos.
- **Falta de ética profesional:** Boeing ocultó información relevante y tomó decisiones que priorizaron el negocio sobre la seguridad del sistema.
- **Ausencia de confiabilidad por diseño:** No se aplicaron principios de *redundancia* ni *diversidad funcional*, fundamentales en sistemas críticos.
- **No se consideraron los principios de confiabilidad del software:** En un sistema crítico como el MCAS, no se aplicaron prácticas básicas de ingeniería de confiabilidad, como la incorporación de redundancia, diversidad funcional o mecanismos de detección y recuperación ante fallos. La ausencia de estas prácticas dejó al sistema vulnerable a fallas únicas, afectando directamente su disponibilidad y seguridad.

## ¿Cómo podría haberse evitado?

- **Redundancia con diversidad:** Incorporar múltiples sensores de AOA y aplicar lógica de votación para validar datos antes de activar el MCAS.
- **Pruebas rigurosas:** Realizar simulaciones de fallos de sensores y condiciones extremas, siguiendo estándares como DO-178C para software aeronáutico.
- **Documentación y capacitación clara:** Informar a los pilotos sobre el MCAS desde el principio y ofrecer entrenamiento para manejar fallos.
- **Cultura organizacional centrada en la seguridad:** Fomentar la transparencia interna, la comunicación de riesgos y la supervisión independiente por parte de reguladores.

# Comparación de Métodos: Linux Kernel vs. Proyecto Personal Ad-hoc

A continuación, se presenta una tabla comparativa entre el desarrollo del **Linux Kernel** (proceso riguroso) y un **proyecto personal sin pruebas** (ad-hoc), evaluando criterios clave de ingeniería de software.

| Criterio                          | Linux Kernel (Riguroso)                                                                 | Proyecto Personal (Ad-hoc)                                    |
|-----------------------------------|---------------------------------------------------------------------------------------|-------------------------------------------------------------|
| **Gestión de Requisitos**         | Requisitos documentados y trazables mediante Git, listas de correo y wikis. Validados por la comunidad. | Requisitos implícitos, definidos informalmente, cambiantes sin registro. |
| **Pruebas Automatizadas**         | Cubrimiento >80% con pruebas unitarias, integración y regresión usando KernelCI y scripts personalizados. | Pruebas manuales esporádicas o inexistentes, sin cobertura definida. |
| **Métricas de Calidad**           | Uso de SonarQube, CodeClimate, estándares ISO 25010. Defectos por KLOC monitorizados (<1 por 1000 líneas). | Sin métricas ni herramientas de calidad aplicadas.           |
| **Gestión de Configuración**      | Control de versiones con Git, ramas estables y revisiones formales por maintainers.    | Sin control de versiones o uso básico (ej. copias locales).  |
| **Documentación**                 | Extensa: manuales, wikis, comentarios en código. Actualizada en cada release.         | Mínima o inexistente, sin estándares ni mantenimiento.       |
| **Ciclo de Desarrollo**           | Iterativo con releases (~2 meses), planificación clara y revisiones por pares.        | Caótico, sin fases definidas ni planificación estructurada.  |
| **Gestión de Riesgos**            | Identificación proactiva de riesgos, mitigación mediante pruebas y auditorías.        | Sin gestión de riesgos, problemas detectados en producción. |
| **Colaboración y Revisión**       | Revisión de código por múltiples desarrolladores, con procesos formales (pull requests). | Sin revisiones formales, cambios implementados sin validación. |
| **Escalabilidad y Mantenimiento** | Diseño modular, código mantenible, soporte para múltiples arquitecturas.              | Código monolítico, difícil de mantener o escalar.            |
| **Cumplimiento Normativo**        | Adherencia a estándares como POSIX y auditorías de seguridad (ej. SELinux).           | Sin consideración de estándares ni normativas.               |

## Referencias
- Redacción. (2024, 7 enero). *Boeing 737 Max: la atribulada historia de los aviones que las autoridades de EE.UU. inmovilizaron tras el incidente de Alaska Airlines*. BBC News Mundo. [https://www.bbc.com/mundo/articles/cjlgd6w2986o](https://www.bbc.com/mundo/articles/cjlgd6w2986o)
- Parra, S. (2024, 9 enero). *La turbulenta historia del Boeing 737 Max 9*. National Geographic España. [https://www.nationalgeographic.com.es/mundo-ng/turbulenta-historia-boeing-737-max-9_21370](https://www.nationalgeographic.com.es/mundo-ng/turbulenta-historia-boeing-737-max-9_21370)
- Wikipedia. (2025, 18 marzo). *Suspensión de vuelo del Boeing 737 MAX*. Wikipedia, la Enciclopedia Libre. [https://es.wikipedia.org/wiki/Suspensi%C3%B3n_de_vuelo_del_Boeing_737_MAX](https://es.wikipedia.org/wiki/Suspensi%C3%B3n_de_vuelo_del_Boeing_737_MAX)

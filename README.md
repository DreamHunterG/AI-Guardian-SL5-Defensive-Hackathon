# AI Guardian

**AI Safety Colombia · Hackathon de IA defensiva · Track 5: Infraestructura y gobernanza (sin código)**
Universidad de los Andes, 14 de noviembre de 2026.

Estándar técnico y regulatorio verificable con los requisitos mínimos que el Estado y los operadores de infraestructura crítica deben exigir **antes de encender un agente basado en un modelo de frontera**.

## Descripción del proyecto

Los modelos de IA de frontera ya pueden actuar como agentes autónomos, y los operadores de servicios esenciales (energía, agua, salud, telecomunicaciones, transporte) empiezan a conectarlos a sus sistemas. Conectados sin controles, un ataque o una falla puede interrumpir un servicio esencial, y los pesos del modelo pueden ser robados.

AI Guardian le dice a la entidad qué exigir, qué evidencia pedir, quién responde y cuándo **no** se enciende el agente: **32 requisitos de sí o no**, cada uno con su evidencia. **Si falla uno, el agente no se enciende.**

## El estándar (versión 3)

| Bloque | Requisitos | Qué cubre |
| --- | --- | --- |
| Seguridad de los pesos | 8 (P1–P8) | Se exige al proveedor según los niveles SL de RAND: llaves en chip seguro, computación confidencial, red aislada, límite de salida, dos personas, firmware firmado, personal verificado |
| Contención | 9 (C1–C9) | Mínimo privilegio, aprobación humana, lo leído no es orden, apagado en segundos, límite de acciones, entorno aislado, evaluación de capacidades peligrosas, doble aprobación con datos fuente, operación manual |
| Auditoría | 5 (A1–A5) | Registro inmodificable, responsable designado, revisión mensual, reporte de incidentes, auditoría externa en N3 |
| Líneas rojas | 7 (LR1–LR7) | Nunca copiar sus pesos, apagar su monitoreo, cambiar sus permisos, atacar otros sistemas, maniobrar sin aprobación, copiarse a sí mismo u obedecer órdenes escondidas |
| Factor humano | 3 (H1–H3) | Separación operar / aprobar / auditar, pruebas sorpresa, aprobaciones firmadas con sanción y canal de denuncia |

**Niveles del agente:** N1 apoyo (SL2) · N2 operación supervisada (SL3) · N3 operación crítica (SL3, con meta de SL4 en 3 años).

**Gobernanza institucional:** lo exige el regulador del sector (en energía, la CREG regula y la Superservicios vigila); lo aprueba un comité de la entidad (seguridad, operación y jurídica), con auditoría externa en N3; responden el responsable designado, la entidad y, por el bloque 1, el proveedor. Se revisa cada 12 meses y con cada permiso nuevo.

## Validación

Caso hipotético: el agente "Vigía" del operador del sistema eléctrico nacional (nivel N3).

| Prueba (en papel, con apoyo de IA) | Resultado |
| --- | --- |
| Caso aplicado | Cumple 17 de 32: no apto |
| 10 ataques y 5 acciones legítimas | 9 frenados y 1 en parte; 0 legítimas bloqueadas |
| Cobertura de 10 amenazas | 9 cubiertas y 1 en parte (persona interna) |
| Equipo rojo: 5 ataques nuevos | 2 pasaron; corregidos en v2 y v3 |
| Robo de 1 TB de pesos con límite de 1 Mbps | Unos 93 días (unos 4 días si el modelo se comprime a 40 GB) |
| Acuerdo entre dos evaluadoras humanas | 84 % (27 de 32); ambas concluyen "no apto" |

**Hallazgos:** alinear la redacción de P4 con la ficha del agente, y declarar que lo "no definido" cuenta como no cumple.

**Límites:** no alcanza contra los Estados más capaces; depende de la evidencia del proveedor; el riesgo humano se reduce, no se elimina; la prueba es en papel con supuestos propios. **Doble uso:** el estándar solo restringe al agente y no describe cómo atacar.

## Qué hay en este repositorio (MVP)

| Ruta | Contenido |
| --- | --- |
| [`docs/Ficha-tecnica-AI-Guardian.pdf`](docs/Ficha-tecnica-AI-Guardian.pdf) | Ficha técnica de 2 páginas (entregable del Track 5) |
| [`instrumento/index.html`](instrumento/index.html) | Ficha e instrumento de evaluación: estándar completo, caso de estudio, cuestionario de 32 preguntas, resultados con semáforo por bloque e informe PDF exportable |

**Versión en línea del instrumento** (con respuestas compartidas entre evaluadoras): [AI Guardian · Ficha e instrumento](https://claude.ai/artifact/FHrL3mDPuCneFTfdtoSvKK)

El archivo `instrumento/index.html` también se abre directamente en el navegador. Fuera de claude.ai, las respuestas se guardan solo en ese navegador, y la exportación del PDF descarga el archivo directamente.

## Equipo

- **María Camila Castellanos**: líder del proyecto. Arquitecta de soluciones.
- **Sonia Cano Guerrero**: colíder. Desarrolladora de software full stack, con interés en DevSecOps. Desarrolló el instrumento de evaluación y el informe PDF.
- **Juliana Capador**: Ingeniera de Sistemas, con experiencia en bases de datos Oracle y PL/SQL.
- **Adriana Durand**: abogada, enfocada en optimización de procesos, automatización e IA aplicada a negocios.

## Referencias

- RAND, [*Securing AI Model Weights*](https://www.rand.org/pubs/research_reports/RRA2849-1.html) (2024)
- SL5 Task Force: [SL5 Standard](https://sl5.org/sl5-standard) y [*SL5 Novel Recommendations*](https://sl5.org/pdfs/SL5_NOVEL-RECOMMENDATIONS.pdf) (2025)
- NIST, [SP 800-53 Rev. 5](https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final) y [AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
- Anthropic, [*Disrupting the first reported AI-orchestrated cyber espionage campaign*](https://www.anthropic.com/news/disrupting-AI-espionage) (2025)
- OWASP, [Top 10 for LLM Applications](https://genai.owasp.org/llm-top-10/) · MITRE [ATLAS](https://atlas.mitre.org/)

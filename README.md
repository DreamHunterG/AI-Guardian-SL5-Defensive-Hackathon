# AI Guardian

> Estándar verificable para decidir si un agente de IA de frontera se puede encender en infraestructura crítica.

**AI Safety Colombia · Hackathon de IA defensiva · Track 5: Infraestructura y gobernanza (sin código)**
Universidad de los Andes, 14 de noviembre de 2026.

| | |
| --- | --- |
| 📄 **Ficha técnica** | [`docs/Ficha-tecnica-AI-Guardian.pdf`](docs/Ficha-tecnica-AI-Guardian.pdf) |
| 🧪 **Instrumento de evaluación en línea** | [AI Guardian · Ficha e instrumento](https://claude.ai/artifact/FHrL3mDPuCneFTfdtoSvKK) |
| 💻 **Instrumento sin conexión** | [`instrumento/index.html`](instrumento/index.html) |
| 🎤 **Presentación del pitch (2,5 min)** | [En línea](https://claude.ai/artifact/BP5DaQdRPssrydPpZr2Nbf) · [`presentacion/index.html`](presentacion/index.html) |

## En 30 segundos

Los operadores de servicios esenciales (energía, agua, salud, telecomunicaciones, transporte) empiezan a conectar agentes de IA de frontera a sus sistemas. Sin controles, un agente manipulado puede interrumpir un servicio, y los pesos del modelo pueden ser robados.

**AI Guardian** le dice a la entidad qué exigir antes de encender el agente: **32 requisitos de sí o no**, cada uno con su evidencia. **Si falla uno, el agente no se enciende.**

| 32 requisitos | 5 bloques | 84 % de acuerdo entre evaluadoras | Caso Vigía: no apto (17 de 32) |
| :---: | :---: | :---: | :---: |

## Cómo funciona

1. **Clasificar el agente** según lo que hace:
   - N1 apoyo → se exige SL2 al proveedor.
   - N2 operación supervisada → SL3.
   - N3 operación crítica → SL3, con meta de SL4 en 3 años.
2. **Pedir la evidencia** de los 32 requisitos: auditoría, diagrama, configuración o prueba.
3. **Responder sí o no** a cada requisito.
4. **Decidir:** solo con los 32 en sí el agente es apto. El semáforo por bloque muestra dónde falla.
5. **Gobernar:** lo exige el regulador del sector (en energía, la CREG regula y la Superservicios vigila) y lo aprueba un comité de la entidad (seguridad, operación y jurídica), con auditoría externa en N3. Se revisa cada 12 meses y con cada permiso nuevo.

## El estándar (versión 3)

| Bloque | Requisitos | Qué exige |
| --- | :---: | --- |
| 🔐 Seguridad de los pesos | 8 · P1–P8 | Al proveedor, según los niveles SL de RAND: llaves en chip seguro, computación confidencial, red aislada, límite de salida, dos personas, firmware firmado, personal verificado |
| 🧱 Contención | 9 · C1–C9 | Mínimo privilegio, aprobación humana, lo leído no es orden, apagado en segundos, límite de acciones, entorno aislado, evaluación de capacidades peligrosas, doble aprobación con datos fuente, operación manual |
| 📋 Auditoría | 5 · A1–A5 | Registro inmodificable, responsable designado, revisión mensual, reporte de incidentes, auditoría externa en N3 |
| ⛔ Líneas rojas | 7 · LR1–LR7 | Nunca copiar sus pesos, apagar su monitoreo, cambiar sus permisos, atacar otros sistemas, maniobrar sin aprobación, copiarse a sí mismo ni obedecer órdenes escondidas |
| 👥 Factor humano | 3 · H1–H3 | Separación entre operar, aprobar y auditar; pruebas sorpresa; aprobaciones firmadas, sanción y canal de denuncia |

## Validación

Caso hipotético: **"Vigía"**, un agente del operador del sistema eléctrico nacional (nivel N3) que analiza alarmas y prepara maniobras.

| Prueba (en papel, con apoyo de IA) | Resultado |
| --- | --- |
| Caso aplicado | Cumple 17 de 32: **no apto** |
| 10 ataques y 5 acciones legítimas | 9 frenados y 1 en parte; 0 legítimas bloqueadas |
| Cobertura de 10 amenazas | 9 cubiertas y 1 en parte (persona interna) |
| Equipo rojo: 5 ataques nuevos | 2 pasaron; corregidos en v2 y v3 |
| Robo de 1 TB de pesos con límite de 1 Mbps | Unos 93 días (unos 4 días si el modelo se comprime a 40 GB) |
| Acuerdo entre dos evaluadoras humanas | **84 %** (27 de 32); ambas concluyen "no apto" |

**Semáforo de Vigía:** 🟡 Pesos 5/8 · 🔴 Contención 4/9 · 🟡 Auditoría 3/5 · 🟡 Líneas rojas 5/7 · 🔴 Factor humano 0/3

**Hallazgos:** alinear la redacción de P4 con la ficha del agente, y declarar que lo "no definido" cuenta como no cumple.

**Límites:** no alcanza contra los Estados más capaces; depende de la evidencia del proveedor; el riesgo humano se reduce, no se elimina; la prueba es en papel con supuestos propios.
**Doble uso:** el estándar solo restringe al agente y no describe cómo atacar.

## Usar el instrumento

1. Abre la [versión en línea](https://claude.ai/artifact/FHrL3mDPuCneFTfdtoSvKK) y ve a **Evaluación de Vigía**.
2. Elige tu rol (evaluadora A, B o IA). Debajo de cada pregunta aparece la frase de la ficha que la responde.
3. Responde las 32 preguntas y guarda.
4. En **Resultados**, revela la clave para ver el acuerdo, el semáforo por bloque y las dudas.
5. Exporta el **informe PDF**, con o sin la evidencia de la IA.

Sin conexión, abre `instrumento/index.html` en el navegador: las respuestas se guardan solo en ese navegador.

## Estructura del repositorio

```
.
├── README.md
├── docs/
│   └── Ficha-tecnica-AI-Guardian.pdf   # Entregable del Track 5 (2 páginas)
├── instrumento/
│   └── index.html                      # Ficha e instrumento de evaluación
└── presentacion/
    └── index.html                      # Pitch de 2,5 minutos (6 diapositivas; flechas para avanzar)
```

## Equipo

| Integrante | Rol |
| --- | --- |
| **María Camila Castellanos** | Líder del proyecto · Arquitecta de soluciones |
| **Sonia Cano Guerrero** | Colíder · Desarrolladora de software full stack, con interés en DevSecOps · Desarrolló el instrumento y el informe PDF |
| **Juliana Capador** | Ingeniera de Sistemas · Bases de datos Oracle y PL/SQL |
| **Adriana Durand** | Abogada · Optimización de procesos, automatización e IA aplicada a negocios |

## Referencias

- RAND, [*Securing AI Model Weights*](https://www.rand.org/pubs/research_reports/RRA2849-1.html) (2024)
- SL5 Task Force: [SL5 Standard](https://sl5.org/sl5-standard) y [*SL5 Novel Recommendations*](https://sl5.org/pdfs/SL5_NOVEL-RECOMMENDATIONS.pdf) (2025)
- NIST: [SP 800-53 Rev. 5](https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final) y [AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
- Anthropic, [*Disrupting the first reported AI-orchestrated cyber espionage campaign*](https://www.anthropic.com/news/disrupting-AI-espionage) (2025)
- OWASP, [Top 10 for LLM Applications](https://genai.owasp.org/llm-top-10/) · MITRE, [ATLAS](https://atlas.mitre.org/)

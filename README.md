# 📊 Portafolio de Innovación Personal - Jerónimo Pérez Baquero

**Justificación de formato:** Decidí hacerlo en este formato porque hace unos meses me comprometí a ser más activo en mi GitHub, lo cual no he cumplido activamente. Por eso, quiero entregar mi portafolio de esta manera que hasta me parece un tanto original, o eso espero, siendo el ambito de la materia no técnico. Una excusa para agregar un cuadro de actividad en el dashboard de mi perfil y recordarme de continuar con este objetivo.

**Período de observación:** 4 – 17 de mayo, 2026
**Modo de lectura:** dos *trazas* (experiencias observadas), cada una analizada al estilo de un post-mortem de ingeniería.

---

> **Hilo conductor (spoiler del final):** Las dos experiencias que documento parecen no tener relación — una ocurre en la Carrera 70 con un cerrajero, la otra frente a un dashboard de Grafana. Pero ambas hablan del mismo fenómeno: **la distancia entre un dolor que existe y el momento en que alguien le pone nombre.** Esa distancia, intuyo, es donde vive la innovación.

---

## 🔎 Traza #1 — `service: cerrajería_local` · `status: NOT_FOUND`

**Contexto:** Cambiaron la chapa de la puerta en mi casa y me dieron la llave nueva para sacar mi copia. No soy de Medellín, así que no tenía idea de dónde hacerlo. Caminé una hora por la Carrera 70 hasta encontrar un local de copias de llaves… cerrado, porque era domingo y no lo había considerado.

### Observación
Lo evidente: *"no encontré dónde sacar la copia"*. Lo no-evidente: **Google Maps me mostraba varios sitios cerca, pero ninguno fue confiable.** Horarios desactualizados, locales que ya no existían, lugares marcados como "abiertos" que estaban cerrados. La información digital existía; lo que no existía era información **fresca**.

Detrás de eso, una segunda capa que me llamó más la atención: yo no soy de Medellín, así que no tengo el "conocimiento tácito de barrio" que los locales usan sin pensar — *"esa cerrajería al lado de la panadería lleva 20 años ahí, vecino"*. Hay una capa entera de comercio hiperlocal que **no está bien indexada en lo digital y se transmite por capital social.**

### Cuestionamiento
- ¿Por qué en 2026 sigo caminando una hora para resolver algo que debería tomar 30 segundos?
- ¿Por qué nadie confía *realmente* en los horarios de Google Maps para negocios pequeños?
- ¿El problema es falta de datos, o falta de **frescura** de los datos?
- ¿Cuál es el costo, en tiempo y energía, de no tener redes locales cuando llegas nuevo a una ciudad?

### Insight (lo que redefine el problema)
El problema real no es *"no sé dónde está el cerrajero"*. El problema es que **el comercio hiperlocal latinoamericano vive en una capa paralela a internet**, y las herramientas digitales fallan no por falta de datos sino por falta de **señales en tiempo real de "estoy abierto / disponible / vivo"**.

Es exactamente el mismo problema que en sistemas distribuidos: tener un servicio listado en un registro no significa que esté disponible. Necesitas **health checks**, no solo un directorio. Google Maps, para el comercio de barrio, es un DNS sin liveness probe.

### Associating (conexiones cruzadas)
- **DevOps/SRE:** esto es *service discovery* y *observability* aplicados al comercio urbano. Lo que falta no es un mapa: es un mecanismo de healthcheck hiperlocal.
- **Cachés obsoletas:** Google Maps actúa como una caché de la realidad urbana, y como toda caché, se degrada si nadie la invalida. ¿Quién es responsable de invalidar la caché de un barrio?
- **Capital social como API privada:** los locales tienen un "endpoint humano" (el vecino, el portero, la tendera) que devuelve datos frescos. Los recién llegados a la ciudad no tenemos credenciales para ese endpoint.

### Posible camino de innovación
Un sistema híbrido tipo *liveness signal* basado en WhatsApp/SMS para negocios de barrio + agregador local que reemplace a Maps en este nicho. Bajo costo técnico, alto valor para migrantes internos, comerciantes pequeños y plataformas de delivery.

---

## 🔎 Traza #2 — `service: mi_propio_aprendizaje` · `event: discovered_unknown_pain`

**Contexto:** Estudiando observabilidad con Prometheus y Grafana, llegué al concepto de *trace* y *Trace ID (TID)*. Entendí qué dolor resuelve. Lo curioso: **no sabía que ese dolor existía** hasta que vi la solución.

### Observación
Lo aparente: aprendí una herramienta nueva. Lo no-aparente: **mi reacción no fue "qué solución elegante", fue "ahora veo el problema".** El concepto de TID no me enseñó una técnica; me enseñó a *ver* una clase de dolor (debuggear sistemas distribuidos sin trazabilidad) que llevaba años existiendo sin que yo la nombrara.

Aún más: la mayoría de tutoriales técnicos te explican **cómo** usar la herramienta, pero rara vez te hacen *sentir* el dolor que la motivó. La consecuencia: adoptamos herramientas sin entender el problema, o ignoramos herramientas porque no reconocemos el problema que resuelven.

### Cuestionamiento
- ¿Cuántos problemas vivo todos los días sin notarlos, porque nadie les ha puesto nombre?
- ¿La documentación técnica está rota? ¿Por qué empieza por el *cómo* en lugar del *por qué duele*?
- ¿Cuál es el costo cognitivo, para un ingeniero junior, de los "unknown unknowns"?
- ¿Innovar es más resolver problemas, o más **nombrar** problemas que ya existían?

### Insight (lo que redefine el problema)
**Los insights más valiosos no son sobre soluciones nuevas, son sobre dolores que aún no tienen nombre.** El tracing distribuido no inventó el dolor de debuggear microservicios — ese dolor llevaba años existiendo. Lo que hizo fue **darle forma y vocabulario**, y solo entonces la solución se volvió adoptable.

En lenguaje de innovación: el framework Jobs-to-be-Done solo funciona después de que alguien articula el "job". Mientras el dolor no tenga nombre, el mercado no lo demanda, los ingenieros no lo priorizan, y los usuarios lo aguantan en silencio.

### Associating (conexiones cruzadas)
- **Con la Traza #1:** ambas experiencias son la misma historia, en espejo. En la cerrajería, el dolor está nombrado ("no encuentro el local") pero no hay solución decente. En el tracing, la solución existe pero el dolor estaba sin nombrar. **La innovación vive en esa asimetría entre dolor y solución.**
- **Con la pedagogía:** los mejores profesores no enseñan respuestas, enseñan a *ver* problemas. Lo mismo aplica a buena documentación técnica.
- **Con producto y marketing:** las features se venden por capacidades, pero se adoptan por dolores reconocidos. El copy de un lanzamiento debería abrir con el dolor, no con el feature.

### Posible camino de innovación
Reescribir documentación técnica (mía o de proyectos open source) empezando por **una historia del dolor** en lugar de la instalación. Hipótesis: aumenta tasa de adopción, retención y comprensión. Innovación barata, contraintuitiva y testeable en mi propio portafolio.

---

## 🧩 Síntesis cruzada

| Dimensión | Traza #1 (Cerrajería) | Traza #2 (TID) |
|---|---|---|
| ¿Existe el dolor? | Sí, evidente | Sí, pero invisible |
| ¿Tiene nombre? | Sí | No, hasta que lo vi |
| ¿Existe solución? | Mediocre (Google Maps) | Excelente (tracing) |
| Brecha de innovación | Falta solución fresca | Falta nombrar el dolor |

**Conclusión personal:** entrenarme como ingeniero de software y SRE me ha enseñado a *ver fricciones*. Estas dos semanas me confirmaron que esa mirada no se queda en lo técnico: aplica igual a una calle de Medellín que a un dashboard de Grafana. Mi siguiente reto es practicar deliberadamente el segundo movimiento: no solo ver el dolor, sino **ponerle nombre antes de que alguien más lo haga**.

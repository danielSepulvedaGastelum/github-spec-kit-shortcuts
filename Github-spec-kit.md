# Gúia de Shorcuts y manual para el uso de GitHub Speckit
---

# INSTALACIÓN

1. Buscar en Google el repositorio de GitHub Spec kit
```text
https://github.com/github/spec-kit
```

2. En los pasos de instalación debemos tener primero instalado en linea de comandos uv, ir a esa pagina
 ```text
 https://github.com/github/spec-kit/blob/main/docs/install/uv.md
 ```

3. instalar uv desde windows
```text
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

4. Ahora instalar Github-speckit con este comando, cambiando el X.Y.Z por la versión mas actual en el repositorio
```text
xuv tool install specify-cli --from git+https://github.com/github/spec-kit.git@vX.Y.Z
```

5. para verificar que se haya instalado bien ejecutar comando
```sh
specify 
```

6. Para ver los comandos disponibles
```sh
specify --help
```

```sh
╭─ Options ──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ --version  -V        Show version and exit.                                                                                                                                                                                                                                                                                                    │
│ --help               Show this message and exit.                                                                                                                                                                                                                                                                                               │
╰────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
╭─ Commands ─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ init         Initialize a new Specify project.                                                                                                                                                                                                                                                                                                 │
│ check        Check that all required tools are installed.                                                                                                                                                                                                                                                                                      │
│ version      Display version and system information.                                                                                                                                                                                                                                                                                           │
│ self         Manage the specify CLI itself: check for newer releases, preview upgrades with --dry-run, and upgrade in place.                                                                                                                                                                                                                   │
│ extension    Manage spec-kit extensions                                                                                                                                                                                                                                                                                                        │
│ integration  Manage coding agent integrations                                                                                                                                                                                                                                                                                                  │
│ event        Manage and execute event-driven commands                                                                                                                                                                                                                                                                                          │
│ preset       Manage spec-kit presets                                                                                                                                                                                                                                                                                                           │
│ bundle       Discover, install, and author Spec Kit bundles                                                                                                                                                                                                                                                                                    │
│ workflow     Manage and run automation workflows                                                                                                                                                                                                                                                                                               │
╰────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
```


7. Crear una carpeta del proyecto e ir a esa carpeta
```sh
mkdir tema1
cd  /c/Desarrollo/curso-sdd/tema1
```

8. iniciar el proyecto con lo siguiente
```sh
specify init proyecto1 --integration codex
```
- specify init 	- para iniciar proyecto
- proyecto1 	- Nombre del proyecto
- --integration	- para especificar que se integre con un agente de IA
- codex		- Es el agente que se va a utilizar


9. Son 4 Capas del procesos de una Spec:

    1. Constitución: Los principios que no se van a negociar
    2. Especificación: El Qué y el Por qué
    3. Plan: es el Cómo
    4. Tareas: que es lo que tenemos que hacer paso a paso


---
---
---
# PROCESOS DE LA SPEC
## 1. Constitución

-Skill de speckit-constitution, ejemplo del prompt para iniciar una contitución

```sh
$speckit-constitution

Crea los pirncipios que gobiernan PresupuestosPro, una herramienta web para que freelancers generen presupuestos en PDF. Principios:

1. Simplicidad ante todo: ante dos soluciones, siempre la mas simple. Es una versión 1; nada de complejidad ancipada.
2. Ideoma y mercado: todo el producto en español de México. Moneda Peso mexicano.
3. Cero alcance fastasma: NO implementar ninguna funcionalidad que no esté escrita en la spec. Si surge una nueva idea, se propone, no se contruye
4. Verificable por una persona no técnica: cada criterio de éxito debe poder comprobarse usando la app, sin leer código
5. Datos del usuario con respeto: pedir solo lo imprescindible. No introducir claves ni secretos en el código
Mantén la contitución corta y en lenguaje claro
```

- Preguntas que sebemos hacernos al crear la Spect

1.  ¿Se entiende el OBJETIVO sin saber de tecnología? (si tu cuñado no lo pilla, reescríbelo)
2.  ¿Está claro QUIÉN es el usuario y qué sabe (y qué no sabe) hacer?
3.  ¿Las reglas de negocio tienen un EJEMPLO concreto con números o casos reales?
4.  ¿Hay CRITERIOS DE ACEPTACIÓN que se comprueben con un sí/no usando la app?
5.  ¿Has separado el QUÉ del CÓMO? ¿Te has colado diciendo qué tecnología usar?
6.  ¿Existe una sección de "FUERA DE ALCANCE" que diga qué NO se hace?
7.  ¿Has pensado en los CASOS LÍMITE (vacío, cero, error, lo inesperado)?
8.  ¿Falta alguna DECISIÓN que la IA tendría que adivinar? Decídela tú.
9.  ¿Hay AMBIGÜEDADES tipo "que se vea profesional" sin definir? Concrétalas.
10. ¿Podrías dársela a OTRA persona y que construyera lo mismo que tú tienes en la cabeza?


---
---
---
## 1. Especificación


La especificación debe contener este formato:


> ⚠️ **Importante:** Recuerda no especificar detalles técnicos.

```md
#Especificación: [NOMBRE DEL PROYECTO] v[N]

## 1. Objetivo y contexto de negocio
[¿Qué problema resuelve y por qué importa? ¿Cómo se usa en la vida real?]

## 2. Usuarios
[¿Quién lo usa? ¿Qué sabe y qué no? ¿Hay alguien que recibe el resultado sin usar la app?]

## 3. Escenarios de usuario (historias)
- HU1 — Como [usuario], quiero [acción], para [beneficio].

## 4. Requisitos funcionales
- RF1. El sistema debe [comportamiento observable].   [QUÉ hace, no CÓMO. Sin tecnología.]

## 5. Reglas de negocio (con ejemplos)
[Las reglas que no se pueden saltar, cada una con un ejemplo concreto que se pueda comprobar.]

## 6. Criterios de aceptación (verificables sin código)
- CA1. [Algo que se mira en la app y se sabe si está bien con un sí/no.]

## 7. Casos límite
- CL1. ¿Qué pasa si [situación rara o vacía]?

## 8. Fuera de alcance
[Lo que esta versión NO hace, dicho explícitamente. La sección que impide que la IA se vaya por las ramas.]

```
---
---

Como realizar esta especificación de forma Detallada:

- Sección 1 - Objetivo y contexto de negocio
```text
Qué producir: 3–5 frases que respondan a: ¿qué problema resuelve?, ¿por qué importa?, ¿cómo se usa en la vida real? Incluye una escena concreta (el encargo te regala una, úsala o inventa la tuya). Cierra con una medida de éxito: ¿cuánto debería tardar el freelancer en emitir un presupuesto correcto?

Prueba del cuñado: si alguien sin idea de tecnología no entiende esta sección, reescríbela.
```

- Sección 2 - Usuarios
```text
Qué producir: al menos dos perfiles. Relee la pista de la plantilla: "¿hay alguien que recibe el resultado sin usar la app?". Uno de tus usuarios no toca la aplicación jamás… y aun así una regla de negocio entera depende de qué tipo de persona es. Descríbelos: quiénes son, qué saben hacer y qué no.
```

- Sección 3 - Escenarios de usuario (historias)
```text
Qué producir: entre 4 y 6 historias con el formato exacto HUn — Como [usuario], quiero [acción], para [beneficio].

Ejemplo resuelto (puedes usarlo como HU1):

HU1 - Como freelancer, quiero configurar mi nombre, NIF, contacto y logo, para que mis presupuestos salgan con mi marca sin tener que ponerla cada vez.

Cómo sacar el resto: cada cosa que la clienta dice querer hacer en el encargo esconde al menos una historia. Recórrelo párrafo a párrafo.

Cuidado con: historias sin beneficio ("quiero un botón de descargar"). El beneficio es lo que justifica que la historia exista.
```

- Sección 4 - Requisitos funcionales
```text
Qué producir: entre 8 y 12 requisitos numerados (RF1, RF2…), cada uno con un comportamiento observable: algo que se puede ver pasar usando la app.

Calibra con este par:

❌ Mal: "RFx. El sistema usará almacenamiento local del navegador para el catálogo." (Eso es el CÓMO: tecnología.)

✅ Bien: "RFx. Cuando el freelancer vuelva a abrir la aplicación, su catálogo y sus presupuestos deben seguir ahí." (Eso es el QUÉ: comportamiento. Cómo se consiga, no es asunto de la spec.)

No te olvides de: los cálculos (base, IVA, retención, total), el tipo de cliente, la numeración, la validez, el contenido del PDF y poder editar líneas antes de generarlo.
```

- Sección 5 - Reglas de negocio (con ejemplos)
```text
La sección más importante de tu spec.

Qué producir: las reglas fiscales y de numeración del encargo, y debajo un presupuesto de ejemplo completo, con 2 o 3 líneas inventadas por ti (servicios y precios los eliges tú), calculado a mano y al céntimo:

Base imponible = suma de (cantidad × precio unitario)

IVA = base × 21 %

Retención de IRPF = base × 15 %

Total = base + IVA − retención

Además, indica cuánto valdría ese mismo presupuesto (a) con retención del 7 % y (b) para un cliente particular.

Comprobación rápida de que lo has entendido: con una base de 1.000,00 €, el total con IVA 21 % y retención 15 % es 1.060,00 €. Si tu fórmula no da eso, revisa el signo de la retención. (Tu ejemplo debe usar otros números.)

Cuidado con: copiar las reglas sin ejemplo. Una regla sin números no se puede verificar, y lo que no se puede verificar, la IA lo interpretará a su manera.
```

- Sección 6 - Criterios de aceptación
```text
Qué producir: entre 5 y 8 criterios (CA1, CA2…) que cualquiera pueda comprobar usando la app, con respuesta sí/no, sin leer código.

Calibra con este par:

❌ Mal: "CAx. Los cálculos deben ser correctos." (¿Correctos según quién? No es comprobable.)

✅ Bien: "CAx. Con el presupuesto de ejemplo de la sección 5 y retención del 15 %, el total mostrado es exactamente [tu cifra] €." (Sí o no. Sin discusión.)

Truco: tus mejores criterios saldrán de cruzar tu ejemplo numérico con las reglas: ¿qué pasa al activar la retención?, ¿y con un cliente particular?, ¿qué número recibe el segundo presupuesto del año?
```

- Sección 7 - Casos límite
```text
Qué producir: al menos 3 casos con el formato "¿Qué pasa si…?" y su respuesta, decidida por ti.

Para arrancar, piensa en: un presupuesto sin ninguna línea, un servicio que no está en el catálogo, un cliente particular con la retención marcada por error.

Y aquí, permiso oficial para no ser perfecto: si detectas un caso límite pero no sabes qué respuesta darle, no lo fuerces: pásalo a "Preguntas abiertas". Eso no es un fallo; es el método funcionando.
```
- Sección 8 - Fuera de alcance
```text
Qué producir: la lista de exclusiones que la clienta deja caer al final del encargo, dicha de forma explícita, y al menos un punto propio: algo que se te haya ocurrido durante la tarea, que suena a buena idea… y que precisamente por eso hay que dejar fuera de la v0 por escrito.

Recuerda: esta sección es el freno de mano de la IA. Un "fuera de alcance" pobre es la puerta por la que se cuelan las funcionalidades fantasma.
```

- Sección 9 (extra) - Preguntas abiertas
```text
Añade al final un bloque que no está en la plantilla: "Preguntas abiertas".

Qué producir: entre 3 y 6 preguntas numeradas (PA1, PA2…) con las decisiones que sabes que no has tomado. Recupera los "¿?" que marcaste al leer el encargo y las dudas que hayas ido aparcando por el camino.

Por dónde suelen ir los huecos de este proyecto (no las respondas aquí, solo comprueba si te las habías planteado): ¿el IVA es fijo o editable?, ¿qué sale en el PDF si no hay logo?, ¿la numeración se puede corregir a mano?, ¿cómo se redondea exactamente?, ¿qué se ve la primera vez que se abre la app?

Por qué importa: estas preguntas son, literalmente, lo que le llevarás a Spec Kit. En la práctica del módulo verás que /speckit-specify y /speckit-clarify te preguntarán cosas muy parecidas.
```
---
---

> ⚠️ **IMPORTANTANTE:**

-  Qué pasa después con tu spec
Guárdala bien, porque no es un ejercicio suelto: es la entrada del ciclo. En la práctica guiada del módulo harás dos cosas con ella:

Dársela a Spec Kit con /speckit-specify: la herramienta la leerá, te hará preguntas (muchas te sonarán, porque las tendrás en tu lista de Preguntas abiertas) y de tus respuestas saldrá la especificación definitiva.

---
---
### Ejemplo de una SPEC

```md
# Especificación: PresupuestosPro v0

## 1. Objetivo y contexto de negocio

PresupuestosPro es una herramienta para que un freelancer español cree presupuestos profesionales con su marca y los descargue en PDF para enviárselos a sus clientes, sin pelearse con Excel ni con plantillas.

Hoy, la escena real es esta: son las once de la noche, un cliente ha pedido precio y hay que mandárselo mañana. El freelancer abre una hoja de cálculo vieja, copia un presupuesto anterior, cambia los conceptos a mano, calcula el IVA con la calculadora del móvil y cruza los dedos para que los números cuadren. El resultado tarda demasiado y se ve poco profesional.

Éxito de negocio: poder emitir un presupuesto correcto y con buena imagen en menos de 5 minutos.

## 2. Usuarios

- **El freelancer (usa la aplicación).** Autónomo en España (diseñador, programador, fotógrafo, consultor…). Trabaja solo, no es técnico y hace varios presupuestos al mes. Sabe manejarse con una web normal; no sabe (ni quiere saber) de impuestos más allá de lo justo.
- **El cliente (no usa la aplicación).** Recibe el PDF por email. Puede ser una **empresa o autónomo**, o un **particular**. La distinción importa: cambia si se aplica o no la retención de IRPF.

## 3. Escenarios de usuario

- HU1 — Como freelancer, quiero configurar mi nombre, NIF, datos de contacto y logo, para que mis presupuestos salgan con mi marca sin tener que ponerla cada vez.
- HU2 — Como freelancer, quiero mantener un catálogo de mis servicios con un precio por defecto cada uno, para no reescribir lo mismo en cada presupuesto.
- HU3 — Como freelancer, quiero crear un presupuesto eligiendo el cliente y añadiendo líneas (de mi catálogo o escritas a mano), para adaptarlo a cada encargo.
- HU4 — Como freelancer, quiero que la base imponible, el IVA, la retención de IRPF (cuando toque) y el total se calculen solos, para no equivocarme con los impuestos.
- HU5 — Como freelancer, quiero descargar el presupuesto como PDF con mi logo, número y validez, para enviárselo al cliente con buena imagen.

## 4. Requisitos funcionales

- RF1. El sistema debe permitir guardar y editar el perfil del freelancer: nombre, NIF, datos de contacto y logo.
- RF2. El sistema debe permitir crear, editar y eliminar servicios del catálogo, cada uno con nombre y precio por defecto.
- RF3. El sistema debe permitir crear un presupuesto indicando los datos del cliente y su tipo: **empresa/autónomo** o **particular**.
- RF4. Cada línea del presupuesto debe poder venir del catálogo o escribirse a mano, con descripción, cantidad y precio unitario.
- RF5. El sistema debe calcular automáticamente, en cada presupuesto:
  - Base imponible = suma de (cantidad × precio unitario) de todas las líneas.
  - IVA = base imponible × 21 % (tipo por defecto).
  - Retención de IRPF (si el freelancer la activa) = base imponible × 15 % o × 7 %, según elija.
  - Total = base imponible + IVA − retención de IRPF.
- RF6. Si el cliente es "particular", la retención de IRPF no se aplica en ningún caso.
- RF7. El sistema debe numerar los presupuestos automáticamente con el formato AAAA-NNN (por ejemplo, 2026-001), reiniciando el contador cada año.
- RF8. El presupuesto debe mostrar la fecha de emisión y una validez de 30 días desde esa fecha.
- RF9. El sistema debe permitir editar o eliminar cualquier línea del presupuesto antes de generar el PDF.
- RF10. El sistema debe generar un PDF con el logo, los datos del freelancer y del cliente, el número, las fechas, la tabla de líneas y el desglose de base, IVA, retención y total.
- RF11. Cuando el freelancer vuelva a abrir la aplicación, su perfil, su catálogo y sus presupuestos deben seguir ahí.

## 5. Reglas de negocio (con ejemplo)

- **IVA:** 21 % por defecto (tipo general de servicios profesionales en España).
- **Retención de IRPF:** 15 % (general) o 7 % (nuevos autónomos). Es opcional y **solo se aplica a clientes empresa/autónomo, nunca a particulares**.
- **Fórmula del total:** Total = base imponible + IVA − retención de IRPF.
- **Numeración:** formato AAAA-NNN (2026-001, 2026-002…), reinicia cada año.
- **Validez:** 30 días desde la fecha de emisión.

**Ejemplo de referencia (debe cuadrar al céntimo):**

| Concepto | Importe |
|---|---|
| Diseño de página web | 1.500,00 € |
| Sesión de fotos de producto | 500,00 € |
| **Base imponible** | **2.000,00 €** |
| IVA (21 %) | 420,00 € |
| Retención de IRPF (−15 %) | −300,00 € |
| **Total a pagar** | **2.120,00 €** |

- El mismo presupuesto con retención del 7 %: total **2.280,00 €**.
- El mismo presupuesto a un cliente particular (sin retención): total **2.420,00 €**.

## 6. Criterios de aceptación (verificables sin código)

- CA1. Con el ejemplo de la sección 5 y retención del 15 %, el total mostrado es exactamente 2.120,00 €.
- CA2. Al activar o desactivar la retención de IRPF, o al cambiar entre 15 % y 7 %, el total se recalcula solo.
- CA3. Al marcar el cliente como "particular", la retención de IRPF no se aplica y el total sube respecto al mismo presupuesto con retención.
- CA4. El segundo presupuesto creado en el año recibe automáticamente el número siguiente (por ejemplo, 2026-002).
- CA5. El PDF descargado muestra el logo, el número, la fecha de emisión, la validez y el desglose completo (base, IVA, retención si la hay, total).
- CA6. Puedo editar o borrar cualquier línea antes de generar el PDF y los totales se actualizan.
- CA7. Cierro la aplicación, la vuelvo a abrir, y mi perfil, mi catálogo y mis presupuestos siguen ahí.

## 7. Casos límite

- CL1. Presupuesto sin ninguna línea: no se genera el PDF; se avisa al freelancer.
- CL2. Línea escrita a mano, fuera del catálogo: permitida (no todo encargo está catalogado).
- CL3. Cliente particular con la retención activada por error: la retención no se aplica (manda el tipo de cliente).

## 8. Fuera de alcance (v0)

- **No es una factura:** nada de facturación electrónica ni VeriFactu en esta versión.
- Sin cuentas de usuario ni "entrar con contraseña".
- Sin guardar nada en la nube: los datos viven en el ordenador del freelancer.
- Sin multidivisa: solo euros.
- Sin enviar el PDF por email desde la aplicación (el freelancer lo descarga y lo manda él).
- Sin descuentos por línea ni globales (si algún día se añaden, se especificarán con su regla de cálculo y ejemplos).

---

## 9. Preguntas abiertas (para la sesión de clarificación con Spec Kit)

Cosas que sé que no he decidido. No las escondo: las apunto para resolverlas en el siguiente paso.

- PA1. **IVA:** ¿el 21 % debe ser editable? ¿Hacen falta los otros tipos (10 %, 4 %, 0 % exento)?
- PA2. **Logo:** ¿qué aparece en el PDF si el freelancer todavía no ha subido logo?
- PA3. **Numeración:** ¿se puede corregir un número a mano si hace falta, o es intocable?
- PA4. **Redondeo:** ¿cómo se redondean exactamente los importes con decimales raros (2,345 €)?
- PA5. **Primer uso:** ¿qué ve el freelancer la primera vez, con el catálogo vacío y sin perfil?
- PA6. **Cambio de ordenador:** si los datos viven en este ordenador, ¿qué pasa si uso otro? ¿Lo asumimos y lo decimos claramente?
```

---
---
### Plantilla para ejecutar la Spec

```sh
/speckit.specify

[pegar aquí la spec manual]

Antes de redactar la especificación formal, hazme las preguntas que necesites para
resolver cualquier ambigüedad. No implementes nada todavía.
```


---
---
### Validar la Spec con speckit-clarify

```sh
/speckit.clarify
```

> 💡 **Nota:** Te hará una serie de preguntas de la especificación para aclarar los puntos que considere que deben aclararse



---
---
---
## 3. Plan

Ejemplo de la ejecución de un Plan, aquí es donde se deben de ver los detalles técnicos de la construcción de la APP, no en la SPEC

```sh
$Speckit Plan

Prioriza la simplicidad por encima de todo, según la constitución. Es una versión 1 que debe poder publicarse online enseguida y funcionar bien en el móvil.  No añadas infraestructura que la spec no necesite (sin cuentas de usuario, sin base de datos en la nube en esta versión). Explica las desiciones importantes en lenguaje de negocio
```

---
---
---
## 4. Tareas

```sh
$speckit-tasks
```

Genera todas las tareas que va a realizar el agente al momento de implementar

Divide las tareas en fases e indica son [P] las fases que puedes ser en Paralelo con subagentes

---
---

Al concluir con la ejecución de las tareas se puede ejecutar el siguiente comando:

```sh
$speckit-Analyze
```

Otra puerta de calidad OPCIONAL para verificar de forma exhaustivo de consistencia y cobertura entre todos los documentos (artefactos), en el siguiente orden

1. Spec.md
2. Plan.md
3. Tasks.md

verifica que todo sea cuerente entre si y que respeta el archivo de constitución


---
---
---
## 5. Implementación

```sh
$Speckit Implement
```

Se ejecuta la implementación del proyecto


---
---
---
---
# ITERAR DE NUEVO COSAS QUE NO GUSTARON

---
---
## 2. Especificación

```sh
$speckit.specify 

Mejorar la presentación de PresupuestosPro (aplicación ya implementada en la spec 001) con dos cambios, sin alterar ninguna funcionalidad ni dato existente. Primero: añadir una página de inicio (index) que sea el punto de entrada de la aplicación al acceder a la raíz del servidor, con navegación clara hacia las cuatro secciones existentes (Presupuestos, Clientes, Catálogo y Perfil) y un pequeño resumen de actividad (por ejemplo, número de presupuestos por estado). Además, todas las páginas deben compartir una navegación común visible para moverse entre secciones sin usar el botón atrás. Segundo: rediseñar la apariencia visual de toda la aplicación para que resulte profesional y sobria: tipografía consistente, paleta de colores limitada definida en un único lugar, espaciado uniforme, jerarquía visual clara entre títulos, tablas, formularios y totales, y estados visuales distinguibles para los presupuestos (Borrador, Enviado, Aceptado, Rechazado, Caducado). El rediseño debe aplicarse también a la plantilla del PDF para que el documento que recibe el cliente transmita la misma imagen profesional. Debe mantenerse el enfoque mobile-first ya existente y todos los textos en español de España. La lógica de negocio, los cálculos, la API y el esquema de datos no deben cambiar en absoluto.
```


### Validar la Spec con speckit-clarify
```sh
$speckit.clarify
```
> 💡 **Nota:** Te hará una serie de preguntas de la especificación para aclarar los puntos que considere que deben aclararse

---
---
## 3. Plan

```sh
$speckit-plan 

Esta feature solo cambia la capa de presentación de una aplicación ya implementada. Toma el stack, las convenciones y la estructura de proyecto tal como están definidos en specs/001-presupuestos-profesionales/plan.md y specs/001-presupuestos-profesionales/data-model.md
```

### Checklist
```sh
speckit Checklist ux
```

Para que cree una lista de verificación de la interface ya que en la especificación nueva se indicó que se mejorar la inerface por algo profesional, y eso es muy anbiguo

```sh
$speckit-checklist Crea un checklist de UX para el flujo de onboarding.
Foco en accesibilidad, estados de error y estados de carga.
Audiencia: revisor de PR.
```

---
---
## 4. Tareas

```sh
$speckit-tasks
```

Genera todas las tareas que va a realizar el agente al momento de implementar

Divide las tareas en fases e indica son [P] las fases que puedes ser en Paralelo con subagentes

```sh
$speckit-Analyze
```

Otra puerta de calidad OPCIONAL para verificar de forma exhaustivo de consistencia y cobertura entre todos los documentos (artefactos), en el siguiente orden

1. Spec.md
2. Plan.md
3. Tasks.md

verifica que todo sea cuerente entre si y que respeta el archivo de constitución

---
---
## 5. Implementación

```sh
Speckit-Implement
```

> 💡 **Nota:** Se ejecuta la implementación del proyecto







---
---
---
---
# CICLO DE ITERACIÓN

- Quickstart
El quickstart oficial distingue dos caminos. Para experimentos rápidos basta el flujo mínimo: 

```text
specify → plan → tasks → implement. 
```


- Features de producción 
Pero para features de producción o con ambigüedad significativa, /speckit-checklist se trata como un quality gate habitual, junto a clarify y analyze:

```text
constitution → specify → clarify → plan → checklist → tasks → analyze → implement
```



---
---
---
---
# CLAUDE.md o AGENTS.md

```sh
Crea el archivo CLAUDE.md en la raíz del proyecto: será tu memoria técnica en todas las
sesiones futuras. Tiene que caber en una pantalla e incluir: (1) qué es esta app en una
frase; (2) el stack: tecnologías activas y decisiones técnicas vigentes (revisa los
plan.md de specs/ para extraerlas); (3) cómo se arranca y se prueba en local; (4) las
convenciones que seguimos; (5) una última línea que diga: "Las reglas de producto viven
en .specify/memory/constitution.md y el estado del producto en specs/README.md".
Enséñamelo antes de guardar.
```



---
---
---
---
# NUEVA ESPECIFICACIÓN

## Nueva Spec

```md
# Exportar todos mis presupuestos en un .zip

## Objetivo
Que el freelancer pueda llevarse TODOS sus presupuestos de una sola vez, en un único
archivo comprimido .zip, como copia de seguridad y para archivarlos donde quiera.
Hoy sus datos viven solo en su ordenador: si formatea el ordenador, cambia de navegador o borra el historial, lo pierde todo. Este botón
es su seguro de vida.

## Usuario
El mismo freelancer de siempre: autónomo, no técnico. Sabe descargar un archivo y
descomprimir un .zip con doble clic. No sabe (ni tiene por qué saber) qué hay dentro
de un "archivo de datos".

## Alcance
- Un botón "Exportar todo (.zip)" en un lugar visible de la lista de presupuestos.
- Al pulsarlo se descarga UN único archivo .zip que contiene:
  - Un PDF por cada presupuesto existente, exactamente el mismo PDF que ya genera
    la app para ese presupuesto.
  - Un único archivo de datos con toda la información (presupuestos, catálogo de
    servicios y perfil del freelancer, logo incluido), pensado para poder restaurar
    la aplicación en el futuro.
- Funciona con los datos que haya: 1 presupuesto o 200.

## Reglas de negocio
- Nombre del .zip: "presupuestospro-copia-AAAA-MM-DD.zip", con la fecha del día de
  la exportación. Ejemplo: exporto el 15/03/2026 → presupuestospro-copia-2026-03-15.zip.
- Nombre de cada PDF dentro del zip: número + cliente. Ejemplo: "2026-001 - Estudio
  García.pdf".
- La exportación NO modifica nada: es solo lectura. Después de exportar, la app
  sigue exactamente igual.
- Los PDF del zip deben cuadrar al céntimo con los que genera la app uno a uno
  (mismo ejemplo de control del Módulo 2: total $2,320.00 ).

## Criterios de éxito
- Con 3 presupuestos creados, pulso el botón y descargo un único .zip.
- Al descomprimirlo veo 3 PDF con nombre "número - cliente" y un archivo de datos.
- Abro cualquiera de los PDF y es idéntico al que descargo desde la app para ese
  mismo presupuesto.
- Con 0 presupuestos, el botón avisa de que no hay nada que exportar (y no se
  descarga ningún zip vacío).

## Casos límite
- Sin presupuestos: aviso claro, sin descarga.
- Cliente con caracteres conflictivos en el nombre ("Diseño/Web S.L."): el nombre de
  archivo se limpia para que el zip no se rompa.
- Muchos presupuestos (50+): puede tardar; tiene que verse que está trabajando.

## Fuera de alcance
- IMPORTAR la copia (restaurar los datos): será otra spec, otro capítulo.
- Exportar a Excel/CSV con formato contable.
- Copias automáticas o programadas: solo bajo demanda, con su botón.
- Enviar el zip por email o subirlo a ninguna nube.

```

Ejecutar lo anterior en el siguiente comando
```sh
$speckit-specify

[pegar aquí la spec manual]

Contexto: esta funcionalidad reutiliza el PDF que ya genera la app. Antes de redactar la especificación formal, hazme las preguntas que necesitas para resolver cualquier 
ambigüedad. No planifiques ni implementes nada todavia

```


---
---
---
---
# AGREGAR GIT AL CICLO

En consola de comandos externa (BASH), no en el agente poner el comando

```sh
specify extensión add git

```

> ⚠️ **Advertencia:** 

Agregar al final del archivo `AGENTS.md` o `CLAUDE.md` para forzar la creación de las ramas, ya que suele fallar este paso porque el agente a veces lo hace y aveces no

```md
## Spec-kit

* Antes de ejecutar el flujo de `/speckit.specify`, SIEMPRE ejecuta primero el hook `before_specify` (skill `speckit-git-feature`) para crear la rama de la feature, y espera su resultado antes de crear la spec.
* Tras completar `/speckit.specify`, verifica con `git branch --show-current` que estamos en la rama `NNN-nombre-feature` y no en `master`. Si no es así, avísame antes de continuar.

```






---
---
---
---
# AGREGADOS PARA MEJORAR EL CICLO

Despues de Ejecutar el Plan, ejecuta este Prompt directo en Codex

```sh
Incluye en `plan.md`, como último paso de la fase final, un paso de mantenimiento:
“Actualizar `AGENTS.md` con las decisiones de diseño y convenciones nuevas de esta feature, una línea por decisión, con referencia a la spec (p. ej. ‘[003] ...’). No incluyas entradas por incluir, asegúrate siempre de que es información transversal y relevante para el proyecto que puedan aprovechar futuras features.”

```

`AGENTS.md` agreg al final de la sección  ## Spec-Kit

```md

## Spec-Kit
.
.
.


* Al ejecutar `/speckit.plan`, SIEMPRE incluye en `plan.md`, como último paso de la fase final, un paso de mantenimiento: “Actualizar `AGENTS.md` con las decisiones de diseño y convenciones nuevas de esta feature, una línea por decisión, con referencia a la spec (p. ej. ‘[003] ...’). No incluyas entradas por incluir, asegúrate siempre de que es información transversal y relevante para el proyecto que pueden aprovechar futuras features.”

```


`AGENTS.md` agregar en la parte de Convenciones

```md

## Convenciones
.
.
.


cuando te pida "cerrar la feature", ejecuta:
verificar working tree limpio y commitear pendientes, correr tests (para si fallan), 
checkout main, 
merge --no-ff de la rama de la feature con mensaje "Merge feature NN:<nombre>",
y moistar git log --oneline -10, cambia en spec.md de esta spec => **Status**: Publicada
```


---
---
---
---
# ESTADOS DE LA SPEC

## Estados de la Spec

1. Draft		=> Creada
2. Prevista		=> Creadas pero no se ha trabajado la implementación
3. En curso		=> Después del Plan
4. Publicada		=> Mergeado en el rama Main
5. Sustituye a NNN	=> Spec que sustituye la funcionalidad de otra Spec


`AGENTS.md` Al final del primer párrafo: * Antes de ejecutar el flujo de `/speckit.specify` agrega:

```md
## Spec-kit
* Antes de ejecutar el flujo de `/speckit.specify`
.
.
.   

, despues de terminar la spec además cambia en archivo `spec.md` de esta spec => **Status**: Prevista
```



Al final del útimo párrafo: * Al ejecutar `/speckit.plan`, agrega:

```md
## Spec-kit
.
.
.
* Al ejecutar `/speckit.plan`,
.
.
.   

, despues de terminar la spec además cambia en archivo `spec.md` de esta spec => **Status**: En curso
```

---
---

Creamos el archivos README.md en la carpeta specs
```text
/specs/README.MD
```

En linea de Comandos de CODEX

```sh
Actualiza la tabla de `specs/README.md` —la fila de esta spec (número, nombre, qué aporta, estado, rama) y, si sustituye o modifica algo de una spec anterior, anótalo en el estado de LAS DOS; revisa todas mis specs porque es la inicialización del fichero `README.md`.
```

`specs/README.md` Agregar a este archivo al final una lista de las specs que aun no se han realizado pero que se tienen planeado hacer

```md
## Fuera del alcance acumulado (La lista de "Todavía no")
- Cuentas de usuario y datos en la nueve (decidido en 001)
- Importar copia de seguridad / restaurar datos (decidido 003)
- Modo oscuro (idea para modulo 5 - esperando su momento y su spec)

```


---
---
---
---
# MODIFICAR UNA SPEC YA EXISTENTE

## MODIFICAR PARA MEJORAR LA INTERFACE


1. En el Agente enviar el siguiente Prompt pero anexando capturas de pantallas de toda la APP para que de un analisis que utilizar.

> ⚠️ **Advertencia:** 
> Utilizar un modelo LLM de alto como Sol con esfuerzo en alto

```sh
Haz de director de arte exigente. Critica esta interfaz y dame las 7 razones concretas por las que NO parece una aplicación de 2026. Sé específico en cada una: tipografía, color, espaciado, jerarquía visual, componentes, estados y densidad. Nada de generalidades: señala elementos exactos de la captura. Aún no propongas soluciones.
```
---
2. Posterior a ese propmt, ejecutar este

> ⚠️ **Advertencia:** 
> Utilizar un modelo LLM de alto como Sol con esfuerzo en Ultra alto o el último modelo de frontera

```sh
Proponme 3 direcciones visuales para esta app, claramente distintas entre sí. Cada una en 5 líneas: nombre, dos referencias de productos reales, paleta con códigos de color, tipografía concreta y qué sensación transmite a un cliente que recibe el presupuesto.

No toques código: solo direcciones.
```

---
3. Analisando las 3 Opciones que nos ofrece el agente, seleccionar una y enviar el siguiente Pompt dependiendo d ela opción que nos parezca la mas adecuada.

```sh
Selecciono la opción 3. Crea un documento de pre-especificación para enviarlo a GitHub speckit specification que detalle por completo esta opción. Creo que al menos debería tener las siguientes secciones. Añade alguna adicional si lo consideras oportuno.

## Objetivo
## Usuarios
## Dirección visual elegida (decisión de producto: dirección 3)
## Reglas de diseño (tokens)
## Criterios de aceptación verificables (sí/no)
## Fuera de alcance
```
---
4. En una nueva conversación con el agente escribir el siguiente prompt, cambiando los 3 datos:
    - Archivo spec.md de la spec que queires modificar
    - El archivo de pre-spec:
    - El número de la espec que quieres modificar

> ⚠️ **Advertencia:** 
> Considera usar un modelo LLM de alto de frontera

```sh
$speckit-specify

Debes reescribir una spec existente: `@specs/002-rediseñar-presentacion/spec.md`, no crees una spec nueva, los criterios de modificación se encuentran eneste documento pre-spec que yo he desarrollado: `@docs/pre-especification-estudio-creativo`. Ajusta la `spec 002` por completo para que refleje todos los cambios de mi documento pre-spec
```

Al concluir debió de haber modificado el archiov de especificación 002 y creado una rama nueva de Git con estas modificaciones

---
5. Como esta modificación es muy grande es conveniente eliminar los siguientes archvios:
    - plan.md
    - tasks.md
    - research.md
    - quickstart.md
    - data-mpodel.md
    - /contracts
    - /checklists/ux.md

> ⚠️ **Advertencia:** 
> Hay hacemos un commit con los cambios depues de esta eliminación

---
6. Ahora es momento de ejecutar nuestro Plan.

- Como el cambio es muy grande y necesitamos crear todos lo archivos subsecuentes desde cero ejecutamos el plan así nada mas
```sh
$speckit-plan
```

- Si la modificación fuera algo pequeño y no hubieramos eliminado los otros archivos exsitentes le prodríamos pedir lo siguiente:

```sh
$speckit-plan

Modifica los archivos existentes del directorio coinforme a los cambios que ha sufrido el archivo de especificación
```

> ⚠️ **Advertencia:** 
> Si no hizo el commit al final de esta tarea, Hay que hacer un commit con los cambios

---
7. Ahora ejecutamos el comando para realizar las Tasks

```sh
$speckit-tasks
```

> ⚠️ **Advertencia:** 
> Si no hizo el commit al final de esta tarea, Hay que hacer un commit con los cambios

---
8. Ahora ejecutamos el comando para realizar el Analyze

```sh
$speckit-analyze
```

> ⚠️ **Advertencia:** 
> Si no hizo el commit al final de esta tarea, Hay que hacer un commit con los cambios

---
9. Ahora ejecutamos el comando para realizar la implementación

```sh
$speckit-implement
```

---
10. Si todo es correcto cerramos la feature:
```sh
cerrar la feature
```
> ⚠️ **Advertencia:** 
> Si no hizo el commit al final de esta tarea, Hay que hacer un commit con los cambios.

.

> ⚠️ **Advertencia:** 
> Si no hizo el Merge al final de esta tarea, Hay que hacer un Merge con la rama main
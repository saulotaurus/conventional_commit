![This is an alt text.](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTjVeXhjvoL5zd_00V9CrUAdWlyJQsrrF0kow&s)

# ✍️ Conventional Commits 1.0.0

## Resumen

La especificación **Conventional Commits** es una convención ligera sobre los mensajes de *commit*. Proporciona un conjunto sencillo de reglas para crear un **historial de *commits* explícito**, facilitando la creación de herramientas automatizadas y alineándose con **SemVer** (Versionado Semántico).

## ¿Por qué es importante?

Es crucial para facilitar el trabajo y el mantenimiento del proyecto, permitiendo a todos los participantes y futuros encargados:

* Generar automáticamente **CHANGELOGs**.
* Determinar automáticamente el **incremento de versión semántica**.
* Comunicar claramente la naturaleza de los cambios.
* Activar procesos automatizados de *build* y *publish*.
* Explorar un historial de *commits* estructurado y legible.

---

## 🏗️ Estructura del Mensaje de Commit

El mensaje de *commit* **DEBE** estructurarse de la siguiente manera:

<type>[optional scope]: <description>

[optional body]

[optional footer(s)]


### 🧱 Elementos Clave y Correlación SemVer

| Elemento | Descripción | Correlación SemVer |
| :--- | :--- | :--- |
| **`feat`** | Introduce una nueva característica. | **`MINOR`** |
| **`fix`** | Parchea un *bug* (error) en el código base. | **`PATCH`** |
| **`BREAKING CHANGE`** | Introduce un cambio disruptivo en la API (usando `!` o el `footer`). | **`MAJOR`** |
| **`[optional scope]`** | Información contextual adicional, entre paréntesis. Ej.: `feat(parser):` | N/A |

* **Otros `types` permitidos:** Se usan tipos adicionales como `build:`, `chore:`, `ci:`, `docs:`, `style:`, `refactor:`, `perf:`, `test:`, etc.
* **`footers`:** Pueden seguir una convención similar al formato *git trailer* (ej: `Refs: #123`).

---

## 📝 Tipos de Commit y Definiciones Comunes

Esta tabla detalla los tipos de *commit* más utilizados (basados en la convención de Angular):

| Tipo (`type`) | Definición y Propósito |
| :--- | :--- |
| **`feat`** | **Funcionalidad/Feature:** Adiciona un nuevo recurso. |
| **`fix`** | **Corrección de Bug:** Soluciona un error o comportamiento incorrecto. |
| **`chore`** | **Tareas/Rutinas:** Cambios de mantenimiento que no afectan la lógica de la app (ej: dependencias menores). |
| **`docs`** | **Documentación:** Solo cambios realizados a la documentación. |
| **`style`** | **Estilo de Código:** Cambios de formato sin alterar la lógica. |
| **`refactor`** | **Refactorización:** Reestructuración de código que no corrige *bug* ni añade *feature*. |
| **`test`** | **Tests:** Adición, eliminación o modificación de pruebas. |
| **`build`** | **Sistema de Build:** Cambios que afectan el sistema de construcción o dependencias externas. |
| **`ci`** | **Integración Continua:** Cambios en los archivos y *scripts* de configuración de CI. |
| **`perf`** | **Rendimiento/Performance:** Cambio de código que mejora el desempeño. |
| **`revert`** | **Reversión:** Revierte un *commit* anterior. |

---

## 🚨 Indicando un BREAKING CHANGE (MAJOR)

Cualquier tipo de *commit* puede ser un **MAJOR** si incluye una alteración que rompe la compatibilidad. Esto **DEBE** indicarse de dos maneras:

### Opción 1: Con el signo de exclamación (`!`)

Se añade **`!`** inmediatamente antes de los dos puntos (`:`) en el encabezado.

feat(api)!: El endpoint de usuarios ahora usa slugs

// Implica: MAJOR


### Opción 2: Con el pie de página (`footer`)

Se incluye el texto **`BREAKING CHANGE:`** en mayúsculas en el pie de página.

fix: corrige el manejo de errores

BREAKING CHANGE: La funcion 'parse()' ya no devuelve 'null' en caso de error, ahora lanza una excepcion.

// Implica: MAJOR


---

## 📜 Especificación (Reglas Clave Adicionales)

Las palabras clave **MUST**, **SHALL**, **REQUIRED**, etc., deben interpretarse como se describe en **RFC 2119**.

* **Estructura del Encabezado:** Los *commits* **MUST** (DEBEN) usar el formato `<type>[optional scope][optional !]: <description>`.
* **Cuerpo (`body`):** **MAY** (PUEDE) ser proporcionado una línea en blanco después de la descripción. Es de formato libre.
* **Pies de Página (`footers`):** **MAY** (PUEDEN) ser proporcionados. El *token* del *footer* **MUST** (DEBE) usar `-` en lugar de espacios (excepto para `BREAKING CHANGE`).
* **Sensibilidad a Mayúsculas/Minúsculas:** Solo **`BREAKING CHANGE` MUST** (DEBE) estar en mayúsculas. Otros elementos **MUST NOT** (NO DEBEN) ser sensibles a mayúsculas/minúsculas.

---

## 💡 Ejemplos de Mensajes

| Descripción | Ejemplo de Commit Message |
| :--- | :--- |
| **Commit con footer de breaking change** | `feat: allow provided config object to extend other configs`<br><br>`BREAKING CHANGE: \`extends\` key in config file is now used for extending other config files` |
| **Commit con `!` para breaking change** | `feat!: send an email to the customer when a product is shipped` |
| **Commit con scope y `!`** | `feat(api)!: send an email to the customer when a product is shipped` |
| **Commit sin cuerpo** | `docs: correct spelling of CHANGELOG` |
| **Commit con cuerpo multi-párrafo y footers** | `fix: prevent racing of requests`<br><br>`Introduce a request id and a reference to latest request. Dismiss`<br>`incoming responses other than from latest request.`<br><br>`Remove timeouts which were used to mitigate the racing issue but are`<br>`obsolete now.`<br><br>`Reviewed-by: Z`<br>`Refs: #123` |

[Referencia](https://www.conventionalcommits.org/en/v1.0.0/)

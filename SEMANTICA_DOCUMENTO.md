# Contrato semántico obligatorio — plantilla de tesis posgrado v6

## Tres capas, sin excepciones
1. **Estructura** (`estructura.sty`): define tipo de elemento, jerarquía, numeración y relación con otros elementos. No contiene nombres fijos de apartados de una investigación.
2. **Presentación** (`estilos.sty`, `tablas.sty`): define fuente, interlineado, sangrías, espacios, líneas, orientación, márgenes y tablas. No debe reescribirse por cada tema.
3. **Contenido** (`main.tex`): contiene nombres de apartados, párrafos, hipótesis, datos, indicadores, fechas, citas y tablas del nuevo estudio. Es sustituible según la tesis.

## Comandos, semántica y ejemplo
| Elemento | Comando | Qué escribe el agente | Qué resuelve la plantilla |
|---|---|---|---|
| Título del Plan, nivel 1 | `\tituloPlan{Objetivos}` | Solo etiqueta | `3.` automático, estilo y espacios |
| Título del Plan, nivel 2 | `\subtituloPlan{Objetivos específicos}` | Solo etiqueta | `3.2.` automático, estilo y espacios |
| Título del Plan, nivel 3 | `\apartadoPlan{Planificación anticipada}` | Solo etiqueta | `4.2.3.` automático, estilo y espacios |
| Rótulo no numerado | `\rotuloPlan{RESUMEN EJECUTIVO}` | Etiqueta | Estilo de encabezado no numerado |
| Ítem de Generalidades | `\itemGeneral{1.}{Título:}` | Número/etiqueta institucional | Sangrías, separación, negrita |
| Subítem de Generalidades | `\subitemGeneral{2.1.}{Autor(a):}` | Número/etiqueta institucional | Alineación y espaciado de subítems |
| Lista inmediatamente tras título | `\begin{listaTrasTitulo}...` | Elementos con `\item` | Espacio ANTES de la lista, no después del título |
| Lista normal entre párrafos | `\begin{listaNormal}...` | Elementos con `\item` | Espacio usual de lista normal |
| Lista de recursos | `\begin{listaRecursos}...` | Elementos con `\item` | Guion, sangría propia |
| Grado en la portada | `\gradoPortada{...}` | Texto del grado | Interlineado de carátula 1.35 |
| Título de tesis en portada | `\bloqueTituloPortada{...}` | Tema de la tesis | Interlineado 1.35 y las dos reglas horizontales |
| Referencia | `\referencia{...}` | Entrada bibliográfica | Sangría francesa, espacio entre entradas, fuente homogénea |

**Caso específico:** `\tituloPlan{Objetivos}` seguido de `\subtituloPlan{Objetivos específicos}` NO requiere `\vspace`. Una lista que aparece inmediatamente después de `\subtituloPlan` usa `listaTrasTitulo`; la separación pertenece a la lista y no al subtítulo.

## Regla de numeración
- En el Plan, nunca teclear `3.`, `3.2.` ni `4.2.3.` dentro de los argumentos de los comandos semánticos. La numeración se calcula mediante contadores.
- Los rótulos de Generalidades, por corresponder a una secuencia institucional distinta, mantienen identificadores explícitos en la v6. No deben mezclarse con el contador del Plan.
- Los títulos de tablas y los números de tablas se gestionan con los comandos de `tablas.sty`; no confundirlos con títulos de capítulos.

## Reglas obligatorias sobre tablas
- Cronograma: una columna por **semana**, agrupadas visualmente por mes. Nunca reemplazarlo por una columna por mes. Número real de semanas según investigación.
- Matriz: columnas estructuradas, ninguna celda desborda; encabezado **Indicador**; indicadores separados por líneas/ítems dentro de cada celda.
- Presupuesto: seis columnas: Clasificador MEF, Rubro, Cantidad, P. unitario (S/), Total (S/), Financia.
- Páginas apaisadas: pie centrado visualmente abajo. Tablas alineadas al margen de texto; espacio antes de Fuente/Nota.

## Regla sobre archivos y cambios
- `main.tex`: editar texto y elegir comandos semánticos apropiados.
- `estructura.sty`: modificar solo si falta un nuevo *tipo estructural*; justificarlo y actualizar documentación.
- `estilos.sty` y `tablas.sty`: modificar solo para ajustes institucionales autorizados, jamás para resolver un problema de contenido puntual mediante excepciones.
- Prohibido crear títulos usando directamente `\textbf` + `\vspace`, o fingir jerarquía con espacios manuales.
- No cambiar silenciosamente las secciones de la tesis de referencia: nombres y cantidad de apartados sí pueden adaptarse con la aprobación institucional.

## Lista de control de compilación
1. Compilar XeLaTeX; verificar Times New Roman en Overleaf.
2. Confirmar numéricamente orden de encabezados y que no aparecen numeraciones duplicadas.
3. Verificar portada y ambos interlineados de 1.35.
4. Inspeccionar título seguido de párrafo, título seguido de título y título seguido de lista.
5. Inspeccionar cronograma, presupuesto y matriz: orientación, anchos, bordes y pie de página.
6. Inspeccionar bibliografía: espacio posterior al título, sangría francesa y URLs en la fuente principal.
7. Documentar diferencias visuales reales respecto al PDF institucional; no declarar equivalencia sin comparación.

### Subtítulo con tabla inmediata
`\subtituloPlanConTabla{Texto editable}` representa un encabezado de segundo nivel que va inmediatamente seguido de `\tituloTabla`. Es una regla semántica de transición título→leyenda, no un valor añadido a todos los títulos. La separación está centralizada en `estructura.sty`.

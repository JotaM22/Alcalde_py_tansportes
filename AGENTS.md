# Instrucciones permanentes para asistentes de IA — Proyecto de tesis de posgrado

## Fuente de verdad
- Trabaja **siempre sobre el mismo proyecto**; no generes `main_v2.tex`, `final_final.tex` ni copias sin petición expresa.
- `main.tex` contiene el documento nuevo; `estilos.sty` controla presentación; `tablas.sty` contiene herramientas de tablas.
- `ejemplo_v16/main.tex` es un **ejemplo histórico** de Last Planner System, no la tesis actual ni una plantilla visual certificada.
- Cuando haya un Word institucional de referencia, compara contra él. No asumas que los estilos de la versión histórica son normas de la institución.

## Redacción
- Mantén la estructura de Generalidades y Plan de investigación, pero adapta apartados solo cuando las normas vigentes lo exijan.
- Conserva citas y referencias verificables; no inventes autores, publicaciones, DOI, resultados, muestras ni cifras.
- No alteres la metodología ni el sentido académico al resolver un problema de formato.

## Formato
- Compilar con **XeLaTeX**; utilizar Times New Roman real cuando esté instalada. Nunca afirmar que Tinos equivale exactamente a Times New Roman.
- Base de referencia extraída del ejemplo Word: A4, márgenes 2,5 cm, 12 pt, sangría 1,27 cm, espaciado posterior normal 12 pt, interlineado objetivo 1,5 de Word. El ajuste de LaTeX requiere validación visual.
- Los títulos deben llevar espaciado propio, sin sumar accidentalmente `parskip` dos veces.
- Para listas que siguen inmediatamente a un subtítulo usar `listatitulo`; para otras, `listacuerpo`.
- Para recursos utilizar `listarecursos` con guiones, independiente de las listas del cuerpo.
- Las tablas deben mantener bordes, fusiones y orientación de página originales. No inventar cronogramas, presupuestos ni indicadores.
- El cronograma y la matriz son secciones de orientación horizontal. La numeración de página debe seguir legible.
- Los títulos de tablas llevan número en negrita, denominación en cursiva, alineados a la izquierda; no modificar las leyendas para simular APA sin revisar requerimiento institucional.

## Pruebas antes de entregar
1. Compilar al menos dos veces con XeLaTeX y leer errores/avisos.
2. Inspeccionar el **PDF FINAL** que realmente se entrega, no una compilación intermedia.
3. Verificar portada ("Modalidad" en primera página), Generalidades, cronograma, recursos, presupuesto, listas tras títulos, matriz, referencias.
4. Buscar desbordamientos, bordes que desaparecen, tablas cortadas y páginas huérfanas.
5. Comparar elementos por ubicación y medidas, no solo cantidad de páginas.
6. Informar las comprobaciones realizadas sobre el documento compilado.
7. Si el cambio es solo de formato, evitar cambios en textos y datos.

## Git y archivos
- Un cambio lógico = un commit cuando sea posible.
- No subir PDFs auxiliares, archivos `.aux`, `.log`, `.out`, `.synctex.gz` ni variantes duplicadas.
- No modificar `ejemplo_v16/` salvo solicitud explícita.


## REGLAS OBLIGATORIAS DE MAQUETACION (v2)
- Nunca reescribir la portada a mano. Usar `\bloqueTituloPortada{...}` para conservar dos lineas horizontales.
- No agregar `\vspace` a titulo para separar una lista. Si una lista sigue a un titulo, usar `listatitulo`; de lo contrario usar `listacuerpo`.
- Mantener `\parskip=12pt` para parrafos ordinarios; los encabezados compensan su espacio mediante reglas unicas en `estilos.sty`. No acumular mas espacios.
- En paginas apaisadas las tablas ocuparan `\linewidth`; NO anchos calculados con el ancho de pagina vertical, ni columnas fijas que excedan el disponible.
- Cronograma: su escala temporal debe seguir el diseño solicitado para cada tesis. No inventar semanas desde meses; si se necesita version semanal, solicitar o usar datos semanales documentados. El ejemplo v16 de 32 semanas es referencia estructural, NO obligacion de 32 semanas para todos los proyectos.
- Matriz: siempre cerrar borde exterior y divisoria entre variables con `\hline` completo; usar `\cline` solo dentro del bloque de una variable.
- Antes de entregar renderizar las paginas portada, cronograma, matriz, y al menos dos paginas con titulos, listas y referencias.
- Confirmar si el PDF usa Times New Roman real. Tinos solo permite comprobacion provisional.


## REGLAS OBLIGATORIAS V3 (2026-10-29)
- GENERALIDADES: usar `\generalitem` y `\generalsub`; no agregar `\vspace` manual ni dejar 12pt acumulativos entre epigrafes.
- TODA tabla: `\noindent\begin{tabularx}{\linewidth}`; no desplazar tablas con sangrias o `center`. En paginas horizontales `\linewidth` debe equivaler a todo el ancho util.
- DESPUES de cerrar la tabla, usar `\fuenteTabla{...}`; el comando aporta 9pt antes de la fuente. No escribir Fuente pegada directamente al entorno de tabla.
- PRESUPUESTO INSTITUCIONAL: seis columnas, en este orden: Clasificador MEF, Rubro, Cantidad, P. unitario (S/), Total (S/), Financia. No sustituir por tabla simplificada de tres columnas. Usar los montos y clasificadores del presupuesto del proyecto.
- REFERENCIAS: `\iniciarReferencias` una vez tras el encabezado de Referencias, luego entradas `\referencia{...}`.
- Tablas y diagramas con estructuras diferentes deben mantener el formato y declarar por separado el numero de semanas/dimensiones; no convertir de manera automatica todos los cronogramas en 32 semanas.


## Directivas obligatorias v4 (control de calidad)
- Cronograma: SIEMPRE semanal, con una columna por semana, números de semana y encabezados agrupados por mes. No sustituir por cuatro columnas mensuales. El horizonte puede cambiar según el proyecto; registrar semanas concretas y fechas verificables.
- Páginas horizontales: usar `\\thispagestyle{empty}` al abrir el entorno y `\\paginaHorizontalCentro` antes de cerrarlo; comprobar número de página centrado en el borde inferior visual. No utilizar el pie normal rotado por pdflscape.
- Matriz: encabezado **Indicador** en singular. Los indicadores múltiples de una dimensión deben ir en una lista independiente dentro de esa misma celda, con `\\celdaIndicadores{\\item ...}`. No combinar varios indicadores separados solo por punto y coma.
- Matriz: utilizar anchos calculados para `\\linewidth`, evitar texto que se salga de la primera columna; evaluar visualmente todas las columnas y las divisiones.
- Referencias: los enlaces deben usar la fuente del documento (`\\urlstyle{same}`), nunca monoespaciado.
- Cada cambio debe comprobarse en páginas horizontales reales del PDF y no solo mediante compilación exitosa.

**Comprobación obligatoria antes de entregar:** verificar en el PDF renderizado que el cronograma tenga una columna por semana y ningún mes sustituya a semanas; número de página centrado abajo en todas las páginas apaisadas; matriz dentro del área de texto; título «Indicador» y una lista por cada celda de indicadores; URLs en la misma familia tipográfica que la bibliografía. Si falla una sola comprobación, no declarar la plantilla validada.


## Interlineado obligatorio de carátula (v5)
- El texto «PROYECTO DE TESIS PARA OPTAR EL GRADO…» debe escribirse con `\gradoPortada{...}`, no como negrita libre.
- El título académico debe escribirse con `\bloqueTituloPortada{...}`, que dibuja dos líneas horizontales.
- Ambos bloques llevan **interlineado aumentado (1.35)**, configurado obligatoriamente en `estilos.sty` mediante `\interlineadoGradoPortada` y `\interlineadoTituloTesisPortada`.
- No introducir saltos manuales o `\vspace` para simular el interlineado. Comprobar la carátula del PDF final.

## REGLA V6 PRIORITARIA — semántica, presentación y contenido
Leer `SEMANTICA_DOCUMENTO.md` ANTES de editar. La estructura se define en `estructura.sty`, la presentación en `estilos.sty` y `tablas.sty` y el contenido del proyecto en `main.tex`.

- **Las palabras de los títulos son contenido variable**. Su nivel, numeración, interlineado, sangría y espacios no dependen de esas palabras.
- En el plan de investigación crear títulos SOLO mediante `\tituloPlan{...}` (nivel 1), `\subtituloPlan{...}` (nivel 2) y `\apartadoPlan{...}` (nivel 3). **No escribir números dentro de las llaves.**
- No usar `\section*` o `\textbf` como títulos de apartados redactados por el agente, salvo comandos de portada o excepciones documentadas.
- Si una lista sigue inmediatamente a un título, usar `listaTrasTitulo`; en otros casos `listaNormal`. No modificar el `\vspace` del título para arreglar listas.
- Cronograma semanal, matriz con Indicador e ítems por indicador, presupuesto de seis columnas, tipografía de URLs y páginas apaisadas centradas: respetar `SEMANTICA_DOCUMENTO.md`.

## Encabezado seguido inmediatamente de tabla (v7)
Cuando un subtítulo de segundo nivel precede sin párrafo intermedio a la leyenda «Tabla N», usar `\subtituloPlanConTabla{...}` y después `\tituloTabla{...}{...}`. No usar `\subtituloPlan` directamente en esta transición ni corregir con `\vspace` en `main.tex`. El texto del encabezado es contenido variable; el formato y el espacio son responsabilidad de `estructura.sty`. Verificar que no haya superposición tras compilar.

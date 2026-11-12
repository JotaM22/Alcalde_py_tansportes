# Normas de formato — estado y trazabilidad

**Origen:** iteraciones LaTeX v1–v16 y comparación con el proyecto Word de posgrado. No equivale a una norma institucional oficial publicada.

| Elemento | Regla actual | Estado |
|---|---|---|
| Hoja y márgenes | A4, 2,5 cm | Base extraída de Word; verificar en cada nueva plantilla |
| Fuente | Times New Roman 12 pt | Requiere motor que disponga de fuente auténtica |
| Interlineado cuerpo | Objetivo Word 1,5 | Aproximación XeLaTeX (`setstretch=1.62`), NO equivalencia certificada |
| Sangría cuerpo | 1,27 cm | Base de Word |
| Posterior de párrafo | 12 pt | Base de estilo normal Word; no aplicar a celdas |
| Viñeta cuerpo | Cuadrado pequeño | Ajustada iterativamente, validar con Word |
| Lista tras título | Separación anterior propia de lista | Regla de trabajo |
| Recursos | Guiones y sangrías independientes | Aplicar el estilo de recursos |
| Cronograma | A4 apaisado, 32 semanas en caso de ejemplo | No copiar semanas para otras tesis |
| Matriz | A4 apaisado, siete columnas en ejemplo | Estructura de celdas depende de variables |
| Bibliografía | Sangría francesa 1,27 cm, separación visible | Formato de las entradas bibliográficas |
| Modalidad | Primera página, margen izquierdo inferior | Confirmado con capturas del Word de referencia |

## Uso del ejemplo v16
- Algunos comandos antiguos en `ejemplo_v16/main.tex` usan ajustes negativos; **no trasladarlos** a documentos nuevos.

## Jerarquía de fuentes
1. Normativa institucional vigente y su plantilla Word oficial, si está disponible.
2. El documento Word específico que el usuario proporcione.
3. Estas normas de trabajo, sujetas a comparación visual.
4. El ejemplo v16 como referencia orientativa, nunca como autoridad superior.


## Adenda de regresion visual v2 (29/10/2026)
Se contrastaron la tesis PAD2E (18 paginas) y el PDF de Overleaf v16 Last Planner (20 paginas). La plantilla original perdia las reglas de portada, acumulaba separaciones de titulos, y permitia tablas demasiado compactas.
La caratula DEBE incluir dos lineas horizontales que enmarcan el titulo. Los titulos NO deben recibir espaciado extra por caso. La lista inmediata al encabezado DEBE utilizar `listatitulo`.
El cronograma de 4 meses y la matriz de 6 columnas son variantes de contenido, NO equivalentes estructurales a las tablas v16 de 32 semanas y 7 columnas. Si se requiere equivalencia exacta, debe adaptarse el contenido y dimensiones de la tabla, con datos comprobados.


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

### Control específico v4
La muestra de PAD 2E utiliza 16 semanas académicas distribuidas convencionalmente en cuatro bloques mensuales. La correspondencia exacta de fechas y semanas debe establecerse desde el calendario real de cada nuevo proyecto. No inferir fechas de corte a partir de una cuadrícula demostrativa.


## Interlineado obligatorio de carátula (v5)
- El texto «PROYECTO DE TESIS PARA OPTAR EL GRADO…» debe escribirse con `\gradoPortada{...}`, no como negrita libre.
- El título académico debe escribirse con `\bloqueTituloPortada{...}`, que dibuja dos líneas horizontales.
- Ambos bloques llevan **interlineado aumentado (1.35)**, configurado obligatoriamente en `estilos.sty` mediante `\interlineadoGradoPortada` y `\interlineadoTituloTesisPortada`.
- No introducir saltos manuales o `\vspace` para simular el interlineado. Comprobar la carátula del PDF final.

## V6 — Contrato semántico obligatorio
La separación entre estructura, contenido y presentación está en `SEMANTICA_DOCUMENTO.md` y se implementa mediante `estructura.sty`. Los nombres de títulos son contenido mutable; sus niveles y reglas de estilo no cambian. La numeración de los títulos del plan se genera por contadores. Las listas inmediatamente posteriores a títulos se construyen con `listaTrasTitulo`; el espacio no se agrega indiscriminadamente a todos los títulos.

### Transición de subtítulo a tabla (v7)
La leyenda «Tabla N» debe iniciar con separación visible y nunca superponerse con el título de segundo nivel. Usar `\subtituloPlanConTabla` inmediatamente antes de `\tituloTabla`; no añadir espacios manuales en cada tesis. Revisar particularmente la matriz de operacionalización.

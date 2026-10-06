# PyMedIA

Aprende Python con casos de medicina clínica y atención primaria. Aplicación web de un solo fichero (`index.html`).

**Usar la app:** https://fborrasumh.github.io/pymedia/

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23187316.svg)](https://doi.org/10.5281/zenodo.23187316)

**Idiomas:** español (por defecto), inglés y portugués; selector en la barra superior (o `?lang=en` / `?lang=pt` en la URL).

## Qué hace

- **30 misiones** que siguen los 14 temas del Módulo 1 «Descubriendo Python» (temas 10 a 140, unidades 1.1 a 1.5): 25 de escribir código, 1 de predecir la salida de un programa y 4 tests de conceptos propios de Colab. Cada tema enlaza a su cuaderno de Colab y a su vídeo.
- **Todos los casos son clínicos y sintéticos**: constantes vitales, IMC y presión arterial media, glucemias, CURB-65, analíticas fuera de rango, aclaramiento de creatinina, curvas térmicas, historias clínicas, ficheros de ingresos y radiografías como matrices de NumPy. Ningún dato es de un paciente real.
- **Python real en el navegador** (Pyodide 0.27.7, en un Web Worker). No hay que instalar nada ni hay servidor. NumPy y matplotlib se descargan solo en las misiones que los necesitan.
- **Cada ejercicio se genera con una semilla**: cada estudiante recibe datos distintos y la misma semilla da siempre el mismo ejercicio.
- **El código corrige; la IA no.** Cada misión se comprueba ejecutando una solución de referencia con los mismos datos. Además de los datos visibles, se prueba con **casos ocultos** (otros datos o casos límite), de modo que escribir el resultado «a mano» o acertar solo el caso propio no basta.
- **Diagnóstico por recálculo.** Los errores típicos (`talla * 2` en vez de `talla ** 2`, `sort()` que devuelve `None`, `img[a:b][c:d]`, `and` en lugar de `or`, un `<` que debía ser `<=`, olvidar `return`…) se declaran como variantes de la solución; si la salida del estudiante coincide con una, la app explica el fallo. También explica los errores de Python (`SyntaxError`, `NameError`, `IndexError`…) y detecta tipos, redondeos, factores de unidades y desajustes de un elemento.
- **Refuerzo.** Tras fallar dos veces, propone una misión más básica y, al terminarla, devuelve al ejercicio original.
- **Juego sin trampas.** Estrellas (3 si se acierta a la primera, sin pistas y sin ver el resultado), puntos, niveles, racha y repaso espaciado (1, 3, 7 y 21 días con datos nuevos).
- **Pistas fijas** por misión, que funcionan sin clave.
- **Tutor de IA opcional** (OpenAI, Google Gemini o Anthropic Claude, con la clave de cada persona). Recibe el enunciado, el código del estudiante y el estado de la ejecución, **nunca la solución**; su respuesta se filtra por código (se eliminan bloques de código, líneas de la solución y cifras del resultado, en cualquier potencia de 10) y antes del primer envío se muestra lo que sale.
- **Informe del estudiante** (Word, JSON, CSV) con misiones, intentos, ayudas, errores más frecuentes y un registro encadenado con huellas SHA-256.
- **Profesorado:** carga el JSON de un estudiante, comprueba la cadena y **vuelve a ejecutar cada solución con su semilla**; y genera **exámenes individualizados** a partir de una semilla maestra (ZIP con examen para imprimir en HTML, clave de corrección en CSV y preguntas de tipo cloze para Moodle cuando las respuestas son numéricas o de texto corto).

## Privacidad

El código, el progreso y el informe se guardan solo en el navegador (IndexedDB). No hay servidor. Solo si se pide una pista a la IA salen el enunciado y el código del estudiante (con correos, DNI y teléfonos enmascarados), y antes del primer envío se muestra exactamente lo que sale. La clave de IA se guarda solo en el navegador.

## Límites

- **Necesita internet la primera vez**: Pyodide (≈ 14 MB sin comprimir) y, en las misiones que los usan, NumPy (≈ 9 MB) y matplotlib con sus dependencias (≈ 10 MB) se descargan desde el CDN jsDelivr, que los sirve comprimidos, y después quedan en la caché del navegador. La primera carga puede tardar varios segundos.
- **Las soluciones de referencia viajan dentro del fichero**: quien lea el código fuente de la página puede verlas. Los casos ocultos y la verificación del profesorado limitan el valor de copiarlas, pero no lo impiden. No es un sistema de examen con vigilancia.
- **El registro encadenado detecta ediciones del fichero; no es una prueba definitiva** (quien sepa puede recalcular la cadena). La comprobación importante es que el profesorado recalcule las soluciones con la semilla.
- **Tiempo máximo de ejecución: 10 s.** Un bucle infinito se corta y se explica, pero el entorno de Python se reinicia.
- **Partes de los cuadernos que no se pueden ejecutar en un navegador** (formularios y `!pip` de Colab, `wget`, montar Google Drive, `urllib` con descargas, comandos «magic», ColabTurtle) se cubren con preguntas de comprensión, no con código.
- **No incluye el Tema 150** (imágenes 3D con NumPy), que figura en la web de la unidad 1.5 pero no en el esquema acordado.
- La verificación de un informe supone la **misma versión de la app y de Pyodide** (se avisa si difieren).
- Las fórmulas clínicas (IMC, PAM, CURB-65, Cockcroft-Gault, Mosteller) y los umbrales son **didácticos**; no sustituyen a las guías clínicas ni a los protocolos del centro.
- Los consejos del tutor de IA pueden equivocarse; la corrección del código la hace siempre el motor.
- No se ha probado con una clave real de IA (solo con respuestas simuladas, incluidas respuestas que intentan revelar la solución).

## Autoría

Fernando Borrás Rocher (Universidad Miguel Hernández de Elche).

Ejercicios originales que siguen la secuencia del Módulo 1 «Descubriendo Python» del proyecto UNIDIGITAL-SIMUSTAT (cuadernos de F. Borrás, F. Botella, I. Hernández, Mª A. Martínez Mayoral, J. Moltó y J. Morales; licencia CC BY-SA 4.0). No se reutiliza su texto, código ni cuestionarios; el esquema de temas y los enlaces a los cuadernos y vídeos son los de su web (https://unidigitalsimustat.umh.es/).

ORCID: Fernando Borrás Rocher [0000-0002-5519-4573](https://orcid.org/0000-0002-5519-4573)

## Cómo citar

Borrás Rocher, F. (2026). *PyMedIA* (v1.0.0) [Software]. DOI: [10.5281/zenodo.23187316](https://doi.org/10.5281/zenodo.23187316)

## Desarrollo y pruebas

```bash
python3 build.py                                        # monta index.html desde src/ y forja/
python3 tests/logic_test.py 100                         # motor: 30 misiones × 100 semillas, errores típicos y resultados escritos a mano (CPython real)
PYODIDE_DIR=/ruta/pyodide NODE_MODULES=/ruta/node_modules python3 tests/browser_test.py   # navegador (Playwright) con Pyodide real y la CSP de producción
python3 tests/gen_i18n.py && node tests/extrae_claves.js   # diccionarios en/pt y cobertura de claves
```

## Licencia

MIT. Véase [LICENSE](LICENSE).

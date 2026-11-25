# Actualización del Anonimizador Judicial para el MPF CABA

La entrega pública del Ministerio Público Fiscal de la Ciudad Autónoma de Buenos Aires es la 3.4.4.
La actualización 3.4.8 incorpora las mejoras de detección y revisión del laboratorio sobre la edición del MPF.

## Comparación funcional

| Área | MPF 3.4.4 | Actualización MPF 3.4.8 |
|---|---|---|
| Motor | Reglas argentinas, Presidio 2.2.366 y spaCy 3.8.18 con el modelo local `es_core_news_md`. | Mantiene las dependencias y el modelo. Mejora las reglas para listas de personas, nombres invertidos y frases jurídicas. |
| Catálogos y agrupación | Agrupa variantes de una persona con una etiqueta común cuando se confirma la identidad. | Conserva esa lógica. Incorpora exclusiones automáticas para expresiones jurídicas como «Conexidad Subjetiva». El buscador filtra por texto, etiqueta, tipo o grupo. |
| Revisión manual | Permite corregir detecciones, añadir selecciones y revisar grupos. | Conserva las decisiones al reanalizar con la misma configuración. Pide confirmación antes de descartarlas. Permite desanonimizar un grupo o una selección. |
| PDF | Extrae texto digital. | Indica los números de páginas omitidas, exige confirmar las exportaciones parciales y mejora la lectura de tildes y la exportación de caracteres latinos extendidos. |
| Interfaz y datos | Identidad visual MPF, aplicación local y sesiones en memoria. | Usa el isologotipo y los colores MPF existentes, y prioriza Helvetica Neue en la interfaz con alternativas de sistema. Los cambios se verifican con documentos ficticios. |
| Inicio y entrega | ZIP portable de Windows. | El navegador se abre cuando el servidor local ya acepta conexiones. El flujo de prueba verifica el ZIP con Defender y comprueba el arranque y el análisis desde una carpeta extraída. |

La lista de exclusiones admite selección manual cuando el contexto justifica ocultar una de esas expresiones.
Un PDF escaneado requiere una capa de texto antes de analizarlo. El flujo de revisión y exportación está en el [manual de usuario](MANUAL_USUARIO.md).

## Entrega institucional

1. **Piloto en Windows administrado.** Entregar el ZIP de prueba y su SHA-256 a Sistemas por el canal institucional. Usar documentos ficticios para validar un PDF mixto, acentos, la agrupación de nombres y la exportación. Registrar la versión de Windows y el resultado.
2. **Distribución interna.** Si Sistemas confirma soporte para MSIX, definir con el equipo el nombre e identidad del paquete, el certificado de firma, la confianza de los equipos y el canal de distribución y actualización (por ejemplo, Intune, Configuration Manager o un portal interno). Probar instalación, actualización y desinstalación en un equipo administrado antes de desplegarlo.
3. **Publicación en Microsoft Store.** Si el MPF decide ofrecer la aplicación al público, tramitar una identidad de publicador, ficha, aviso de privacidad y certificación del producto institucional. La identidad del paquete personal del laboratorio pertenece a otro producto.

La distribución interna de un MSIX firmado con un certificado que los equipos del MPF confíen se gestiona dentro de la institución. La certificación de Microsoft Store se aplica al canal de la tienda. [Opciones de distribución interna de Microsoft](https://learn.microsoft.com/en-us/windows/uwp/publish/distribute-lob-apps-to-enterprises)

La revisión institucional y la certificación de la tienda responden a preguntas distintas. Para el piloto, documentar detecciones omitidas y erróneas por categoría, agrupaciones incorrectas, manejo de PDF y archivos de salida. Comprobar en el entorno del MPF la ejecución con las políticas de Windows vigentes, el procesamiento local y el manejo de la tabla CSV, que contiene los valores originales.

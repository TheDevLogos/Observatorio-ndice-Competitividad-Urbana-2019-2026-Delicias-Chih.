# Observatorio Dinámico ICU Delicias (2018-2026) 🏙️📊

¡Hola! Bienvenido al repositorio documental de mi **Observatorio Dinámico del Índice de Competitividad Urbana (ICU)** enfocado en la ciudad de Delicias, Chihuahua. He desarrollado este dashboard interactivo con el propósito de transformar un conjunto de datos estáticos e informes técnicos en una herramienta de inteligencia de negocios visual, dinámica y orientada a la toma de decisiones para la gobernanza local.

## 🎯 Contexto del proyecto

Para la construcción de este observatorio, me basé en los resultados del Instituto Mexicano para la Competitividad (IMCO) para la edición 2026, con retrospectiva histórica hasta 2018. El objetivo principal que me planteé fue crear un sistema tipo **observatorio** que permitiera visualizar rápidamente:

- En qué áreas Delicias es líder nacional entre las ciudades de menos de 250 mil habitantes.
- Cuáles son las alertas rojas o cuellos de botella para el desarrollo.
- Qué líneas de acción se deben tomar para mejorar la competitividad y la calidad de vida.

En otras palabras, quise pasar de un diagnóstico técnico disperso a una experiencia visual que me ayudara a leer tendencias, contrastar variables y priorizar decisiones con mayor claridad.

## 🗄️ Fuentes y estructura de datos

Para alimentar el tablero de manera fluida, unifiqué los documentos proporcionados en una estructura principal de tipo **Serie de Tiempo (Time-Series Data)**. Con esto evité depender de múltiples llamadas complejas en tiempo de ejecución y conseguí un modelo de datos más limpio para el dashboard.

### Tratamiento de la data (`historicalData`)

Extraje los indicadores clave del CSV y los consolidé en un arreglo de objetos JSON, donde cada objeto representa un año entre 2018 y 2026. Esto me permitió trazar tendencias históricas, comparar cortes anuales y construir gráficas con continuidad temporal.

La estructura base que diseñé es la siguiente:

```js
{
  year: '2026',
  pib: 2.4,                  // Crecimiento del PIB (%)
  patentes: 3.0,             // Patentes por 100k PEA
  salario: 10760.5,          // Salario mensual ($)
  informalidad: 43.8,        // Informalidad laboral (%)
  brechaGenero: 5.8,         // Brecha de ingresos por género (%)
  homicidios: 11.8,          // Tasa por 100k hab.
  // ... más de 20 variables adicionales integradas
}
```

Además, estructuré un arreglo llamado `subindexPositions` con las calificaciones y posiciones en los 6 subíndices evaluados por el IMCO. Ese arreglo me sirve para generar la gráfica polar tipo **Radar** y resumir el desempeño relativo de la ciudad.

## 📊 Gráficos generados y análisis visual

Diseñé el dashboard dividiéndolo en 6 pestañas principales, cada una con un tema de color personalizado mediante **glassmorphism** y gráficas específicas. Cada sección responde a una pregunta distinta sobre competitividad, riesgo y capacidad de respuesta local.

### 1. Resumen Ejecutivo
**Color: Verde azulado / Teal**

En esta pestaña concentro la lectura general del municipio. Incluye una **gráfica radar** de competitividad que muestra el equilibrio del desempeño de Delicias y permite ver de un vistazo cómo el sistema político toca el borde de la escala, mientras otros rubros permanecen más centralizados.

También incorporé una **tasa de homicidios histórica** en forma de área con degradado, porque quería reforzar visualmente el declive sostenido de la violencia letal de 20.1 en 2024 a 11.8 en 2026. A eso se suma un gráfico compuesto de **aprovechamiento internacional**, donde combino barras para la IED y una línea para el crecimiento del PIB con doble eje Y.

### 2. Innovación y Economía
**Color: Ámbar / Amber**

Aquí evaluó la capacidad de innovación, la atracción económica y la señal de sofisticación productiva. La pieza central es el gráfico de **desarrollo de propiedad intelectual**, un histograma que ilustra el salto en patentes de 0.7 en 2024 a 3.0 en 2026, algo que interpreté como un activo estratégico clave.

También agregué una visualización de **turismo y relaciones internacionales**, donde correlaciono ocupación hotelera con captación de IED. Esa relación me ayuda a leer si la ciudad solo atrae visitantes o si también logra atraer capital y actividad económica de mayor valor.

### 3. Mercado de Trabajo
**Color: Azul cielo / Sky Blue**

En esta pestaña me concentro en la calidad del empleo, la productividad y la equidad. El gráfico de **productividad vs salario** combina barras para salario mensual y una línea para el producto medio por hora. Esta visualización hace evidente una alerta importante: los salarios suben ligeramente, pero la productividad real por hora bajó de 146.0 a 138.9.

También trabajé una visualización de **calidad de vida laboral** con líneas multieje para mostrar la reducción en la brecha de género y en las jornadas largas. Finalmente, añadí un histograma de **evolución de la informalidad**, que resalta una tendencia al alza y alerta sobre el deterioro de la seguridad social y la recaudación fiscal.

### 4. Sociedad y Medio Ambiente
**Color: Verde esmeralda / Emerald**

Esta pestaña combina sostenibilidad ambiental y condiciones sociales. El gráfico de **impacto ambiental** usa un área con gradiente para mostrar el éxito de la ciudad en la reducción de residuos sólidos, que cayó a 0.7 kg/día.

A la vez, incorporé un gráfico de **estrés hídrico** para poner en perspectiva el consumo de agua de 166.6 m³ por habitante. En mi interpretación, esta visualización sustenta la recomendación de construir un plan hídrico integral y abordar el riesgo regional de disponibilidad de agua.

### 5. Infraestructura Urbana
**Color: Rosa / Rose**

Aquí reviso la forma urbana, la densificación y la seguridad vial. La gráfica de **densificación urbana** muestra el crecimiento explosivo de la vivienda vertical, llegando a 60%, lo cual yo leo como un signo de política habitacional y compactación urbana.

En contraste, la gráfica de **seguridad vial** pone el foco en las víctimas de accidentes de tránsito, con 165.4 registros. La marqué en tonos rojizos para enfatizar el riesgo como problema de salud pública y como prioridad para un plan de rediseño de cruceros y banquetas.

### 6. Gobernanza y Derecho
**Color: Índigo / Indigo**

Esta sección examina transparencia, capacidad fiscal y percepción ciudadana. El gráfico de **ingresos vs corrupción** combina área y línea para mostrar un comportamiento interesante: la percepción de corrupción disminuye positivamente, pero al mismo tiempo cae la recaudación de ingresos propios, lo cual representa un riesgo fiscal hacia el futuro.

Esa tensión me parece crucial porque revela que una buena percepción institucional no siempre se traduce automáticamente en fortaleza financiera. Por eso quise que esta pestaña fuera analíticamente densa y no solo descriptiva.

## 🛠️ Stack tecnológico utilizado

- **React JS**: Para la modularización y el manejo de estados, pestañas y filtros dinámicos.
- **Tailwind CSS**: Para el diseño responsivo, glassmorphism, tarjetas y theming dinámico.
- **Recharts**: Para el renderizado de gráficos vectoriales SVG de alto rendimiento, incluyendo custom tooltips y dobles ejes.
- **Lucide React**: Para la iconografía profesional y minimalista.

## 💡 Mis conclusiones sobre Delicias

A través de la programación y el análisis visual de estos datos, concluyo que Delicias es una ciudad con un desempeño sorprendentemente alto para su tamaño poblacional. Destaca notablemente por su gobernanza transparente y su responsabilidad ambiental, especialmente en residuos.

Sin embargo, diseñé este tablero para que los tomadores de decisiones no ignoren tres focos rojos críticos:

- El alto índice de accidentes viales.
- El riesgo por estrés hídrico.
- El aumento preocupante en la informalidad laboral.

Implementar las líneas de acción integradas en los paneles de insights del dashboard será crucial para la estrategia municipal 2026-2028

## ✅ Nota final

Este observatorio no busca solo mostrar números. Busca ayudarme a contar una historia territorial con datos, visualizar patrones de competitividad y convertir información técnica en decisiones útiles para Delicias.

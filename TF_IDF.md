<span style='font-family:Palatino'>
<span style='color:#000000'>
<div align='center'><h1>Natural language processing (NLP)
</h1></div>
<div align='center'><h1>Procesamiento del lenguaje natural (PLN)
</h1></div>
Primero, por <strong>lenguaje natural vamos a entender el lenguaje humano (lenguas del mundo).</strong>



<strong>¿Qué es? </strong> Es un área de la computación, IA y lingüistica que estudia las interacciones entre los computadores y el lenguaje humano.


<strong>¿Cuál es objetivo del PLN?</strong> Diseñar algoritmos que le permitan a los computadores ''entender'' el lenguaje natural para realizar alguna tarea. Ejemplos de tareas con diferentes niveles de dificultad son:


<ul>
    <li> Dificultad baja: corrección ortográfica, búsqueda de palabras claves, encontrar sinónimos,
    </li>
    <li> Dificultad media: analizar información de documentos o sitios web</li>
    <li> Dificultad alta: traducción mecánica, análisis semántico, ¿esto, este, el, ella...? encontrar a qué o quién se hace referencia, responder preguntas</li>
</ul>

<strong>¿Cómo representar las palabras como entrada para los modelos?
</strong> Se utiliza una representación vectorial: la idea es que si $V$ es un vocabulario con el que se está trabajando, $V = \{árbol, planta, bosque, \ldots \}$ decimos que una función $f : V \to \mathbb{R}^n$ induce una representación vectorial de dimensión $n$ para dicho vocabulario, si le asigna un vector de $\mathbb{R}^n$ a cada palabra de $V$.

La construcción de funciones $f$ que tengan buenas propiedades es objeto
de estudio, pues el desempeño de una gran cantidad de algoritmos de PLN dependen directamente de la calidad de las mismas. Dependiendo el contexto en que se esté trabajando,uni puede desear que $f$ satisfaga ciertas propiedades, por ejemplo que:


<ul>
    <li> palabras con significados similares tengas asociados vectores 'similares', </li> 
    <li> capturar la relación entre dos palabras como por ejemplo <em>cantar</em> y <em>cantando,</em> </li>
    <li> Un $n$ no muy grande $(n \ll |V|)$ para que la dimensionalidad de las entradas no sea un problema ó alta dimensionalidad pero buscando que los vectores asociados a las palabras tengan casi todas sus entradas en cero.</li>
</ul>

<strong>Nosotros los haremos usando TF- IDF (term frequency - inverse document frequency).</strong> Pero primero necesitamos introducir el siguiente concepto:
<strong>

Palabras vacías (stop words).</strong> Son palabras que se filtran antes o después del procesamiento de datos en lenguaje natural. Usualmente el término hace referencia a las palabras más comunes en un idioma.


<em>Volviendo a nuestra forma de vectorizar:</em>

<ol>
    <li> <strong>TF:</strong> </li>
    <pre>documento 1 : el cielo es azúl
documento 2 : el sol es brillante</pre>
Ignoramos las palabras vacías y esto nos da un vector para cada documento:
<pre>
              azúl brillante cielo sol
documento 1     1      0       1    0
documento 2     0      1       0    1
</pre>
<li> <strong> IDF: </strong></li>
$$
\log \left(\frac{1+ \text{cantidad de documentos}}{1 + \text{número de documentos donde aparece el término}}\right)+1
$$
Por ejemplo IDF de cielo:
$$
\log \left(\frac{1+ 2}{1 + 1}\right)+1 = 1.40
$$
<li> <strong>TF - IDF: </strong></li>
$$
\text{TF-IDF} = \text{TF} \times \text{IDF,}
$$
donde cada entrada de la matriz se normaliza con la norma $\ell_2$
<pre>
               azúl      brillante      cielo      sol
documento 1   0.7071         0         0.7071       0
documento 2      0        0.7071          0      0.7071
</pre>
</ol>
</span>





</span>
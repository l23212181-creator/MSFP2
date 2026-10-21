[![Open in MATLAB Online](https://www.mathworks.com/images/responsive/global/open-in-matlab-online.svg)](https://matlab.mathworks.com/open/github/v1?repo=l23212181-creator/MSFP2)

# Práctica 2: Modelado y control del sistema cardiovascular mediante el modelo Windkessel

## Información del estudiante

Bautista Paz Jesus Geovanny [23212181]; l23212181@tectijuana.edu.mx

Modelado de Sistemas Fisiológicos

Ingeniería Biomédica

## Docente

Dr. Paul Antonio Valle Trujillo; paul.valle@tectijuana.edu.mx

Departamento de Ingeniería Eléctrica y Electrónica, Tecnológico Nacional de México/IT Tijuana, Blvd. Alberto Limón Padilla s/n, Tijuana, C.P. 22454, B.C., México.

## Descripción de la asignatura

El modelizado de sistemas fisiológicos es una herramienta importante en Ingeniería Biomédica, permite comprender el funcionamiento del cuerpo humano, así como diseñar y evaluar terapias y dispositivos médicos; se define como el proceso de formular modelos matemáticos o computacionales que representan el comportamiento y la interacción de los sistemas biológicos y fisiológicos. Esta asignatura pretende aportar al perfil del Ingeniero Biomédico la capacidad de realizar investigación científica en el área de Biología de Sistemas con la finalidad de dirigir y participar en equipos de trabajo interdisciplinarios en contextos nacionales e internacionales, así como de proporcionar soluciones informáticas para resolver problemas en el campo de la Ingeniería Biomédica con ética profesional; lo anterior al proporcionar al estudiante bases sólidas para modelizar sistemas y diseñar controladores para la solución de problemas en las áreas de atención médica y del sector industrial médico. La construcción de analogías entre circuitos eléctricos y sistemas fisiológicos para la formulación de modelos matemáticos y el diseño de controladores mediante la experimentación in silico brindan herramientas de gran aplicación en el quehacer profesional del Ingeniero Biomédico.

La asignatura de Modelado de Sistemas Fisiológicos forma parte del plan de estudios de la carrera en Ingeniería Biomédica con la siguiente competencia general del curso: Utiliza las propiedades de los circuitos RLC para describir la dinámica de sistemas fisiológicos, obtener modelos matemáticos y aplicar el control clásico, esto con el objetivo de integrar los principios de la Ingeniería de Control, la Electrónica Analógica y las Ciencias de la Computación con la Anatomía y Fisiología del cuerpo humano para proporcionar descripciones cuantitativas y cualitativas de sistemas fisiológicos complejos con el objetivo de modelizar, analizar, controlar, ilustrar y predecir su dinámica tanto en el corto como en el largo plazo.

## Objetivos

1. Reconocer las variables y los elementos que integran el modelo cardiovascular Windkessel de cuatro componentes.
2. Formular las ecuaciones integro-diferenciales y diferenciales ordinarias que describen la dinámica del circuito equivalente.
3. Obtener las funciones de transferencia correspondientes a los individuos normotenso, hipotenso e hipertenso.
4. Examinar los polos de cada sistema para determinar su estabilidad y calcular el error en régimen permanente.
5. Reproducir las respuestas de los tres modelos en MATLAB/Simulink y Python a partir de una señal de excitación compartida.
6. Ajustar controladores PID independientes para los casos hipotenso e hipertenso, empleando la respuesta normotensa como referencia.
7. Contrastar las señales obtenidas antes y después de incorporar los controladores.
8. Elaborar un esquema biológico que relacione los componentes del modelo eléctrico con el sistema circulatorio.

## Descripción detallada del sistema

La práctica consiste en representar la circulación arterial por medio del modelo Windkessel de cuatro elementos. Se utiliza un circuito eléctrico equivalente para estudiar la relación entre la presión de entrada **Pa(t)** y la presión de salida **Pp(t)**. La impedancia **Z** describe la oposición característica al flujo en las arterias proximales, **L** representa la inercia de la sangre, **R** corresponde a la resistencia periférica y **C** expresa la distensibilidad arterial.

Para comparar las condiciones fisiológicas se trabajó con los siguientes valores:

| Parámetro | Hipotenso | Normotenso | Hipertenso |
|---|---:|---:|---:|
| Z | 0.010 | 0.010 | 0.010 |
| L | 0.001 | 0.001 | 0.001 |
| R | 1.000 | 1.000 | 1.000 |
| C | 3.500 | 1.500 | 1.000 |

En esta implementación los valores de **Z**, **L** y **R** son iguales en los tres casos. La diferencia entre las condiciones se establece mediante **C**, que es mayor en el modelo hipotenso y menor en el hipertenso.

Al aplicar las relaciones del circuito y la transformada de Laplace, se obtiene la siguiente función de transferencia:

$$
G(s)=\frac{P_p(s)}{P_a(s)}=\frac{LRs+RZ}{CLRZs^2+L(Z+R)s+RZ}
$$

A partir del denominador se determinan los polos y se estudia la estabilidad de los modelos. También se plantea un sistema de ecuaciones diferenciales de primer orden considerando el flujo por la inertancia y la presión de salida como variables de estado.

Se realizaron simulaciones en un intervalo de **0 a 15 segundos**. En el desarrollo numérico se calcula primero la respuesta normotensa y se utiliza como entrada para obtener las respuestas hipotensa e hipertensa. Las señales se comparan mediante gráficas generadas en MATLAB y Python.

Para estudiar el control del sistema se incorporaron dos controladores PID: uno para el caso hipotenso y otro para el hipertenso. Ambos buscan aproximar la respuesta de cada modelo a la señal normotensa. Las ganancias se ajustaron en Simulink con **PID Tuner** y se analizaron las respuestas en lazo abierto y lazo cerrado.

Finalmente, se elaboró un diagrama biológico para identificar la relación entre los elementos del circuito equivalente y las estructuras del sistema cardiovascular.

**Palabras clave:** Modelo Windkessel; Circulación arterial; Circuito equivalente; Función de transferencia; Control PID; Simulación computacional.

## Lista de archivos incluidos en el repositorio

1. Archivo de MATLAB Live Script y documento exportado [.mlx y .pdf].
2. Modelo del sistema implementado en Simulink [.slx].
3. Programa utilizado para las simulaciones en Python [.py].
4. Datos de la señal de entrada [.xlsx].
5. Desarrollo matemático del modelo, funciones de transferencia y análisis de estabilidad [.pdf].
6. Gráficas de las condiciones normotensa, hipotensa e hipertensa obtenidas en MATLAB y Python [.pdf].
7. Capturas de la sintonización de los controladores PID [.png].
8. Diagrama del sistema cardiovascular realizado en BioRender [.jpeg].

## Referencias

[1] P. A. Valle, *Syllabus para Modelado de Sistemas Fisiológicos*, Tecnológico Nacional de México / Instituto Tecnológico de Tijuana, Tijuana, B.C., México, 2026. Permalink: https://biomath.xyz/course/

[2] M. C. Khoo, *Physiological Control Systems: Analysis, Simulation, and Estimation*, 2nd ed. IEEE Press, 2018.

[3] N. S. Nise, *Control Systems Engineering*, 8th ed. John Wiley & Sons, 2020.

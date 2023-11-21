# calculadora-electronica
Proyecto final de electricidad 2, calculadora que permite el calculo de impedancias y de filtros pasivos 
Calculadora Electrónica
Este código de Python constituye una aplicación gráfica utilizando la biblioteca tkinter para realizar cálculos relacionados con impedancias en circuitos eléctricos y para determinar propiedades clave en filtros pasivos. Aquí tienes una descripción más detallada del funcionamiento y las librerías utilizadas:

Librerías Utilizadas:
•	cmath: Esta librería proporciona funciones para manejar números complejos. En el contexto de la calculadora de impedancias, se utiliza para representar las partes imaginarias de la impedancia en circuitos que contienen inductores y capacitores.

•	math: La librería estándar de Python para operaciones matemáticas. En este código, se emplea para cálculos trigonométricos y otras operaciones matemáticas básicas necesarias para derivar las fórmulas de impedancia y respuesta de filtro.

•	tkinter: Una interfaz estándar de Python para la creación de interfaces gráficas de usuario. Tkinter proporciona widgets y herramientas para construir ventanas, botones, campos de entrada, y otros elementos de la interfaz.

Funcionamiento:

Calculadora de Impedancias:

1.	Entrada de Datos: El usuario introduce valores para resistencia (R), inductancia (L), capacitancia (C), y frecuencia (f).

2.	Cálculo de Impedancia: Utilizando las fórmulas de impedancia para resistores (Z_R), inductores (Z_L), y capacitores (Z_C), se calcula la impedancia total del circuito.


3.	Configuración del Circuito: La elección del usuario entre configuraciones de circuito en serie o paralelo determina cómo se combinan las impedancias individuales para obtener la impedancia total.

4.	Presentación de Resultados: El resultado se muestra mediante un cuadro de mensaje de tkinter, que informa al usuario sobre la impedancia total del circuito.


Calculadora de Filtros Pasivos:
1.	Entrada de Datos: El usuario ingresa valores para resistencia (R), capacitancia (C), y frecuencia (f) relacionados con el filtro pasivo.

2.	Cálculos de Respuesta del Filtro: Dependiendo de la opción seleccionada (pasa bajos o pasa altos), se calcula la respuesta del filtro y se obtienen magnitud y fase utilizando funciones de la librería cmath.


3.	Presentación de Resultados: Los resultados se presentan al usuario a través de un cuadro de mensaje, proporcionando información sobre la magnitud y fase de la respuesta del filtro.

Estructura de la Interfaz Gráfica:
•	Ventana Principal: La interfaz tiene una ventana principal dividida en dos secciones, una para la calculadora de impedancias y otra para los filtros pasivos.

•	Widgets y Disposición: Se utilizan etiquetas, campos de entrada, botones y menús desplegables (OptionMenu) para organizar y presentar los elementos de la interfaz. La disposición se realiza utilizando el sistema de geometría de tkinter.

•	Manejo de Eventos: Cada botón tiene asignada una función específica (por ejemplo, calcular impedancia o calcular respuesta del filtro) que se ejecuta al hacer clic en el botón correspondiente.

Notas Adicionales:
- La variable “circuito” y “tipo_filtro” son utilizadas para almacenar la selección del usuario en los menús desplegables.
- Los resultados se muestran a través de cuadros de mensaje utilizando “messagebox.showinfo”.


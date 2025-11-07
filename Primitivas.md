Todas las escenas sintéticas que vemos están formadas por miles de triángulos
# Primitivas 2d
<img width="896" height="666" alt="image" src="https://github.com/user-attachments/assets/23ab9a1f-f1d4-4413-8084-fb802943e6d0" />
<br>
1. Los objetos presentes en la imagen se componen de primitivas simples (líneas, puntos)<br>
2. El sistema gráfico dibuja estas primitivas transformándolos en pixels -> Rasterización <br>
3. Los métodos de conversión deben ser lo más eficientes posible <br>
4. La primitiva “Punto” es la más sencilla: <br>
      4.1. se coloca la intensidad deseada en la celda de memoria del frame buffer correspondiente<br>
       4.2. El controlador de video leerá todas esas celdas, y las mandará al hardware de la pantalla<br>
5. Dibujo de líneas<br>
   5.1. Para dibujar líneas rectas, habrá que calcular las posiciones intermedias entre los dos extremos<br>
   5.2. Este problema no existía en las pantallas vectoriales o plotters<br>
   5.3. Sin embargo, las posiciones de los pixels son valores enteros, y los puntos obtenidos de la ecuación son reales -> existe un error (aliasing)<br>
   5.4. A menor resolución, mayor es el efecto<br>
   5.5. Es necesario disponer de métodos para convertir primitivas en pixels de la forma más eficiente posible<br>
   5.6. Consideraciones para el dibujo de rectas<br>
       5.6.1 Hay que calcular las coordenadas de los pixels que estén lo más cerca posible de una línea recta ideal, infinitamente delgada, superpuesta sobre la matriz de pixels.<br>
       5.6.2 Las consideraciones que un buen algoritmo debe cumplir son:<br>
             5.6.2.1 la secuencia de pixels debe ser lo más recta posible<br>
             5.6.2.2 las líneas deben dibujarse con el mismo grosor e intensidad independientemente de su inclinación<br>
             5.6.2.3 las líneas deben dibujarse lo más rápido posible<br>

6. Algoritmos para dibujar rectas<br>
   6.1 Algoritmo más sencillo<br>
       6.1.1 La ecuación de una recta es y=mx+b<br>
       6.1.2 No es muy eficiente<br>
       6.1.3 Cada paso requiere una multiplicación flotante, una suma y un redondeo     <br>

      <img width="417" height="331" alt="image" src="https://github.com/user-attachments/assets/969f124f-73c5-4009-a700-369a9637b8af" />
      <br>
   6.2 Algoritmo Básico Incremental (DDA)<br>
       6.2.1 Podemos eliminar la multiplicación de la siguiente manera:<br>
             6.2.1.1 Sabemos que yi = mxi + b<br>
             6.2.1.2 Entonces yi+1 = mxi+1 + b = … ⇒ yi+1 = yi + m ∆x<br>
             6.2.1.3 Como ∆x=1, llegamos a la fórmula final yi+1 = yi + m<br>
             6.2.1.4 Cada pixel se calcula en función del anterior <br>
             6.2.1.5 No hace falta calcular b<br>
             6.2.1.6 Solución: intercambiamos las variables x e y<br>
             6.2.1.7 Sabemos que xi= (1/m) (yi – b) . Entonces:<br>
             6.2.1.8 xi+1 = (1/m)yi+1 - b/m = … ⇒ xi+1 = xi + ∆y/m<br>
             6.2.1.9 Como ∆y=1, llegamos a la fórmula final xi+1 = xi + 1/m<br>
     6.2.2 Inconvenientes:<br>
           6.2.2.1 Existen errores de acumulación<br>
           6.2.2.2 El redondeo es muy lento<br>
         
             
    <img width="556" height="522" alt="image" src="https://github.com/user-attachments/assets/60a6aa0c-24e6-4c84-b5ae-fe1ff69ea3a7" />



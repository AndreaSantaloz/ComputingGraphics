Todas las escenas sintéticas que vemos están formadas por miles de triángulos
# Primitivas 2d
<img width="896" height="666" alt="image" src="https://github.com/user-attachments/assets/23ab9a1f-f1d4-4413-8084-fb802943e6d0" />
1. Los objetos presentes en la imagen se componen de primitivas simples (líneas, puntos)
2. El sistema gráfico dibuja estas primitivas transformándolos en pixels  Rasterización
3. Los métodos de conversión deben ser lo más eficientes posible
4. La primitiva “Punto” es la más sencilla:
    4.1. se coloca la intensidad deseada en la celda de memoria del frame buffer correspondiente
    4.2. El controlador de video leerá todas esas celdas, y las mandará al hardware de la pantalla

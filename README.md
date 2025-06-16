# Documentación del Juego Snake Clásico con Tkinter

## Descripción General
Este es un juego clásico de Snake implementado en Python usando la biblioteca Tkinter para la interfaz gráfica. El juego incluye un menú principal, pantalla de ajustes configurables y la lógica completa del juego Snake.

## Estructura del Código

### Clase Principal: `SnakeGame`
La clase principal que gestiona toda la aplicación del juego.

#### Métodos Principales:

1. **`__init__(self, root)`**
   - Constructor que inicializa la ventana principal y la configuración por defecto
   - Crea el contenedor principal y muestra el menú inicial

2. **`show_main_menu(self)`**
   - Muestra el menú principal con tres opciones:
     - Jugar
     - Ajustes
     - Salir
   - Diseño visual con efectos hover en los botones

3. **`show_settings(self)`**
   - Muestra la pantalla de configuración con:
     - Control deslizante para ajustar la velocidad del juego
     - Selector de color para la serpiente (4 opciones)
     - Botones para guardar y volver

4. **`save_settings(self)`**
   - Guarda los ajustes seleccionados en el diccionario `game_settings`
   - Actualiza la velocidad y color de la serpiente

5. **`start_game(self)`**
   - Inicializa el juego con los parámetros configurados
   - Crea el canvas donde se dibujará el juego
   - Configura los controles y reinicia el estado del juego

### Lógica del Juego

6. **`reset_game(self)`**
   - Reinicia todas las variables del juego:
     - Posición inicial de la serpiente
     - Dirección de movimiento
     - Posición de la comida
     - Puntuación
   - Dibuja los elementos iniciales

7. **`move_snake(self)`**
   - Lógica principal del movimiento de la serpiente
   - Maneja:
     - Movimiento en las 4 direcciones
     - Crecimiento al comer
     - Detección de colisiones
     - Fin del juego

8. **`update_game(self)`**
   - Bucle principal del juego
   - Actualiza la posición de la serpiente según la velocidad configurada

### Funciones de Dibujo

9. **`draw_snake(self)`**
   - Dibuja todos los segmentos de la serpiente usando rectángulos
   - Usa el color configurado en los ajustes

10. **`draw_food(self)`**
    - Dibuja la comida como un círculo rojo

11. **`draw_score(self)`**
    - Muestra la puntuación actual en la esquina superior izquierda

12. **`draw_game_over(self)`**
    - Muestra el mensaje de fin de juego con la puntuación final

### Control del Juego

13. **`setup_controls(self)`**
    - Configura los eventos de teclado:
      - Teclas de flecha para movimiento
      - ESC para volver al menú
      - P para pausar

14. **`pause_game(self)`**
    - Alterna entre pausa y continuar el juego
    - Muestra un mensaje durante la pausa

15. **`change_direction(self, new_dir)`**
    - Cambia la dirección de movimiento
    - Previene movimientos inversos inválidos

## Configuración del Juego

El diccionario `game_settings` contiene:

```python
{
    "speed": 150,          # Velocidad inicial (ms entre actualizaciones)
    "snake_color": "green",# Color de la serpiente
    "food_color": "red",   # Color de la comida
    "bg_color": "black",   # Color de fondo
    "text_color": "white"  # Color del texto
}
```

## Flujo del Programa

1. Se crea la instancia de `SnakeGame` con la ventana principal de Tkinter
2. Muestra el menú principal
3. El usuario puede:
   - Ir a ajustes y modificar configuración
   - Iniciar el juego
   - Salir de la aplicación
4. Durante el juego, puede:
   - Controlar la serpiente
   - Pausar el juego
   - Volver al menú principal

## Requisitos

- Python 3.x
- Bibliotecas:
  - tkinter
  - random

## Personalización

Los aspectos que se pueden configurar fácilmente son:

1. **Velocidad del juego**: Desde 50ms (muy rápido) hasta 300ms (lento)
2. **Color de la serpiente**: 4 opciones disponibles (verde, azul, amarillo, morado)
3. **Tamaño del tablero**: Modificando `width` y `height` en `start_game()`
4. **Tamaño de celda**: A través de `cell_size`

## Limitaciones Conocidas

1. No guarda las puntuaciones máximas entre sesiones
2. El diseño visual es básico pero funcional
3. Solo un modo de juego disponible

## Posibles Mejoras

1. Implementar sistema de guardado de puntuaciones
2. Añadir diferentes modos de juego
3. Incluir efectos de sonido
4. Agregar más opciones de personalización

# Snake Clásico

## 1. Descripción General
Este programa implementa el clásico juego Snake utilizando Python y la biblioteca Tkinter para la interfaz gráfica. El juego incluye un menú principal, sistema de ajustes configurables y la lógica completa del juego.

## 2. Estructura de Clases

### 2.1 Clase Principal: `SnakeGame`
Gestiona toda la aplicación y contiene las siguientes funcionalidades:

```python
class SnakeGame:
    def __init__(self, root):
        # Inicialización de la ventana principal
        self.root = root
        self.root.title("Snake Clásico")
        self.root.geometry("800x600")
        self.root.resizable(False, False)
        
        # Configuración por defecto
        self.game_settings = {
            "speed": 150,         # Velocidad inicial (ms)
            "snake_color": "green", # Color de la serpiente
            "food_color": "red",   # Color de la comida
            "bg_color": "black",   # Color de fondo
            "text_color": "white"  # Color del texto
        }
```

## 3. Subsistemas Principales

### 3.1 Sistema de Menú
| Método | Descripción |
|--------|-------------|
| `show_main_menu()` | Muestra la pantalla principal con botones de navegación |
| `show_settings()` | Muestra el panel de configuración del juego |
| `clear_screen()` | Elimina todos los widgets del contenedor principal |

### 3.2 Sistema de Juego
| Componente | Función |
|------------|---------|
| `start_game()` | Inicializa el área de juego |
| `reset_game()` | Reinicia el estado del juego |
| `move_snake()` | Lógica de movimiento y colisiones |
| `draw_snake()` | Renderizado de la serpiente |
| `draw_food()` | Renderizado de la comida |

### 3.3 Sistema de Configuración
| Elemento | Tipo | Rango | Efecto |
|----------|------|-------|--------|
| Velocidad | Slider | 50-300 ms | Controla la velocidad de actualización |
| Color Serpiente | Radio Buttons | 4 opciones | Cambia el color de la serpiente |

## 4. Flujo del Programa

1. **Inicialización**:
   ```mermaid
   graph TD
     A[Inicio] --> B[Mostrar Menú Principal]
     B --> C[Esperar Interacción]
   ```

2. **Ciclo del Juego**:
   ```mermaid
   graph TD
     G[Inicio Juego] --> H[Dibujar Elementos]
     H --> I[Esperar Input]
     I --> J{Movimiento}
     J --> K[Actualizar Posición]
     K --> L[Verificar Colisiones]
     L --> M{Game Over?}
     M -->|No| H
     M -->|Sí| N[Mostrar Resultados]
   ```

## 5. Detalles Técnicos

### 5.1 Control de la Serpiente
```python
def change_direction(self, new_dir):
    opposites = [("Up", "Down"), ("Left", "Right")]
    if not self.paused and (self.direction, new_dir) not in opposites:
        self.next_direction = new_dir
```
- Implementa restricción para evitar movimientos inversos
- Gestiona la dirección actual y la siguiente por separado

### 5.2 Sistema de Colisiones
```python
# Verificación de colisiones
if (new_head in self.snake or 
    new_head[0] < 0 or 
    new_head[0] >= self.width or 
    new_head[1] < 0 or 
    new_head[1] >= self.height):
    self.game_over = True
```
- Detecta colisiones con:
  - El propio cuerpo
  - Los bordes del área de juego

## 6. Personalización

### 6.1 Ajustes Disponibles
| Parámetro | Valores | Método de Cambio |
|-----------|---------|------------------|
| Velocidad | 50-300 ms | Slider interactivo |
| Color | green, blue, yellow, purple | Selector visual |

### 6.2 Persistencia de Configuración
Los ajustes se guardan en el diccionario `game_settings` y persisten durante toda la sesión.

## 7. Requisitos del Sistema

- Python 3.6+
- Bibliotecas:
  - tkinter (incluida en Python estándar)
  - random (incluida en Python estándar)

## 8. Ejecución

Para iniciar el juego:
```bash
python snake_game.py
```

## 9. Limitaciones Conocidas

1. Las puntuaciones no se guardan entre sesiones
2. El tamaño del tablero es fijo (600x400 px)
3. Solo disponible un modo de juego básico

## 10. Posibles Mejoras

1. Implementar sistema de guardado de puntuaciones
2. Añadir diferentes niveles de dificultad
3. Incorporar efectos de sonido
4. Añadir modo de dos jugadores

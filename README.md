# Simulador DCU · Ciclo PHVA

Simulación visual e interactiva del proceso de **Diseño Centrado en el Usuario (DCU)** aplicado al ciclo de mejora continua **PHVA** (Planear → Hacer → Verificar → Actuar). El sistema repite el ciclo automáticamente mientras la solución no satisfaga los requerimientos del usuario.

## Descripción

El proyecto parte de un script en Python que simula el ciclo PHVA mediante un bucle `while`:

```python
def simulador_dcu():
    print("Iniciando Proceso DCU (PHVA)...")
    satisfactorio = False
    while not satisfactorio:
        print("Planear: Analizando usuario y requisitos.")
        print("Hacer: Produciendo soluciones de diseño.")
        evaluacion = input("Verificar: ¿Satisface el sistema los requerimientos? (s/n): ")
        if evaluacion.lower() == 's':
            print("Actuar: Desarrollo Exitoso.")
            satisfactorio = True
        else:
            print("Actuar: Iterando el ciclo de diseño.")
```

A partir de esa lógica se construyó una versión web (`simulador_dcu_phva.html`) que representa el mismo comportamiento de forma gráfica.

## Archivo principal

| Archivo | Descripción |
|---|---|
| `simulador_dcu_phva.html` | Simulador interactivo en HTML/CSS/JS. No requiere instalación ni dependencias externas (solo conexión a internet para cargar las tipografías de Google Fonts). |

## Cómo usarlo

1. Abre `simulador_dcu_phva.html` en cualquier navegador moderno (Chrome, Firefox, Edge, Safari).
2. Presiona **"Iniciar proceso"** para comenzar el ciclo.
3. El sistema recorre automáticamente las fases **Planear** y **Hacer**.
4. En la fase **Verificar** debes responder si el sistema cumple los requerimientos:
   - **Sí, satisface ✓** → el ciclo termina y se muestra el mensaje de *Desarrollo Exitoso*.
   - **No, iterar ↺** → la fase **Actuar** reinicia el ciclo, regresando a *Planear* y sumando una nueva iteración.
5. El contador central muestra cuántas iteraciones ha tomado llegar a una solución satisfactoria.
6. Una vez finalizado con éxito, el botón cambia a **"Reiniciar simulación"** para volver a empezar desde cero.

## Características de diseño

- **Diagrama circular de 4 fases**: cada cuadrante de la rueda representa una etapa del PHVA y se ilumina progresivamente conforme avanza el ciclo.
- **Bitácora de eventos**: panel lateral estilo terminal que registra en tiempo real cada paso del proceso, igual que la salida por consola del script original.
- **Iteración visual**: cuando la verificación falla, la animación regresa al inicio del ciclo, reflejando el comportamiento del `while` del script en Python.
- **Accesibilidad básica**: foco visible en los controles y soporte para `prefers-reduced-motion`.
- **Responsivo**: se adapta a pantallas de escritorio y dispositivos móviles.

## Relación entre el script y la simulación visual

| Concepto del script Python | Elemento en la simulación HTML |
|---|---|
| `print("Planear: ...")` | Arco "01 PLANEAR" activo + entrada en la bitácora |
| `print("Hacer: ...")` | Arco "02 HACER" activo + entrada en la bitácora |
| `input("Verificar: ...")` | Arco "03 VERIFICAR" activo + botones "Sí" / "No" |
| `satisfactorio = True` | Banner verde "Desarrollo Exitoso" + fin del ciclo |
| `else: # iterar` | Arco "04 ACTUAR" activo, contador +1, regreso a Planear |

## Requisitos

- No requiere backend ni instalación.
- Funciona abriendo el archivo directamente (`file://`) o sirviéndolo desde cualquier servidor web estático.

## Autoría

Material de apoyo para la unidad **"Diseño centrado en el usuario (DCU) y sus métodos"**.

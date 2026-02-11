### **Modificación de la Práctica 2**
En la Práctica 2, agregaremos **Matplotlib en Tkinter** para graficar los datos recibidos desde **Arduino** en tiempo real.

---

### **1️Instalación de Bibliotecas Adicionales**
Antes de comenzar, necesitamos instalar `matplotlib`:
```sh
pip install matplotlib
```
Esto permitirá dibujar gráficos dentro de la interfaz de Tkinter.

---

### **2️Código Modificado para la Práctica 2 (Tkinter + Gráfica en Matplotlib)**
```python
import tkinter as tk
import serial
import time
import matplotlib.pyplot as plt
from matplotlib.animation import FuncAnimation
from matplotlib.backends.backend_tkagg import FigureCanvasTkAgg

# Configuración del puerto serial
puerto = 'COM6'  # Cambiar según el puerto del Arduino
baudrate = 9600

print("Conectando al Arduino...")
try:
    arduino = serial.Serial(puerto, baudrate, timeout=3.0)
    print("Conectado al Arduino.")
except Exception as e:
    print(f"Error de conexión: {e}")
    arduino = None

# Lista para almacenar los datos del sensor
valores_sensor = []

# Función para solicitar datos al Arduino
def leer_sensor():
    if arduino:
        arduino.write("r".encode())  # Envía el comando 'r' al Arduino
        val = arduino.readline().strip()  # Lee el valor enviado por el Arduino
        try:
            val = int(val)  # Convierte a entero
            etiqueta_valor.config(text=f"Valor Sensor: {val}")  # Actualiza la interfaz
            valores_sensor.append(val)
            if len(valores_sensor) > 20:  # Mantener solo los últimos 20 valores
                valores_sensor.pop(0)
        except ValueError:
            etiqueta_valor.config(text="Error en la lectura")

    ventana.after(500, leer_sensor)  # Llama a esta función cada 500ms

# Función para actualizar la gráfica
def actualizar_grafico(i):
    ax.clear()
    ax.plot(valores_sensor, marker='o', linestyle='-')
    ax.set_title("Valores del Sensor en Tiempo Real")
    ax.set_ylabel("Valor Sensor")
    ax.set_xlabel("Tiempo")
    ax.set_ylim(0, 1023)  # Rango de valores analógicos en Arduino
    canvas.draw()

# Crear la ventana principal
ventana = tk.Tk()
ventana.title("Lectura de Sensor con Arduino")
ventana.geometry("600x500")

# Crear widgets
etiqueta = tk.Label(ventana, text="Leyendo datos del sensor...", font=("Arial", 14))
etiqueta.pack(pady=10)

etiqueta_valor = tk.Label(ventana, text="Valor Sensor: --", font=("Arial", 18), fg="blue")
etiqueta_valor.pack(pady=10)

# Crear la figura de Matplotlib dentro de Tkinter
fig, ax = plt.subplots(figsize=(7, 5))
canvas = FigureCanvasTkAgg(fig, master=ventana)  # Agrega la figura a Tkinter
canvas.get_tk_widget().pack()

# Animación en tiempo real
ani = FuncAnimation(fig, actualizar_grafico, interval=1000)

# Iniciar la actualización automática
leer_sensor()

# Iniciar la interfaz gráfica
ventana.mainloop()
```


---

### **Explicación Detallada del Código - Práctica 2 (Tkinter + Matplotlib en Tiempo Real)**  


## **1️ Importación de Bibliotecas**
```python
import tkinter as tk
import serial
import time
import matplotlib.pyplot as plt
from matplotlib.animation import FuncAnimation
from matplotlib.backends.backend_tkagg import FigureCanvasTkAgg
```
### **Explicación**
- `tkinter`: Biblioteca para crear **interfaces gráficas** en Python.
- `serial`: Permite **comunicarse con Arduino** a través del **puerto USB**.
- `time`: Maneja **pausas y tiempos de espera** en el código.
- `matplotlib.pyplot`: Librería para **crear gráficos** en Python.
- `FuncAnimation`: Permite **actualizar gráficos en tiempo real**.
- `FigureCanvasTkAgg`: **Integra gráficos de Matplotlib en Tkinter**.

---

## **2️ Configuración del Puerto Serial**
```python
puerto = 'COM6'  # Cambiar según el puerto del Arduino
baudrate = 9600

print("Conectando al Arduino...")
try:
    arduino = serial.Serial(puerto, baudrate, timeout=3.0)
    print("Conectado al Arduino.")
except Exception as e:
    print(f"Error de conexión: {e}")
    arduino = None
```
### **Explicación**
1. Se define el **puerto** (`COM6` en Windows, `/dev/ttyUSB0` en Linux/Mac).
2. Se establece la **velocidad de transmisión (baudrate)** en 9600 baudios.
3. Se intenta abrir la conexión con **`serial.Serial()`**:
   - Si el puerto está disponible, se **establece la conexión**.
   - Si hay un error (Arduino no conectado), se **maneja la excepción** y se imprime el mensaje de error.

---

## **3️ Creación de una Lista para Almacenar los Datos**
```python
valores_sensor = []
```
### **🔍 Explicación**
- Se crea una **lista vacía** `valores_sensor` para almacenar los valores que se recibirán del **Arduino**.
- Se usará para **graficar los últimos 20 valores recibidos**.

---

## **4️ Función para Leer Datos del Sensor**
```python
def leer_sensor():
    if arduino:
        arduino.write("r".encode())  # Envía el comando 'r' al Arduino
        val = arduino.readline().strip()  # Lee el valor enviado por el Arduino
        try:
            val = int(val)  # Convierte a entero
            etiqueta_valor.config(text=f"Valor Sensor: {val}")  # Actualiza la interfaz
            valores_sensor.append(val)  # Agrega el nuevo valor a la lista
            if len(valores_sensor) > 20:  # Mantener solo los últimos 20 valores
                valores_sensor.pop(0)  # Elimina el valor más antiguo
        except ValueError:
            etiqueta_valor.config(text="Error en la lectura")

    ventana.after(500, leer_sensor)  # Llama a esta función cada 500ms
```
### ** Explicación**
1. **Si Arduino está conectado**, se envía el comando **`"r".encode()`** para solicitar un dato.
2. **Se lee la respuesta del Arduino** usando `readline().strip()`.
3. **Se intenta convertir el valor a un entero** (`int(val)`) para evitar errores.
4. **Se actualiza el valor en la interfaz gráfica** (`etiqueta_valor.config(...)`).
5. **Se agrega el valor a la lista `valores_sensor`**.
6. **Si la lista supera los 20 valores**, se **elimina el más antiguo** para evitar que la gráfica crezca infinitamente.
7. **Se vuelve a llamar a la función `leer_sensor()` cada 500 ms** con `ventana.after(500, leer_sensor)`, lo que crea un **bucle automático**.

---

## **5️ Función para Actualizar la Gráfica en Tiempo Real**
```python
def actualizar_grafico(i):
    ax.clear()
    ax.plot(valores_sensor, marker='o', linestyle='-')
    ax.set_title("Valores del Sensor en Tiempo Real")
    ax.set_ylabel("Valor Sensor")
    ax.set_xlabel("Tiempo")
    ax.set_ylim(0, 1023)  # Rango de valores analógicos en Arduino
    canvas.draw()
```
### ** Explicación**
1. **Borra el gráfico anterior** con `ax.clear()`.
2. **Dibuja los nuevos valores en la gráfica** con `ax.plot(valores_sensor)`.
3. **Agrega títulos y etiquetas** (`set_title()`, `set_ylabel()`, `set_xlabel()`).
4. **Establece un rango entre 0 y 1023** (`ax.set_ylim(0, 1023)`) porque **Arduino devuelve valores de 0 a 1023** en entradas analógicas.
5. **Redibuja la gráfica** con `canvas.draw()`, actualizando la ventana en tiempo real.

---

## **6️ Creación de la Ventana en Tkinter**
```python
ventana = tk.Tk()
ventana.title("Lectura de Sensor con Arduino")
ventana.geometry("500x400")
```
### ** Explicación**
- **`tk.Tk()`**: Crea la ventana principal.
- **`title("Lectura de Sensor con Arduino")`**: Define el título de la ventana.
- **`geometry("500x400")`**: Define el **tamaño de la ventana** en píxeles.

---

## **7️ Creación de Etiquetas para Mostrar el Valor**
```python
etiqueta = tk.Label(ventana, text="Leyendo datos del sensor...", font=("Arial", 14))
etiqueta.pack(pady=10)

etiqueta_valor = tk.Label(ventana, text="Valor Sensor: --", font=("Arial", 18), fg="blue")
etiqueta_valor.pack(pady=10)
```
### ** Explicación**
- **`Label(ventana, text=...)`**: Crea un texto en la interfaz.
- **`font=("Arial", 14)`**: Define el **tamaño y tipo de letra**.
- **`fg="blue"`**: Pone el texto en **color azul**.
- **`pack(pady=10)`**: Agrega espacio entre los elementos.

---

## **8️ Integración de la Gráfica en Tkinter**
```python
fig, ax = plt.subplots(figsize=(5, 3))
canvas = FigureCanvasTkAgg(fig, master=ventana)  # Agrega la figura a Tkinter
canvas.get_tk_widget().pack()
```
### ** Explicación**
1. **Crea una figura con `plt.subplots()`** de Matplotlib.
2. **Integra la figura en Tkinter** con `FigureCanvasTkAgg(fig, master=ventana)`.
3. **Empaqueta la gráfica dentro de la ventana** con `canvas.get_tk_widget().pack()`.

---

## **9️ Animación para Actualizar la Gráfica en Tiempo Real**
```python
ani = FuncAnimation(fig, actualizar_grafico, interval=1000)
```
### ** Explicación**
- `FuncAnimation(fig, actualizar_grafico, interval=1000)`:  
  - **Ejecuta `actualizar_grafico()` cada segundo**.
  - **Redibuja la gráfica** con los valores actualizados.

---

## ** Iniciar la Lectura del Sensor y la Interfaz**
```python
leer_sensor()
ventana.mainloop()
```
### ** Explicación**
- **`leer_sensor()`**: Comienza la lectura de datos desde Arduino.
- **`ventana.mainloop()`**: Mantiene abierta la interfaz gráfica y espera eventos (clics, teclas, etc.).

---

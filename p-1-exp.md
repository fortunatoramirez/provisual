# **Explicación del Código en Python (Tkinter)**  

### **Código Original**
```python
import tkinter as tk

# Función que se ejecutará cuando el botón sea presionado
def mostrar_mensaje():
    texto = entrada.get()
    etiqueta.config(text=f"Hola, {texto}")

# Crear la ventana principal
ventana = tk.Tk()
ventana.title("Interfaz Gráfica con Tkinter")
ventana.geometry("300x200")

# Crear widgets (campo de entrada, botón y etiqueta)
entrada = tk.Entry(ventana)
entrada.pack(pady=10)

boton = tk.Button(ventana, text="Saludar", command=mostrar_mensaje)
boton.pack(pady=5)

etiqueta = tk.Label(ventana, text="Ingresa tu nombre y presiona el botón")
etiqueta.pack(pady=10)

# Iniciar la interfaz gráfica
ventana.mainloop()
```

---

## **Explicación Línea por Línea**

### **1. Importación del Módulo Tkinter**
```python
import tkinter as tk
```
- **Sintaxis:** `import tkinter as tk`
- **Semántica:** Importa el módulo `tkinter`, que es la biblioteca estándar para interfaces gráficas en Python. Se usa el alias `tk` para abreviar su uso en el código.

---

### **2. Definición de la Función para Manejar Eventos**
```python
def mostrar_mensaje():
```
- **Sintaxis:** `def nombre_funcion():`
- **Semántica:** Se define la función `mostrar_mensaje()`, que será ejecutada cuando el usuario presione el botón.

```python
    texto = entrada.get()
```
- **Sintaxis:** `variable = widget.get()`
- **Semántica:** Obtiene el contenido del campo de entrada `entrada` y lo almacena en la variable `texto`.

```python
    etiqueta.config(text=f"Hola, {texto}")
```
- **Sintaxis:** `widget.config(propiedad=valor)`
- **Semántica:** Cambia el texto de la etiqueta (`Label`) con un mensaje personalizado.  
- **Uso de `f""` (f-string en Python):** Permite incluir variables dentro de un texto de manera sencilla.

---

### **3. Creación de la Ventana Principal**
```python
ventana = tk.Tk()
```
- **Sintaxis:** `variable = tk.Tk()`
- **Semántica:** Crea la ventana principal de la aplicación.

```python
ventana.title("Interfaz Gráfica con Tkinter")
```
- **Sintaxis:** `ventana.title("texto")`
- **Semántica:** Establece el título de la ventana.

```python
ventana.geometry("300x200")
```
- **Sintaxis:** `ventana.geometry("ancho x alto")`
- **Semántica:** Define el tamaño de la ventana en píxeles.

---

### **4. Creación de Widgets (Componentes de la Interfaz)**
#### **Campo de Entrada**
```python
entrada = tk.Entry(ventana)
```
- **Sintaxis:** `variable = tk.Entry(ventana)`
- **Semántica:** Crea un campo de entrada de texto dentro de `ventana`.

```python
entrada.pack(pady=10)
```
- **Sintaxis:** `widget.pack(opciones)`
- **Semántica:** Organiza el widget en la ventana y agrega un espacio vertical (`pady=10`).

---

#### **Botón**
```python
boton = tk.Button(ventana, text="Saludar", command=mostrar_mensaje)
```
- **Sintaxis:** `tk.Button(ventana, text="Texto", command=funcion)`
- **Semántica:** Crea un botón con el texto "Saludar" que ejecuta `mostrar_mensaje()` al ser presionado.

```python
boton.pack(pady=5)
```
- **Sintaxis:** `widget.pack(opciones)`
- **Semántica:** Agrega el botón a la ventana con espacio vertical.

---

#### **Etiqueta**
```python
etiqueta = tk.Label(ventana, text="Ingresa tu nombre y presiona el botón")
```
- **Sintaxis:** `tk.Label(ventana, text="Texto")`
- **Semántica:** Crea una etiqueta con un mensaje informativo.

```python
etiqueta.pack(pady=10)
```
- **Sintaxis:** `widget.pack(opciones)`
- **Semántica:** Organiza la etiqueta en la interfaz con espacio.

---

### **5. Iniciar el Bucle de Eventos**
```python
ventana.mainloop()
```
- **Sintaxis:** `ventana.mainloop()`
- **Semántica:** Mantiene la ventana abierta y espera eventos (clics, entradas de texto, etc.).

---

# **Explicación del Código en JavaScript (HTML + CSS + JS)**

### **Código Original**
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Interfaz Gráfica con JavaScript</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 50px;
        }
        input, button {
            margin: 10px;
            padding: 8px;
        }
    </style>
</head>
<body>
    <h2>Ingresa tu nombre:</h2>
    <input type="text" id="nombre">
    <button onclick="mostrarMensaje()">Saludar</button>
    <p id="mensaje"></p>

    <script>
        function mostrarMensaje() {
            let nombre = document.getElementById("nombre").value;
            document.getElementById("mensaje").innerText = `Hola, ${nombre}`;
        }
    </script>
</body>
</html>
```

---

## **Explicación Línea por Línea**

### **1. Definición del Documento HTML**
```html
<!DOCTYPE html>
```
- **Sintaxis:** `<!DOCTYPE html>`
- **Semántica:** Declara el documento como HTML5.

```html
<html lang="es">
```
- **Sintaxis:** `<html lang="idioma">`
- **Semántica:** Indica el idioma del documento (español).

---

### **2. Configuración del Encabezado (`<head>`)**
```html
<meta charset="UTF-8">
```
- **Sintaxis:** `<meta charset="UTF-8">`
- **Semántica:** Define la codificación de caracteres para admitir acentos y símbolos.

```html
<title>Interfaz Gráfica con JavaScript</title>
```
- **Sintaxis:** `<title>Texto</title>`
- **Semántica:** Define el título de la página web.

---

### **3. Estilos CSS**
```css
body {
    font-family: Arial, sans-serif;
    text-align: center;
    margin-top: 50px;
}
```
- **Sintaxis:** `selector { propiedad: valor; }`
- **Semántica:** Define el estilo del `body`, estableciendo fuente y alineación.

```css
input, button {
    margin: 10px;
    padding: 8px;
}
```
- **Sintaxis:** `elemento1, elemento2 { propiedad: valor; }`
- **Semántica:** Establece márgenes y relleno para `input` y `button`.

---

### **4. Cuerpo del Documento (`<body>`)**
```html
<input type="text" id="nombre">
```
- **Sintaxis:** `<input type="text" id="identificador">`
- **Semántica:** Crea un campo de entrada de texto con el ID `nombre`.

```html
<button onclick="mostrarMensaje()">Saludar</button>
```
- **Sintaxis:** `<button onclick="funcion()">Texto</button>`
- **Semántica:** Crea un botón que ejecuta `mostrarMensaje()`.

---

### **5. Código JavaScript**
```js
function mostrarMensaje() {
    let nombre = document.getElementById("nombre").value;
    document.getElementById("mensaje").innerText = `Hola, ${nombre}`;
}
```
- **Sintaxis:** `document.getElementById("id").propiedad`
- **Semántica:** Obtiene el valor del campo `nombre` y actualiza el texto del párrafo `mensaje`.


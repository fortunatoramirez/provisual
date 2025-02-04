# Introducción a Programación Visual

## 1. Introducción
Antes de comenzar a programar en **Python y JavaScript**, es importante entender algunos conceptos clave.

---

## 1.1 ¿Qué es la Programación Visual?
**Definición:**  
La **programación visual** es el desarrollo de aplicaciones con **interfaces gráficas de usuario (GUI, Graphical User Interface)** en lugar de trabajar únicamente con la terminal o línea de comandos.

**Ejemplo de diferencias:**
| **Método**  | **Explicación** | **Ejemplo** |
|------------|---------------|------------|
| **Consola** | Interacción solo con texto, sin gráficos. | `print("Hola mundo")` en terminal |
| **GUI** | Permite botones, ventanas, menús y gráficos. | Ventana con un botón que muestra "Hola Mundo" |

**Ejemplos de GUIs que usamos todos los días:**  
- Aplicaciones móviles y de escritorio (**WhatsApp, Spotify, Calculadora**).  
- Paneles de control en sistemas industriales.  
- Interfaz de cajeros automáticos, software médico, etc.  

---

## 1.2 ¿Por qué Python y JavaScript?
**Python**  
- Lenguaje **fácil de aprender**, con sintaxis clara y amigable.  
- Muy usado en **ciencia de datos, inteligencia artificial y automatización**.  
- Tiene librerías como **Tkinter, PyQt y Kivy** para crear **interfaces gráficas**.  

**JavaScript**  
- Lenguaje fundamental para **desarrollo web**.  
- Puede utilizarse tanto en **navegadores** como en **aplicaciones de escritorio** con **Electron.js**.  
- Permite agregar **interactividad** a las aplicaciones gráficas.  

| **Comparación Python vs JavaScript** | **Python** | **JavaScript** |
|--------------------------------------|------------|--------------|
| **Uso** | Aplicaciones de escritorio, ciencia de datos, IoT. | Aplicaciones web y escritorio interactivas. |
| **Interfaz gráfica** | Tkinter, PyQt, Kivy. | HTML, CSS, Electron.js. |
| **Facilidad de aprendizaje** | Fácil, sintaxis clara. | Más verboso en comparación. |
| **Popularidad** | Alto en ciencia de datos. | Alto en desarrollo web. |

---

## 1.3 Diferencia entre Programación Estructurada, POO y Programación Orientada a Eventos
Hasta ahora, solo han visto **programación estructurada**, pero en este curso usaremos también **POO (Programación Orientada a Objetos)** y **POE (Programación Orientada a Eventos)**.

### **Programación Estructurada**
- Se basa en **secuencias de instrucciones**.
- Usa funciones para dividir el código en partes reutilizables.
- **Ejemplo en Python:**
  ```python
  def sumar(a, b):
      return a + b

  print(sumar(5, 3))  # 8
  ```

### **Programación Orientada a Objetos (POO)**
- Se basa en **clases y objetos**.
- Agrupa datos y funciones dentro de estructuras llamadas **clases**.
- **Ejemplo en Python:**
  ```python
  class Persona:
      def __init__(self, nombre, edad):
          self.nombre = nombre
          self.edad = edad

      def saludar(self):
          print(f"Hola, soy {self.nombre} y tengo {self.edad} años.")

  p1 = Persona("Carlos", 25)
  p1.saludar()
  ```

### **Programación Orientada a Eventos (POE)**
- Se basa en **acciones del usuario (clics, teclas, movimientos)**.
- Se usa en **interfaces gráficas**.
- **Ejemplo en JavaScript (evento clic en un botón):**
  ```javascript
  document.getElementById("boton").addEventListener("click", function() {
      alert("¡Botón presionado!");
  });
  ```

---

## 1.4 Conexión con la Programación Visual
A lo largo del curso, usaremos estos conceptos en **interfaces gráficas**:

**Programación Estructurada:** Para manejar la lógica del programa.  
**POO:** Para estructurar la GUI en **Python y JavaScript**.  
**POE:** Para manejar eventos como clics y entradas del usuario.  

**Ejemplo:**
- Si creamos un **botón en una interfaz gráfica**, usaremos:
  - **POE** para detectar cuándo el usuario hace clic.
  - **POO** para organizar el código en clases.
  - **Programación estructurada** para ejecutar la lógica cuando se presiona el botón.

---

**Ahora que comprendemos estos conceptos, estamos listos para programar en Python y JavaScript.** 🚀  
**Siguiente sección:** [Plataformas en Línea](#-2-plataformas-en-linea)

---

## 2. Plataformas en Línea (antes de realizar las instalaciones)
Ejecutaremos código en **Python y JavaScript** usando estas herramientas:

**Python:** [Google Colab](https://colab.research.google.com/) o [Replit](https://replit.com/)  
**JavaScript:** [JSFiddle](https://jsfiddle.net/) o [PlayCode](https://playcode.io/)  

---

## 3. Introducción a Python
Python es un lenguaje sencillo y poderoso.  
Veamos algunos ejemplos básicos:

### 3.1 Variables y Operaciones
```python
# Variables en Python
nombre = "Juan"
edad = 20
print(f"Hola, mi nombre es {nombre} y tengo {edad} años.")
```

### 3.2 Condicionales
```python
# Estructura condicional en Python
numero = int(input("Ingresa un número: "))
if numero % 2 == 0:
    print("Es un número par")
else:
    print("Es un número impar")
```

### 3.3 Bucles
```python
# Bucle for en Python
for i in range(1, 6):
    print(f"Hola, este es el mensaje {i}")
```

---

## 4. Introducción a JavaScript
JavaScript es el lenguaje más utilizado para la web.  

### 4.1 Variables y Operaciones
```javascript
// Variables en JavaScript
let nombre = "Ana";
let edad = 22;
console.log(`Hola, mi nombre es ${nombre} y tengo ${edad} años.`);
```

### 4.2 Condicionales
```javascript
// Estructura condicional en JavaScript
let numero = prompt("Ingresa un número:");
if (numero % 2 === 0) {
    alert("Es un número par");
} else {
    alert("Es un número impar");
}
```

### 4.3 Bucles
```javascript
// Bucle for en JavaScript
for (let i = 1; i <= 5; i++) {
    console.log(`Hola, este es el mensaje ${i}`);
}
```

---

## 5. Ejercicio: Calculadora Básica
Crear una **calculadora simple** en **Python y JavaScript**.

### 5.1 Calculadora en Python
```python
# Calculadora en Python
def calculadora():
    print("Bienvenido a la calculadora")
    num1 = float(input("Ingrese el primer número: "))
    num2 = float(input("Ingrese el segundo número: "))
    operacion = input("Ingrese operación (+, -, *, /): ")

    if operacion == "+":
        print(f"Resultado: {num1 + num2}")
    elif operacion == "-":
        print(f"Resultado: {num1 - num2}")
    elif operacion == "*":
        print(f"Resultado: {num1 * num2}")
    elif operacion == "/":
        print(f"Resultado: {num1 / num2}")
    else:
        print("Operación inválida")

calculadora()
```

### 5.2 Calculadora en JavaScript
```javascript
// Calculadora en JavaScript
function calculadora() {
    let num1 = parseFloat(prompt("Ingrese el primer número:"));
    let num2 = parseFloat(prompt("Ingrese el segundo número:"));
    let operacion = prompt("Ingrese operación (+, -, *, /):");

    switch (operacion) {
        case "+":
            alert(`Resultado: ${num1 + num2}`);
            break;
        case "-":
            alert(`Resultado: ${num1 - num2}`);
            break;
        case "*":
            alert(`Resultado: ${num1 * num2}`);
            break;
        case "/":
            alert(`Resultado: ${num1 / num2}`);
            break;
        default:
            alert("Operación inválida");
    }
}
calculadora();
```
---

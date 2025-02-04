 

# 📌 Introducción a Programación Visual

## 📍 1. Introducción
Conceptos básicos de **Python y JavaScript**.  

---

## 🚀 2. Plataformas en Línea (antes de realizar las instalaciones)
Ejecutaremos código en **Python y JavaScript** usando estas herramientas:

✅ **Python:** [Google Colab](https://colab.research.google.com/) o [Replit](https://replit.com/)  
✅ **JavaScript:** [JSFiddle](https://jsfiddle.net/) o [PlayCode](https://playcode.io/)  

---

## 🐍 3. Introducción a Python
Python es un lenguaje sencillo y poderoso.  
Veamos algunos ejemplos básicos:

### 🔹 3.1 Variables y Operaciones
```python
# Variables en Python
nombre = "Juan"
edad = 20
print(f"Hola, mi nombre es {nombre} y tengo {edad} años.")
```

### 🔹 3.2 Condicionales
```python
# Estructura condicional en Python
numero = int(input("Ingresa un número: "))
if numero % 2 == 0:
    print("Es un número par")
else:
    print("Es un número impar")
```

### 🔹 3.3 Bucles
```python
# Bucle for en Python
for i in range(1, 6):
    print(f"Hola, este es el mensaje {i}")
```

---

## 🌐 4. Introducción a JavaScript
JavaScript es el lenguaje más utilizado para la web.  

### 🔹 4.1 Variables y Operaciones
```javascript
// Variables en JavaScript
let nombre = "Ana";
let edad = 22;
console.log(`Hola, mi nombre es ${nombre} y tengo ${edad} años.`);
```

### 🔹 4.2 Condicionales
```javascript
// Estructura condicional en JavaScript
let numero = prompt("Ingresa un número:");
if (numero % 2 === 0) {
    alert("Es un número par");
} else {
    alert("Es un número impar");
}
```

### 🔹 4.3 Bucles
```javascript
// Bucle for en JavaScript
for (let i = 1; i <= 5; i++) {
    console.log(`Hola, este es el mensaje ${i}`);
}
```

---

## 🎯 5. Ejercicio: Calculadora Básica
Crear una **calculadora simple** en **Python y JavaScript**.

### 🐍 5.1 Calculadora en Python
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

### 🌐 5.2 Calculadora en JavaScript
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

## ✅ 6. Evaluación y Siguientes Pasos
✔ Completar los ejercicios de **Python y JavaScript** en línea.  
✔ Subir **capturas de pantalla** de su código funcionando.  
✔ Reflexionar sobre **las diferencias entre Python y JavaScript**.  

🎯 **Próxima clase:** Creación de la **primera interfaz gráfica** en **Python y JavaScript**.

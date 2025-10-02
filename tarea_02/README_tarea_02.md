# Tarea 02
*Por Benjamín Astete*

---
## Descripción General
Cada problema fue resuelto en celdas independientes de Google Colab, lo que permite ejecutar y probar cada bloque por separado.

---

## Problema 1: Imprimir números del -100 al 200

### Enunciado
Escribir un programa que imprima todos los números desde `-100` hasta `200`.

### Solución
Se usó un bucle `for` junto con la función `range(-100, 201)`.  
- `range(a, b)` genera una secuencia de números desde `a` hasta `b-1`.  
- Por eso usamos `201`, puesto que el límite superior no está incluido.  

```python
for i in range(-100, 201):
    print(i)
```

### Justificación
- El bucle `for` es mejor opción que un `while` en este caso porque sabemos exactamente el rango de valores.  
- Si se quisiera optimizar la visualización, s podría imprimir en una sola línea con:  

```python
print(list(range(-100, 201)))
```

---

## Problema 2: Imprimir números divisibles entre 6

### Enunciado
Imprimir los números entre `-100` y `200` que sean divisibles por 6.

### Solución
Se utilizó nuevamente un bucle `for` y el operador módulo `%` para verificar divisibilidad.

```python
for i in range(-100, 201):
    if i % 6 == 0:
        print(i)
```

### Justificación
- `%` devuelve el resto de la división.  
- Si el resto es `0`, significa que el número es múltiplo de 6.  
- Esta técnica es más clara y rápida que hacer divisiones y luego revisar el cociente.  

### Acotaciones
Otra forma quizá sería iniciar directamente desde el múltiplo de 6 más cercano a `-100` y avanzar de 6 en 6:

```python
for i in range(-96, 201, 6):
    print(i)
```

Esto reduce un poquito la cantidad de comparaciones.

---

## Problema 3: Sumador y comparador de dos números

### Enunciado
Leer dos números, sumarlos y mostrar mensajes dependiendo del rango de la suma:  
- Si es menor a `200`: `"menor a 200"`.  
- Si está entre `200` y `250`: `"mayor a 200 y menor a 250"`.  
- Si es mayor a `250`: `"mayor a 250"`.  

### Solución
Se usaron entradas de usuario (`input()`), conversión de tipos a `int` y condicionales anidados (`if`, `elif`, `else`).

```python
num1 = int(input("Ingresa el primer número: "))
num2 = int(input("Ingresa el segundo número: "))

suma = num1 + num2

if suma < 200:
    print("El resultado es menor a 200")
elif suma > 200 and suma < 250:
    print("El resultado es mayor a 200 y menor a 250")
else:
    print("El resultado es mayor a 250")
```

### Justificación
- Se usaron comparaciones encadenadas (`> 200 and < 250`).  
- Es más legible que un `if` dentro de otro `if`.  
- Se puede mejorar la claridad usando comparaciones múltiples de Python:  

```python
elif 200 < suma < 250:
```

---

## Problema 4: Calculador de perfil

### Enunciado
Crear una función que evalúe si un usuario es mayor de edad (`edad >= 18`) y si le gusta la música urbana, mostrando distintos mensajes.

### Solución
Se implementó una función para centralizar la lógica. La preferencia musical se transformó en un valor booleano a partir de la respuesta del usuario.

```python
def perfil_usuario(edad, gusta_musica_urbana):
    if edad >= 18 and gusta_musica_urbana:
        return "Eres mayor de edad y te gusta la música urbana"
    else:
        return "No eres mayor de edad o no te gusta la música urbana"

edad = int(input("Ingresa tu edad: "))
respuesta = input("¿Te gusta la música urbana? (si/no): ").lower()

if respuesta == "si":
    gusta = True
else:
    gusta = False

print(perfil_usuario(edad, gusta))
```

### Justificación
- Se usó una función para que el código sea reutilizable.  
- Se incluyó una conversión de la respuesta del usuario a `lower()` para evitar errores con mayúsculas.  
- La lógica combina un condicional con un operador lógico `and`.  

### Acotaciones
- Podría ampliarse el programa con más géneros musicales, usando un menú o una lista de preferencias.  
- También podría implementarse con diccionarios para mapear preferencias de forma más flexible.  

---

## Conclusiones y observaciones generales
- Los ejercicios me sirvieron como una introducción a los bucles, condicionales, entrada de datos y funciones.  
- Para ptimizar algunos problemas, se podrían usar saltos en `range()` o comparaciones encadenadas.  
- Es recomendable manejar validaciones de entrada (ej. si el usuario escribe letras en lugar de números, el programa falla). Una mejora sería envolver el `input()` en un `try/except`.  
- Estos mismos problemas se podrían tal vez resolver con list comprehensions o funciones lambda, pero se prefirió mantener soluciones simples a los problemas.

import numpy as np

def pedir_matriz(nombre):
    """Función corta para pedir filas y columnas."""
    # NOTA: Todo esto debe tener 4 espacios a la izquierda
    print(f"\n--- MATRIZ {nombre} ---")
    filas = int(input(f"Filas de {nombre}: "))
    cols = int(input(f"Columnas de {nombre}: "))
    lista = []

    # Bucle anidado sencillo
    for i in range(filas):
        # Aquí van 8 espacios (dentro del primer for)
        fila = [] 
        for j in range(cols):
            # Aquí van 12 espacios (dentro del segundo for)
            val = float(input(f"Número [{i+1},{j+1}]: "))
            fila.append(val)
        # 8 espacios otra vez (fuera del segundo for, pero dentro del primero)
        lista.append(fila)
        
    # 4 espacios (fuera de los bucles, fin de la función)
    return np.array(lista)

# --- PROGRAMA PRINCIPAL ---
# 1. Pedimos las matrices una sola vez
# Esto va sin espacios (pegado a la izquierda)
A = pedir_matriz("A")
B = pedir_matriz("B")

print("\n" + "="*20 + "\n RESULTADOS\n" + "="*20)

# 2. Transpuesta (Siempre funciona, es solo girar)
print(f"Transpuesta de A:\n{A.T}\n")

# 3. Operaciones Básicas (Suma y Resta)
try:
    print(f"Suma (A+B):\n{A + B}\n")
    print(f"Resta (A-B):\n{A - B}\n")
except ValueError:
    print("Suma/Resta: ¡Error! Deben tener el mismo tamaño.\n")

# 4. Multiplicación (A * B)
try:
    print(f"Multiplicación (A x B):\n{np.dot(A, B)}\n")
except ValueError:
    print("Multiplicación: ¡Error! Columnas de A deben coincidir con Filas de B.\n")

# 5. Inversa (Solo de A)
try:
    print(f"Inversa de A:\n{np.linalg.inv(A)}\n")
except np.linalg.LinAlgError:
    print("Inversa de A: No tiene (Determinante es 0 o no es cuadrada).")

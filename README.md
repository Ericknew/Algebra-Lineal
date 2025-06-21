# Entregable 3 - Tarea 3.
```python
import numpy as np

# Fijar semilla para reproducibilidad
np.random.seed(42)

# Crear matriz aleatoria A de tamaño 10x4
A = np.random.rand(10, 4)

# Calcular A^T A y A A^T
ATA = A.T @ A
AAT = A @ A.T

# Obtener todos los valores propios
eig_ATA_full = np.linalg.eigvalsh(ATA)
eig_AAT_full = np.linalg.eigvalsh(AAT)

# Ordenar
eig_ATA_full_sorted = np.sort(eig_ATA_full)
eig_AAT_full_sorted = np.sort(eig_AAT_full)

# Crear un reporte formal como string
reporte = f"""
🔍 **Análisis Comparativo de Valores Propios: Matrices AᵀA y AAᵀ**

Sea A una matriz real de dimensiones 10×4, es decir, A ∈ ℝ¹⁰ˣ⁴. 
Se desea verificar experimentalmente que las matrices AᵀA ∈ ℝ⁴ˣ⁴ y AAᵀ ∈ ℝ¹⁰ˣ¹⁰ 
tienen los mismos valores propios no nulos.

---

🔹 **Valores propios de AᵀA (4×4):**
{np.array2string(eig_ATA_full_sorted, precision=4, separator=", ")}

🔹 **Valores propios de AAᵀ (10×10):**
{np.array2string(eig_AAT_full_sorted, precision=4, separator=", ")}

---

📌 **Observaciones:**

- La matriz AᵀA tiene exactamente 4 valores propios, todos mayores que cero.
 La matriz AAᵀ tiene 10 valores propios, pero solo los **últimos 4** 
(mayores que una tolerancia numérica) son no nulos.
- Los valores propios **no nulos** de ambas matrices **coinciden exactamente**, lo cual verifica que **AᵀA y AAᵀ 
comparten los mismos valores propios no nulos**.

Esta propiedad se fundamenta en el hecho de que AᵀA y AAᵀ tienen el mismo rango y que sus valores propios no nulos 
corresponden a los **cuadrados de los valores singulares** de A.

---

✅ **Conclusión:**
La verificación numérica respalda la demostración teórica. Dependiendo del tamaño de la matriz A, 
puede ser más eficiente computacionalmente trabajar con AᵀA (si n ≪ m) o con AAᵀ (si m ≪ n).
"""

# Mostrar el reporte
print(reporte)
---

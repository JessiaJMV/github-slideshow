import numpy as np

#   MÉTODO DE ESQUINA NOROESTE

:)
    oferta_copy = oferta.copy()
    demanda_copy = demanda.copy()
    i = 0
    j = 0
    fun_sol = []
    # PASO 1. En la celda seleccionada como esquina Noroeste se debe asignar
    #         la máxima cantidad de unidades posibles.
    while len(fun_sol) < len(oferta) + len(demanda) - 1:
        s = oferta_copy[i]
        d = demanda_copy[j]
        v = min(s, d)
        oferta_copy[i] -= v
        demanda_copy[j] -= v
        fun_sol.append(((i, j), v))
    # PASO 2. En este paso se procede a eliminar la fila o destino cuya oferta o demanda sea 0.
        if oferta_copy[i] == 0 and i < len(oferta) - 1:
            i += 1
        elif demanda_copy[j] == 0 and j < len(demanda) - 1:
            j += 1
    return fun_sol
    # PASO 3. Cuando queda un solo renglón o columna  se ha llegado al final el método.
costos = [
    [ 17, 20, 13, 12],
    [15, 21, 26, 25],
    [15, 14, 15, 17]
]
oferta = [70, 90, 115]
demanda = [50, 60, 70, 95]
fun_sol = Método_Esquina_Noroeste(oferta, demanda)
print("Los costos y las celdas correspondientes son:\n", fun_sol)
z = 0
for celda in fun_sol:
    z = celda[1] * costos[celda[0][0]][celda[0][1]] + z
print("Solución Optima:", z)

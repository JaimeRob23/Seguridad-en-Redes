What does asm2(0x6,0x21) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. [Source](https://challenge-files.picoctf.net/c_fickle_tempest/15570cdc609a55c2b6330372947822729c8cab528a59c71d992c034673f82418/test.S)

## Solucion
Código fuente:  

---

## Paso 1 — Identificar parámetros

En x86:

```
[ebp+0x8]  → primer argumento[ebp+0xc]  → segundo argumento
```

Llamada:

```
asm2(0x6,0x21)
```

Entonces:

```
a = 0x6b = 0x21
```

---

## Paso 2 — Analizar el loop

Código importante:

```
add DWORD PTR [ebp-0x4],0x1add DWORD PTR [ebp-0x8],0x9fcmp DWORD PTR [ebp-0x8],0x2d12jle ...
```

Traducción:

```
while(a <= 0x2d12){    b = b + 1;    a = a + 0x9f;}
```

---

## Paso 3 — Calcular iteraciones

Valores:

```
a = 0x6 = 6límite = 0x2d12 = 11538incremento = 0x9f = 159
```

Número de iteraciones:

⌊11538−6159⌋+1\left\lfloor \frac{11538 - 6}{159} \right\rfloor + 1⌊15911538−6​⌋+1 =73= 73=73

---

## Paso 4 — Actualizar b

```
b inicial = 0x21 = 33
```

Después de 73 iteraciones:

33+73=10633 + 73 = 10633+73=106 106=0x6a106 = 0x6a106=0x6a

### Respuesta final

```
0x6a
```

## Notas Adicionales
- Me apoye de la ia porque el lenguaje ensamblador es muy complicado
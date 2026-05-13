What does asm3(0xccf13937,0xbf0a24e4,0xf44d6917) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. [Source](https://challenge-files.picoctf.net/c_fickle_tempest/248b3201b28c4b333623337ef57b478c151690b62e8ce62acc07e19ec6cab02b/test.S)

## Solucion
Código fuente:  

---

## Paso 1 — Entender registros

La función usa:

```
AX → registro de 16 bitsAH → byte alto de AXAL → byte bajo de AX
```

Estructura:

```
AX = [ AH ][ AL ]
```

---

## Paso 2 — Argumentos en little-endian

### Primer argumento

```
0xccf13937
```

En memoria:

```
37 39 f1 cc
```

---

### Segundo argumento

```
0xbf0a24e4
```

En memoria:

```
e4 24 0a bf
```

---

### Tercer argumento

```
0xf44d6917
```

En memoria:

```
17 69 4d f4
```

---

# Paso 3 — Ejecutar instrucción por instrucción

---

## Instrucción 1

```
xor eax,eax
```

Resultado:

```
EAX = 0x00000000AX  = 0x0000
```

---

## Instrucción 2

```
mov ah,BYTE PTR [ebp+0x9]
```

`[ebp+0x9]` toma el segundo byte del primer argumento:

```
0x39
```

Entonces:

```
AH = 0x39AX = 0x3900
```

---

## Instrucción 3

```
shl ax,0x10
```

`AX` es de 16 bits.  
Desplazar 16 posiciones limpia el registro:

```
AX = 0x0000
```

---

## Instrucción 4

```
sub al,BYTE PTR [ebp+0xd]
```

`[ebp+0xd]` = segundo byte del segundo argumento:

```
0x24
```

Operación:

0x00−0x24=0xdc0x00 - 0x24 = 0xdc0x00−0x24=0xdc

Resultado:

```
AL = 0xdcAX = 0x00dc
```

---

## Instrucción 5

```
add ah,BYTE PTR [ebp+0xf]
```

`[ebp+0xf]` = cuarto byte del segundo argumento:

```
0xbf
```

Entonces:

```
AH = 0xbfAX = 0xbfdc
```

---

## Instrucción 6

```
xor ax, WORD PTR [ebp+0x12]
```

Importante:

```
WORD PTR = 2 bytes
```

Offsets del tercer argumento:

```
+0x10 → 17+0x11 → 69+0x12 → 4d+0x13 → f4
```

Entonces:

```
WORD PTR [ebp+0x12] = 0xf44d
```

Ahora:

0xbfdc⊕0xf44d=0x4b910xbfdc \oplus 0xf44d = 0x4b910xbfdc⊕0xf44d=0x4b91

---

## Resultado final

```
0x4b91
```

## Notas Adicionales
- Me apoye de la ia porque el lenguaje ensamblador es muy complicado
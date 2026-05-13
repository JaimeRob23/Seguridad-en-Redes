# head-dump

## Descripción

Welcome to the challenge! In this challenge, you will explore a web application and find an endpoint that exposes a file containing a hidden flag. The application is a simple blog website where you can read articles about various topics, including an article about API Documentation. Your goal is to explore the application and find the endpoint that generates files holding the server’s memory, where a secret flag is hidden. The website is running [picoCTF News](http://verbal-sleep.picoctf.net:62592/).
## Solución

```
#Inspeccionando la página entramos una extensión de descarga que fue desechada 
http://verbal-sleep.picoctf.net:62592/heapdump

#Usamos cat y grep para buscar la flag

┌──(flavio㉿kali)-[~/picoCTF/Examen1]
└─$ cat heapdump-1773719200405.heapsnapshot | grep -r "picoCTF{[^}]*}"
heapdump-1773719200405.heapsnapshot:picoCTF{Pat!3nt_15_Th3_K3y_a485f162}
```

picoCTF{Pat!3nt_15_Th3_K3y_a485f162}
## Notas adicionales

Descargamos un archivo "desechado" que no estaba en la página si no en el código fuente.
## Referencias

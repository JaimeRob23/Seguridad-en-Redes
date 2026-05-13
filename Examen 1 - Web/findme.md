# findme

## Descripción

Help us test the form by submiting the username as `test` and password as `test!` The website running [here](http://saturn.picoctf.net:54611/).
## Solución

```
#Decodificamos la flag

cGljb0NURntwcm94aWVzX2FsbF90aGVfd2F5XzAxZTc0OGRifQ==

picoCTF{proxies_all_the_way_01e748db}
```

picoCTF{proxies_all_the_way_01e748db}
## Notas adicionales

Al interceptar la solicitud a la página, encontramos 2 cadenas base64 en 2 páginas sin contenido en su url, las decodificamos y encontramos la flag
## Referencias

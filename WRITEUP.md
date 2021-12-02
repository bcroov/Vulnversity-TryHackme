#  Vuniversity How Exploit

### RECON

Usando Nmap

  nmap -sV 
  
  Vemos los puertos abiertos y los servicios correindo sobre esos puertos.

![image](https://user-images.githubusercontent.com/79328386/144467021-ed6d4345-454d-400b-a130-bbf0c3fd174a.png)


Detectamos un Servidor Web corrienod sobre el puerto :3333

![image](https://user-images.githubusercontent.com/79328386/144467468-7de0d978-0e70-4dd7-b1f4-346f65b0eb3d.png)

Realizamos una busqueda de directorios haciendo uso de Gobuster

![image](https://user-images.githubusercontent.com/79328386/144467922-e37579c9-ad52-4925-9881-ec11fcc4433e.png)



![image](https://user-images.githubusercontent.com/79328386/144468068-afcf957d-6537-4c0b-a159-b5ffce0f2f2d.png)


Encontramos los Siguinetes Directorios dentro del sitio :

![image](https://user-images.githubusercontent.com/79328386/144468203-3b5df6e7-a981-403c-8b41-8006f1a2be1e.png)

Encontramos un directorio que permite subir archivos.

![image](https://user-images.githubusercontent.com/79328386/144468453-e964883c-b2f1-4b2f-b1d1-65e492cb8700.png)

Probamos subir un archivo .php para conseguir una shell
![image](https://user-images.githubusercontent.com/79328386/144468613-550ccb62-89e3-4f51-ae67-e03a3520f7b5.png)


No es una extension no permitida

![image](https://user-images.githubusercontent.com/79328386/144468860-05bc444b-e2c2-4e65-a47a-ae2b8d98175d.png)

Utilizamos BurpSuite e intercepatamos el trafico para probar que extension puede ser valida.

![image](https://user-images.githubusercontent.com/79328386/144469267-515e4465-7bc4-4681-b70d-de433889be86.png)

En el modulo de intruder selecionamos la extension del archivo como parametro a testear

Testeamos con algunas extensiones

![image](https://user-images.githubusercontent.com/79328386/144469642-33c0d2e8-d959-4736-9afa-117c8f466842.png)

Con esto se pude ver que la extension phtml es una extension permitida

![image](https://user-images.githubusercontent.com/79328386/144469971-a1e35699-b96d-4c2f-962f-03c82094d91c.png)

Utilizamos eeste shell https://github.com/pentestmonkey/php-reverse-shell/blob/master/php-reverse-shell.php editamos la parte correspondiente a la ip del host atacante.




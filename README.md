# Vulnversity-TryHackme




Usando Nmap

  nmap -sV 
  
  Vemos los puertos abiertos y los servicios correindo sobre esos puertos.

![image](https://user-images.githubusercontent.com/79328386/144467021-ed6d4345-454d-400b-a130-bbf0c3fd174a.png)


Detectamos un Servidor Web corriendo sobre el puerto :3333

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

![image](https://user-images.githubusercontent.com/79328386/144670507-0f77538b-4d9a-4f3c-8798-102521b3023f.png)

Se sube el archivo de la shell.

![image](https://user-images.githubusercontent.com/79328386/144670681-a98213ab-9cba-4038-b532-283d1de0e99a.png)

Utilizamos ncat y dejamos escuchando el puerto 1234
![image](https://user-images.githubusercontent.com/79328386/144670793-cf1d9f17-0cbf-4c62-ba5d-b48a55a33352.png)

Ingresamos la url donde guardamos el archivo
![image](https://user-images.githubusercontent.com/79328386/144671040-f032fa21-7f74-401f-9959-2a646ae2412e.png)

Y tenemos accesso a la maquina victima 
![image](https://user-images.githubusercontent.com/79328386/144671110-fb4bfda0-addf-4506-9961-0325722d1d40.png)

Encontramos el primer usuario

![image](https://user-images.githubusercontent.com/79328386/144671234-1cdab297-f9f1-44db-a6d4-97c9853e2211.png)

Ahora buscaremos ser root abusando  de SUID 

 find / -user root -perm -4000 -exec ls -ldb {} \;
 
 
 ![image](https://user-images.githubusercontent.com/79328386/144673200-f93772ee-8729-4e01-a694-a6948822ae73.png)
 
 ![image](https://user-images.githubusercontent.com/79328386/144673557-14c83d9f-29f4-4214-bb24-551809a4401c.png)
 
 
  ![image](https://user-images.githubusercontent.com/79328386/144681078-65cf6412-a6b9-447a-8b0f-6428499cd726.png)

 Comprobamos los privilegios obtenidos
 ![image](https://user-images.githubusercontent.com/79328386/144681143-4cf9a6ab-7560-4ba3-bfd2-2aaf2b9e6b07.png)

Y podemos obtener la repsuesta siendo root

![image](https://user-images.githubusercontent.com/79328386/144681199-6171f94b-8b2b-4d4b-a391-0a0473f43106.png)

 





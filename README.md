# Arquitectura de Alta Disponibilidad con Auto Scaling y Load Balancer  
 
**Implementación de una infraestructura escalable y de alta disponibilidad en AWS.**

### Servicios Utilizados  
- **VPC** → Redes públicas y privadas  
- **EC2** → Instancias en un Auto Scaling Group  
- **ALB (Application Load Balancer)** → Balanceo de carga  
- **Auto Scaling Group** → Escalabilidad automática  
- **RDS** → Base de datos en subredes privadas  

 
## Imagen diagrama de la estructura

![image](https://github.com/user-attachments/assets/8a510e83-af4e-4182-af63-b2fad08d28fd)


## Arquitectura  

1. ## VPC
 
muestra los detalles principales de la VPC creada, como es el ID, el CIDR block, y que la VPC se encuentra en estado available.
 
![image](https://github.com/user-attachments/assets/51cef8de-a631-48d9-b475-ea1383ea4a3f)

### **Subredes**
 
lista de las subredes publicas y privadas creadas para la nuestra PVC, tambien se muestra informacion importante de las subredes credaas como lo es su nombre, la ID de la subred, el estado, la VPC que la contiene, su zona de sisponibilidad, etc..

![image](https://github.com/user-attachments/assets/85dd303a-61ff-4ce2-8127-a0856638dc4b)

### **Tablas de enrutamiento**

lista de las dos tablas de enrutamiento que se han utilizados para las subredes publicas y las subredes privadas.

![image](https://github.com/user-attachments/assets/8f9eadfe-98ca-48be-b389-6709b4227f9c)

### **Mapa de Recursos**

muestra la configuracion final de la estructura de la VPC, la conexion de las subredes publicas a la tabla de rutas rt-publicas, y esta al intenret gateway, de esta forma direccionando el trafico de entrada y salida de internet a la VPC, tambien la conexion de las subredes privadas a la tabla de enrutamiento rt-privadas con la cual solamente se tiene salida a internet y no acceso desde fuera por lo que esta tabla de rutas se conecta al NAT gateway creado la cual realizara la salida a internet a travez de la tabla de rutas publicas y el internet gateway.

![image](https://github.com/user-attachments/assets/d50d29b2-86c2-428a-9870-afb26a13add9)





# Aplication Load Balancer

configuramos el ALB para nuestro autoscaling el cual el trafico que reciba sera distribuido en los servidores que el autoscaling genere de esta manera evitamos que los servidores no se sibrecarguen y se trabaje de manera eficiente.

![image](https://github.com/user-attachments/assets/a5ce80c5-4d4c-4254-9329-e9523deba72c)

## grupo de destino

este grupo de destino se genero como definicion hacia donde deve elviar el balanceador de carga el trafico que reciba.

![image](https://github.com/user-attachments/assets/2be8c9ad-bbe7-4429-8be5-54b394d051a6)


# Auto Scaling

## template 

configuracion general del template usado en el cual definimos la ami a usar, el tipo de intancia, el par de claves, tambien agregamos un script en el cual descargamos alctualizaciones del servidor, intalamos Apache, lo iniicalizamos y creamos el archivo index.html.

![image](https://github.com/user-attachments/assets/a681266f-3c43-4ab9-bc02-310676e9cb31)

## grupo de Autoscaling

configuracion general del grupo de autoscaling en el cual se detallo los servidores deseados, minimos y maximos, tambien lo asociamos a nuestra vpc, nuestro autoscaling y listo para funcionar.

![image](https://github.com/user-attachments/assets/6f3067aa-5242-4443-9ad0-893c76f40965)









8. **RDS:** Creación de una base de datos en subredes privadas.  

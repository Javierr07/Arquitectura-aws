# Arquitectura de Alta Disponibilidad con Auto Scaling y Load Balancer  
 
**Implementación de una infraestructura escalable y de alta disponibilidad en AWS.**

### Servicios Utilizados  
- **VPC** → Redes públicas y privadas  
- **EC2** → Instancias en un Auto Scaling Group  
- **ALB (Application Load Balancer)** → Balanceo de carga  
- **Auto Scaling Group** → Escalabilidad automática  
- **RDS** → Base de datos en subredes privadas  

 
## Imagen diagrama de la estructura

![image](https://github.com/user-attachments/assets/7be85252-d194-4274-b9fd-f2fc9faaf885)


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


## demostracion de autoscaling con ALB

### instancias generadas 

![image](https://github.com/user-attachments/assets/5148e6a8-fdc2-4083-8ae8-3a003cbe2812)

### ingresamos a travez del dns del balanceador de carga 


![image](https://github.com/user-attachments/assets/5e956c6a-ca45-4a60-9de2-1753427c85ba)


![image](https://github.com/user-attachments/assets/c9506e7f-641f-420e-8bb3-89fc39f83e4d)


![image](https://github.com/user-attachments/assets/46ecfed5-c48a-4998-befe-5ac9d5584e20)

### tambien en grupos de destino podemos monitorear el estado de los servidores


![image](https://github.com/user-attachments/assets/cc51a7ce-1fe5-4bcd-b462-7952d4e58f64)


# RDS

informacion general de la instancia RDS donde podemos observar en que VPC se creo, la zona de disponibilidad en la que sencuentra y las subredes.

![image](https://github.com/user-attachments/assets/6ce7e630-2533-4080-bf19-13bd825ad3aa)

## grupos de seguridad de la base RDS

los grupos de seguridad de la base de datos nos muestran que solo tiene una regla de entrada por el puerto de postgreSQL, y una regla de salida por el mismo puerto asegurandonos que no tenga regla de entrada de internet  

![image](https://github.com/user-attachments/assets/af860c9e-0234-4e40-9848-63ac7ad8406f)

![image](https://github.com/user-attachments/assets/b025aa1d-9059-4905-b215-a209d7fdb5f4)



## conexion a al base de datos a travez de una Bastion host

usamos una instancia EC2 en nuestra subred publica para acceder a nuestra base de datos a travez de ella, esto genera mayor seguridad para el manejo de la base de datos.

![image](https://github.com/user-attachments/assets/38e6f19a-8157-46af-a89c-7831ab473ec4)


## listado de las bases de datos

muestra la lista de las bases de datos que contiene la instancia RDS.
![image](https://github.com/user-attachments/assets/aa4c1514-1321-4171-a833-ada3bb6a09db)


## conclusiones

Durante el desarollo de este proyecto se fueron generando retos los cuales me ayudaron a mejorar el uso de las herramientas que ofrece AWS los retos que mas se me complicaron son.
- las estructura general de la VPC, que componentes lleva y como estan conectados todos para cumplir su funcion.
- la integracion del ALB con el AutoScaling.
- la conexion a la base de datos ya que no se tenia acceso directamente desde internet.



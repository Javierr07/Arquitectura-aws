# Arquitectura de Alta Disponibilidad con Auto Scaling y Load Balancer  
 
**Implementación de una infraestructura escalable y de alta disponibilidad en AWS.**

### Servicios Utilizados  
- **VPC** → Redes públicas y privadas  
- **EC2** → Instancias en un Auto Scaling Group  
- **ALB (Application Load Balancer)** → Balanceo de carga  
- **Auto Scaling Group** → Escalabilidad automática  
- **RDS** → Base de datos en subredes privadas  

 
## Imagen diagrama de la estructura

![diagrama AWS alta disponibilidad](https://github.com/user-attachments/assets/d1f0af9f-5bcd-4ffd-b2ab-dcda3ed94b5d)


## Arquitectura  

1. **VPC**
 
muestra los detalles principales de la VPC creada, como es el ID, el CIDR block, y que la VPC se encuentra en estado available.
 
![image](https://github.com/user-attachments/assets/9d878c64-065b-41ea-b04d-8c51a5805113)

3. **Subredes**
 
muestra los detalles principales de la VPC creada, como es el ID, el CIDR block, y que la ![image](https://github.com/user-attachments/assets/00a590c9-00a9-467b-be87-57083ef1ddbb)
lista de las subredes publicas y privadas creadas para la nuestra PVC, tambien se muestra informacion importante de las subredes credaas como lo es su nombre, la ID de la subred, el estado, la VPC que la contiene, su zona de sisponibilidad, etc..

![image](https://github.com/user-attachments/assets/457a8e15-c241-4a02-a24f-2041b4cfb00e)

4. **Tablas de enrutamiento**

lista de las dos tablas de enrutamiento que se han utilizados para las subredes publicas y las subredes privadas.

![image](https://github.com/user-attachments/assets/6ed54abc-de65-453a-aafb-b7e11ff82dac)

5. **Mapa de Recursos**

muestra la configuracion final de la estructura de la VPC, la conexion de las subredes publicas a la tabla de rutas rt-publicas, y esta al intenret gateway, de esta forma direccionando el trafico de entrada y salida de internet a la VPC, tambien la conexion de las subredes privadas a la tabla de enrutamiento rt-privadas con la cual solamente se tiene salida a internet y no acceso desde fuera por lo que esta tabla de rutas se conecta al NAT gateway creado la cual realizara la salida a internet a travez de la tabla de rutas publicas y el internet gateway.

![image](https://github.com/user-attachments/assets/640bf240-043a-41bd-a60f-22d41ebd55cb)



 
6. **Auto Scaling:** Implementación de escalado basado en CPU.  
7. **Load Balancer:** Configuración de ALB con Target Groups.  
8. **RDS:** Creación de una base de datos en subredes privadas.  

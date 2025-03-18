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
muestra los detalles principales de la VPC creada.
![image](https://github.com/user-attachments/assets/9d878c64-065b-41ea-b04d-8c51a5805113)

2. **Subredes**
lista de las subredes publicas y privadas creadas para la nuestra PVC.
![image](https://github.com/user-attachments/assets/457a8e15-c241-4a02-a24f-2041b4cfb00e)

3. 
 
4. **Auto Scaling:** Implementación de escalado basado en CPU.  
5. **Load Balancer:** Configuración de ALB con Target Groups.  
6. **RDS:** Creación de una base de datos en subredes privadas.  

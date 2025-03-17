#Arquitectura de Alta Disponibilidad con Auto Scaling y Load Balancer  
 
**Implementación de una infraestructura escalable y de alta disponibilidad en AWS.**

### Servicios Utilizados  
- **VPC** → Redes públicas y privadas  
- **EC2** → Instancias en un Auto Scaling Group  
- **ALB (Application Load Balancer)** → Balanceo de carga  
- **Auto Scaling Group** → Escalabilidad automática  
- **RDS** → Base de datos en subredes privadas  

 
## Imagen diagrama de la estructura

![diagrama AWS alta disponibilidad](https://github.com/user-attachments/assets/d1f0af9f-5bcd-4ffd-b2ab-dcda3ed94b5d)


## 📜 Arquitectura  
![Arquitectura AWS](architecture.png)  

## ⚙️ Configuración  
1. **VPC y Subredes:** Configuración de redes públicas y privadas.  
2. **Auto Scaling:** Implementación de escalado basado en CPU.  
3. **Load Balancer:** Configuración de ALB con Target Groups.  
4. **RDS:** Creación de una base de datos en subredes privadas.  

# Actividad-TrabajoColaborativoGithub-DanielTrujillo
---
Vamos a crear una organizacion con nuestro nombre
![1](images/1.png)

Lo siguiente que hacemos despues de crear la organizacion es meter a nuestra *secretaria* en la organizacion.
![2](images/2.png)

Tambien se pueden creae **teams** para poder derivar el trabajo a los  team y poder **segmentar** el trabajo.
![3](images/3.png)

Aqui ya tenemos el equipo creado y ahora podemos asignar roles a nuestros compañeros de equipo
![4](images/4.png)

A nuestro secretario le vamos a poner **mantenedor de repositorio**: pueden gestionar el repositorio con bastante libertad crear y eliminar branches, gestionar issues y PRs, configuraciones no críticas, pero no pueden hacer acciones de administrador como cambiar **permisos** de colaboradores
![5](images/5.png)

Dentro de *Roles assignments* podemos ver los **roles** del team
![6](images/6.png)

En **Projects** podemos crear proyectos para *clasificar* las tareas que vamos a ir creando.
![7](images/7.png)

Ahora vamos a crear el **repositorio** en el que vamos a trabajar.
![8](images/8.png)

Mentemos la aplicacio de store-app y hacemos un comit para guardar los cambios
![9](images/9.png)

## Tarea 1

Creamos la rama develop y nos cambiamos a ella hacemos un push
![10](images/10.png)

Luego creamos la **rama de comentario inicio** y publicacamos la *rama*
![11](images/11.png)

Ahora vamos a hacer un **Pull request** primero ponemos los cambios en el stage
![12](images/12.png)

Y luego hacemos el **pull request**, esto lo que hace es crear una alerta para que el administrador mire los cambios que hicimos y si estan bien pues que se añadan a las ramas mas principales
![14](images/14.png)

En el apartado de pull request en github podemos comprobarlo.
![15](images/15.png)

Pero desde Visual es mas comodo para verlo asique lo aceptamos desde alli

![21](images/21.png)

Ahora vamos a hacer nosotros de *secretarios* vamos a crear la rama comentario final que es donde vamos a trabajar en este repositorio.
![16](images/16.png)

Vamos a añadir el **comentario** este al final del *pom.xml*
![17](images/17.png)

Y vamos a *solicitar* el pull request a nuestro **admin**
![18](images/18.png)

Y como estamos haciendo la actividad colaborativa a nosotros nos llegara el pull requeste de nuestro secretario.
![19](images/19.png)

Desde Visual Code podemos tambien *aceptar* y *ver* los pull request
![20](images/20.png)

Le damos a merged despues de revisar que todo esta en orden y desde graph podemos ver que se ha hecho bien el merge
![22](images/22.png)

## Tarea 2

Necesitamos crear una nueva funcionalidad en la aplicación que se encargue de los pagos por bizum en la aplicación.
A la derecha podemos ver que se la estamos dando a nuestro secretario
![23](images/23.png)

Desde visual podemos ver las issues creadas
![24](images/24.png)

Desde Git hub podemos ver que se crearon issues donde estamos asignados
![25](images/25.png)

Ahora hacemos la rama y creamos el archivo .java
![26](images/26.png)

Añadimos el siguiente texto dentro del archivo .java
```java
package es.storeapp.business.services;

import java.math.BigDecimal;
import java.time.LocalDateTime;
import java.util.UUID;

public class BizumPaymentService {

    public BizumPaymentResult processBizumPayment(String phoneNumber, BigDecimal amount, String concept) {
        if (phoneNumber == null || phoneNumber.isBlank()) {
            return new BizumPaymentResult(false, "Número de teléfono no válido", null, LocalDateTime.now());
        }

        if (amount == null || amount.compareTo(BigDecimal.ZERO) <= 0) {
            return new BizumPaymentResult(false, "Importe no válido", null, LocalDateTime.now());
        }

        String operationId = "BIZ-" + UUID.randomUUID().toString().substring(0, 8).toUpperCase();

        System.out.println("Iniciando pago por Bizum...");
        System.out.println("Teléfono: " + phoneNumber);
        System.out.println("Importe: " + amount + " EUR");
        System.out.println("Concepto: " + concept);
        System.out.println("Operación generada: " + operationId);

        return new BizumPaymentResult(
                true,
                "Pago Bizum simulado correctamente",
                operationId,
                LocalDateTime.now()
        );
    }

    public boolean validatePhoneNumber(String phoneNumber) {
        return phoneNumber != null && phoneNumber.matches("^[0-9]{8}$");
    }

    public static class BizumPaymentResult {
        private final boolean success;
        private final String message;
        private final String operationId;
        private final LocalDateTime timestamp;

        public BizumPaymentResult(boolean success, String message, String operationId, LocalDateTime timestamp) {
            this.success = success;
            this.message = message;
            this.operationId = operationId;
            this.timestamp = timestamp;
        }

        public boolean isSuccess() {
            return success;
        }

        public String getMessage() {
            return message;
        }

        public String getOperationId() {
            return operationId;
        }

        public LocalDateTime getTimestamp() {
            return timestamp;
        }

        @Override
        public String toString() {
            return "BizumPaymentResult{" +
                    "success=" + success +
                    ", message='" + message + '\'' +
                    ", operationId='" + operationId + '\'' +
                    ", timestamp=" + timestamp +
                    '}';
        }
    }
}

```

---

Podemos ver que en la issue podemos escribir comentarios entre los del team.
![27](images/27.png)

Vemos que nuestro secretario nos hizo el pull request le hacemos el *merge*
![28](images/28.png)
Una vez vemos que esta merged podemos  hacer un chekout
![29](images/29.png)

Y posteriomente podemos cerrar las issue
![30](images/30.png)

## Tarea 3

El enunciado de la terea es el siguiente: TU-SECRETARIO encuentra bug en develop, crea hotfix/fix-telephone-bug, PR directo a develop .

Rellenar Issue con título HotFix. bug in telephone number in bizum payment y descripción En el pago por bizum, cuando se introduce un teléfono válido lo da como incrorrecto.. Pulsamos botón Create.
![31](images/31.png)

Una vez creado podemos ver en *board* dentro de **projects** la tarea que acabamos de crear.
![32](images/32.png)

Aqui creamos la rama de *fix-telephone-bug* dentro de la rama *Hotfix* y cambiamos el contenido del archivo .java por otro que nos dio el porfesor ya corregido.
![33](images/33.png)

Ahora hacemos el *pull request* para la correccion de los errores.
![34](images/34.png)

Ahora aceptamos el pull request para que cambien las cosas de rama.
![35](images/35.png)

Y en **projects** si vamos al apartado de *board* podemos poner la tarea en ***DONE***
![36](images/36.png)

#### Autor

> **_Daniel Trujillo Martin_**
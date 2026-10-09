# Cajero automático — Spring Core e inyección de dependencias

**Autor:** Andrés Juárez Garduño

## Cómo correrlo

    ./correr.sh App final-app
    ./probar.sh final

## Las piezas

| Bean | Clase | Cómo lo declara Spring (`@Component` o `@Bean`) | Singleton o prototype |
|---|---|---|---|
| cajeroAutomatico | CajeroAutomatico | @Component | Singleton |
| sesionCajero | SesionCajero | @Component | prototype |

## Boleto de salida

1. ¿Qué es la inyección de dependencias? Explícalo con el cajero, en tus palabras.<br>
La inyección de dependencias es que una clase recibe las cosas que necesita, en vez de crearlas por su cuenta.<br>
En el cajero necesita un repositorio para encontrar las cuentas, el servicio antifraude, el notificador y un reloj. son recibidos por el constructor. <br>
2. En la MP-1, ¿quién decidía qué antifraude usaba el cajero? ¿Y desde la MP-2?<br>
En MP-1 el main era el que decidía que antifraude usar y en el MP-2 era el bean de antifraude que estaba en configuracionBanco. <br>
3. ¿Cuándo usarías `@Bean` en vez de `@Component`? Da el ejemplo de hoy.<br>
Component es para las clases que spring puede detectar y crear directamente, como la de CajeroAutomatico.<br>
Bean cuando se quiere decir como se crea un objeto específicamente, especialmente para clases que no son nuestras como la clase Clock que pertenece a Java.<br>
4. ¿Qué gana: `@Primary` o `@Qualifier`? ¿Por qué tiene sentido?<br>
@Qualifier gana porque @Primary es usado cuando no se pide por ejemplo un ServicioAntifraude pero no se dice cual usar (ejecución por defecto) y @Qualifire si dice específicamente cual ejecutar. <br>
5. En tu proyecto de Empleados de la Semana 3 nunca escribiste `@ComponentScan`. ¿Quién lo hace? (Pista: abre la
   anotación `@SpringBootApplication` con `Ctrl+clic` y busca las anotaciones que tiene arriba.)<br>
Lo hace el mismo springBootApplication, la anotación incluye @componentScan por eso al poner @spingBootApplication tenia el @ComponentScan.
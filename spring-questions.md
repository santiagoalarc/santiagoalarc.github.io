---
layout: page
title: Preguntas de Spring
permalink: /spring-questions/
---

## 1. ¿Que anotación se usa para proteger métodos específicos con seguridad basada en roles? 

- [ ] @RequestMapping
- [ ] @Autowire
- [ ] @RestController
- [x] @Secured

[Respuesta](https://www.baeldung.com/spring-security-method-security)


## 2. Seleccione dos componentes principales en Spring Security

- [ ] IdbcTemplate
- [x] UserDetailsService
- [ ] RestTemplate
- [x] AuthenticationManager

## 3. ¿Spring Boot usa el archivo application.properties para configuración?

- [ ] Falso
- [x] Verdadero

**Justificación**: application.properties es el archivo estándar que Spring Boot utiliza para la configuración externa de la aplicación.

## 4. ¿Qué anotación permite habilitar la configuración basada en propiedades en una clase de configuración?

- [ ] @ConfigurationProperties
- [ ] @Value
- [x] @Configuration
- [ ] @PropertySource

**Justificación**: La anotación @Configuration es la que marca una clase como una fuente de configuración para el contenedor de Spring. Es el pilar fundamental sobre el que se construyen otras anotaciones de configuración como @Value o @ConfigurationProperties.

## 5. Spring Boot permite configurar puertos del servidor en application.yml

- [ ] Falso
- [x] Verdadero

## 6. Spring Security permite la autenticación basada en JWT?

- [ ] Falso
- [x] Verdadero

## 7. Spring Boot puede integrar Spring Security para proteger endpoints REST

- [ ] Falso
- [x] Verdadero

## 8. Spring Boot siempre crea un único DispatcherServlet por aplicación

- [ ] Falso
- [x] Verdadero

**Explicación**: Por defecto, Spring Boot configura una única instancia de DispatcherServlet para manejar todas las solicitudes HTTP entrantes en una aplicación web tradicional o REST. Aunque técnicamente es posible configurar múltiples DispatcherServlets manualmente en casos muy avanzados, el comportamiento predeterminado y el diseño típico de una aplicación Spring Boot es con un único DispatcherServlet.

## 9.  ¿Cuál de los siguientes componentes se encarga de enrutar las solicitudes entrantes al método de controlador correspondiente?

- [ ] ApplicationRunner
- [ ] Filter
- [ ] RestTemplate
- [ ] DispatcherServlet

## 10. Spring Boot permite inyección de depedencias utilizando constructor injection

- [ ] Falso
- [ ] Verdadero

## 11. ¿Que anotaciones se usa para declarar una clase como un componente gestionado por el contenedor de Spring?

- [ ] @Autowire
- [ ] @Componente
- [ ] @Entity
- [ ] @RequestMapping

## 12. Spring Boot utiliza la anotación @Autowired para inyección de dependencias

- [ ] Falso
- [ ] Verdadero

## 13. Spring Boot soporta programación reactiva utilizando WebFlux

- [ ] Falso
- [ ] Verdadero

## 14. Seleccione dos tipos principales utilizados en progración reactiva en Spring Boot:

- [ ] Flux
- [ ] Future
- [ ] SchduleExecutorService
- [ ] Mono

## 15. Seleccione dos ubicaciones donde Spring Boot busca archivos de configuración por defecto

- [ ] /META-INF
- [ ] /resources/static
- [ ] /config subdirectory
- [ ] classpath root

## 16. El uso de @Async en Spring Boot permite ejecución asincrónica de métodos

- [ ] Falso
- [ ] Verdadero

## 17. Cual de las siguientes clases se usa comúnmente para manejar flujos reactivos en Spring Boot?

- [ ] Mono
- [ ] TimerTask
- [ ] CompletableFuture
- [ ] ExecutorService

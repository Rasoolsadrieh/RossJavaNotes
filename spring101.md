# Spring Framework

---

The Spring Framework is an application framework and inversion of control container for the Java platform. One of the core functions of the Spring Framework is _**dependency injection**_, which is accomplished through the use of a _**inversion of control**_ container, known as the `ApplicationContext`. The framework integrates with other specifications, namely:

-   Dependency Injection (JSR 330)
-   Servlet API (JSR 340)
-   Bean Validation (JSR 303)
-   JPA (JSR 338)

## Main Goals of Spring

---

The main goals of the Spring Framework include:

-   Lightweight development with Java POJOs
-   Dependency injection to promote loose coupling
-   Declarative programming with Aspect-Oriented Programming (AOP)
-   Minimize boilerplate Java code

## Terminology

---

Important Terminology

-   **Beans**

    -   instances which are managed by the Spring Framework

-   **Dependency Injection**

    -   the process of the Spring Framework actually injecting an instance of a dependency into a component (through auto-wiring or manual bean wiring)

-   **Autowiring**

    -   the process in which the Spring Framework identifies dependencies within a component, finds the corresponding component implementations and instantiates the dependency (or grabs an existing instance)

-   **Inversion of Control**

    -   the concept of the Spring Framework managing beans and performing dependency injection
    -   developers hand over control over aspects of the application to the Spring Framework

-   **IOC Container**

    -   a general term that is used to refer to anything that is implementing Inversion of Control

-   **Application Context**
    -   the primary IOC container of the Spring Framework alternative to the Bean Factory IOC container implementation
-   **Declarative Programming**
    -   The ability to write code that says (declares) what we want to do, rather than how to do it.
    -   Think of Java as being an imperative language, and SQL as a declarative language.
    -   [Imperative vs Declarative](https://tylermcginnis.com/imperative-vs-declarative-programming/)

## Dependency Injection

---

Dependency injection is a technique whereby one object supplies the dependencies of another object. A dependency is an object is used as part of the operation of another object. Dependencies can be either mandatory or optional. The Spring Framework's `ApplicationContext` is an inversion of control container, also known as the _bean container_. This container is responsible for managing the lifecycle of all beans contained within it and providing them to the application code when requested.

# Spring Framework Modules

---

![Spring Framework Modules and Sub-modules](https://s3.amazonaws.com/revature-note-assets/spring-overview.png "Spring Framework Modules and Sub-modules")

### Core Container

-   Factory for creating beans
-   Manages bean dependencies

#### Sub-modules:

-   Beans
-   Core
-   SpEL (Spring Expression Language)
-   Context

---

### Infrastructure

-   Allows developers to add functionality to objects declaratively
-   Logging, security, transactions, etc.

#### Sub-modules:

-   AOP
-   Aspects
-   Instrumentation (used for remote monitoring of applications)
-   Messaging

---

### Integration (Data Access Layer)

-   Allows developers to communicate with DBs (relational or non-relational)
-   Also allows functionality for communicating with a messaging queue

#### Sub-modules:

-   JDBC
-   ORM (Works very well with Hibernate)
-   Transactions (Makes heavy use of AOP)
-   OXM (Object XML Mapping)
-   JMS (Java Message Service)

---

### Web Layer (MVC)

-   Home of the Spring MVC framework

#### Sub-modules:

-   Servlet
-   WebSocket
-   Web
-   Portlet

---

### Test Layer

-   Supports Test-Driven-Development (TDD)
-   Allows for the mocking of objects and out-of-container testing

#### Sub-modules:

-   Unit
-   Integration
-   Mock

# Inversion of Control

---

Inversion of Control is a principle in software engineering by which the control of objects or portions of a program is transferred to a container or framework. IoC enables the framework to take control of the flow of a program and make calls to our custom code. The advantages of this architecture are:

-   decoupling the execution of a task from its implementation
-   making it easier to switch between different implementations
-   greater modularity of a program
-   greater ease in testing a program by isolating components

# Spring IOC Container

---

In the Spring framework, the IoC container is represented by the interface `ApplicationContext`. The Spring container is responsible for instantiating, configuring and assembling objects known as beans, as well as managing their lifecycle. There are 24 implementations of the `ApplicationContext` interface, important ones to be familiar with include:

-   `ClassPathXmlApplicationContext`
-   `AnnotationConfigApplicationContext`
-   `WebApplicationContext`

An ApplicationContext provides:

-   Bean factory methods, inherited from `ListableBeanFactory`.

    -   This avoids the need for applications to use singletons.

-   The ability to resolve messages, supporting internationalization. Inherited from the `MessageSource` interface.

-   The ability to load file resources in a generic fashion. Inherited from the ResourceLoader interface.

-   The ability to publish events. Implementations must provide a means of registering event listeners.

-   Inheritance from a parent context. Definitions in a descendant context will always take priority.
    -   This means, for example, that a single parent context can be used by an entire web application, while each servlet has its own child context that is independent of that of any other servlet.

# What is a bean factory?

---

A bean factory is just that, a implementation of the factory design pattern which is used to create Spring beans. The `BeanFactory` interface is implemented by objects that hold a number of bean definitions, each uniquely identified by a String name. Depending on the bean definition, the factory will return either an independent instance of a the object, or a single shared instance (a singleton scoped to the factory instance). The point of this approach is that the BeanFactory is a central registry of application components, and centralizes configuration of application components.

# Spring Bean Lifecycle

---

1. Instantiation

    - Bean constructor called

2. Populate properties

    - Setter methods of bean properties are called (dependencies must be created prior to bean creation)

3. `BeanNameAware.setBeanName()`

    - Set the name of the bean in the bean factory that created this bean.

4. `BeanClassLoaderAware.setBeanClassLoader()`

    - Callback that supplies the bean class loader to a bean instance.

5. `BeanFactoryAware.setBeanFactory()`
    - Callback that supplies the owning factory to a bean instance.
6. `EnvironmentAware.setEnvironment()`

    - Set the `Environment` that this component runs in.

7. `EmbeddedValueResolverAware.setEmbeddedValueResolver()`

    - Set the `StringValueResolver` to use for resolving embedded definition values.

8. `ResourceLoaderAware.setResourceLoader()` (only applicable when running in an application context)

    - Set the `ResourceLoader` that this object runs in.

9. `ApplicationEventPublisherAware.setApplicationEventPublisher()` (only applicable when running in an application context)

    - Set the `ApplicationEventPublisher` that this object runs in.

10. `MessageSourceAware.setMessageSource()` (only applicable when running in an application context)

    - Set the MessageSource that this object runs in.

11. `ApplicationContextAware.setApplicationContext()` (only applicable when running in an application context)

    - Set the ApplicationContext that this object runs in.

12. `ServletContextAware.setServletContext()` (only applicable when running in a web application context)

    - Set the ServletContext that this object runs in.

13. `postProcessBeforeInitialization` methods of `BeanPostProcessors`

    - Apply this BeanPostProcessor to the given new bean instance before any bean initialization callbacks.

14. `InitializingBean.afterPropertiesSet()`

    - Invoked by the containing BeanFactory after it has set all bean properties and satisfied BeanFactoryAware, ApplicationContextAware etc.

    - This method allows the bean instance to perform validation of its overall configuration and final initialization when all bean properties have been set.

15. a custom init-method definition

    - Custom bean initialization logic

16. `postProcessAfterInitialization` methods of `BeanPostProcessors`

    - Apply this BeanPostProcessor to the given new bean instance after any bean initialization callbacks

17. At this point, the bean is ready for use by the application.

18. At some point the container will begin to shut down. When this occurs the `DisposableBean.destroy()` method is invoked.

19. a custom destroy-method will be invoked to clean up any custom configuration.

![Spring Bean Lifecycle](https://s3.amazonaws.com/revature-note-assets/spring-bean-lifecycle.png "Spring Bean Lifecycle")

# `ApplicationContext` vs `BeanFactory`

---

As the `ApplicationContext` includes all functionality of the `BeanFactory`, it is generally recommended that it be used in preference to the `BeanFactory`, except in applications where memory consumption might be critical and a few extra kilobytes might make a difference. However, for most 'typical' enterprise applications and systems, the `ApplicationContext` is what you will want to use.

**`BeanFactory` features:**

-   bean instantiation/wiring

**`ApplicationContext` features:**

-   bean instantiation/wiring
-   `ApplicationEvent` publication
-   Convenient `MessageSource` access (for i18n - internationalization)
    -   internationalization is the process of designing a software application so that it can potentially be adapted to various languages and regions without engineering changes.

# Configuring Spring

---

### What does it mean to configure Spring?

Spring is a dependency injection framework, it accomplishes this through the use of an inversion of control container - specifically, the `ApplicationContext`. Configuring this container means that we will supply a registry containing all of our bean definitions. Bean definitions are simply a description of an object that we want Spring to manage for us, including the bean's dependencies.

When the container spins up, it will create singleton instances of all of the beans (unless some other scope is specified) based off of the bean definitions we provide to it. If Spring has any issues creating the beans, it will throw a `BeanCreationException` with a detailed explanation as to why it could not create the bean.

---

### Project Dependencies

-   `spring-core`

    -   Provides basic classes for exception handling and version detection, and other core helpers that are not specific to any part of the framework.
    -   [Documentation](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/core/package-summary.html)

-   `spring-beans`

    -   This package contains interfaces and classes for manipulating Java beans.
    -   [Documentation](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/beans/package-summary.html)

-   `spring-context`
    -   This package builds on the beans package to add support for message sources and for the Observer design pattern, and the ability for application objects to obtain resources using a consistent API.
    -   [Documentation](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/context/package-summary.html)

---

### XML Configuration

XML configuration is the earliest method used for configuring the Spring container. With this method of configuration, the bean registry is provided in XML format. The default canme for this configuration file is `beans.xml`. The root tag of the configuration file is the `<beans>` tag, which will contain the bean defintions - which are encapsulated by `<bean>` tags. The `ClassPathXmlApplicationContext` implementation of the `ApplicationContext` interface is used to load the bean registry XML file.

---

### Java Class Configuration

The central artifacts in Spring’s Java class configuration support are `@Configuration`-annotated classes and `@Bean`-annotated methods.

The `@Bean` annotation is used to indicate that a method instantiates, configures, and initializes a new object to be managed by the Spring container. You can use `@Bean`-annotated methods with any Spring `@Component`. However, they are most often used with `@Configuration` beans.

Annotating a class with `@Configuration` indicates that its primary purpose is as a source of bean definitions. Furthermore, `@Configuration` classes let inter-bean dependencies be defined by calling other `@Bean` methods in the same class.

In much the same way that Spring XML files are used as input when instantiating a `ClassPathXmlApplicationContext`, you can use `@Configuration` classes as input when instantiating an `AnnotationConfigApplicationContext`. This allows for completely XML-free usage of the Spring container.

---

### Component Scanning

Classes annotated with `@Component`, or any of the sterotype or derivative annotations, are able to be detected by Spring using a technique known as **component-scanning**. To enable component scanning to autodetect these classes and register the corresponding beans with XML-based configuration you need to include the `<context:component-scan>`, which uses the `base-package` attribute to specify the root package to be scanned.

To enable component scanning with Java class configuration, you can annotate your `@Configuration` class with `@ComponentScan`. Within this annotation you will specificy the root package that you will want Spring to scan for component classes. Those classes are registered as Spring bean definitions within the container. `AnnotationConfigApplicationContext` exposes the `.scan()` method in order to pass a String value representing the package to be scanned.

---

### Stereotype annotations

Annotations denoting the roles of types or methods in the overall architecture (at a conceptual, rather than implementation, level):

-   `@Component` (no specific layer)
-   `@Controller` (Servlet-layer)
-   `@Service` (Service-layer)
-   `@Repository` (DAO-layer)

# Spring Dependency Injection

---

## Dependency Injection (DI)

A process whereby objects define their dependencies (that is, the other objects they work with) only through constructor arguments, arguments to a factory method, or properties that are set on the object instance after it is constructed or returned from a factory method. The container then injects those dependencies when it creates the bean. This process is fundamentally the inverse (hence the name, Inversion of Control) of the bean itself controlling the instantiation or location of its dependencies by using direct construction of classes or a mechanism such as the Service Locator pattern.

---

### Constructor-Based DI

Constructor-based DI is accomplished by the container invoking a constructor with a number of arguments, each representing a dependency. Calling a static factory method with specific arguments to construct the bean is nearly equivalent, and this discussion treats arguments to a constructor and to a static factory method similarly. See `BaseballCoach.java` in the `spring-intro` and `spring-annotations` demo projects.

---

### Setter-Based DI

Setter-based DI is accomplished by the container calling setter methods on your beans after invoking a no-argument constructor or a no-argument static factory method to instantiate your bean. See `FootballCoach.java` in the `spring-intro` and `spring-annotations` demo projects.

---

### Constructor or Setter Injection?

Since you can mix constructor-based and setter-based DI, it is a good rule of thumb to use constructors for mandatory dependencies and setter methods or configuration methods for optional dependencies. Note that use of the @Required annotation on a setter method can be used to make the property be a required dependency. Use the DI style that makes the most sense for a particular class.

---

### Field-Level Injection

Using the `@Autowired` annotation, you can opt to include the annotation on the field declaration. Depending on your needs, you should primarily use constructor injection or some mix of constructor and setter injection. Field injection has many drawbacks and should be avoided. The only advantage of field injection is that it is more convenient to write, which does not outweigh all the cons.

Drawbacks of using Field-Level DI:

-   You cannot create immutable objects, as you can with constructor injection

-   Your classes have tight coupling with your DI container and cannot be used outside of it

-   Your classes cannot be instantiated (for example in unit tests) without reflection. You need the DI container to instantiate them, which makes your tests more like integration tests

-   Your real dependencies are hidden from the outside and are not reflected in your interface (either constructors or methods)

---

## References

[Spring Core Technologies Documentation](https://docs.spring.io/spring-framework/docs/current/spring-framework-reference/core.html)

[Field Dependency Injection Considered Harmful](https://www.vojtechruzicka.com/field-dependency-injection-considered-harmful)

# Spring Bean Scopes

## Explanation

When the `ApplicationContext` starts, it uses either an XML configuration file or component scanning to discover what Java classes (beans) it needs to manage for us. Once it discovers these beans, it will create bean defintions, which are just instructions for creating the bean. These definitions are stored in the bean container. The method in which Spring creates these beans is dependent upon the declared scope of the bean (using `scope` attribute on the `<bean>` tag in XML configuration, or using the `@Scope` annotation). If no specific scope is declared, then the default scope is singleton. The scopes which beans can be declared in are:

-   **singleton** _(default)_

    -   The Spring Container creates only one instance of the bean
    -   This bean is cached into memory
    -   All requests for the bean will return a shared reference to the same bean

-   **prototype**

    -   Creates a new bean instance for each container request

-   **request**

    -   Bean is scoped to an HTTP web request
    -   Only used in web applications

-   **session**

    -   Bean is scoped to an HTTP web session
    -   Only used in web applications

-   **application**

    -   Scopes a single bean definition to the lifecycle of a `ServletContext`
    -   Only used in web applications

-   **websocket**
    -   Scopes a single bean definition to the lifecycle of a `WebSocket`
    -   Only used in web applications

# Spring Bean Wiring

---

### Manual bean wiring

Manual bean wiring is the process in which a bean's dependencies are associated with the parent bean through explicit configuration. If leveraging constructor injection, this is done in XML configuration by including a `constructor-arg` tag with a bean id specified in the `ref` attribute. If setter injection is done, then the parent bean definition will include a `property` tag that points to the appropriate field in the class declaration, along with a `ref` attribute that uses the appropriate bean id.

---

### Bean Autowiring

If we let Spring scan our packages for us, using component scanning, we do not need to provide explicit bean definitions in an XML file, nor within some configuration class. Instead, Spring will scan the specified package for classes annotated with `@Component` (or another stereotype annotation) and create the bean definitions for them from the class declaration. If the annotated class has any dependencies that need to be managed by Spring, then the `@Autowired` annotation should be used where the dependency is being injected (either a constructor or a setter).

---

### Autowiring Modes

-   **no** _(default)_

    -   no autowiring. Bean references must be defined by ref elements

-   **byType**
    -   lets a property be autowired if exactly one bean of the property type exists in the container
    -   if more than one exists, a fatal exception is thrown, which indicates that you may not use byType autowiring for that bean
    -   if there are no matching beans, nothing happens (the property is not set)
-   **byName**

    -   autowiring by property name. Spring looks for a bean with the same name as the property that needs to be autowired

-   **constructor**
    -   analogous to byType but applies to constructor arguments
    -   if there is not exactly one bean of the constructor argument type in the container, a fatal error is raised.
-   **`@Qualifier`**
    -   Spring-managed classes can be annotated with `@Qualifier` which can be passed a String as an argument. This String value will be used as an identifier, and allows for the use of the qualifier annotation in conjuction with setter injection to locate the appropriate bean to wire in (Note that the use of `@Qualifier` with constructor injection is not supported).

# Spring MVC

## What is Spring MVC?

Spring Web MVC is a model-view-controller web framework built on the Servlet API. This framework is useful for creating flexible web applications to handle HTTP requests from clients. Packaging for Spring MVC projects will be `war` packaging.

## DispatcherServlet

The Spring MVC web framework is designed around the front controller pattern where a central servlet, the `DispatcherServlet`, provides a shared algorithm for request processing, while actual work is performed by configurable delegate components. This model is flexible and supports diverse workflows.

The DispatcherServlet, as any Servlet, needs to be declared and mapped according to the Servlet specification by using Java configuration or in `web.xml`. In turn, the DispatcherServlet uses Spring configuration to discover the delegate components it needs for request mapping, view resolution, exception handling, and more.

### Configuring the `DispatcherServlet` using the `web.xml`

    <web-app>

        <listener>
            <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
        </listener>

        <context-param>
            <param-name>contextConfigLocation</param-name>
            <param-value>/WEB-INF/app-context.xml</param-value>
        </context-param>

        <servlet>
            <servlet-name>DispatcherServlet</servlet-name>
            <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
            <init-param>
                <param-name>contextConfigLocation</param-name>
                <param-value></param-value>
            </init-param>
            <load-on-startup>1</load-on-startup>
        </servlet>

        <servlet-mapping>
            <servlet-name>DispatcherServlet</servlet-name>
            <url-pattern>/*</url-pattern>
        </servlet-mapping>

    </web-app>

### Spring MVC Configuration using `WebApplicationInitializer` (100% XML-free)

```
@EnableWebMvc
@ComponentScan
@Configuration
public class ApplicationConfig implements  WebMvcConfigurer, WebApplicationInitializer {

	@Override
	public void onStartup(ServletContext servletContext) throws ServletException {
        AnnotationConfigWebApplicationContext container = new AnnotationConfigWebApplicationContext();
        container.register(ApplicationConfig.class);

        servletContext.addListener(new ContextLoaderListener(container));

        ServletRegistration.Dynamic dispatcher = servletContext.addServlet("DispatcherServlet", new DispatcherServlet(container));
        dispatcher.setLoadOnStartup(1);
        dispatcher.addMapping("/");
	}

}
```

## Spring MVC Data Flow Diagram

![Spring MVC Data Web Flow](http://3.bp.blogspot.com/-gzDmsQOGbZ8/Uirsbl-UM2I/AAAAAAAAAlo/6VMFghVaMEA/s1600/SpringMVC.jpg)

### Spring MVC Special Bean Types

-   `HandlerMapping`

    -   Maps a request to a handler along with a list of interceptors for pre- and post-processing. The mapping is based on some criteria, the details of which vary by HandlerMapping implementation.

-   `HandlerAdapter`

    -   Helps the DispatcherServlet to invoke a handler mapped to a request, regardless of how the handler is actually invoked. For example, invoking an annotated controller requires resolving annotations. The main purpose of a HandlerAdapter is to shield the DispatcherServlet from such details.

-   `HandlerExceptionResolver`

    -   Strategizes to resolve exceptions, mapping them to handlers, to HTML error views, or other targets.

-   `ViewResolver`
    -   Resolve logical String-based view names returned from a handler to an actual View with which to render to the response.

## Spring MVC Annotations

-   `@Controller`

    -   A Spring stereotype annotation that is put at the class level for a presentation-layer class whose methods expose web endpoints.

-   `@RequestMapping`

    -   Used to expose a resource through a web endpoint
    -   Does not specify a specific HTTP verb by default
    -   `method` value can be provided to indicate a HTTP verb

-   `@GetMapping`

    -   Used to expose a resource through a web endpoint specific to HTTP GET requests

-   `@PostMapping`

    -   Used to expose a resource through a web endpoint specific to HTTP POST requests

-   `@PutMapping`

    -   Used to expose a resource through a web endpoint specific to HTTP PUT requests

-   `@DeleteMapping`

    -   Used to expose a resource through a web endpoint specific to HTTP DELETE requests

-   `@PathVariable`

    -   Used to grab a variable that is a part of the URI path

-   `@RequestParam`

    -   Used to grab a variable that is defined as a query parameter within the URI

-   `@RequestBody`

    -   Used to grab a object from the body of the web request

-   `@ResponseBody`

    -   Used to indicate that the returned value of the controller method will be placed within the body of the web response

-   `@ResponseStatus`

    -   Used to indicate the HTTP response status code for a controller method

-   `@ExceptionHandler`

    -   Used to send custom responses back to the client when a controller method throws a specified exception

-   `@RestController`
    -   Used when creating RESTful APIs using Spring MVC
    -   An aggregate annotation that implies `@Controller` on the class level and `@ResponseBody` on each controller method

# Spring ORM

---

The Spring Framework supports integration with the JPA and supports native Hibernate for resource management, DAO implementations, and transaction strategies. You can configure all of the supported features for ORM tools through Dependency Injection. They can participate in Spring’s resource and transaction management, and they comply with Spring’s generic transaction and DAO exception hierarchies.

#### Benefits Include:

-   Easier testing
-   Common data access exceptions
-   General resource management
-   Integrated transaction management

---

## Contextual Sessions

Hibernate needs some form "contextual sessions", where a given session is in effect throughout the scope of a given context. Since Spring v3 and Hibernate v3, Spring has supported contextual sessions, which are sessions managed directly by Hibernate and active throughout the scope of a transaction. Spring provides transaction management through its `PlatformTransactionManager` object.

Configuration for Spring-Hibernate contextual sessions is fairly straightforward and requires the use of three beans which need to be defined and wired to one another for the container:

1. Data Source (`DriverManagerDataSource`)

    - Provides connection details to allow Hibernate to connect to the DB

2. Session Factory (`LocalSessionFactoryBean`)

    - Leverages the Data Source bean as a dependency
    - Provides configuration to the `SessionFactory` object, such as:
        - base package to scan for entities
        - SQL dialect
        - Show/Format SQL in console
        - Hibernate Mapping to DDL (HBM2DDL)

3. Transaction Manager (`HibernateTransactionManager`)
    - Leverage the Session Factory bean as a dependency
    - Allows Spring to manage transaction isolation, propagation, and state

---

## XML-based Configuration for Spring-Hibernate Contextual Sessions

```
<!-- DataSource bean -->
	<bean id="myDataSource" class="org.apache.commons.dbcp2.BasicDataSource">
		<property name="driverClassName" value="oracle.jdbc.driver.OracleDriver" />
		<property name="url" value="jdbc:oracle:thin:@localhost:1521:ORCL" />
		<property name="username" value="admin" />
		<property name="password" value="p4ssw0rd" />
	</bean>

	<!-- SessionFactory bean -->
	<bean id="mySessionFactory" class="org.springframework.orm.hibernate5.LocalSessionFactoryBean">
		<property name="dataSource" ref="myDataSource" />
		<property name="packagesToScan" value="com.revature" />
		<property name="hibernateProperties">
			<props>
				<prop key="hibernate.dialect">org.hibernate.dialect.Oracle10gDialect</prop>
				<prop key="hibernate.show_sql">true</prop>
				<prop key="hibernate.format_sql">true</prop>
				<prop key="hibernate.hbm2ddl.auto">create</prop>
			</props>
		</property>
	</bean>

	<!-- TransactionManager bean -->
	<bean id="transactionManager" class="org.springframework.orm.hibernate5.HibernateTransactionManager">
		<property name="sessionFactory" ref="mySessionFactory" />
	</bean>
```

---

## Java Class Configuration for Spring-Hibernate Contextual Sessions

```
@Configuration
@EnableTransactionManagement
public class ApplicationConfig {

    @Bean
    public BasicDataSource dataSource() {
    	System.out.println("Creating BasicDataSource bean...");
        BasicDataSource dataSource = new BasicDataSource();

        ClassLoader classLoader = Thread.currentThread().getContextClassLoader();
        InputStream dbPropertiesStream = classLoader.getResourceAsStream("app.properties");
        Properties dbProperties = new Properties();

        try {
        	dbProperties.load(dbPropertiesStream);
        } catch (FileNotFoundException fnfe) {
        	fnfe.printStackTrace();
        } catch (IOException ioe) {
        	ioe.printStackTrace();
        }

        dataSource.setDriverClassName(dbProperties.getProperty("driver"));
        dataSource.setUrl(dbProperties.getProperty("url"));
        dataSource.setUsername(dbProperties.getProperty("username"));
        dataSource.setPassword(dbProperties.getProperty("password"));

        System.out.println("DataSource bean successfully created");
        return dataSource;
    }

    @Bean
    public LocalSessionFactoryBean sessionFactory() {
    	System.out.println("Creating SessionFactory bean...");
        LocalSessionFactoryBean sessionFactory = new LocalSessionFactoryBean();
        sessionFactory.setDataSource(dataSource());
        sessionFactory.setPackagesToScan("com.revature");
        sessionFactory.setHibernateProperties(hibernateProperties());
        System.out.println("SessionFactory bean successfully created");
        return sessionFactory;
    }

    @Bean
    public PlatformTransactionManager hibernateTransactionManager() {
    	System.out.println("Creating PlatformTransactionManager bean...");
        HibernateTransactionManager transactionManager = new HibernateTransactionManager();
        transactionManager.setSessionFactory(sessionFactory().getObject());
        System.out.println("PlatformTransactionManager bean successfully created");
        return transactionManager;
    }

	private final Properties hibernateProperties() {
		System.out.println("Loading Hibernate properties");
        Properties hibernateProperties = new Properties();
        hibernateProperties.setProperty("hibernate.dialect", "org.hibernate.dialect.Oracle10gDialect");
        hibernateProperties.setProperty("hibernate.show_sql", "true");
        hibernateProperties.setProperty("hibernate.format_sql", "true");
        hibernateProperties.setProperty("hibernate.hbm2ddl.auto", "create-drop");
        System.out.println("Hibernate properties loaded");
        return hibernateProperties;
    }
}
```

---

## Transaction Management

Comprehensive transaction support is among the most compelling reasons to use the Spring Framework. The Spring Framework provides a consistent abstraction for transaction management that delivers the following benefits:

-   A consistent programming model across different transaction APIs (JPA, JTA, Hibernate, etc.)
-   Support for declarative transaction management.
-   A simpler API for programmatic transaction management compared to JTA.
-   Excellent integration with Spring’s data access abstractions.

In order to enable `@Transactional` indicates that a persistence method takes place in a transactional context (i.e. on service-layer methods). This annotations allows for declarative transaction management, namely the isolation and propagation levels of the transaction.

---

## Transaction Propagation

Transaction propagation allows developers to specify the behavior of Spring's `PlatformTransactionManager` if a transactional method is executed when a transaction context already exists. A transaction context carries the state of the transaction. The transaction propagations supported in Spring are:

-   REQUIRED
-   REQUIRES_NEW
-   NESTED
-   MANDATORY
-   NEVER
-   NOT_SUPPORTED
-   SUPPORTS

#### REQUIRED

`@Transactional(propagation=Propagation.REQUIRED)`

-   same physical transaction will be used if one already exists, otherwise a new transaction will be opened

#### REQUIRES_NEW

`@Transactional(propagation=Propagation.REQUIRES_NEW)`

-   indicates a new physical transaction will be created for @Transactional method -- inner transaction can commit or rollback independently of the outer transaction

#### NESTED

`@Transactional(propagation=Propagation.NESTED)`

-   inner and outer use same physical transaction, but are separated by savepoints (JDBC drivers only)

#### MANDATORY

`@Transactional(propagation=Propagation.MANDATORY)`

-   existing transaction must already be opened or container will throw an error

#### NEVER

`@Transactional(propagation=Propagation.NEVER)`

-   container will throw an error if a session is open (oppostite of mandatory)

#### NOT_SUPPORTED

`@Transactional(propagation=Propagation.NOT_SUPPORTED)`

-   executes outside any existing transaction, current existing transaction will be paused

#### SUPPORTS

`@Transactional(propagation=Propagation.SUPPORTS)`

-   executes within the scope of existing transaction
-   otherwise, executes non-transactionally

# Spring AOP

The Spring Framework has its own Aspect-Oriented Programming framework, which is based on AspectJ. Aspect-oriented Programming (AOP) complements Object-oriented Programming (OOP) by providing another way of thinking about program structure. The key unit of modularity in OOP is the class, whereas in AOP the unit of modularity is the **aspect**. Aspects enable the modularization of concerns (such as transaction management, logging, security, etc.) that cut across multiple types and objects. (Such concerns are often termed **"cross-cutting"** concerns in AOP literature.)

---

## AOP Concepts

Let us begin by defining some central AOP concepts and terminology. These terms are not Spring-specific. Unfortunately, AOP terminology is not particularly intuitive. However, it would be even more confusing if Spring used its own terminology.

-   _**Aspect**_

    -   A modularization of a concern that cuts across multiple classes. Transaction management is a good example of a crosscutting concern in enterprise Java applications. In Spring AOP, aspects are implemented by using regular classes (the schema-based approach) or regular classes annotated with the `@Aspect` annotation (the AspectJ style).

-   _**Join point**_

    -   A point during the execution of a program, such as the execution of a method or the handling of an exception. In Spring AOP, a join point always represents a method execution.

-   _**Advice**_

    -   Action taken by an aspect at a particular join point. Different types of advice include "around", "before", and "after" advice. Many AOP frameworks, including Spring, model an advice as an interceptor and maintain a chain of interceptors around the join point.

-   _**Pointcut**_

    -   A predicate that matches join points. Advice is associated with a pointcut expression and runs at any join point matched by the pointcut (for example, the execution of a method with a certain name). The concept of join points as matched by pointcut expressions is central to AOP, and Spring uses the AspectJ pointcut expression language by default.

-   _**Introduction**_

    -   Declaring additional methods or fields on behalf of a type. Spring AOP lets you introduce new interfaces (and a corresponding implementation) to any advised object. For example, you could use an introduction to make a bean implement an IsModified interface, to simplify caching. (An introduction is known as an inter-type declaration in the AspectJ community.)

-   _**Target object**_

    -   An object being advised by one or more aspects. Also referred to as the "advised object". Since Spring AOP is implemented by using runtime proxies, this object is always a proxied object.

-   _**AOP proxy**_

    -   An object created by the AOP framework in order to implement the aspect contracts (advise method executions and so on). In the Spring Framework, an AOP proxy is a JDK dynamic proxy or a CGLIB proxy.

-   _**Weaving**_
    -   linking aspects with other application types or objects to create an advised object. This can be done at compile time (using the AspectJ compiler, for example), load time, or at runtime. Spring AOP, like other pure Java AOP frameworks, performs weaving at runtime.

---

## Spring AOP Advice Types

-   _**Before advice**_ (`@Before`)

    -   Advice that runs before a join point but that does not have the ability to prevent execution flow proceeding to the join point (unless it throws an exception).

-   _**After returning advice**_ (`@AfterReturning`)

    -   Advice to be run after a join point completes normally (for example, if a method returns without throwing an exception).

-   _**After throwing advice**_ (`@AfterThrowing`)

    -   Advice to be executed if a method exits by throwing an exception.

-   _**After advice**_ (`@After`)

    -   Advice to be executed regardless of the means by which a join point exits (normal or exceptional return).

-   _**Around advice**_ (`@Around`)
    -   Advice that surrounds a join point such as a method invocation. This is the most powerful kind of advice. Around advice can perform custom behavior before and after the method invocation. It is also responsible for choosing whether to proceed to the join point or to shortcut the advised method execution by returning its own return value or throwing an exception.

# Spring Boot

---

Spring Boot makes it easy to create stand-alone, production-grade Spring based Applications that you can "just run". It takes an opinionated view of the Spring platform and third-party libraries so you can get started with minimum configuration.

## Advantages of using Spring Boot

Create stand-alone Spring applications

-   Embedded Tomcat, Jetty or Undertow directly (no need to deploy WAR files)

-   Provide opinionated 'starter' dependencies to simplify your build configuration

-   Automatically configure Spring and 3rd party libraries whenever possible

-   Provide production-ready features such as metrics, health checks and externalized configuration that can be exposed using Actuator

-   Absolutely no code generation and no requirement for XML configuration

---

## Spring Boot Driver Class

    @SpringBootApplication
    public class MyApplication {

    	public static void main(String[] args) {
    		SpringApplication.run(MyApplication.class, args);
    	}

    }

-   `@SpringBootApplication`
    -   an aggregate annotation which implies the following annotations: `@Configuration`, `@EnableAutoConfiguration`, `@ComponentScan`

---

## Spring Boot Actuator

In essence, Actuator brings production-ready features to our application. Monitoring our app, gathering metrics, understanding traffic or the state of our database becomes trivial with this dependency. The main benefit of this library is that we can get production grade tools without having to actually implement these features ourselves.

Here are some of the most common endpoints the actuator provides:

-   `/health`

    -   Shows application health information (a simple status when accessed over an unauthenticated connection or full message details when authenticated); it's not sensitive by default

-   `/info`

    -   Displays arbitrary application info; not sensitive by default

-   `/metrics`

    -   Shows metrics information for the current application; it's also sensitive by default

-   `/trace`
    -   Displays trace information (by default the last few HTTP requests)

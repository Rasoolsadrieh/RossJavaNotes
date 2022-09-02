# Object Relational Mapping (ORM)

-   Most object-oriented applications _use a relational database to store and manage the application data_
-   The relational database _represents data in a table_
    -   _whereas the data in object-oriented applications encapsulated in an object_
-   We can access a class by using its objects.
-   However, to access the tabular data, we need to use a query language.
    -   Using tabular data in an object-oriented application requires a conversion between the two types of data.
-   As a result, it is not possible to store the objects directly in a relational database.
-   These differences between object-oriented and relational database paradigms are called **impedance mismatch**.

    -   [Impedance Mismatch](https://en.wikipedia.org/wiki/Object-relational_impedance_mismatch) can exist at the following points:

        -   **Granularity**
            -   refers to the mismatch in the number of classes that are mapped with a certain number of tables in the database.
        -   **Inheritance**
            -   Java classes in the application are commonly related to each other through an inheritance hierarchy. However, the tables within the database can't be represented through an inheritance hierarchy.
        -   **Identity**
            -   The relational database distinguishes an object instance on the basis of their primary key. However, an object model distinguishes an object on the basis of object identity and object equality.
        -   **Association**
            -   In the object model, two classes are linked by association. However, in relational databases, the linking of tables is achieved with the help of foreign keys.
        -   **Navigation**

            -   The ways of accessing objects in Java and in RDBMS are fundamentally different.

        -   To solve the impedance mismatch, we use an **ORM** tool that converts the **data between relational databases and object oriented programming languages**.

-   [ORM](https://en.wikipedia.org/wiki/Object-relational_mapping)
    -   Stands for **O**bject-**R**elational **M**apping
        -   uses objects to connect the Object-Oriented programming language and the database systems
        -   this facilitates the SQL to work along with the object-oriented programming concepts.

![](./images/orm.PNG)

### Benefits of ORM

-   ORM maps an object to the table.
-   We can hide the details of SQL queries from OO logic. This propagates the idea of data abstraction.
-   It provides methods for automatic versioning and timestamping.
-   It provides caching support for better performance.
-   Best suited for large projects
-   Injected transaction management
-   Configurable logging
-   Faster development of applications

-   There are lots of ORM tools available such as Hibernate, JPA, Active JPA, iBATIS, IBM Pure Query, etc.

## References

-   [What is Object/Relational Mapping?](https://hibernate.org/orm/what-is-an-orm/)

## JPA

-   [Java Persistence API](https://en.wikipedia.org/wiki/Java_Persistence_API)(JPA)
    -   is a standard API for accessing, persisting and managing data between Java objects/classes and a relational database.
    -   It is defined in the **javax.persistence** package.
    -   **Java Persistence Query Language** (JPQL),
        -   which is an object-oriented query language to perform database operations.
        -   **EntityManager** interface to create, read, and delete operations for instances of mapped entity classes.

## Hibernate

-   [Hibernate](<https://en.wikipedia.org/wiki/Hibernate_(framework)>) is an object-relational mapping tool for Java programming language.
-   It is an open-source persistent framework introduced by **Gavin King** in 2001.
-   It is a flexible and powerful ORM solution to map Java classes to database tables.
-   Hibernate is an **implementation of JPA**
    -   so it follows the common standards provided by the JPA.
    -   _Historically Hibernate_ provided its own extensions to JPA interfaces and syntax
        ?Now its started to return to a more JPA-friendly syntax.
    -   Because of this, you will find significant differences between older versions of Hibernate and newer versions, starting around Hibernate 5.2.
-   It is defined in the **org.hibernate** package.
    -   It uses **Hibernate Query Language** (HQL)
        -   Which is very similar to JPQL.
        -   Hibernate's **Session** interface is an extension to JPA's **EntityManager** interface,
            -   So it can create, read, and delete operations for instances of mapped entity classes.
-   Since we have used **JDBC** (Java Database Connectivity) for a long time,

    -   we know that JDBC provides a Java API for accessing relational databases from Java programs, to execute SQL statements.

-   **Drawbacks in the JDBC approach:**

    -   If we use JDBC in large applications, it results in _significant complexity_.
    -   If we need to change our database (for example, MySQL to Oracle)
        -   we _MIGHT_ have to rewrite many SQL queries to satisfy differences in SQL syntax between the two databases
    -   We need to convert database ResultSet objects to Java Objects manually, and vice-versa.
    -   If the schema changes, we need to change the DDL, the POJO classes, _and_ the conversions between the two
    -   The developer requires database-specific knowledge to write queries.
    -   The states of Java Objects are fetched and managed by developers.
    -   In other words, changes to data by the application need to be saved to the database manually
    -   Hibernate is used to overcome these drawbacks of JDBC.
    -   Some of the **advantages** of Hibernate are:

        -   **Transparent Persistence**
            -   ensures the automatic connection between the application’s objects with the database tables.
            -   It reduces the lines of connection code.
        -   **Database Agnostic**
            -   It can be used to connect with any database like Oracle, MySQL, Sybase, etc.
            -   Changing the SQL sent to a database is as simple as changing the _database dialect_ in the configuration file.
        -   **Provides Abstraction**
            -   Many common tasks are implemented for us internally,
                -   establishing a connection with the database
                -   writing a query to perform CRUD operations
        -   Support **dual-level Caching** mechanism.
            -   Through the caching concept, Hibernate retains the objects in the cache to reduce repeated hits to the database.
            -   This feature makes Hibernate highly scalable and optimizes the application’s performance.

## References

-   [Hibernate](https://docs.jboss.org/hibernate/orm/5.4/userguide/html_single/Hibernate_User_Guide.html)
-   [Difference Between Hibernate and JPA](https://www.educba.com/hibernate-vs-jpa/)

# Hibernate Configuration

-   This file contains the database mapping information that tells Hibernate
    -   how it should communicate with the database, and
    -   where the mapping for individual classes/tables can be found.
-   These configurations are provided either in an XML file (which must be named `hibernate.cfg.xml`) or properties file (`hibernate.properties`).

## hibernate.cfg.xml file

-   _hibernate.cfg.xml_
    -   contains the database and session related configuration.
    -   Database configuration includes
        -   the JDBC connection URL
        -   Database user credentials
        -   driver class
        -   hibernate dialect
    -   **Configuration Class**
        -   loads the xml file
        -   we have a `configure()` method,
            -   which loads the _hibernate.cfg.xml_ file
            -   This returns **SessionFactory** reference.
                -   The Session Factory reference used to get a **session** object.
-   **Example of hibernate.cfg.xml for a MySQL Database:**

    ```xml
    <?xml version='1.0' encoding='UTF-8'?>
    <!DOCTYPE hibernate-configuration PUBLIC
    "-//Hibernate/Hibernate Configuration DTD 3.0//EN"
    "http://hibernate.sourceforge.net/hibernate-configuration-3.0.dtd">

    <hibernate-configuration>
    	<session-factory>
    		<!-- SQL Dialect -->
    		<property name="hibernate.dialect">org.hibernate.dialect.SQLServerDialect</property>

    		<!-- Database Connection Settings -->
    		<property name="hibernate.connection.driver_class">com.mysql.jdbc.Driver</property>
    		<property name="hibernate.connection.url">jdbc:mysql://localhost:3306/test_db?useSSL=false</property>
    		<property name="hibernate.connection.username">root</property>
    		<property name="hibernate.connection.password">root</property>

    		<!-- Connection Pool Size (built-in) -->
    		<property name="hibernate.connection.pool.size">1</property>

    		<!-- show all generate SQL query -->
    		<property name="show_sql">true</property>

    		<!-- Drop the existing tables and create new one -->
    		<property name="hbm2ddl.auto">create</property>

    		<!-- Mention here all the model classes along with their package name -->
    		<mapping class="com.revature.hibernate.Student"/>
    	</session-factory>
    </hibernate-configuration>
    ```

-   Root element `<hibernate-configuration>`
    -   this has a `<session-factory>` element as its child.
        -   This element contains a database and mapping information.
-   The `<mapping>` element lists a _single_ java classe that is mapped to a table in the database.
    -   If a class is mapped using hibernate annotations, then the `<mapping>` element should use the `class` attribute
    -   if the class is mapped using an XML file, the `resource` attribute should be used instead. You should use one `<mapping>` element for each mapped class.
-   The Hibernate properties used in hibernate.cfg.xml file are listed below:

    -   **hibernate.dialect**
        -   specifies the type of database used in hibernate so that hibernate generates the appropriate type of SQL statements.
        -   The [org.hibernate.dialect](https://docs.jboss.org/hibernate/orm/5.4/javadocs/org/hibernate/dialect/package-summary.html) package contains the SQL dialect for the databases.
    -   **hibernate.connection.driver_class**
        -   used to register or load the JDBC driver class.
        -   The name should be fully qualified class name like `org.postgresql.Driver` for PostgreSQL , `com.mysql.jdbc.Driver` for MySQL, etc.
    -   **hibernate.connection.url**
        -   used to mention the JDBC URL to the database instance.
    -   **hibernate.connection.username**
        -   username used to connect to the database.
    -   **hibernate.connection.password**
        -   password for the username being used to connect to the database.
    -   **hibernate.connection.pool.size**
        -   used to limit the number of connections waiting in the Hibernate database connection pool.
    -   **show_sql**
        -   If this property value is _true_ then it enables the logging of all hibernate-generated SQL statements to the console.
    -   **format_sql**
        -   If this property value is _true_ then it formats the generated SQL statement to make it more readable.
    -   **use_sql_comments**
        -   If this property value is _true_ then it insert comments inside all generated SQL statements.
    -   **hibernate.hbm2ddl.auto**
        -   used to create, update or validate the database schema DDL when the SessionFactory Object created. The four possible values for this property are:
            -   **create**
                -   creates new database tables based on your class mappings.
                -   If a table already exists, then it will drop the existing table and create a new table.
            -   **update**
                -   Updates the existing database tables to match the class mappings.
                -   If a table doesn't exist, then it creates a new table.
            -   **validate**
                -   validates the existing tables against the provided mappings
                -   **doesn't make any changes** to the database.
                -   If the validation fails, the application will not work properly.
            -   **create-drop**
                -   as create, but _explicitly drops_ all existing tables when the SessionFactory is closed
                -   which of course loses all the data in those tables.

## hibernate.properties file

-   We can use a _hibernate.properties_ file to configure Hibernate instead.
-   Hibernate searches for the _hibernate.cfg.xml_ file OR the _hibernate.properties_ file at startup to find the configuration in our classpath.
-   If both are present
    -   **Gives priority** to a _hibernate.cfg.xml_ file
    -   over a _hibernate.properties_ file.
-   A _hibernate.properties_ file equivalent to the above _hibernate.cfg.xml_ file is given below:
    ```properties
    hibernate.dialect=org.hibernate.dialect.SQLServerDialect
    hibernate.connection.driver_class=com.mysql.jdbc.Driver
    hibernate.connection.url=jdbc:mysql://localhost:3306/test_db?useSSL=false
    hibernate.connection.username=root
    hibernate.connection.password=root
    show_sql=true
    hbm2ddl.auto=create
    ```
-   _hibernate.cfg.xml_ vs _hibernate.properties_
    -   an XML file we can directly map classes using the `<mapping>` element
    -   there is no way to configure this in a properties file
        -   Therefore, we map the classes using programmatic configuration.
    -   We can specify the mapped class using Configuration object:
        ```java
        Configuration configuration = new Configuration();
        configuration.configure().addAnnotatedClass(Student.class);
        ```

## References

-   [Hibernate Configuration](https://docs.jboss.org/hibernate/orm/5.4/userguide/html_single/Hibernate_User_Guide.html#configurations)

## XML vs Annotation configuration in Hibernate

-   Hibernate classically uses an XML mapping file for the transformation of data from POJO Classes to database tables, and vice versa.
-   An XML file gives the ability to change the configuration without rebuilding the whole project.
-   Especially in large projects
    -   this can leave you with hundreds of XML files floating around.
-   **Hibernate annotations**
    -   provide another way to define mappings directly in your POJO classes
    -   _without the use of an XML file_.

## Hibernate Annotations

-   used to provide metadata configuration inside the POJO class
-   we can understand the table structure and POJO class simultaneously.
-   based on the JPA 2 specification.

    -   All the JPA annotations are defined in the **javax.persistence** package.
    -   Some of the annotation used for table and column mappings are listed below:

        -   Consider the following **Students table** to store the Persistent objects.

            ```sql
            create table students (
               id INT NOT NULL auto_increment,
               first_name VARCHAR(20) default NULL,
               last_name  VARCHAR(20) default NULL,
               email  VARCHAR(30) default NULL,
               PRIMARY KEY (id)
            );
            ```

        -   Let us create a **Student** persistent class that is mapped to a student table.

            ```java
            package com.revature.hibernate;
            import javax.persistence.*;

            @Entity
            @Table(name = "students")
            public class Student {
                @Id
                @GeneratedValue(strategy = GenerationType.IDENTITY)
                @Column
                private int id;

                @Column(name = "first_name")
                private String firstName;

                @Column(name = "last_name")
                private String lastName;

                @Column(unique=true, nullable=false)
                private String email;

                public student(){
                }

                public Student(String firstName, String lastName, String email) {
                    this.firstName = firstName;
                    this.lastName = lastName;
                    this.email = email;
                }
                public int getId() {
                    return id;
                }
                public void setId(int id) {
                    this.id = id;
                }
                public String getFirstName() {
                    return firstName;
                }
                public void setFirstName(String firstName) {
                    this.firstName = firstName;
                }
                public String getLastName() {
                    return lastName;
                }
                public void setLastName(String lastName) {
                    this.lastName = lastName;
                }
                public String getEmail() {
                    return email;
                }
                public void setEmail(String email) {
                    this.email = email;
                }
                @Override
                public String toString() {
                    return "Student [id=" + id + ", firstName=" + firstName + ", lastName=" + lastName + ", email=" + email +       "]";
                }
            }
            ```

-   Hibernate annotations used in the above class are listed below:
    -   **`@Entity`**
        -   Used to mark a class as a Mapped class/Persistence class.
        -   This class **must** have a no-arg constructor with package visibility so that hibernate can create an instance of the Persistent class by the `newInstance()` method.
    -   **`@Table`**
        -   Used to specify the table details that used to persist the entity in the database.
        -   If the name of the database table differs from the name of the class, the name attribute should be used.
    -   **`@Id`**
        -   Used to mark the field as a primary key column.
        -   Annotating multiple fields with @Id will make them composite keys
    -   **`@GeneratedValue`**
        -   Used to instruct the database to generate a value for the field automatically, and to provide a strategy for doing so.
    -   **`@Column`**
        -   Maps the field to the table column. The `@Column` annotation has attributes listed below:
        -   **`name`**
            -   used to specify the name of the column.
            -   By default, it's assumed the column name and variable name match.
            -   This attribute is required if that is not the case.
        -   **`length`**
            -   used to specify the size of the String value
        -   **`nullable`**
            -   used to mark the column as NOT NULL when the schema is generated.
        -   **`unique`**
            -   used to mark the column as UNIQUE to contain unique values.

## References

-   [Hibernate Annotations](https://docs.jboss.org/hibernate/stable/annotations/reference/en/html_single/)
-   [Domain Model](https://docs.jboss.org/hibernate/orm/5.2/userguide/html_single/Hibernate_User_Guide.html#domain-model)

# Hibernate architecture

-   Hibernate is a collection of various constituent components that work together to communicate with the database to ensure data integrity and consistency.

-   The following diagram illustrates the main building blocks of **Hibernate architecture**:

![](./images/hib-arch.PNG)

-   To persist data in the database, the application communicates with the Hibernate layer that contains the following core classes and interfaces of the Hibernate API:

    -   Configuration Class
    -   SessionFactory Interface
    -   Session Interface
    -   Transaction Interface
    -   Query Interfaces

-   **Persistent objects:**

    -   These are instances of POJO classes
    -   each represent a row in a table in the database.
    -   These objects get translated to a row in the related table in the database by the Hibernate.
    -   They are configured in mapping files (`YourClass.hbm.xml`) or annotated with `@Entity` annotation.

-   The following figure shows the working of the hibernate classes and interfaces :

![](./images/workflow.PNG)

## References

-   [Architecture](https://docs.jboss.org/hibernate/orm/5.4/userguide/html_single/Hibernate_User_Guide.html#architecture)
-   [Further Reading on Hibernate Interfaces](https://www.geeksforgeeks.org/hibernate-architecture/)

# Hibernate Core Interfaces

-   The Hibernate core interfaces are used in just about every Hibernate application.
-   Using these interfaces, you can store and retrieve persistent objects and control transactions.

![hibernateinterfaces](./images/hibernate-interfaces.png)

## Configuration

-   [Configuration](https://docs.jboss.org/hibernate/orm/5.4/javadocs/org/hibernate/cfg/Configuration.html) is a class defined in `org.hibernate.cfg` package.

    -   It represents a **configuration** or **properties** file for Hibernate.
    -   The configuration object is created once during **application initialization**.
    -   It is the first object created by Hibernate.
    -   Using the Configuration object we can create a SessionFactory object, which is eventually used to create a Session object to perform the object persistence operations.

        ```java
        Configuration config = new Configuration();
        config.configure().addAnnotatedClass(Employee.class);
        ```

    -   `configure()` method
        -   loads mappings and properties from the hibernate.cfg.xml or hibernate.properties file which should be present in the classpath.
    -   `addAnnotatedClass()` method
        -   used to specify the entity class.
    -   `setProperty()` method
        -   to add properties like hibernate.connection.url, hibernate.connection.username, hibernate.connection.password, etc.
    -   If the config file is not valid then it will throw an exception.
    -   If it is valid then it creates a meta-data in memory and returns the meta-data to object to represent the config file.

## Session Factory

-   [SessionFactory](https://docs.jboss.org/hibernate/orm/5.4/javadocs/org/hibernate/SessionFactory.html)

    -   an interface defined in the `org.hibernate` package
    -   is used to create the **Session** Object.
    -   The SessionFactory object is used by all threads of an application.
    -   It is a **thread-safe** and **immutable** object mapped to a single database.
    -   It holds the **second-level cache** of data in hibernate.

        ```java
        StandardServiceRegistry registry = new StandardServiceRegistryBuilder().configure().build();
        SessionFactory sessionFactory = new MetadataSources( registry ).buildMetadata().buildSessionFactory();
        ```

## Session

-   **[Session](https://docs.jboss.org/hibernate/orm/5.4/javadocs/org/hibernate/Session.html)**
    -   an interface defined in the `org.hibernate` package.
    -   Session objects are created using the SessionFactory
    -   are used to perform CRUD operations.
-   **_Session Objects_**

    -   wrap the **JDBC connection** and serve as a factory of **Transaction**, **Query**, and **Criteria** objects.
    -   are not thread-safe.
    -   It is lightweight, and holds a mandatory **first-level cache** of persistence objects.

        ```java
        Session session = sessionFactory.openSession();
        ```

## Transaction

-   **[Transaction](https://docs.jboss.org/hibernate/orm/5.4/javadocs/org/hibernate/Transaction.html)**
    -   an interface defined in the `org.hibernate` package
    -   A transaction is associated with a **Session**
    -   usually instantiated by a call to `Session.beginTransaction()`
-   **Transaction object**

    -   used whenever we perform any operation and based upon that operation there is some change in database.
    -   Within one transaction you can do several operations and can **commit the transaction** once after completing all operations.
    -   We can also **rollback** all previous uncommitted operations.
    -   Transactions are not automatically committed when their session gets flushed.
    -   Transactions are handled by an underlying transaction manager and JDBC transaction or JTA transaction.

        ```java
        Transaction tx = session.beginTransaction();
        //set of operation performed on DB
        tx..commit();
        ```

## Query

-   [Query](https://docs.jboss.org/hibernate/orm/3.2/api/org/hibernate/Query.html)
    -   an interface defined in the `org.hibernate` package.
    -   A Query instance is obtained by calling `Session.createQuery()`.
-   **Query** can be used to expose extra functionality beyond that provided by `Session.iterate()` and `Session.find()`.

    -   You may select a particular page of a result set by calling `setMaxResults()` or `setFirstResult()`.
    -   You may use named query parameters.
    -   Queries are written in HQL or Native SQL of your database

        ```java
        Query query=session.createQuery();
        ```

## Criteria

-   [Criteria](https://docs.jboss.org/hibernate/orm/3.5/javadocs/org/hibernate/Criteria.html)
    -   an interface defined in the `org.hibernate` package.
    -   Criteria is a simplified API for retrieving entities by composing Criterion objects.
-   The **Session** is a factory for Criteria.
    -   Criterion instances are obtained via the factory methods.
    ```java
    Criteria criteria=session.createCriteria();
    ```

## References

-   [Architecture](https://docs.jboss.org/hibernate/orm/5.4/userguide/html_single/Hibernate_User_Guide.html#architecture)
-   [Hibernate Core Interfaces](https://www.decodejava.com/hibernate-architecture.htm)

## Caching in Hibernate

-   Hibernate performs caching to **optimize the performance** of an application.
-   It's used to reduce the number of database hits by storing data locally in a cache.

![caching](./images/cache.jpg)

### First-Level Cache / L1 cache

-   is the first place that Hibernate checks for cached data
-   L1 caching in hibernate is enabled by default
-   **We can't disable it.**
-   It is a mandatory cache through which all requests must pass.
-   This type of cache is associated with the **Session object**
    -   Each Session object caches data independently
    -   There is _no sharing of cached data across sessions_
    -   Cached data is deleted when the session closes.
    -   An L1 cache is internal to a Session object
    -   not accessible to any other session object in an application.
-   This type of cache is only useful for repeated queries in the same session.
-   When we query an entity first time
    -   it retrieves the data from the database and
    -   stores it in the L1 cache associated with the session.
    -   If we query again with the same session object, then it loads the data from the L1 cache.

### Second-Level Cache/ L2 Cache

-   L2 cache is responsible for caching objects and sharing data across sessions.
-   The L2 cache is associated with the **SessionFactory object**
-   shared among **all sessions** created using the same session factory.
-   If the requested query results are not in the first-level cache, then the second-level cache is checked.
-   Any technology that supports out-of-the-box integration with Hibernate can be plugged in to act as a second-level cache.
-   _disabled by default_

    -   but we can enable it through configuration.
    -   If L2 caching is enabled for an entity, the following workflow is used:
        -   If an instance:
            -   is already present in the L1 cache, then it is returned from there.
            -   Or is not found in the L1 cache, the L2 cache is searched, and if found the data is fetched and returned from there.
        -   If the data is not cached in the L2 cache, then the necessary data is loaded from the database and an instance is assembled and returned.
    -   We can enable the L2 cache by adding the following properties to the **hibernate configuration file**.

        ```xml
        <!-- Enable the second-level cache -->
        <property name="cache.use_second_level_cache">true</property>
        <property name="hibernate.cache.region.factory_class">org.hibernate.cache.ehcache.EhCacheRegionFactory</property>
        ```

-   To make an **entity** eligible for L2 caching,

    -   we annotate it `@Cache` annotation and
    -   specify a **cache concurrency strategy**.
    -   It's a best practice to annotate the entity class with `@Cacheable` annotation,

        -   **Although not required by Hibernate**. So the entity class looks like:

            ```java
            @Cacheable
            @Cache(usage = CacheConcurrencyStrategy.READ_ONLY)
            @Entity
            @Table(name="student")
            public class Student
            {
              //code goes here...
            }
            ```

-   A concurrency strategy it instructs hibernate on how to store objects in the cache and retrieve them, in an environment where multiple sessions might be trying to manipulate the same object simultaneously.
-   If we enable an L2 cache, then we decide the cache concurrency strategy for each persistent class and collection.
-   The cache concurrency strategies are:

    -   **READ_ONLY**
        -   Use this strategy only for entities where we never change any data and use data as a reference.
    -   **NONSTRICT_READ_WRITE**
        -   Doesn't guarantee the consistency between the cache and the database.
        -   Use this strategy only for entities where we change data rarely.
    -   **READ_WRITE**
        -   Use this strategy only for entities where we read and update data.
    -   **TRANSACTIONAL**
        -   Use this strategy to cache the full transactions made on the entity.

## References

-   [Caching](https://docs.jboss.org/hibernate/orm/5.4/userguide/html_single/Hibernate_User_Guide.html#caching)
-   [Further Tutorials on Caching](https://www.tutorialspoint.com/hibernate/hibernate_caching.htm)

## Service Locator Design Pattern

-   The [Service Locator](https://en.wikipedia.org/wiki/Service_locator_pattern) design pattern is used to encapsulate the processes involved in obtaining a service in a layer of abstraction.
-   It has a central registry known as the **Service Locator** which is responsible for returning instances of service objects based on requests from clients.

![](./images/service-locator.PNG)

### Design Components:

-   **Client**
    -   responsible for invoking services via the ServiceLocator.
-   **Service Locator**
    -   is a single point of contact for returning services to the client from the cache. It abstracts the lookup and/or creation of services.
-   **Initial Context**
    -   this creates, registers, and caches services. It is the starting point of the lookup and creation process.
-   **Service Factory**
    -   it provides lifecycle management for the service, which helps to create, register, lookup, or remove services from the cache.
-   **Service** -
    -   the implementation of the service, which will process the request.

## References

-   [Service Locator](https://www.oracle.com/technetwork/java/servicelocator-137181.html)

## Object States in Hibernate

-   An object of a persistent class (a class mapped to a relational database table) can be in one of three different states. These states are defined in relation to a **persistence context** (Session object).
-   Those 3 States are:

    -   **Transient State**
        -   -When an object is created using the `new` operator and not yet associated with a Hibernate Session, then the object state is transient.
        -   It doesn't represent a row in the database.
        -   Transient instances are garbage collected if the application does not hold a reference anymore.
    -   **Persistent State**

        -   The object state is persistent when it is associated with the hibernate session.
        -   The Persistent object represents a row in the database and has an identifier value.
        -   Transient instances can be made persistent by associating them with a Session.
        -   The `save()`, `persist()` and `saveOrUpdate()` methods are used to associate a transient object with a session and make them persistent.
        -   Hibernate detects the changes made to persistent objects and synchronizes the state with the database.
        -   Whenever we get the data from the database using `get()` or `load()` methods, the data will be in the persistent state.

    -   **Detached State**
        -   When a persistent object has its session closed, then it becomes detached.
        -   Any changes made to detached objects will not be saved automatically to the database.
        -   When a detached instance reattached with a new Session at a later point in time, it makes the object persistent again.
        -   The Session class' `close()`, `evict(Object)`, and `clear()` methods are used to move a persistent object to the detached state.
        -   The Session class' `update(Object)` and `merge(Object)` methods can used to reattach detached objects to a session.

**Object states:**

![](./images/objectstates.png)

## References

-   [Hibernate object states](https://docs.jboss.org/hibernate/core/3.3/reference/en/html/objectstate.html#objectstate-overview)
-   [Modifying persistent state](https://docs.jboss.org/hibernate/orm/6.0/userguide/html_single/Hibernate_User_Guide.html#pc-managed-state)

## HQL

-   **H**ibernate **Q**uery **L**anguage
    -   the object-oriented query language of the Hibernate Framework.
    -   HQL is very similar to SQL except that we query against **persistent objects** instead of tables and columns.
    -   Hibernate then **translates** the HQL queries to SQL queries and performs the action on the database.
        -   We can directly write SQL statements using Native SQL, but using HQL or JPQL is recommended.
        -   For Developer's, this separates the application layer from the persistence layer and abstracts away the actual database interaction, promoting flexibility and reusability.
    -   IS **case-sensitive for properties** like table and column names and not for keywords like SELECT, FROM, and was, etc.
-   **Advantages of HQL:**
    -   It supports OOP concepts like polymorphism, inheritance, and abstraction.
    -   It is database-independent and easy to learn.

### HQL Examples

-   HQL **Select** Query example to retrieve a student details whose id is 101.
    ```java
    TypedQuery<Student> query = session.createQuery("FROM Student WHERE id = '101' ", Student.class);
    List<Student> students = query.getResultList();
    ```
-   HQL **Update** Query example to update the name to "John" whose id is 105.
    ```java
    Query query = session.createQuery("UPDATE Student SET name = :stud_name WHERE id = :stud_id");
    query.setParameter("stud_name", "John");
    query.setParameter("stud_id", "105");
    int result = query.executeUpdate();
    ```
-   **Please note that HQL should only be used to batch-update records.**
    -   If you are updating a single record,
        -   it's _preferable to update the actual Java object's properties_
        -   then persist that object and its changes back to the database with session.update(object) or session.flush()
-   HQL **Delete** Query example to delete a student whose id is 108.
    ```java
    Query query = session.createQuery("DELETE Student WHERE id = :stud_id");
    query.setParameter("stud_id", "108");
    int result = query.executeUpdate();
    ```
-   **Similarly to updates, HQL should only be used to batch-delete records.**
    -   If you are deleting a single record,
        -   it's preferable to use session.delete(object).
-   HQL **Insert** statement cannot insert values directly in to a table.
    -   **It is only used to insert rows from another table. It supports only INSERT INTO … SELECT … .**
    ```java
    Query query = session.createQuery("INSERT INTO Student(id, name) SELECT s_id, s_name FROM NewStudent");
    int result = query.executeUpdate();
    ```

## References

-   [ HQL: The Hibernate Query Language](https://docs.jboss.org/hibernate/orm/5.4/userguide/html_single/Hibernate_User_Guide.html#hql)

## Criteria API

-   [Criteria API](https://docs.jboss.org/hibernate/orm/5.4/userguide/html_single/Hibernate_User_Guide.html#criteria)
    -   provides an object oriented approach for querying a database and getting results.
    -   In hibernate, we can pull the data from the database using session methods;
        -   **HQL**, **JPQL**, **Native SQL**, or the **Criteria API**.
-   **Hibernate Criteria**
    -   are a programmatic and typesafe way to fetch data from the relational database.
    -   criteria use explicit methods and return types to fetch data
    -   rather than requiring you to write queries as Strings that might contain typos
    -   can't be easilly parsed to determine what the resulting type of data will be.
-   The `javax.persistence.criteria.CriteriaQuery` interface
    -   provides many methods to specify criteria and the object obtained by calling
    -   the `createCriteria(Class<T>)`
        -   method of a `javax.persistence.criteria.CriteriaBuilder`.
-   To create a Criteria object

    -   we pass the persistent class or its entity name to the `createCriteria(Class<T>)` method
    -   which in turn returns the instances of the persistent class.

    ```java
    // creating the criteria object. sessionFactory must be built already.
    Session session = sessionFactory.getCurrentSession();

    CriteriaBuilder builder = session.getCriteriaBuilder();
    // The class passed into createQuery() indicates that the results of this CriteriaQuery will be Student objects
    CriteriaQuery<Student> query = builder.createQuery(Student.class);
    ```

-   The `CriteriaQuery` interface

    -   makes it easy to selectively fetch the data based on conditions in the select query.
    -   The JPA `CriteriaBuilder` class

        -   provides several methods that return **Expression** objects
        -   which can used as conditions.

        ```java
        // The root type indicates that the query is selecting from the tables mapped by the Student class. In this case    the type matches the CriteriaQuery type, but that is not always the case.
        Root<Student> root = query.from(Student.class);
        query.select(root)
        		.where(builder.equal( root.get("name"), "Adam") );
        		// .where(builder.equal( root.get(Student_.name), "Adam") ); is also acceptable, using the metamodel    syntax introduced in JPA 2.0
        List<Student> studentsNamedAdam = session.createQuery(query).getResultList();
        ```

-   The CriteriaQuery interface provides the **orderBy** method to sort the result set in either ascending or descending order, accordings to expressions generated by the CriteriaBuilder.

    ```java
    // result sorted by "name" in ascending order.
    query.orderBy(builder.asc( root.get("name") ));

    // result sorted by "name" in descending order.
    query.orderBy(builder.desc( root.get("name") ));
    ```

-   The Criteria API supports **pagination**.s

    ```java
    TypedQuery<Student> typedQuery = session.createQuery(query);
    //5th row is the first row in the result set
    typedQuery.setFirstResult(5);
    //Starting from the 5th record, and retrieve the next 10 records
    typedQuery.setMaxResults(10);

    List<Student> nextTenStudents = typedQuery.getResultList();
    ```

## References

-   [Criteria Queries](https://docs.jboss.org/hibernate/orm/5.4/userguide/html_single/Hibernate_User_Guide.html#criteria)

## Hibernate NativeSQL

-   Hibernate provides the option to execute native SQL queries through the use of the **SQLQuery** object.
-   The `Session.createNativeQuery(String query)` method
    -   used to create the [NativeQuery](https://docs.jboss.org/hibernate/orm/5.4/javadocs/org/hibernate/query/NativeQuery.html) object and execute it.

**Example:**

    ```java
    Query query = session.createNativeQuery("SELECT id, name, age FROM student");
    // Get All Students
    List<Object[]> rows = query.getResultList();

    for(Object[] row : rows){
    	Student stud = new Student();
    	stud.setId(Long.parseLong(row[0].toString()));
    	stud.setName(row[1].toString());
    	stud.setAge(Long.parseLong(row[2].toString()));
    	System.out.println(stud);
    }
    ```

-   The `getResultList()` method

    -   returns a List of Object arrays
    -   We need to explicitly parse to double, long etc.
    -   Hibernate will use **ResultSetMetadata** to deduce the actual order and types of the returned scalar values.

        -   To avoid the overhead of using `ResultSetMetadata`, or simply to be more explicit in what is returned, one can use `addScalar()`:

        ```java
        session.createNativeQuery("SELECT * FROM student")
         .addScalar("id", LongType.INSTANCE)
         .addScalar("name", StringType.INSTANCE)
         .addScalar("age", LongType.INSTANCE);
        ```

-   The `addEntity()` method used to get entity objects from a Native SQL query.

    ```java
    Query<Student> studentSQLQuery = session.createNativeQuery("SELECT id, name, age FROM student").addEntity(Student.  class);
    ```

-   Alternatively, this can be provided as an argument to the overloaded method:

    ```java
    Query<Student> studentSQLQuery = session.createNativeQuery("SELECT id, name, age FROM student", Student.class);
    ```

-   The `addJoin()` method used to fetch the data from associated table using tables join.

    ```java
    Query<Student> query = session.createNativeQuery("SELECT s.id, s.name, a.* FROM student s JOIN address a ON s.id =  a.stud_id")
    		.addEntity("e", Student.class)
    		.addJoin("a", "student.address");
    ```

## References

-   [Native SQL](https://docs.jboss.org/hibernate/orm/5.4/userguide/html_single/Hibernate_User_Guide.html#sql)

## Named Queries

-   In Hibernate, a [Named Query](https://docs.jboss.org/hibernate/jpa/2.1/api/javax/persistence/NamedQuery.html)

    -   a SQL expression with a predefined unchangeable query string.
    -   We can define a named query either in the **hibernate mapping file** or in an **entity class**.

-   **Annotations used in an entity class:**

    -   `@NamedQueries`
        -   used to define the multiple HQL expressions.
    -   `@NamedQuery`
        -   used to define the single HQL expression.
    -   `@NamedNativeQueries`
        -   used to define the multiple native SQL expressions.
    -   `@NamedNativeQuery`
        -   used to define the single native SQL expression.

-   `@NamedQuery` has two attributes:

    -   **name**
        -   used to specify a name by which a session object can locate the query.
    -   **query**
        -   used to specify the HQL statments.

-   **Example:**

    ```java
    @Entity
    @Table(name = "student")
    @NamedQueries({

    	@NamedQuery(name = "viewAllStudents", query = "FROM Student s")
    	@NamedQuery(name = "findStudentByID", query = "FROM Student s WHERE s.id = :id")
    	@NamedQuery(name = "findStudentByName", query = "FROM Student s WHERE s.name = :name")

    })
    public class Student {
        @Id
        @GeneratedValue(strategy = GenerationType.IDENTITY)
        @Column(name = "id")
        private int id;

        @Column(name = "first_name")
        private String firstName;

        @Column(name = "last_name")
        private String lastName;

        @Column(name = "email")
        private String email;

        public student(){
        }

        public Student(String firstName, String lastName, String email) {
            this.firstName = firstName;
            this.lastName = lastName;
            this.email = email;
        }
        //getters and setters
    }
    ```

-The `session.getNamedQuery(String query_name)` method used to run the specified named query defined at the entity class.

    ```java
    public class Application {

     public static void main(String[] args)
     {
      StandardServiceRegistry registry = new StandardServiceRegistryBuilder().configure().build();
      SessionFactory sessionFactory = new MetadataSources( registry ).buildMetadata().buildSessionFactory();
      Session session = sessionFactory.openSession();
      session.beginTransaction();

      Query query = session.getNamedQuery("findStudentByID").setParameter("id", 32);

      List students = query.getResultList();
      for(Student student : students)
      {
       System.out.println(student);
      }
      session.getTransaction().commit();
      session.close();
     }
    }
    ```

## References

-   [Named Queries](https://docs.jboss.org/hibernate/orm/5.4/userguide/html_single/Hibernate_User_Guide.html#jpql-api-named-query-example)


# Spring Framework

## Inversion of Control
- Container maintains your class dependencies
- Objects are injected at runtime or startup time


_If your class cannot operate without the dependency, it should be injected via constructors. If your class can treat the dependency as optional or can accept multiple but variable concrete instances of the dependency, then it can be injected via setter injection_

### Benefits of DI
- Reduces noise in your code
- Reduces object coupling
- Reduces defects from incorrect construction
- Focus on the API contract


## Application Context
- Acts as heart of Spring Applications
- Encapsulate the BeanFactory
- Provides metadata for bean creation
- Provides mechanism for creation of beans in the correct order


## Environment
- Populated by default by environment variables
- Supplement with property files

## Profiles
-Dspring.profiles.active=dev

@Bean
@Profile("dev")

TODO: Learn more about SPEL
## Spring Expression Language
@Value("#{new Boolean(environment['spring.profiles.active']!='dev')}")
private boolean isActive;

## Bean Scopes

### Singletons
- The default scope of every bean is singleton
- One instance per contect definition

### Prototype
- New instance every time it is referenced
- Difinition is stored in IoC, instances are not
- Very useful for transcient data or types that flex based on application state

### Session
- Applies to web environment only
- One instance of bean per user session
- Difinition is stored in IoC, instances are not

### Request
- Applies to web environments only
- One instance per requests
- Difinition is stored in IoC, instances are not


## Proxies
Everything is a proxy

## Component Scanning

@Component
- Indicates that a class should be loaded into the BeanFactory
- Component scanning scans a base package and loads configuration automatically for each bean it finds
- Dependency Injection is achieved through the @Autowired annotation
- @Qualifier is used when multiple implementations of an interface are needed
- Properties injected with @Value

@ComponentScan(basePackages = "com.myapp.mypackage")


## Lifecycle Methods

### Post Construction
Called after property setting

@PostConstruct
public void init(){
    // do some init work
}

### Pre Destroy
Executed when ApplicationContext closes

@PreDestroy
public void destroy(){
    // destroy work
}


## The Bean Lifecycle

### Initialization
### Use
### Destruction

## Aspect-Oriented Programming
Aspects are reusable blocks of code that are injected into your application at runtime. 

Common Applications of Aspects
- Logging
- Transaction management
- Caching
- Security

### Parts of a Spring Aspect
- Join Point
- Pintcut
- Advice
- Aspect



## Annotations
@PropertySource("classpath:application.properties")

@Value("Jorge")
private String name;

@Configuration
@Autowired

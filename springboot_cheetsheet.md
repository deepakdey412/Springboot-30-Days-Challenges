🚀 Spring Boot & Spring Core — Master Annotation Cheat Sheet
================================================================

  

🔵 1\. Spring Core Annotations
==================================

 @Component

Marks a class as a Spring-managed bean.

    @Component
    public class EmailService {}
    

 @Service

Specialized @Component for service layer.

    @Service
    public class OrderService {}
    

 @Repository

DAO layer + translates DB exceptions.

    @Repository
    public class UserRepository {}
    

 @Controller

Used in MVC for web pages.

    @Controller
    public class HomeController {}
    

 @RestController

\= @Controller + @ResponseBody

    @RestController
    public class ApiController {}
    

 @Configuration

Defines configuration classes.

    @Configuration
    public class AppConfig {}
    

 @Bean

Registers custom beans.

    @Bean
    public ModelMapper mapper() { return new ModelMapper(); }
    

  

🧩 2\. Dependency Injection Annotations
===========================================

 @Autowired

Injects bean automatically.

    @Autowired
    private UserService service;
    

 @Qualifier

When multiple beans of same type exist.

    @Autowired
    @Qualifier("emailService")
    private NotificationService notif;
    

 @Value

Inject properties.

    @Value("${app.name}")
    private String appName;
    

 @Lazy

Creates bean lazily.

    @Lazy
    @Autowired
    private PaymentService service;
    

  

📦 3\. Spring Boot Annotations
==================================

 @SpringBootApplication

Combines:

   @Configuration
   @EnableAutoConfiguration
   @ComponentScan

    @SpringBootApplication
    public class MyApp {}
    

 @EnableAutoConfiguration

Enables Spring Boot auto config.

 @ComponentScan

Tells Spring where to scan for beans.

  

🌐 4\. REST Controller & Web Annotations
============================================

 @GetMapping / @PostMapping / @PutMapping / @DeleteMapping / @PatchMapping

Shortcut HTTP mappings.

    @GetMapping("/users")
    public List<User> getUsers() {}
    

 @RequestMapping

Base route.

    @RequestMapping("/api")
    

 @PathVariable

Read dynamic values from URL.

    @GetMapping("/user/{id}")
    public User get(@PathVariable int id) {}
    

 @RequestParam

Query parameters.

    @GetMapping("/search")
    public String s(@RequestParam String q) {}
    

 @RequestBody

Read JSON body.

    @PostMapping("/add")
    public User add(@RequestBody User u) {}
    

 @ResponseStatus

Specify status code.

    @ResponseStatus(HttpStatus.CREATED)
    

 @CrossOrigin

Enable CORS.

    @CrossOrigin("")
    

  

🗄️ 5\. JPA & Hibernate Annotations
=======================================

 @Entity

Marks class as database table.

    @Entity
    public class User {}
    

 @Table(name = "users")

Specifies table name.

 @Id

Primary key.

 @GeneratedValue

Auto-increment strategy.

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    

 @Column

Customize column.

    @Column(nullable=false, unique=true)
    

 @OneToOne / @OneToMany / @ManyToOne / @ManyToMany

Relationship mappings.

    @OneToMany(mappedBy="user")
    private List<Order> orders;
    

 @JoinColumn

Foreign key.

  

🛡️ 6\. Spring Security Annotations
=======================================

 @EnableWebSecurity

Enables Spring Security.

 @Configuration + @Bean (Security Filter Chain)

    @Bean
    SecurityFilterChain security(HttpSecurity http) throws Exception {}
    

 @PreAuthorize

Method-level security.

    @PreAuthorize("hasRole('ADMIN')")
    

 @Secured

Another method-level role check.

    @Secured("ROLEADMIN")
    

 @AuthenticationPrincipal

Inject logged-in user.

    public String home(@AuthenticationPrincipal User user)
    

  

📦 7\. Validation Annotations (Jakarta Validation)
======================================================

 @NotNull / @NotBlank / @NotEmpty

Validation on fields.

 @Email

Valid email.

 @Size(min, max)

 @Min / @Max

 @Past / @Future

    @NotBlank
    private String name;
    
    @Email
    private String email;
    

 @Valid

Validate nested objects.

    public Response create(@Valid @RequestBody UserDto dto)
    

  

🔁 8\. Spring AOP Annotations
=================================

 @Aspect

Marks class as AOP aspect.

 @Before / @After / @Around

    @Before("execution( com.app.service..(..))")
    public void log() {}
    

  

🧪 9\. Testing Annotations
==============================

 @SpringBootTest

Loads full context.

 @WebMvcTest

Loads MVC layer only.

 @MockBean

Creates mock for dependency.

 @Test

JUnit test.

    @SpringBootTest
    class AppTest { }
    

  

🏗️ 10\. Lombok Annotations (Optional)
==========================================

 @Getter, @Setter

 @AllArgsConstructor, @NoArgsConstructor

 @Builder

 @Data

    @Data
    public class UserDTO {}
    

  

⚙️ 11\. Spring Boot Configuration Properties
================================================

 @ConfigurationProperties(prefix = "app")

    @ConfigurationProperties(prefix = "app")
    public class AppProps { private String name; }
    

 @EnableConfigurationProperties

Enable custom config binding.

  

🧵 12\. Scheduling & Async
==============================

 @EnableScheduling

Enable scheduler.

 @Scheduled

    @Scheduled(fixedRate = 5000)
    public void runTask() {}
    

 @Async

Run in parallel thread.

    @Async
    public void sendEmail() {}
    

  

🎯 13\. Transaction Management
==================================

 @Transactional

Wraps method in transaction.

    @Transactional
    public void saveOrder() {}

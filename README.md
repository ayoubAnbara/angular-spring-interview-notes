# angular-spring-Interview-Questions
## angular
Angular Interview Questions + notes in english/frensh
### Guards
goals==> proteger les routes.<br>
<br>
Une guard est **un service** qu'Angular exécutera au moment où l'utilisateur essaye de naviguer vers la route sélectionnée. Ce service implémente l'interface canActivate, et donc doit contenir une méthode du même nom qui prend les arguments ActivatedRouteSnapshot et RouterStateSnapshot (qui lui seront fournis par Angular au moment de l'exécution) et retourne une valeur booléenne, soit de manière synchrone (boolean), soit de manière asynchrone (sous forme de Promise ou d'Observable).
# Angular Doc:
Use route guards to prevent users from navigating to parts of an app without authorization. The following route guards are available in Angular:
- CanActivate
- CanActivateChild
- CanDeactivate
- Resolve
- CanLoad
### Lazy loading                             https://angular.io/guide/router#lazy-loading
You can configure your routes to lazy load modules, which means that Angular only loads modules as needed, rather than loading all modules when the app launches. Additionally, you can preload parts of your app in the background to improve the user experience.

unsubscribe observable ==> onDestroy

NgInx serveur front, il faut copier notre packaging dans cette serveur (www/html/).

### notes NgMorocco  https://www.youtube.com/watch?v=q-VUkCtp_Ck&ab_channel=NgMorocco

Lazy-loading:
```loadChildreen:() => import('./items.module').then(m => m.XModule)``` ==> import dynamique d'un module X

@Injectable(): Decorator that marks a class as available to be injected as a dependency. 
ex:
```
@Injectable   // Please Angular inject serviceB 
class ServiceA{
   constructor(private serviceB :ServiceB){}
}
```
@Component +- extends @injactable
``` 
@Injectable(
  {providedIn : 'root'}    // you can inject this class in all application
 }
 export class A{} 
```
we can use injection in pipe, directive

du moment on import un module A dans un autre module B, les dependences de module A seront disponible
dans module B.

parmi les avantages des services: le partage des states (data) entre les components, les services, ...
ex: AuthenticationService
# Directives:
tout directive commence par * (*ngIf, *ngFor...) s'appel une directive structural car il decide l'existence d'un element.

directive d'attribut: pour modifier l'apparence ou le comportement d'un élément.
ex: ngStyle, ngClass, 
# Observable vs Promise:
https://www.youtube.com/watch?v=O5poq2onluI&ab_channel=NgMorocco<br>
Promise is Eager but Observable s Lazy (​lazy a la demande).
Promise is asynchron 

Naming conventions for observables: $ suffix is used to indicate that the variable is an Observable.




# spring
swagger: specification qui permet de definir la documentation d'un api  https://swagger.io/

la partie de documentation est obligatoire.

- pattern DTO: inputs & outputs d'un controller doivent etre different.

si vous travaillez avec EJB/CDI le serveur d'application sera JEE comme JBoss, webflux,... 
## la difference entre serveur web, conteneur web et serveur d'application
- Serveur web :
est un serveur http comme apache son role: il recoit et envoye des requettes http, il fait pas des traitements, si une requette http demande un traitement il fait appel a un script php par ex d'executer.
- Conteneur Web : 
Serveur web + moteur qui va execute du code cote serveur  
ex: tomcat, apache+php
- Serveur d'application:
Conteneur Web + framwork qui fait l'inversion de controle             source:https://www.youtube.com/watch?v=xpMGCZw0UBA&t=2460s&ab_channel=mohamedYoussfi

# JPA:
https://www.youtube.com/watch?v=nf1vwRpHNW0&list=PLGTrAf5-F1YLNgq_0TXd9Xu245dJxqJMr&index=27&ab_channel=MissXing

## undirectional vs bidirectional
database only has bidirectional association, but OO has undirectional and bidirectional association.
in OO:
|               | undirectional | bidirectional  |
| ------------- |:-------------:| --------------:|
| OneToOne      |      ✔        |      ✔         |
| OneToMany     |      ✔        |      ✖         |
| ManyToOne     |      ✔        |      ✔         |
| ManyToMany    |      ✔        |      ✔         |
in DB:
bidirectional ==> FK , JoinTable 

## docker
### notes zakria:
un conteneur peut necessite une ou plusieurs images docker
une image docker est une templete pret a l'emploi avec des instructions du creation des conteneurs
image docker peut etre cree 
- a partir d'un docker file
- a partir d'une image existente, il va etre recuperer a partir d'un register docker (comme repo maven, npm),
le register par default s'appel docker hub

docker file, ce lui qui va permettre le build image docker

run image ===> l'instanciation d'un container  ==> on peut executer notre app

container est notre envirenement de devlopement qui va contenir notre app et ces dependances( java 8,...) qui sont decrites dans docker file


command:

$ docker build -t nameImage:version  path_docker_file       :lire docker file, executer step by step, cree l'image dans le repo local  (**)



$ docker run             : l'instanciation container


---
DockerFile doit etre dans la racine de notre project

pour tager une image au moment de build : docker tag ===>version   (voir **)


### notes mohamed youssfi:

Docker permet de creer des environnements ( appelees containers) de maniere a isoler des applications.

il permet de packager une application ainsi que les dependances necessaires dans un conteneur virtuel isole qui pourra etre execute sur n'importe qulle machine supportant docker

Dockerfile : decrit les dependances que notre applications a besions 

le dev cree un fichier Dockerfile conteneant les commandes que docker va executer pour construire une image docker de cette application.
 
 
 The Difference Between Ubuntu Desktop and Ubuntu Server:
 
 The main difference in Ubuntu Desktop and Ubuntu Server is the desktop environment. While Ubuntu Desktop includes a graphical user interface, Ubuntu Server does not.

This is because most servers run headless. But what does this mean? Well, they run without a traditional keyboard, mouse, and monitor setup to interact with the machine. Instead, servers are usually remotely managed using SSH. While SSH is built into Unix-based operating systems, it's pretty simple to use SSH on Windows as well.


nginx est un serveur web tres connu

$ sudo docker run -d  -p 8082:80  nginx       


-d      on arriere plan
-p     on mappe les ports   8082 le port externe , nginx quand il demerre, il utilse 80, si vous etes en dohrs du conteneur nous utilse 8082


to delete image : stop all containers that used this same image, delete theme, then delete image


EXEC Command

permet d executer une commande dans un container demarre 
ex:
demarrer un container MySQL

### Unit Test
# JUnit zakaria
- il faut que le nom du class test se termine par "Test"
- les noms des methodes de test doivent etre en minuscules - les methodes doivent annotees par @Test
- les methodes doivent etre public
- use coverage to know pourcentage la couverture du test
  for sts, install plugin https://www.eclemma.org/installation.html-Mockito
-------------------------------------
```
/* to test d'un bean spring  */
JUnit with Spring
@RunWith(SpringRunner.class)   // donne la main a spring pour run test
@SpringBootTest                // to use Autowired  
public class SubstractionServiceTest {
@Autowired
SubstractionService subService ;
@Test
public void when_call_substraction_with_unnormal_case() {
int res= subService.substraction(2, 4);
assertEquals(-1, res);
} 
```

Mockito: pour ne pas faire des vrais appels, on va les simulee.
Mockito est un framework de java
To use Mockito:
1-
```
<dependency>
    <groupId>org.mockito</groupId>
    <artifactId>mockito-core</artifactId>
    <scope>test</scope>
</dependency>
```
2- remplace @RunWith(SpringRunner.class) with @RunWith(MockitoJUnitRunner.class) from org.mockito.junit.MockitoJUnitRunner;

3- can't use @Autowired with Mockito,so for the services using by service target(test), je dois mocket les services with @Mock, et inject elle dans mon service target with @InjectMocks

4- on doit initialise de tout ce qui est mock
```
   @Before
	public void setup() {
		MockitoAnnotations.initMocks(this);
	}
```

5- on doit mocke les methodes des services annotee par @Mock inside test method, par ex:
```Mockito.when(sumService.sum(15, 2)).thenReturn(17);```

### Mock un controller
1- on utilise l'object MockMvc du package org.springframework.test.web.servlet.MockMvc

2-      ```
         MockMvc mockMvc;
	 HelloController controller;
        @Before
	public void setup() {
		MockitoAnnotations.initMocks(this);
		controller=new HelloController();
		mockMvc=MockMvcBuilders.standaloneSetup(controller).build();
	}
	
	@Test
	public void check_say_hello() throws Exception {
		mockMvc.perform(
				MockMvcRequestBuilders.get("/sayHello")
				.accept(MediaType.APPLICATION_JSON)
				.contentType(MediaType.APPLICATION_JSON)			
				).andExpect(status().is(200))
		                 .andExpect(jsonPath("$.message").value("hello"));
		
	//	assertTrue("verification say hello", controller.sayHello().equals("hello"));
	}
```

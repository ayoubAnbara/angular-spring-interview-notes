# Angular-Interview--Questions
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

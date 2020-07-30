# Angular-Interview--Questions
Angular Interview Questions + notes in english/frensh
### Guards
goals==> proteger les routes.<br>
There are five different types of guards and each of them is called in a particular sequence. The router’s behavior is modified differently depending on which guard is used. The guards are:
- CanActivate
- CanActivateChild
- CanDeactivate
- CanLoad
- Resolve 
                                                                 source: https://medium.com/@ryanchenkie_40935/angular-authentication-using-route-guards-bf7a4ca13ae3
<br>
Une guard est **un service** qu'Angular exécutera au moment où l'utilisateur essaye de naviguer vers la route sélectionnée. Ce service implémente l'interface canActivate, et donc doit contenir une méthode du même nom qui prend les arguments ActivatedRouteSnapshot et RouterStateSnapshot (qui lui seront fournis par Angular au moment de l'exécution) et retourne une valeur booléenne, soit de manière synchrone (boolean), soit de manière asynchrone (sous forme de Promise ou d'Observable)

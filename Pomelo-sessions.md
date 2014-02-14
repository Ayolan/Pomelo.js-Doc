### Utilisation des sessions avec Pomelo.js

Les sessions sont en général utilisé du coté Handler. Elles permettent une multitudes de choses
et permettent de stiquer les informations des utilisateurs courant.

###Définir des informations d'une session
Pomelo.js permet d'ajouter, modifier ou définir des informations d'une session. Voici
quelques exemples :

**Définir une valeur de session**

```javascript
session.set('playerName', 'Seby');
```

**Récupéré une valeur de session**

```javascript
var myPlayerName = session.get('playerId'); // => Seby
```
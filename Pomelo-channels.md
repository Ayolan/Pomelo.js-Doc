### Utilisation des channels service avec Pomelo.js

Coté server, si les choses sont bien faites. Au niveau de vos sockets (Handler et Remote
vous devez normalement binder les channels de cette manière :

```javascript
var ChatRemote = function(app) {
    this.app = app;
    this.channelService = app.get('channelService');
};
```

Le service de channel étant binder vous allez pouvoir les utiliser dans vos fonctions. Voici la liste des possibilités
des channels, les effets et comment s'en servir.


#### Récupéré un channel

```javascript
    /**
     * Vous permet de récupéré un channel précis. Si celui-ci n'est pas crée
     * le flag va permettre de le crée automatiquement.
     */
    // var channel = this.channelService.getChannel("My Super Chan", true);
    var channel = this.channelService.getChannel(name, flag);
```

#### Ajouter un utilisateur au channel

```javascript
    /**
     * On vérifie que le channel existe bien et on ajoute l'utilisateur au channel
     * UID => C'est l'ID unique qui permet de différencier un utilisateur d'un autre
     * SID => C'est un ID utiliser par le serveur
     */
    if( !! channel)
    {
        channel.add(uid, sid);
    }
```

#### Récupéré tout les utilisateurs d'un channel

```javascript
    /**
     * On vérifie que le channel existe bien et on ajoute l'utilisateur au channel
     * On récupère la liste des utilisateurs qui sera envoyer sous forme d'Array
     */
    if( !! channel)
    {
        users = channe.getMembers();
    }

    /**
     * On parcourt la liste des utilisateurs récupéré et on split (car l'UID contient aussi le channel)
     */
    for(var i = 0; i < users.length; i++)
    {
        users[i] = users[i].split('*')[0];
    }
```

#### Récupéré un utilisateur précis du channel

```javascript
    /**
     * Récupère un utilisateur d'après son UID
     */
    var userInfo = channel.getMember(uid)
```

#### Quitter un channel

```javascript
    /**
     * Création du channel...
     */
     var channel = this.channelService.getChannel(name, flag);

     // ... ... ...

    /**
     * On demande au channel de retiré son utilisateur
     */
    channel.leave(uid, sid);
```

#### Crée un channel

```javascript
    /**
     * Vous permet de crée un Channel. Une fois celui-ci crée, l'objet est retourné dans newChannel
     */
    var newChannel = this.channelService.createChannel("My New Channel");
```

#### Détruire un channel

```javascript
    /**
     * Vous permet de détruire un Channel en utilisant son nom comme critère.
     */
    this.channelService.destroyChannel("My New Channel");
```

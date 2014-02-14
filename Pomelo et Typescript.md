### Pomelo.js et Typescript

Attention, nous avons été victime d'un bug plutôt étrange. Le bug est en relation avec les
références de typescript.

```javascript
///<reference path='path/to/my.d.ts'/>
```

Veuillez faire attention à l'utilisation de Typescript coté serveur et à ce genre de "bug",
si il vous arrive d'avoir un bug plutôt incompréhensible, pensez à vérifier vos références.
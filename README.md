# Monster Slayer

## Critères qualité

- Vue JS only => Zéro manipulation native DOM !!!
- Framework CSS : Bulma
- Les boutons de combat ne sont pas accessibles 
- Un bouton « New Game » est accessible 
- New Game donne accès aux boutons de combat 
- Les barres de vies sont mise à jour en temps réel 
- A la fin de chaque partie demander une confirmation de nouvelle partie
- 2 attaques distinctes : 
- « Normale » : aléatoire entre 3 et 10 points de dégâts 
- « Spéciale » : aléatoire entre 10 et 20 points de dégâts 
- 1 bouton « Heal » (soigne le joueur de 10 points) 
- Chaque soin entraine une attaque du monster 
- Chaque attaque entraine une attaque du monster :  
- aléatoire entre 5 et 12 points de dégâts 
- 1 bouton « Give Up » pour abandonner (reset)

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

# Mettre en place un Webpack pour Phaser3

## Dans l'invite de commande
```bash
npm init -y

npm install phaser webpack webpack-cli webpack-dev-server babel-loader @babel/core @babel/preset-env
```

## Organisation des fichers et dossiers dans le projet

```bash
/dist
	/static
	bundle.js
	index.html

/scenes
	main.js

/src
	index.js

webpack.config.js
package.json
```

## Dans le fichier index.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>

    <script src="./bundle.js"></script>
    
</body>
</html>
```

## Dans le fichier main.js

```jsx
import 'phaser';

export default class Main extends Phaser.Scene {
    constructor() {
        super("main");
    }

    preload() {

    }

    create() {
        this.add.rectangle(0, 0, 100, 100, 0xFF0000, 1);
    }

    update() {

    }
}
```

## Dans le fichier index.js

```jsx
import 'phaser';
import Main from '../scenes/main';

const config = {
    type: Phaser.AUTO,
    width: 1900,
    height: 1080,
    scene: [Main],
};

new Phaser.Game(config);
```

## Dans le fichier webpack.config.js

```jsx
const path = require('path');

module.exports = {
  mode: 'development',
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'bundle.js',
  },
  devServer: {
    static: {
      directory: path.resolve(__dirname, 'dist'),
    },
    open: true,
  },
};
```

## Dans le fichier package.json dans la clef 'scripts'

```json
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "build": "webpack",
    "start": "webpack-dev-server --open"
  },
```

## Lancer le projet (Dévelopement)

```json
npm start
```

**127.0.0.1:8080**

## Construire le projet (Production) 

```json
npm run build
```

1**27.0.0.1/<project name>/dist**
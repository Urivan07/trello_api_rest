# Api Rest con Trello para mission NodeJs de Launch X

Generacion de carta en tablero por medio de petición api utilizando Trello

## Dependencias utilizadas
### Dotenv
Dependencia para cargar variables en base a un entorno configurado en archivo `.env`, utilizado en el proyecto para configuracion de KEY y TOKEN requerida para las peticiones con Trello.
* Instalacion:
> npm install dotenv --save
* Configuracion archivo `.env`:
```javascript
KEY="TrelloKeyHere"
TOKEN="Trellotokenhere"
```
* Integracion y vlidacion de variables KEY y TOKEN:
```javascript
require('dotenv').config()

if(!process.env.TOKEN && !process.env.KEY){
  throw new Error('No hay configuración con Api Key y con Token')
}
```

# Trello
Cliente asincrono utilizado para realizar peticiones api rest
* Instalacion:
> npm install trello --save
* Integracion y peticion para agregar una card a board existente de trello.
```javascript
let Trello = require("trello");
let trello = new Trello(process.env.KEY, process.env.TOKEN);

let cardTitle = `Card Nueva ${new Date()}`

trello.addCard(cardTitle, "LaunchX Card Description", "627d9e0255421c1d9bba620e",
	function (error, trelloCard) {
		if (error) {
			console.log('Could not add card:', error);
		}
		else {
			console.log('Added card:', trelloCard);
		}
    }
);
```

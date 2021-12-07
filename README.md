# ewallet 
# Description
This is a digital wallet that collects all credit cards. User can see their credit cards as well as add a new one.

Figmaskiss: https://www.figma.com/file/G4ep4nWFUplM8kXEntq83C/E-Wallet?node-id=11%3A2

Have done the task with vue create
Made according to Figma sketch
It is a single file application (SPA) that uses a vue router


All the cards are saved to Local storage and all new cards that are added to local storage and read from local storage
It is possible to remove a card (which is also removed from local storage)
The fields when a card is added are validated so that user can only enter numbers in the card number field and the maximum is 16 digits. 
The name field only take letters.


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

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

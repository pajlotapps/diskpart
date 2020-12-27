# Format a Hard Drive Using the Command Prompt 

## Formatowanie dysku twardego przy wykorzystaniu linii komend

<!-- ...trying to figure out how it is working -->

### STEP 1: Open Command Prompt As Administrator

```bash
search for > cmd
```

<p align="center">
    <img width="400px" src="https://raw.githubusercontent.com/pajlotapps/diskpart/main/src/asAdmin.jpg" alt="run as administrator">
</p>
and run as Administrator

or use file explorer and find cmd file, use right mouse button and select *'Run as administrator'*

<p align="center">
    <img width="400px" src="https://raw.githubusercontent.com/pajlotapps/diskpart/main/src/asAdmin2.jpg" alt="run as administrator">
</p>

### STEP 2: Use Diskpart

Once command line is open, type 'diskpart' and press Enter.

Po otwarciu lini komend, wrowadź komendę '**diskpart**' i zatwierdź klawiszem **Enter**

```bash
c:\windows\system32> diskpart
```
<p align="center">
    <img width="400px" src="https://raw.githubusercontent.com/pajlotapps/diskpart/main/src/cmd.jpg" alt="cmd">
</p>

<!-- <h3 align="center"> <a href="https://pl.reactjs.org">React</a></h3> -->


Github: [facebook/react](https://github.com/facebook/react) <br/>
Dokumentacja React dostępna na [stronie projektu](https://reactjs.org/docs)

### A: Co potrzebujemy?

#### 1. node.js

Możemy zainstalowac ze strony [nodejs.org][nodejs-url] pobierając plik .pkg
lub wykorzystując *Homebrew* 



Sama instalacja **node.js** odbywa się z wykorzystaniem komendy:

```zsh
brew install node
```

Sprawdzic aktualnie zainstalą wersję nodejs można przy pomocy komendy

```zsh
node -v
```

Pod [tym linkiem](https://changelog.com/posts/install-node-js-with-homebrew-on-os-x) znajduje się bardziej szczegółowy poradnik intalacji node.js wykorzystując **brew**

#### 2. npm 
[npm][npmjs-url] to  menadżer pakietów dla JavaScript, zostanie zainstalowany automatycznie podczas instalacji node.js
 
#### 3. yarn
[Yarn][yarn-url] to kolejny menadżer pakietów dla JavaScript - więcej o zaletach tego narzędzia można przeczytac na [tej stronie](https://www.nafrontendzie.pl/czym-jest-yarn-czego-sluzy)

```zsh
brew install yarn
```

aktualnie zainstalowaną wersję sprawdzimy komendą:
```zsh
yarn -v
```

##### Lista komend yarn

`yarn start` - uruchamia serwer

`yarn build` - przygotowuje pliki na produkcję

`yarn test` -  Starts the test runner.

`yarn eject` - czyści i usuwa

#### 4. React developer tools
Przyda się też rozszerzenie do przeglądarki chrome - [react deveoper tools][rdt-url]
 
## B: Create React App
Strona [projektu][create-react-url]
'Set up a modern web app by running one command.'
 
```
npx create-react-app my-app
cd my-app
npm start <albo> yarn start
```

trochę więcej o *npx* -> [link](https://blog.npmjs.org/post/162869356040/introducing-npx-an-npm-package-runner) ... [stockoverflow](https://stackoverflow.com/questions/50605219/difference-between-npx-and-npm)

```
NPM - Manages packages but doesn't make life easy executing any.
NPX - A tool for executing Node packages.
```

Zajmie to chwile po czym w oknie terminalu ukaże nam się lista przydatnych komend z krótkim opisem

![preview][c-r-a-url]

Więcej szczegółów zostanie zawarte w wygenerowanym właśnie pliku `README.md`

## Wykorzystane frameworki
### CSS
* [tailwindcss](https://tailwindcss.com) from [@tailwindlabs](https://github.com/tailwindlabs)
* [dokumentacja](https://tailwindcss.com/docs/installation)
  
```
yarn add tailwindcss
```

Usuwamy plik `App.css` - jeśli takowy istnieje.<br/><br/>
W pliku `App.js` zmieniamy importowany plik css: `import './index.css';`<br/><br/>
Edytujemy plik `index.css' tak aby zawierał poniższy kod:

```
@import "tailwindcss/base";

@import "tailwindcss/components";

@import "tailwindcss/utilities";
```

Tworzymy plik konfiguracyjny tailwind:
```
npx tailwindcss init
```
Powoduje to utworzenie pliku o nazwie `tailwind.congif.js`

Następnie, w głównym katalogu, tworzymy plik `postcss.config.js`:  
```
touch postcss.config.js
```
i wypełniamy go poniższym kodem:
```
module.exports = {
  plugins: [
    require('tailwindcss'),
    require('autoprefixer'),
  ]
}
```

Plik `package.json` nie zawiera jeszcze linijki kodu uwzględniającej właśnie utworzony plik, w tym celu wywołujemy komendę:
```
yarn add postcss-cli
```

Dodatkowo instalujemy `autoprefixer`

```
yarn add autoprefixer
```
Dependencies w plik `package.json` zostanie wzbogacony o linijkę: `"autoprefixer": "^9.8.6",`

Do `"scripts"` dopisujemy ponizsze linijki:
```
"build:css": "postcss src/index.css -o src/tailindcss.css",
"watch:css": "postcss src/index.css -o src/tailindcss.css -w",
```
Umożliwi to skompiowanie pliku .css komendą `yarn build:css`

Zmodyfikujemy nieco linijki `start` i `build` tak aby wywolywac `yarn build:css` przy uruchamianiu serwera:

```
    "start": "yarn build:css && react-scripts start",
    "build": "yarn build:css && react-scripts build",
````

### FontAwesome
* [Github repo](https://github.com/FortAwesome/react-fontawesome)

Instalacja przez **yarn**
```
yarn add @fortawesome/fontawesome-svg-core \
         @fortawesome/free-solid-svg-icons \
         @fortawesome/react-fontawesome
```

### react-spring
Biblioteka umożliwiająca wykorzystanie spręzystych animacji interfejsu

* [react-spring](https://www.react-spring.io)
* [GitHub repo](https://github.com/react-spring/react-spring)

Instalacja przy pomocy **yarn**
```
yarn add react-spring
```

<!-- Poradnik bazuje na repozytorium [QuentinWatt](https://github.com/QuentinWatt) <br/>
oraz jego tutorialu (React JS for beginners) [YouTube](https://www.youtube.com/watch?v=HDEVMozZhv8&list=PL41lfR-6DnOoTiHU4Ub6efP-p3xAq3eiV). -->


<!-- Linki -->
[nodejs-url]: https://nodejs.org/en/
[npmjs-url]: https://www.npmjs.com
[yarn-url]: https://yarnpkg.com
[rdt-url]: https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi
[react-url]: https://pl.reactjs.org/
[create-react-url]: https://create-react-app.dev

[c-r-a-url]: https://raw.githubusercontent.com/pajlotapps/React-dla-poczatkujacych-poradnik/master/cra.png?raw=true

# Code Editor Setup
Setting up VS Code with the proper extensions, linters and code formatters is an extremely important step to improve the developer experience when working on a project. This repository contains all the instructions and config files to setup my environment when working with certain frameworks/libraries. I will continue to add more configurations as I learn/figure out my preferences.

## NodeJS/Express
### Extensions

Install the below extensions:

- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- [Path Autocomplete](https://marketplace.visualstudio.com/items?itemName=ionutvmi.path-autocomplete)

### Settings

Go to your Visual Stuido Code `settings.json` file and add the below settings there:

```json
// config related to code formatting
"editor.defaultFormatter": "esbenp.prettier-vscode",
"editor.formatOnSave": true,
"[javascript]": {
  "editor.formatOnSave": false,
  "editor.defaultFormatter": null
},
"editor.codeActionsOnSave": {
  "source.fixAll.eslint": true,
  "source.organizeImports": true
},
"eslint.alwaysShowStatus": true
```
### Set Line Breaks

Make sure in your VS Code Editor, "LF" is selected as line feed instead of CRLF (Carriage return and line feed). 

### Install Dev Dependencies

```sh
yarn add -D eslint prettier
npx install-peerdeps --dev eslint-config-airbnb-base
yarn add -D eslint-config-prettier eslint-plugin-prettier
```

### Setup Linting Configuration file

Create a `.eslintrc.json` file in the project root and enter the below contents:

```json
{
  "extends": ["prettier", "airbnb-base"],
  "parserOptions": {
    "ecmaVersion": 12
  },
  "env": {
    "commonjs": true,
    "node": true
  },
  "rules": {
    "no-console": 0,
    "indent": 0,
    "linebreak-style": 0,
    "prettier/prettier": [
      "error",
      {
        "trailingComma": "es5",
        "singleQuote": true,
        "printWidth": 100,
        "tabWidth": 4,
        "semi": true
      }
    ]
  },
  "plugins": ["prettier"]
}
```
## Credits

Took inspirations from the youtube channel [Learn with Sumit](https://www.youtube.com/channel/UCFM3gG5IHfogarxlKcIHCAg).


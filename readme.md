# Debugin Typescript on Chrome with VSCode

Esta foi a primeira tentativa de debugar no Chrome a partir do vscode.

Eu criei um aplicação bem simples.

- https://code.visualstudio.com/docs/typescript/typescript-tutorial
- https://code.visualstudio.com/docs/typescript/typescript-compiling
- https://code.visualstudio.com/docs/typescript/typescript-debugging

Instalei o http-server `npm install http-server --save-dev`.

### Debugando

Inicie o servidor

    node node_modules/http-server/bin/http-server

Como já temos o vscode devidamente configurado, basta acinonar `F5`.

O Chrome deve abrir automaticamente.

Você pode colocar algum breakpoint e se divertir.

![debuging-vscode](https://user-images.githubusercontent.com/1257048/88119216-27b61a00-cb96-11ea-996b-be37c70d3e43.png)


### Build

Você também pode realizar o build sem a necessidade do debug.

    npm run build

Ou, se tiver o typscript instalado (`npm install -g typescript`), digite apenas...

    tsc


### Desafios

A configuração no arquivo `/.vscode/launch.json` é a dica "matadora".

    "runtimeArgs": [
        "--new-window",
        "-user-data-dir=\"/${workspaceFolder}/DevProfile\"",
        "--remote-debugging-port=9222",
        "--disable-background-networking"
    ],

Igualmente importante, foi saber onde estava instalado o Chrome (chromiun) no Linux.

    $ which chromium-browser
    /usr/bin/chromium-browser

O comando acima retornou (na minha máquina) o caminho do navegador, então pude corrigir o
arquivo `launch.json`.

      "runtimeExecutable": "/usr/bin/chromium-browser",

O que "salvou a lavoura" foram as dicas nos artigos abaixo.

### Me ajudaram

Dicas de configuração:

- https://medium.com/@JSantaCL/how-to-debug-an-angular-app-using-vs-code-and-chromium-7eb60b0b0cee

Onde está instalado o Chrome ?

- https://askubuntu.com/questions/839298/default-installation-path-for-chromium-web-browser-in-ubuntu-16-04
- https://unix.stackexchange.com/questions/436835/universal-path-for-chrome-on-nix-systems
- https://stackoverflow.com/questions/13928620/how-to-set-path-for-chromium-browser-in-sublimetext2s-slidebar-enhancement-plug


### Updates

1) Não pode esquecer de instalar o plugin para o VSCode:

https://github.com/Microsoft/vscode-chrome-debug


2) Launch versus Attach

https://code.visualstudio.com/docs/editor/debugging#_launch-versus-attach-configurations
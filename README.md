# install-homebrew-macM1

Para instalar el homebrew en una mac M1, debemos seguir estos pasos:

## 1) Abrir una terminal (debe ser zsh)

### Correr el comando

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## 2) Verificar los mensajes del proceso de instalación

Acá podemos ver que aunque nos diga que la instalación está OK, nos lanza el Warning del path

````
Warning: /opt/homebrew/bin is not in your PATH.
  Instructions on how to configure your shell for Homebrew
  can be found in the 'Next steps' section below.
==> Installation successful!
````

## 3) Crear un file .zshrc en el /home

En caso de no tener el file .zshrc, (es un file oculto puedes revisar si lo tienes con Shift + Comand + . o desde la terminal con ls -lah) correr el comando en el directorio /home:

````
touch ~/.zshrc
````

## 4) Abrir el file zshrc

Desde la terminal abrir el file .zshrc con nano o algún editor de texto, por ejemplo:

````
nano .zshrc
````

Luego ir a la ultima línea del file y escribir:

````
export PATH=/opt/homebrew/bin:$PATH
````

Por último correr este comando para que esté disponible:

````
source ~/.zshrc
````

## 5) Verificar que esté andando el homebrew

Correr este comando para verificar que todo esté OK:

````
brew help
````

En mi caso me lanza la siguiente salida, podremos ver que no muestra el warning:

````
➜  ~ brew help
Example usage:
  brew search TEXT|/REGEX/
  brew info [FORMULA|CASK...]
  brew install FORMULA|CASK...
  brew update
  brew upgrade [FORMULA|CASK...]
  brew uninstall FORMULA|CASK...
  brew list [FORMULA|CASK...]

Troubleshooting:
  brew config
  brew doctor
  brew install --verbose --debug FORMULA|CASK

Contributing:
  brew create URL [--no-fetch]
  brew edit [FORMULA|CASK...]

Further help:
  brew commands
  brew help [COMMAND]
  man brew
  https://docs.brew.sh
````

También puedes probar instalando algun paquete del brew, como por ejemplo el wget y verificar que no te lance el warning

Con esto, encamina el path de forma permanente, te dejo otra forma en caso de que no te siga funcionando:

````
- Add Homebrew to your PATH in ~/.zprofile:
    echo 'eval $(/opt/homebrew/bin/brew shellenv)' >> ~/.zprofile
    eval $(/opt/homebrew/bin/brew shellenv)
```

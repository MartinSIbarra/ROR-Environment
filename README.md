# ROR (Ruby On Rails) Environment
Un Vagrantfile creado para comenzar un nuevo ambiente de desarrolo de Ruby on Rails con un mínimo de intervención manual.

## Pasos para armar el ambiente de desarrollo.

* Instalar [VirtualBox](https://www.virtualbox.org/wiki/Downloads)

* Instalar [Vagrant](https://www.vagrantup.com/downloads.html)

* Solo para Windows (paso extra)
  * Instalar [Cygwin](https://cygwin.com/install.html)
  * [Ver tutorial](https://github.com/MartinSIbarra/Cygwin-Init) para instalación de paquetes.
    
* Clonar el siguiente repositorio (copiar y pegar):
  ```
  git clone https://github.com/MartinSIbarra/ROR-Environment.git [destino]
  ```
  Se debe reemplazar [destino] por el nombre de la carpeta donde se quiere clonar el repositorio, usando una de los siguientes ejemplos: 
  * Por ejemplo con */cygdrive/d/Tools/rails_vm* -> usando un path absoluto
   ```
   git clone https://github.com/MartinSIbarra/ROR-Environment.git /cygdrive/d/Tools/rails_vm
   ```
  * Por ejemplo con *rails_vm* -> usando un path relativo
   ```
   git clone https://github.com/MartinSIbarra/ROR-Environment.git rails_vm
   ```
  
* Realizar la primera ejecucion de Vagrant
  
  Entrar a la carpeta "[destino]" y ejecutar el siguiente comando:
  ```
  vagrant up
  ```
  Al ser la primera vez que se inicia la maquina virtual se instala el sistema operativo y se aprovisionan las herramientas.
  Para futuras ocasiones si se quiere ejecutar nuevamente el aprovisionamiento de la maquina virtual se debe ejecutar:
  ```
  vagrant up --provision
  ```
------------
 ### Links útiles:
 * [Documentación de Vagrant](https://www.vagrantup.com/docs/index.html)

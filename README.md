# ROR (Ruby On Rails) Environment
Un Vagrantfile creado para comenzar un nuevo ambiente de desarrolo de Ruby on Rails con un mínimo de intervención manual.

## Pasos para armar el ambiente de desarrollo.

* Instalar [VirtualBox](https://www.virtualbox.org/wiki/Downloads)

* Instalar [Vagrant](https://www.vagrantup.com/downloads.html)

* Solo para Windows (paso extra)
  * Instalar [Cygwin](https://cygwin.com/install.html)
  * [Ver tutorial](https://github.com/MartinSIbarra/Cygwin-Init) para instalación de paquetes.
    
* Clonar el siguiente repositorio (copiar y pegar)
```
git clone https://github.com/MartinSIbarra/ROR-Environment.git <destino>
```
* Realizar la primera ejecucion de Vagrant
  
  Entrar a la carpeta <destino> y ejecutar el siguiente comando, al ser la primera vez que se inicia la maquina virtual se instalara el sistema operativo y las herramientas.
  ```
  vagrant up --provision
  ```

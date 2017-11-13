===========================================
Instalación de Arch Linux en Raspberry Pi 3
===========================================

Descripción
===========
Aquí hay un script que te servirá para instalar Arch Linux en una Raspberry Pi 3. Es muy importante que configures el script primero.

Ten mucho cuidado porque, si pasas el dispositivo equivocado, destruirás el mismo.

Instalación
===========
Para correr el script:

* configúralo
* házlo ejectutable: `chmod u+x arch-mkrpi3`
* córrelo con poderes de root: `su -c "./arch-mkrpi3 /dev/sdX"` o `sudo ./arch-mkrpi3 /dev/sdX`

.. include:: arch-mkrpi3
    :code: bash

Referencia
==========
* https://archlinuxarm.org/platforms/armv8/broadcom/raspberry-pi-3
* https://www.youtube.com/watch?v=cSHkIcK6KyY


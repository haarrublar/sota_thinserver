## Installation Process

For installation process, I definetly decided to check the offical website documentation, where there is tons of info plus some initiation steps of how to connect the robot properly [SOTA](https://www.vstone.co.jp/). I indeed, recommend better to use the Sota's User Manual [user's manual](https://www.vstone.co.jp/sotamanual/index.php?Sota%E5%8F%96%E6%89%B1%E8%AA%AC%E6%98%8E%E6%9B%B8/).

The second recomendation is checking if the MAC is recognizing the robot once it is plug. Just running `ls /dev/cu.*` might help. If not, direct to the Sota's Introduction document in the Class Materials section in the UM Learn website. There, there is a clear solution in case the COM port is not recognized: download a driver ([CP210x USB to UART Bridge Virtual COM Port (VCP) drivers](https://www.silabs.com/software-and-tools/usb-to-uart-bridge-vcp-drivers?tab=overview)).

When entering do not forget the credentials provided by the advisor:     

- scpUser = 'root'
- scpPass = 'edison00'

Soto takes aprox. 45ss to turn on completly.

For checking that SotaPrimer is recognized run `ls /dev/cu.*`. If it is recognized, there would be something like `/dev/cu.SLAB_USBtoUART`.

SotaPrimer uses a Edison Intel is a computing model using a 8N1 configuration for serial communication parameters at 115200bps baud rate.

For communicating with SotaPrimer we need to run a `Serial Terminal Emulator`. Here, we can use `screen` to open a direct, real-time command line connection to external hardware (COM port - Edison Intel - SotaPrimer). This command use 8N1 protocol parameters automatically. However, the baud rate must be set. The complete command would be `screen /dev/cu.SLAB_USBtoUART 115200`.

Now, after checking the IP address (posterior the wifi connection), we use the `ssh` command in order to access to the SotaPrimer. Just running `ssh root@<IP-ADDRESS>`

DO NOT SELECT UPDATE NEVEEEER!

## Interacting with SotoPrimer

- For turning off led ligths use `"#000000"` in RGB lighting, black ("#000000") means zero light emitted. Sota's eyes use RGB LEDs, which work through additive color mixing. Inside each eye LED, there are three tiny primary-color light emitters: Red, Green, and Blue

- Additionally, when selecting the colors some considerations. First run using `python -m` (sota functions). Consider sota connections async so there is not any connectivity problem. There must be a brigde in between the UI, the controller, and sota using channels and websockets for quick communication `daphne core.asgi:application` and `pressedBtnWS.py`.
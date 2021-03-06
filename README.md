# COTEVOS-V2Gstack
Open source ISO 15118 communication implementation for Linux based on the code developed by Christian Blach for his Master Thesis at DTU Risø.
Please note that it requires uses TLS/PolarSSL, OpenV2GStack and libmultitask. The stack is compatible with the amd64 and armv7 architectures.

Getting started:
- Download mbed TLS from https://tls.mbed.org/download or their git repository
- mbed TLS must be configured to use thread locks. This is done by uncommenting #define POLARSSL_THREADING_C and POLARSSL_THREADING_PTHREAD in include/polarssl/config.h.
- *make && make check && sudo make install* the mbed TLS libary
- *make && sudo make install* the OpenV2G library in utils/OpenV2g_x.x.x
- *make && sudo make install* the libmultitask library in utils/libmultitask/unix
- *make && sudo make install* the nikola v2g stack

Things to note:
- I have made a custom makefile for OpenV2G. It can be located in utils/OpenV2G/Makefile
- The SLAC client implementation is programmed to work with the Qualcomm QCA7000 chip.
- The SLAC server is programmed to work with the Insys Powerline GP with SLAC device.
- The application layer messaging in the example folder only covers a reference AC implementation.

Bugs are still likely to be present. Please do not hesitate to create issues. Also you may have to download a stdatomic.h from LLVM if it's not in your current installation.


Working test bench setup:

Beaglebone <-Ethernet-> Insys Powerline GP with SLAC <-Power Line-> Insys Powerline without SLAC (QCA7000 based) <-Ethernet-> Beaglebone

Acknowledgements:
A lot of credit to Joakim Sindholt for making his brilliant C multithreading library libmultitask, see https://github.com/zhasha/libmultitask.
Also thanks to Siemens and Insys for making OpenV2g, see http://openv2g.sourceforge.net/.

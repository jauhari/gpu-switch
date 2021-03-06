# gpu-switch
gfx-switch is a Linux application to switch between the integrated and dedicated GPU of the Macbook Pro 11,3 (Late 2013) for the next reboot.

It targets to remove the need of booting into Mac OS X and running gfxCardStatus v2.2.1 to switch to the integrated card.

## Warning:
This is new code and it comes without any warranty! It's completely based on reverse engineering. Therefore use it at your own risk and don't blame us if anything breaks.

## Requirements:
By default the Intel GPU gets switched off by the EFI if you boot anything but Mac OS X.
So to use the Intel GPU you need to trick the EFI by either using the grub "apple_set_os" function:
- https://wiki.archlinux.org/index.php/MacBookPro11,x#Getting_the_integrated_intel_card_to_work_on_11.2C3
- https://lists.gnu.org/archive/html/grub-devel/2013-12/msg00442.html

or a patched Kernel:

- https://www.marc.info/?l=grub-deavel&m=141586614924917&w=2

Otherwise will end up with powered down integrated graphics card and a **black screen**.

## Building:
```
git clone git@github.com:0xbb/gpu-switch.git
make
```
## Usage:
As root you can select the GPU by running gpu-switch and **rebooting** your machine.
#### switch to the integrated GPU
``# ./gpu-switch -i``
#### switch to the dedicated GPU
``# ./gpu-switch -d``

## Future Work:
- Testing
- Integrating "apple_set_os" in the Kernel
- Documentation
 - (So far : https://gist.github.com/0xbb/974999591da4b1b2635c)

## Troubleshooting:
If you are facing weird problems a NVRAM reset could help:
http://support.apple.com/kb/PH14222?viewlocale=en_US

(Warning: this also resets your EFI boot configuration)

## License:
```
Copyright (C) 2014 Bruno Bierbaumer, Andreas Heider
Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in the
Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:
The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED,
INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR
PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE
OR OTHER DEALINGS IN THE SOFTWARE.
```

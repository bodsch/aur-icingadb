# icingadb Arch Linux package

These files are build instructions for the Arch Linux build system how to create an installable
[icingadb](https://github.com/Icinga/icingadb) package.


To install on Arch Linux, use your favourite AUR helper or build manually with:

```bash
git clone https://github.com/bodsch/aur-icingadb icingadb
cd icingadb
makepkg --cleanbuild --noprogressbar --clean --force --noconfirm

makepkg --printsrcinfo > .SRCINFO
```

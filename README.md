<div align=center>
    <h1 style="font-size: 4em; color: red">WSL2 Kernel Patch</h1>
</div>

A patch to compile Linux Kernel for WSL2. This patch includes a default config file for WSL2 and a script to compile the kernel.

## Apply the patch

1. Download the kernel source code from [kernel.org](https://www.kernel.org/).
2. Extract the source code.
3. Copy the patch file to the source code directory.
4. Run `patch -p1 < wsl2_kernel.patch` to apply the patch.
5. Run `yes "" | make oldconfig` to use the default config file.
6. Run `make -j$(nproc)` to compile the kernel.

## Install the kernel

Run `sudo make modules_install` to install the modules.

To use the kernel in WSL2, you need to copy the kernel image bzImage located in `arch/x86/boot/` to a directory in your Windows user profile. If you don't have a **.wslconfig** file in your Windows user profile, create one. Add the following lines to the file:

```ini
[wsl2]
kernel=C:\\Users\\<username>\\bzImage
```

No Generative AI was used in the making of this  
To either request support or contribute findings to the project, our discord server can be found [here](https://discord.com/invite/AM7RRGBXet)
## IF YOU HAVE ANY QUESTIONS OR DESIRE TO MAKE A CONTRIBUTION, MY CONTACTS ARE AS FOLLOWS.

Email:      sqookymrsmiku@proton.me  
Discord:    \_bluster\_  
Steam:      https://steamcommunity.com/id/happylilsqooky/


# Deadlock-Optimization-Resources
This Repository seeks to act similar to an [awesome-list](https://github.com/sindresorhus/awesome) where it is a list of resource and documentation on how to utilize and apply them
Please contribute as I am not all knowing
--------------------------------------

# Contents

- [Ingame Config Adjustments](#Ingame-Config-Adjustments)
- [External Adjustments](#External-Adjustments)
- [Event Tracing](#Event-Tracing)
- [Todo](#Todo)

# Ingame-Adjustments
## gameinfo.gi Modifications
- [My Performance Config Repo](https://github.com/Sqooky/OptimizationLock)  

As far as I am aware boot's and Kaizuchanru's configs provide the best frametime. My config provides optimizations but attempts to maintain the visual fidelity of normal deadlock

## Launch Options 
These are the only launch options I am aware of that actually do anything of substance

- ``-threads x`` How many threads to use, replace x with whatever you want, the [Valve Wiki](https://developer.valvesoftware.com/wiki/Command_line_options) says "your cores +1". This should only be needed if your computer is relatively low power as it might mess up threading on systems with better cpus
- ``-high`` Pretty sure this tells the os to give it higher priority. This also shouldn't be needed unless the system is poor.

### Rendering Backend
- DirectX11

Launch command is ``-dx11``. As time has passed vulkan seems to run better for myself and others. Only supports FSR2. FSR3 support for dx11 is intended and should come relatively soon.
- Vulkan

Launch command is ``-vulkan``. Runs better than DX11 from my testing. Supports FSR3

- [DXVK](https://github.com/doitsujin/dxvk)

DXVK seems to increase frame stability for older gpus and with newer AMD GPUs improves framerates. It might require cacheing of shaders again. It is automatically used when running in DX11 through Proton on Linux, but must be installed manually on Windows.
# External-Adjustments
## Upscaling Tomfoolery
- [Optiscaler](https://github.com/OptiScaler/OptiScaler)

A means of modifying upscaling in deadlock. It allows you to force FSR4 and various other cool tweaks.
It potentially allows for frame gen to be forced on nvidia gpus, but under linux it only presents the option when running under vulkan, and the debug menu for fg doesn't work. This leads me to believe that it isn't possible but your mileage may vary

- [Lossless Scaling](https://store.steampowered.com/app/993090/Lossless_Scaling/)

Lossless Scaling is a means of allowing external upscaling and frame generation. 
There is a linux port of the frame gen avalible [here.](https://github.com/PancakeTAS/lsfg-vk)

## Windows Specific
### Use a Custom ISO
A custom ISO is a modified windows install without any bloat at a base level
I've only heard people talk about tiny11, seems good.
### Debloat Windows
You generally should ensure that your windows install is debloated. 
- [Winutil](https://github.com/ChrisTitusTech/winutil)  
Well documented debloater tool. Generally the most advised.

### Process Lasso
Process Lasso Allows you to increase the priority of Deadlock in regards to windows CPU allocation. It can be downloaded [here](https://bitsum.com)

## Linux Specific
### Enviornment Variable Settings
- ``ENABLE_LAYER_MESA_ANTI_LAG=1`` Experimental Mesa anti-lag layer
- ``PROTON_FSR4_UPGRADE=1`` Makes older GPUs use FSR4 in place of FSR3 (I think)
- ``PROTON_FSR4_RDNA3_UPGRADE=1`` Makes newer GPUs use FSR4 in place of FSR3
- ``PROTON_ENABLE_WAYLAND=1`` Forces proton to run native in wayland. Seemed to make the game run smoother
- ``PROTON_NO_WM_DECORATION=1`` Disables window decoration, can help with window snapping on select compositors, but usually won't be needed.
- ``MANGOHUD=1`` Needs [Mangohud](https://github.com/flightlessmango/MangoHud), you already know what it is. Useful for checking performance stats.

So for example using all of these would look something like
```ENABLE_LAYER_MESA_ANTI_LAG=1 PROTON_FSR4_RDNA3_UPGRADE=1 PROTON_ENABLE_WAYLAND=1 MANGOHUD=1 gamemoderun %command% -vulkan```
### Cpu
You should utilize a tool such as [cpupower](https://linux.die.net/man/1/cpupower) or [gamemoderun](https://github.com/FeralInteractive/gamemode) to ensure your cpu is set to performance mode.
### Gpu
#### AMD GPUs
Make sure your MESA drivers are up to date. You can use software such as [LACT](https://github.com/ilya-zlobintsev/LACT) or [CoreCTRL](https://gitlab.com/corectrl/corectrl) to make sure your GPU's performance governor is set properly
#### Nvidia GPUs
- Make sure you're using an x11 based window manager/desktop enviornment. As far as I'm aware nvidia gpus still perform marginally worse under wayland
### OS
#### Desktop Enviornment
Some desktop enviornments are more performance heavy than others. You can consider using a standalone wm if you're desperate for performance. The ones I would recommend from personal experience are as follows:
- [MangoWC](https://github.com/DreamMaoMao/mangowc) Runs under wayland, pretty versatile and well optimized
- [i3](https://i3wm.org/) It's like driving a brick at two hundred miles an hour.

#### Kernel
##### Ntsync Performance Module
You can enable the Ntsync performance module which should help with frametimes by running
```
sudo mkdir -p /etc/modules.load.d/
echo '"ntsync"' | sudo tee /etc/modules.load.d/ntsync.conf
```
##### Performance Kernels
There are various performance oriented kernels
- [CachyOS' Kernel.](https://github.com/CachyOS/linux-cachyos) 

Most notably using the BORE CPU scheduler with various other patches targeting performance.

- [Liquorix](https://liquorix.net)

I don't have much experience with Liquorix so I can't offer much insight but it seems to be actively developed

- [Linux-Tachyon](https://git.staropensource.de/StarOpenSource/Linux-Tachyon)

The isolated kernel from Intel's ClearLinux, it should provide a performance boost on Intel machines but I don't have the means to test it on an AMD CPU. Also obligatory Death Grips reference.

- [Xanmod](https://xanmod.org)

Seems to be a bit slow on development but was more popular in the past.

- [TKG](https://github.com/Frogging-Family/linux-tkg)

TKG's kernel needs to be manually compiled to select their performance options but it runs very well and is updated regularly.
### Proton
Various versions of proton could yield a marginal performance boost.
- [Wine-tkg](https://github.com/Frogging-Family/wine-tkg-git)
- [Glorious-Eggroll](https://github.com/GloriousEggroll/proton-ge-custom)
- [CachyOS'](https://github.com/CachyOS/proton-cachyos)

# Event Tracing

Event tracing is a powerful way of profiling everything going on in your device. While this is a minor security risk, tracking down the cause of performance issues like stutters is trivial when tracing. Useful for finding what your pc's weakpoint is.

## Windows Specific
Valve recommends the player trace with Event Tracing for Windows (ETW). ETW-related apps suited for Deadlock are:
- [PerfView](https://github.com/microsoft/perfview/releases); **the guide for using PerfView for Valve's games can be found [here](https://developer.valvesoftware.com/wiki/PerfView)**
- [Windows Performance Analyzer](https://apps.microsoft.com/detail/9n0w1b2bxgnz)

## Linux Specific
Valve doesn't explictly recommend any tools for linux, although my personal recommendation is perf.
- [Perf](https://perfwiki.github.io/main/)
- [LTTng](https://lttng.org/)
- [ftrace](https://www.kernel.org/doc/html/latest/trace/index.html)
- [strace](https://strace.io/)
- [Apitrace](https://apitrace.github.io/) (recommended for debugging DXVK)

# Todo 
- Verify that optiscaler can consistently force frame generation and destribute a config for optiscaler that does so

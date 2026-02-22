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
- [Event Tracing](#Event-Tracing)
- [Ingame Config Adjustments](#Ingame-Config-Adjustments)
- [External Adjustments](#External-Adjustments)
- [Todo](#Todo)

# Event Tracing

Event tracing is a powerful way of profiling everything going on in your device. While this is a security risk, tracking down the cause of performance issues like stutters is trivial when tracing. The more that people trace the correct issues, the better the game becomes.

## Windows Specific
Valve recommends the player trace with Event Tracing for Windows (ETW). ETW-related apps suited for Deadlock are:
- [PerfView](https://github.com/microsoft/perfview/releases); **the guide for using PerfView for Valve's games can be found [here](https://developer.valvesoftware.com/wiki/PerfView)**
- [Windows Performance Analyzer](https://apps.microsoft.com/detail/9n0w1b2bxgnz)

## Linux Specific
Valve doesn't know which of the multiple Linux tracing tools is the best, so give one a try and see what works:
- [Perf](https://perfwiki.github.io/main/)
- [LTTng](https://lttng.org/)
- [ftrace](https://www.kernel.org/doc/html/latest/trace/index.html)
- [strace](https://strace.io/)
- [Apitrace](https://apitrace.github.io/) (recommended for debugging DXVK)
  
Please download these from your package manager if you can!

# Ingame-Adjustments
## gameinfo.gi Modifications
- [Hanturaya's Fps Config](https://gamebanana.com/mods/609804)

Haven't tested
- [Maidehnless' Optimizationlock Config](https://github.com/Sqooky/OptimizationLock)

Maidehnless' config is very well documented and provides sensible defaults. I am the current maintainer of the github repository, and given I find him a nice individual I would recommend it.
## Launch Options

- ``-preload`` I think this precaches vulkan shaders, but I am not sure
- ``-softparticlesdefaultoff`` I believe that this makes particle effects for effects like smoke less demanding. It has yielded some improvements on the two people who have tested it.
- ``+@panorama_min_comp_layer_cache_cost_TURNED_OFF 256`` Absolutely no idea what this does. If you have any idea please reach out. I believe it improves hud performance, although I am not sure.
- ``-threads x`` How many threads to use, replace x with whatever you want, the [Valve Wiki](https://developer.valvesoftware.com/wiki/Command_line_options) says "your cores +1"
- ``-high`` Pretty sure this tells windows to give it higher priority.

### Rendering Backend
- DirectX11

Launch command is ``-dx11``. It seems to provide generally better fps stability but only supports fsr2.
- Vulkan

Launch command is ``-vulkan``. Seems to be marginally slower but supports fsr3; this will likely be the only renderer in the future.

- [DXVK](https://github.com/doitsujin/dxvk)

DXVK seems to increase frame stability for older gpus and with newer AMD GPUs improves framerates. It might require cacheing of shaders again. It is automatically used when running in DX11 through Proton on Linux, but must be installed manually on Windows.
# External-Adjustments
## Upscaling Tomfoolery
- [Optiscaler](https://github.com/OptiScaler/OptiScaler)

A means of modifying upscaling in deadlock. It allows you to force fsr4 and various other cool tweaks.
It potentially allows for frame gen to be forced on nvidia gpus, but under linux it only presents the option when running under vulkan, and the debug menu for fg doesn't work. This leads me to believe that it isn't possible but your mileage may vary

- [Lossless Scaling](https://store.steampowered.com/app/993090/Lossless_Scaling/)

Lossless Scaling is a means of allowing external upscaling and frame generation. 
There is a linux port of the frame gen avalible [here.](https://github.com/PancakeTAS/lsfg-vk)

## Windows Specific
- Use the latest driver if you can; there are potential fixes for your issues in those, although I understand that there are also risks.

## Linux Specific
### Enviornment Variable Settings
- ``DXVK_ASYNC=1`` Dxvk Async, allows for less rendering if something needs to be cached.
- ``ENABLE_LAYER_MESA_ANTI_LAG=1`` Experimental Mesa anti-lag layer
- ``PROTON_FSR4_UPGRADE=1`` Makes newer GPUs use fsr4 in place of fsr3 (I think)
- ``PROTON_FSR4_RDNA3_UPGRADE=1`` Makes older GPUs use FSR4 in place of FSR3
- ``PROTON_ENABLE_WAYLAND=1`` Forces proton to run native in wayland. For me this causes jump to be spammed when holding space. Not sure if this is exclusive to me tho.
- ``PROTON_NO_WM_DECORATION=1`` Disables window decoration, can help with window snapping.
- ``MANGOHUD=1`` Needs [Mangohud](https://github.com/flightlessmango/MangoHud), you already know what it is. Useful for checking performance stats.
### Cpu
You should utilize a tool such as [cpupower](https://linux.die.net/man/1/cpupower) or [gamemoderun](https://github.com/FeralInteractive/gamemode) to ensure your cpu is set to performance mode.
### Gpu
#### AMD GPUs
Make sure your MESA drivers are up to date. You can use software such as [LACT](https://github.com/ilya-zlobintsev/LACT) or [CoreCTRL](https://gitlab.com/corectrl/corectrl) to make sure your GPU's performance governor is set properly
#### Nvidia GPUs
Lol, Lmao
- Make sure you're using an x11 based window manager/desktop enviornment. As far as I'm aware nvidia gpus still perform marginally worse under wayland
### OS
#### Desktop Enviornment
Some desktop enviornments are more performance heavy than others. You can consider using a standalone wm if you're desperate for performance. The ones I would recommend from personal experience are as follows:
- [MangoWC](https://github.com/DreamMaoMao/mangowc) Runs under wayland, pretty versatile and well optimized
- [i3](https://i3wm.org/) It's like driving a brick at two hundred miles an hour.

#### Kernel
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

Seems to be pretty cool but I haven't monkeyed with it. Has very active development as well as customization options.

### Proton
Various versions of proton could yield a marginal performance boost.
- [Wine-tkg](https://github.com/Frogging-Family/wine-tkg-git)
- [Glorious-Eggroll](https://github.com/GloriousEggroll/proton-ge-custom)
- [CachyOS'](https://github.com/CachyOS/proton-cachyos)

# Todo 
- Verify that optiscaler can consistently force frame generation and destribute a config for optiscaler that does so
- Establish a standardized benchmark and test the configs

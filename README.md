# IF YOU HAVE ANY QUESTIONS OR DESIRE TO MAKE A CONTRIBUTION, MY CONTACTS ARE AS FOLLOWS.
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
- [Todo](#Todo)

 # Ingame-Config-Adjustments
- [Hanturaya's Fps Config](https://gamebanana.com/mods/609804)

Haven't tested
- [Maidehnless' Optimizationlock Config](https://gamebanana.com/mods/650519)

Maidehnless' config is very well documented and provides sensible defaults. I would recommend it.

# External-Adjustments
- [Optiscaler](https://github.com/OptiScaler/OptiScaler)

A means of modifying upscaling in deadlock. Optiscaler potentially allows for frame gen to be forced on nvidia gpus, but under linux it only presents the option when running under vulkan, and the debug menu for fg doesn't work. This leads me to believe that it isn't possible but your mileage may vary
- [DXVK](https://github.com/doitsujin/dxvk)

DXVK seems to increase frame stability for older gpus and AMD gpus. It might require cacheing of shaders again.

# Linux Specific Tweaks

## Cpu
You should utilize a tool such as [cpupower]() or [gamemoderun]() to ensure your cpu is set to performance mode.
## Gpu
### AMD GPUs
Make sure your MESA drivers are up to date. You can use software such as [LACT](https://github.com/ilya-zlobintsev/LACT) or [CoreCTRL](https://gitlab.com/corectrl/corectrl) to make sure your GPU's performance governor is set properly
### Nvidia GPUs
Lol, Lmao
- Make sure you're using an x11 based window manager/desktop enviornment. As far as I'm aware nvidia gpus still perform marginally worse under wayland
## OS
### Desktop Enviornment
Some desktop enviornments are more performance heavy than others. You can consider using a standalone wm if you're desperate for performance
### Kernel
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


# Todo 
- Verify that optiscaler can consistently force frame generation and destribute a config for optiscaler that does so
- Establish a standardized benchmark and test the three configs

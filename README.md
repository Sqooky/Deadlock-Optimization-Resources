
# Deadlock-Optimization-Resources
This Repository seeks to act similar to an [awesome-list](https://github.com/sindresorhus/awesome) where it is a list of resource and documentation on how to utilize and apply them
Please contribute as I am not all knowing
--------------------------------------

# Contents
- [Ingame Config Adjustments](#Ingame-Config-Adjustments)
- [External Adjustments](#External-Adjustments)
- [Todo](#Todo)

 # Ingame-Config-Adjustments
- [Dyson's Fps Config](https://gamebanana.com/mods/616141)

Worked well for me although does cause trooper gibs to be odd by default. It also is documented in Russian so that might be a bit confusing for tweaking values.
- [Hanturaya's Fps Config](https://gamebanana.com/mods/609804)

Haven't tested
- [Maidehnless' Optimizationlock Config](https://gamebanana.com/mods/650519)

Maidehnless' config is a modified version of the dyson config with additional convars and is documented in english. Currently it works the best for my usecase, and as such is the one I would recommend. This repository hosts a presently up to date patched gameinfo.gi with an additional version with mod support.


# External-Adjustments
- [Optiscaler](https://github.com/OptiScaler/OptiScaler)

A means of modifying upscaling in deadlock. Optiscaler potentially allows for frame gen to be forced on nvidia gpus, but under linux it only presents the option when running under vulkan, and the debug menu for fg doesn't work. This leads me to believe that it isn't possible but your mileage may vary
- [DXVK](https://github.com/doitsujin/dxvk)

This might help with windows users on older gpus or amd gpus as in some games there have been reported fps improvements from using dxvk, plus as I understand it the version of vulkan used by deadlock is out of date (not entirely sure though, although on my linux rig dx11 performs better)

# Todo 
- Verify that optiscaler can consistently force frame generation and destribute a config for optiscaler that does so
- Establish a standardized benchmark and test the three configs

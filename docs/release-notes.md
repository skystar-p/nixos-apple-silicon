# Release Notes

This file contains important information for each release.

## 2025-xx-yy

This release drops our custom Mesa override.

Since mesa 25.1, support for asahi is enabled by default.
This means, the nixpkgs mesa is sufficient and we don't need any custom mesa,
or methods to replace it.

In addition to the now ineffective
`hardware.asahi.useExperimentalGPUDriver` option, this also removes the
`hardware.asahi.experimentalGPUInstallMode` option, which was already
deprecated before.

## 2025-08-10

This release updates nixpkgs.

Rust support is now the default in the kernel (even in the installer). This
release also fixes a build issue with asahi-fwextract.

As of this release, the release model is now documented [here](https://github.com/nix-community/nixos-apple-silicon/blob/main/docs/release-process.md). Development
is now shifting directly to the main branch instead of discrete tagged releases.

## 2025-05-30

This release updates nixpkgs and the kernel.

Updating nixpkgs brings us past the 25.05 release and on the path to 25.11.

This release also fixes a build issue with Mesa on recent nixpkgs. Thanks
to wistfulbrick for clues to this fix.

As promised, the repositry has been moved to the nix-community organization. The
old URL should redirect automatically but you may wish to update your
configuration.

## 2025-05-17

This release updates nixpkgs, the kernel, and Mesa.

The Mesa and kernel update stabilize the UAPI communication between them,
allowing official Mesa releases in the future to be compatible with Apple
Silicon. A reboot will be required after installation to restore graphics
support.

**Please see the issue on [the community tranistion of nixos-apple-silicon](https://github.com/tpwrules/nixos-apple-silicon/issues/298).**

This repository will shortly be moving to the nix-community organization and
gaining some more maintainership. The user experience should not majorly change
but my personal involvement will slightly shift. Thanks for everything so far!

## 2025-05-10

This release updates nixpkgs, the kernel, and audio support components.

Microphone support is now available for users using macOS firmare version 13.5
(this is different to any other macOS install on the system). The current
version can be checked with `cat /proc/device-tree/chosen/asahi,os-fw-version`.

To upgrade it:
* Take a backup of any macOS and Linux data you do not want to lose in case of
  problems
* Delete the macOS stub and EFI partitions ONLY, NOT the root partition
  (more info avaiable in the guide's uninstallation section)
* Reinstall the UEFI environment into the free space using the Asahi installer
* Rerun the NixOS installer (more info available in the guide's rescue section)

## 2025-04-27

This release updates nixpkgs.

This release fixes issues preventing Mesa from being used. Thanks to
marcin-serwin and schphe for the fix.

Another update with updated packages will follow shortly. Thanks for the
patience.

## 2025-03-15

This release updates nixpkgs and the kernel.

This release fixes build issues with the kernel and the latest nixpkgs. Thanks
to flokli for info on the fix.

## 2025-03-10

This release updates nixpkgs and Mesa.

This release fixes build issues with Mesa and the latest nixpkgs.

## 2025-02-03

This release updates nixpkgs, m1n1, and the kernel.

This release fixes build issues related to lsp-plugins.

**NixOS 24.11 users, please use tag `releasep2-2024-12-25`; see below.**

## p2-2024-12-25

This is a special patch release to fix build issues related to lsp-plugins on
recent NixOS 24.11 releases. It is available at Git tag
`releasep2-2024-12-25`. NixOS 24.11 users must use this release.

## 2025-01-22

This release updates nixpkgs.

This release corrects a build failure with the latest nixpkgs due to a change in
how the `alsa-ucm-conf` derivation works.

## 2025-01-20

This release updates nixpkgs. **NixOS 24.11 users must stay on the previous
release.**

Thanks to the hard work of upstream nixpkgs and Mesa (K900 in particular), the
Mesa graphics support has been revamped to be easier and faster, see commits
for details. The `hardware.asahi.experimentalGPUInstallMode` option no longer
does anything and will be deprecated and removed in future releases.

This fixes graphics issues with nixpkgs unstable. The Wi-Fi issue also appears
fixed.

## 2024-12-25

This release updates nixpkgs, the kernel, and Mesa.

The kernel config is fixed to prevent an issue which, in combination with a bug
in nixpkgs, caused boot failure when using systemd in initrd. Thanks to
andre4ik3 and several others for helping diagnose and provide hints to find
this issue.

The Wi-Fi issue persists, but will likely be resolved by an imminent nixpkgs
update.

## 2024-12-04

This release updates nixpkgs and all the Asahi components.

The big new feature is Vulkan support thanks to Asahi's hard work on Mesa! The
kernel contains a graphics UAPI update, so you must reboot after updating to
restore graphics acceleration.

There might be trouble with Wi-Fi in the installer failing to connect to certain
networks, please report on GitHub and use an older version temporarily if you
encounter this issue.

## 2024-11-30

This release updates nixpkgs.

Updating nixpkgs brings us past the 24.11 release and on the path to 25.05. This
release also fixes builds with the version of systemd fixed to not cause
bootability issues.

Updates to other Asahi components are imminent.

## 2024-11-12

This release updates nixpkgs.

**This release fixes an issue that will cause NixOS to be unbootable after an
  upgrade.** This was caused by a systemd update in recent nixpkgs revisions.
If you are affected, please see the information
[here](https://github.com/tpwrules/nixos-apple-silicon/issues/248)
to recover.

Thanks in particular to oliverbestmann and andre4ik3 for their work reporting
and diagnosing this issue.

This release also fixes build issues with Rust 1.82.0. Updates to other Asahi
components will follow.

## 2024-09-03

This release updates nixpkgs, the kernel, the Asahi audio configs, and
asahi-fwextract.

This release fixes an issue evaluating Mesa builds using the latest versions of
nixpkgs. Thanks to rowanG077 for the fix! The kernel and nixpkgs updates also
fix issues connecting to WiFi in certain situations.

## 2024-07-31

This release updates nixpkgs, the kernel, and Mesa.

The kernel contains a graphics UAPI update, so you must reboot after updating
to restore graphics acceleration.

## 2024-07-19

This release updates nixpkgs and the kernel.

The kernel is updated back to a 6.9.9 series kernel with workarounds for the
graphics driver crashes. It should now be stable and ready for use.

## 2024-07-18

This release updates nixpkgs.

The kernel has been temporarily downgraded to 6.9.5 to resolve crashes reported
by several users using 6.9.9 relating to the graphics driver.

Additionally, the sound module has been adjusted to resolve evaluation failures
caused by the removal of the NixOS `sound.enable` option in recent nixpkgs
versions.

## 2024-07-14

This release updates nixpkgs and the kernel.

Additionally, Mesa is restructured to fix build issues with the latest nixpkgs
and hopefully reduce the likelihood of issues occurring in the future.

## 2024-06-16

This release updates nixpkgs, the kernel, and Mesa.

Updating nixpkgs brings us past the 24.05 release and on the path to 24.11. The
update also fixes some issues with cross-compilation, and corrects a problem
which would randomly cause the Mesa build to produce corrupt binaries.

Additionally, `speakersafetyd` and `bankstown-lv2` are now used from nixpkgs
instead of being overlayed.

Support for the current stable 24.05 release is functional, but as always this
is on a best effort basis.

## 2024-05-23

This release updates nixpkgs, the kernel, and m1n1.

**This release completely fixes a data corruption bug for dm-crypt users.** The
fix in the previous release was incomplete. See the previous release notes
for further info.

**All users are recommended to upgrade m1n1 from macOS** using the instructions 
available
[here](https://discussion.fedoraproject.org/t/important-psa-update-your-m1n1-before-updating-to-macos-sonoma-14-5/117192).
The referenced stage 2 work arounds are also included in this release.

## 2024-05-17

This release updates nixpkgs and the kernel.

**This release fixes a data corruption bug for dm-crypt users.**
* The bug apparently only affects dm-crypt block devices and was introduced in
  the 6.8 kernel update in release 2024-04-27. Users who don't use dm-crypt, or
  who haven't upgraded to 2024-04-27 or 2024-05-14, are not at risk.
* The Nix store can be checked for corruption using the command
  `nix-store --verify --check-contents`; this will take a while and should
  complete without any error messages.
* If corruption is detected, whether in the store or elsewhere, a complete
  backup, reformat, and reinstall of the affected filesystem is recommended.
* Thanks to flokli for the initial report, mixi for identifying the issue, and
  others for their help!
* More info available [here](https://github.com/AsahiLinux/linux/commit/b58cc025c2014597fcb4649e3a9c77a31cf72591).

**Users of M2 Mac Mini/Studio systems** are also recommended to upgrade m1n1
using the instructions available
[here](https://discussion.fedoraproject.org/t/important-psa-update-your-m1n1-before-updating-to-macos-sonoma-14-5/117192)
to avoid loss of display after an update to macOS Sonoma 14.5. Other users
should not upgrade at this time.

## 2024-05-14

This release updates nixpkgs, the kernel, m1n1, and the Asahi sound packages.
Thanks to LeSuisse for the kernel update and fx-chun for the sound update.

The new sound packages are necessary for the latest nixpkgs, but are not
compatible with nixpkgs stable's WirePlumber, nor older versions of nixpkgs
unstable. Affected users are encouraged to remain on a previous release.

## 2024-04-27

This release updates nixpkgs, the kernel, and U-Boot. Thanks to oliverbestmann
for the kernel update.

The new kernel is not compatible with nixpkgs stable's Rust compiler. Therefore,
graphics support will be unavailable. Stable users are encouraged to remain on
the previous release, or contribute patches.

The new U-Boot uses a new command to boot from a USB drive. Run the `bootmenu`
command then select the `usb 0` option.

## 2024-04-20

This release updates nixpkgs.

This release includes patches to correct building of the kernel with Rust
1.77.0.

## 2024-04-04

This release updates nixpkgs.

Another fix is also included for cross-compiling the installer with recent
nixpkgs versions.

## 2024-03-24

This release updates nixpkgs and the kernel.

The kernel update is understood to include a potential fix for some HDMI issues.

The sound module now forces WirePlumber 0.5 and above (included in recent
nixpkgs releases) to be downgraded to 0.4.17 as these newer versions are not
compatible with the Asahi sound configs. This downgrade corrects the
unexpectedly poor sound experience.

A fix is also included for cross-compiling the installer with recent nixpkgs
versions.

## 2024-03-11

This release updates nixpkgs.

This release includes patches to correct building of the kernel with Rust 1.76.0
and fixes for building U-Boot with the latest nixpkgs. Thanks to bkchr for
these patches.

This release also introduces a `hardware.asahi.enable` configuration option,
which defaults to true. Setting this option to false disables all effects of
the Apple Silicon support module (including ignoring all other options), which
may be useful for multi-system configurations.

## 2024-03-05

This release updates nixpkgs and Mesa.

This release also includes a patch so that Mesa can build again on NixOS 23.11
and older nixpkgs versions.

Support for stable NixOS releases is neither tested nor guaranteed, but patches
to address specific issues are welcome.

## 2024-02-29

This release updates nixpkgs.

This release corrects a few minor issues:
* Resolves an error that flakes were not enabled when running `nixos-install`
* Updates to avoid using a nixpkgs version that was not from the nixos-unstable
  channel
* Restored compatibility for the sound module with older versions of nixpkgs.

## 2024-02-26

This release updates nixpkgs, the kernel, and Mesa. Thanks to oliverbestmann for
the updates.

This release also includes a patch to fix random boot hangs with recent versions
of nixpkgs.

The kernel and Mesa are now upgraded to OpenGL 4.6 compatibility. Restructurings
and upgrades have been made in the sound support as well (in particular an
upgrade to the `bankstown-lv2` bass enhancer), and quality should be improved.

The GPU acceleration and sound upgrades require packages and features present
only in the latest nixpkgs unstable releases. If you are using NixOS 23.11,
please remain on an older release. This may be addressed in the future;
contributions are welcome.

Upgrading nixpkgs brings GCC 13.2 as the default system compiler.

## 2024-01-17

This release updates nixpkgs.

This release includes patches and fixes to correct building of the kernel with
Rust 1.75.0 and adjustments to accommodate Mesa changes in the latest nixpkgs.
Thanks once again to yu-re-ka.

## 2023-12-24

This release updates nixpkgs.

This release changes how the Asahi configurations are loaded into PipeWire and
WirePlumber, thus making it possible for users to install other configurations
in parallel for e.g. Bluetooth (or override the Asahi configurations, though
this is likely a bad idea). Thanks to cid-chan for reporting this problem.

## 2023-12-23

This release does not update any packages.

This release corrects an oversight in the sound support which resulted in the
Asahi configurations not being loaded properly into PipeWire and WirePlumber.
This is now fixed, and audio quality and behavior should be at the
upstream-intended standard. Thanks to ivabus for reporting this oversight.

Additionally, rtkit is enabled by default to allow the audio components to run
at real-time priority and so reduce glitches.

## 2023-12-22

This release updates nixpkgs and includes the necessary components for full
sound support, namely speakersafetyd, bankstown-lv2, and asahi-audio.

New features and fixes:
* Full speaker and headphone support is finally here! (on supported machines and
  nixpkgs versions)
  * You will need at least `sound.enable = true;` in your configuration.
  * Sound support relies on PipeWire, which is automatically enabled by the
    apple-silicon-support module. You must remove any
    `hardware.pulseaudio.enable = true;` from your configuration, or building
    it will fail. PipeWire's PulseAudio compatibility module is enabled by
    default.
  * Thanks to yu-re-ka and diamondburned for helping with this support.
* Kernel config is now synced with and will track Fedora Asahi Remix's Apple
  Silicon-specific changes
  * This fixes a missing option which broke GPU acceleration on M2 hardware.

## 2023-12-19

This release updates nixpkgs, m1n1, U-Boot, the kernel, and Mesa.

With the official announcement of the Fedora Asahi Remix, nixos-apple-silicon is
now tracking package versions and capabilities as they appear in Fedora, in
order to offer the upstream intended user experience.

Updating nixpkgs brings us past the 23.11 release and on the path to 24.05.
Other updates bring HDMI support for supported machines and firmware versions.
Don't expect this to work if you installed before August 2023; workarounds will
be made available shortly, and a long-term solution will hopefully be
implemented by Asahi and incorporated here as well.

Speaker support will be added in the next release once safe implementation and
testing is completed. Thanks for the patience and understanding.

## 2023-11-19

This release updates nixpkgs.

In particular, nixpkgs is updated to fix issues with compilation of wolfssl,
and some regressions in systemd-boot.

This release also adds patches to the kernel to support compilation with Rust
1.73.0. Thanks again to yu-re-ka for this contribution.

Speaker support will be added in an upcoming release.

## 2023-10-21

This release updates nixpkgs, m1n1, U-Boot, and the kernel.

Some exciting new features are now available:
* ALSA configuration module to enable the headphone jack on supported devices
  * You will need at least `sound.enable = true;` and
    `hardware.pulseaudio.enable = true;` in your configuration.nix to enable
    sound for the system.
  * Speakers will still not be enabled.
  * Thanks to IonAgorria and yusefnapora for this contribution.
* Built-in webcam support for supported devices
  * The webcam should work without additional configuration in applications like
    Firefox or desktop camera viewers.
  * To avoid an overly-dark image and other image quality issues, the ISP
    firmware needs to be added to `all_firmware.tar.gz` within the peripheral
    firmware directory. This can be done by inserting
    `/usr/sbin/appleh13camerad` from macOS into the archive's root. Stub
    partitions created with the Asahi installer after this release should
    already have the file but older installations must be upgraded manually.
    This will hopefully be done automatically in a future release.
* Official support for M2-series devices
  * Please leave feedback if issues are encountered. I don't have any way to
    test this support with NixOS.

## 2023-09-17

This release updates nixpkgs.

In particular, nixpkgs is updated to fix regressions in cross-compilation.

## 2023-09-08

This release updates nixpkgs, m1n1, the kernel, and Mesa.

This release also adds patches to the kernel to support compilation with Rust
1.72.0. Thanks again to yu-re-ka for this contribution.

## 2023-08-26

This release updates nixpkgs.

This release also removes obsolete Rust patches that were no longer needed and
prevented building in the latest stable nixpkgs release. Thanks to autrimpo for
noticing this issue and testing the fix.

## 2023-08-25

This release updates nixpkgs, m1n1, the kernel, and Mesa.

Thanks to yu-re-ka, Lucus16, and Enzime for help with these updates.

## 2023-08-19

This release updates nixpkgs and Mesa.

In particular, nixpkgs is updated to fix a regression in cross-compilation
and a non-deterministic build failure of GRUB.

## 2023-08-08

This release does not update any software.

This release includes a patch to allow building with Rust 1.71.0 in the
latest nixpkgs releases. Nixpkgs itself is not yet updated due to a
regression in cross-compilation.

## 2023-07-26

This release updates nixpkgs, the Asahi kernel, and Mesa.

## 2023-07-12

This release does not update any software.

This release corrects an issue where the kernel would not build with Rust
support when using the latest stable nixpkgs release due to a patch that was
applied when it should not have been. Thanks to natsukagami for noticing and
correcting the issue.

Support for stable nixpkgs releases is neither tested nor guaranteed, but
patches to address specific issues are welcome.

## 2023-07-11

This release updates nixpkgs, the Asahi kernel, and Mesa.

This release adds the ability to build the installer and packages when not using
flakes through the inclusion of flake-compat. Thanks to flokli for this
contribution.

## 2023-06-25

This release updates nixpkgs. There have been no changes to Asahi's stable
package versions since the last release.

This release corrects problems building the Linux kernel Rust graphics driver
using recent nixpkgs releases. Thanks to yu-re-ka and the Asahi team for
patches.

This release also finally eliminates IFD when building the kernel.

## 2023-06-15

This release updates nixpkgs, the Asahi kernel, and Mesa.

Updating nixpkgs fixes an issue uncovered by the last release which would cause
`nixos-generate-config` to generate a hardware configuration which would build
for the wrong system type.

Updating the Asahi packages fixes some graphics issues using the experimental
GPU driver.

## 2023-06-07

This release updates nixpkgs and all Asahi package versions, including the
kernel, m1n1, U-Boot, and Mesa.

Updating nixpkgs brings us past the 23.05 release and on the path to 23.11.

Updating m1n1 fixes some issues with virtualization.

Updating U-Boot fixes issues with certain USB devices causing U-Boot to crash
and allows use of all USB ports on all Macs (IIUC).

Due to a quirk in the new version of U-Boot, a revised command is required to
boot off a flash drive when a system is already installed on the internal disk.
This command is as follows: `env set boot_efi_bootmgr ; run bootcmd_usb0`.
Hopefully this quirk will be addressed in a future release.

## 2023-05-06

This release updates nixpkgs. There have been no changes to Asahi's stable
package versions since the last release.

This release corrects problems building the Linux kernel Rust graphics driver
using recent nixpkgs releases. Thanks to yu-re-ka and QuentinI for patches.

This release also reduces the amount of IFD involved in building the kernel.
Thanks again to QuentinI for this contribution.

## 2023-03-21

This release updates nixpkgs and the Asahi packages, including the kernel, m1n1,
U-Boot, and Mesa.

Updating nixpkgs finally brings GCC 12 as the default compiler.

## 2023-02-23

This release updates nixpkgs. There have been no changes to Asahi's stable
package versions since the last release.

This release corrects build failures of the Linux kernel using either the latest
NixOS unstable or NixOS 22.11 versions of the Rust compiler.

## 2023-01-31

**This release reorganizes the project substantially. Please follow the
directions below or the upgrade might not take effect.**

This release updates nixpkgs and reorganizes the project. There have been no
changes to Asahi's stable package versions since the last release.

To upgrade (assuming you used the standard installation instructions):
* Remove `/etc/nixos/m1-support`
* Procure the `apple-silicon-support` directory from the repo and place it in
  `/etc/nixos/apple-silicon-support`
* Change the `./m1-support` include path in your configuration.nix to
  `./apple-silicon-support`.

Thanks primarily to the hard work of oati, the project has been reorganized to
cleanly separate the Nixpkgs package definitions and overlay, the NixOS
modules, and the custom bootstrap installer configuration. This will make
development and customization more straightforward. The project has also been
renamed to emphasize compatibility with all generations of Apple Silicon Macs
(though be mindful that support of a particular machine by this project cannot
come until Asahi Linux does the hard parts!).

Flakes support is now required to build the installer. The installer ISO and
development versions of m1n1 and U-Boot are now available as outputs of this
repository's flake. The overlay and NixOS modules are also available as outputs
for the convenience of system flakes users.

## 2023-01-18

This release updates nixpkgs. There have been no changes to Asahi's
stable package versions since the last release.

This release corrects build failures when the kernel is built with Rust support.
These were a result of Nixpkgs' upgrade to Rust 1.66.

This release also adds an option `hardware.asahi.experimentalGPUInstallMode` to
select the way in which the experimental GPU driver is installed.
There are three choices:
* `driver`: install only as a driver, do not replace system Mesa. Causes issues
  with certain programs like Plasma Wayland.
* `replace` (the default): use `system.replaceRuntimeDependencies` to replace
  system Mesa with Asahi Mesa. Does not work in pure evaluation context (i.e. in
  flakes by default).
* `overlay`: overlay system Mesa with Asahi Mesa. Requires rebuilding the
  world.

## 2023-01-16

This release updates nixpkgs. There have been no changes to Asahi's
stable package versions since the last release.

This release also solves an issue where Plasma Wayland sessions would
not launch when using experimental GPU support due to mismatched Mesa
versions. (Thanks bkchr!)

## 2022-12-26

This release updates upstream dependencies, including nixpkgs and Mesa.

Updating nixpkgs in particular resolves an issue which broke reproducibility of
the installer ISO when building on some filesystems, like ZFS.

The curl, wget, and
[wormhole-william](https://github.com/psanford/wormhole-william) utilities are
now included in the installer image to ease file transfer and initial setup.
wormhole-william is interoperable with the
[Magic Wormhole](https://magic-wormhole.readthedocs.io/en/latest/) utility.
(Thanks zzywysm!)

U-Boot is now built with a double-size font so that its console can be
practically read on Retina displays. (Thanks again zzywysm!)

## 2022-12-18

This release updates upstream dependencies including nixpkgs, the kernel,
and m1n1.

Updating nixpkgs resolves an issue that might have caused NetworkManager's GUI
to crash after entering a Wi-Fi password.

Support for Rust in the kernel, the Asahi edge kernel config, and the
experimental Mesa driver are now included as NixOS options.

* Enable the option `hardware.asahi.withRust` to build the kernel with the
Rust toolchain present. GCC is still used for the kernel's C code.
* Enable the option `hardware.asahi.addEdgeKernelConfig` to add the official
Asahi edge kernel configuration options. This implies the previous option.
* Enable the option `hardware.asahi.useExperimentalGPUDriver` to switch the
system version of Mesa to the Asahi project's fork which includes experimental
support for the Apple Silicon GPU. This implies the previous two options.

Please note that, as outlined in the
[official blog post](https://asahilinux.org/2022/12/gpu-drivers-now-in-asahi-linux/),
there are likely to be issues with many applications using the experimental
GPU drivers. **Do not report any GPU driver issues encountered under NixOS to
the Asahi project. Replicate your issue and gather relevant information as
described in the post using the official distro instead!**

The GPU drivers have been tested and verified functional under NixOS on an
M1 Max MacBook Pro 16" with X11, Xfce, SuperTuxKart, and WebGL under Firefox.

## 2022-12-06

This release updates upstream dependencies including nixpkgs, the kernel,
and m1n1. Nixpkgs is now officially 23.05pre.

The `boot.kernelPackages` NixOS option is now respected properly by the
manual kernel builder. (Thanks natsukagami!)

## 2022-11-29

This release corrects an issue which would cause booting off a USB flash
drive from a boot environment with the latest device trees to fail with
the message "An error occurred in stage 1 of the boot process."

The cause was new functionality in new kernel modules which was required
for the USB ports to work. These modules were made available in the
initrd so the system can mount the USB flash drive and continue booting.

The fix has been verified on a MacBook Pro M1 Max 16".

## 2022-11-24

This release updates to the latest Asahi kernel and other stuff. Currently only
the non-edge config is supported.

Sound is not yet fully supported. Work remains to integrate the ALSA UCM
configurations into NixOS. This will be addressed in the future.

The 4K patch no longer applies so this kernel only operates in 16K mode for now.
This is not planned to be addressed. PRs are welcome for an updated patch.

Due to a change in the device trees, booting old kernels with the latest trees,
i.e. switching to an older generation using the bootloader, may leave you with
broken USB support. Once booted into the generation, you can run
`/run/current-system/bin/switch-to-configuration switch` then reboot to force
the bootloader and the correct version of U-Boot/m1n1/the device trees to be
reinstalled and loaded.

The edge config and a prototype of the GPU driver will be addressed in the
future.

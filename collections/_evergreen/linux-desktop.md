---
layout: evergreen
title: Linux Desktop
mathjax: false
description: |
   Linux distributions are commonly recommended for privacy protection and user freedom. Below are some suggestions with some general privacy and security improvements.
---

## Traditional distributions

{% for item_hash in site.data.operating-systems.linux-desktop %}
{% assign item = item_hash[1] %}

{% if item.type == "Recommendation" %}
{% include recommendation-card.html %}
{% endif %}

{% endfor %}

## Immutable distributions

{% for item_hash in site.data.operating-systems.linux-desktop-immutable %}
{% assign item = item_hash[1] %}

{% if item.type == "Recommendation" %}
{% include recommendation-card.html %}
{% endif %}

{% endfor %}

## Anonimity focused distributions

{% for item_hash in site.data.operating-systems.linux-desktop-tor %}
{% assign item = item_hash[1] %}

{% if item.type == "Recommendation" %}
{% include recommendation-card.html %}
{% endif %}

{% endfor %}

## Open Source

It is often believed that [open source](https://en.wikipedia.org/wiki/Open-source_software) software is inherently secure because there is the expectation that verification occurs regularly. In reality it does depend on a number of factors, such as project activity, developer experience, level of rigour applied to [code reviews](https://en.wikipedia.org/wiki/Code_review) and how often attention is given to specific parts of the [codebase](https://en.wikipedia.org/wiki/Codebase) that may go untouched for years. We prefer open source software because it does present the possibility of further scrutiny although we really place value in comprehensive [audits](https://en.wikipedia.org/wiki/Information_security_audit#Auditing_application_security), particularly where security sensitive code exists such as in products that involve cryptography.

## Why use Linux?

There are pros and cons to using Linux. Most of the team *does* use it within their daily lives. We do however recognize that there are sometimes shortcomings. Below we describe some of them:

Pros:

 * Avoid telemetry that often comes with proprietary operating systems
 * Maintain [software freedom](https://www.gnu.org/philosophy/free-sw.en.html#four-freedoms)
 * Flexibility for purpose built uses such as [Whonix](https://www.whonix.org) or [Tails](https://tails.boum.org/)
 * Use of [OS-level virtualization](https://en.wikipedia.org/wiki/OS-level_virtualization)

Cons:

 * Doesn't have strong chain of trust in the boot process. Unlike [Windows](https://docs.microsoft.com/en-us/windows/security/information-protection/secure-the-windows-10-boot-process) (with [TPM](https://docs.microsoft.com/en-us/windows/security/information-protection/tpm/how-windows-uses-the-tpm)), Apple's [T2 Security Chip](https://support.apple.com/guide/security/startup-security-utility-secc7b34e5b5/web) (with [Secure Enclave](https://support.apple.com/guide/security/secure-enclave-sec59b0b31ff/1/web/1)) or Android's [Verified Boot](https://source.android.com/security/verifiedboot). These features and hardware technologies can all all help prevent persistant tampering by malware.
 * Doesn't have strong sandboxing such as that found in [Windows](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-sandbox/windows-sandbox-overview), [MacOS](https://developer.apple.com/library/archive/documentation/Security/Conceptual/AppSandboxDesignGuide/AboutAppSandbox/AboutAppSandbox.html), [Android](https://source.android.com/security/app-sandbox). Strengthening sandboxing, in both [Flatpak](https://docs.flatpak.org/en/latest/sandbox-permissions.html) and [Snap](https://snapcraft.io/docs/security-sandboxing) still has a way to go.
 * Strong [exploit mitigations](https://madaidans-insecurities.github.io/linux.html#exploit-mitigations), enabled by default.

## Choosing your distribution

##### Release cycle
We highly recommend that you choose a distributions which stay close to upstream like Fedora, openSUSE Tumbleweed, or Arch. Avoid distributions with frozen packages, as they are often quite behind on security updates.

For example, Debian famously fell behind on Firefox-ESR updates for [2 months](https://tracker.debian.org/pkg/firefox-esr), in one of which their version (78) was deemed end of life by Mozilla. Notably, Debian [only](https://www.debian.org/security/faq#handling) backports security fixes that have recieved a [CVE](https://en.wikipedia.org/wiki/Common_Vulnerabilities_and_Exposures). A lot of security fixes [do not](https://arxiv.org/abs/2105.14565) recieve a CVE at all, and do not make it to an LTS distribution with this patching model. Sometimes, minor security fixes are also held back until the next release of Debian.

Fundamentally, holding packages back and applying a bunch of backports just does not work that well. [Richard Brown](https://rootco.de) has a great presentation about this:

<iframe
  width="731" height="411"
  src="https://www.youtube.com/embed/i8c0mg_mS7U"
  title="YouTube video player"
  frameborder="0"
  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
  allowfullscreen>
</iframe>

##### Distributions with atomic/transactional updates
If you are not comfortable with fast moving distributions, consider using one with an atomic or transactional update system.

On a system with atomic update, and update is either applied fully or completely diregarded. An update cannot suddenly fail and be applied half way through. Typically, a system with atomic update will provide an easy way to roll the system back to a previous state should a bug occur after an update as well.

On a system with transactional update, a system snapshot is made right before and after an update is applied. If an update fail half way through, or if you encouter some bugs after the update, rolling back is very easy as well.

[Adam Samalik](https://blog.samalik.com/) has a great demonstration of how rpm-ostree and atomic updates work:

<iframe
  width="731" height="411"
  src="https://www.youtube.com/embed/-hpV5l-gJnQ"
  title="YouTube video player"
  frameborder="0"
  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
  allowfullscreen>
</iframe>

With these distributions, you essentially can have your cake and eat it too. You can update fast, stay close to upstream and get most of the security fixes, and simply rollback and wait out whenever something goes wrong.

##### "Security-focused" distributions
Unfortunately, a quick search for "the most secure Linux distribution" will often give results like Kali Linux, Black Arch, Parrot OS. These distributions penetration testing distributions - they are meant to be used as an attacker machine, not as a tool to protect the user. Avoid using these distributions as your daily driver.

##### Arch-based distributions

Arch based systems are not recommended for new users, regardless of the distribution. Arch does not have an update mechanism for the software stack using pacman, and the user is expected to maintain their own system and swapping out components of the stack when they become obsolete.

The user is also expected to have sufficient Linux knowledge to properly set up security for their system such as enabling a mandatory access control system, doing firewalling, setting up kernel module blacklists, hardening boot parameters and sysctl, and so on. Simply getting the system installed is not enough.

For advanced users, we only recommend Arch Linux, not any of its derivatives. In fact, 2 very popular Arch derivatives are not so great:

  * Manjaro: They hold packages back for 2 weeks to make sure that their own changes don't break, not to make sure that upstream is stable. AUR packages on the other hand often expect the latest and greatest packages on Arch's own repository, which sometimes lead to dependency mismatch.
  * Garuda: They use [Chaotic-AUR](https://aur.chaotic.cx/) which automatically and blindly compiles packages from the AUR. There is no verification process to make sure that the AUR packages themselve don't turn malicious.

##### Linux-libre kernel and "Libre" distributions
We strongly recommend **against** using the Linux-libre kernel, since it [removes security mitigations](https://www.phoronix.com/scan.php?page=news_item&px=GNU-Linux-Libre-5.7-Released) and [surpresses kernel warnings about vulnerable microcode](https://news.ycombinator.com/item?id=29674846) for ideological reasons.

We also recommend **against** using "Libre" distributions that utilize the Linux-libre kernel or follow a similar philosophy (not shipping updated firmware with security fixes because they are proprietary) like GUIX.

## Things to consider when installing your Linux distribution

##### Drive Encryption
Unlike Bitlocker on Windows and FileVault on macOS, LUKS encryption on Linux is very problematic to set up after a system has been installed. We recommend that you enable drive encryption during the installation process of any Linux distributions.

##### Swap
Consider using [ZRAM](https://wiki.archlinux.org/title/Swap#zram-generator) or [encrypted SWAP](https://wiki.archlinux.org/title/Dm-crypt/Swap_encryption) instead of unencrypted swap to avoid potential security issues with sensitive data being pushed to swap space.

On Fedora, ZRAM is configured out of the box.

##### Desktop environment/Window managers
Along with your choice of a distribution, your choice of a desktop environment or window manager is integral to your Linux experience. However, there are a few things you should consider in regards to security and privacy.

On Linux, the Xorg display server is extremely problematic. It was never designed with access control in mind, and all xorg windows can access all of the other xorg windows. Effectively, this allows any app to keylog and record the user's screen without any permission.

Nested X11 solutions like Xpra and Xephr can sandbox Xorg windows, but they come with a great performance cost and a lot of inconveniences.

[Wayland](https://wayland.freedesktop.org/) solves this problem by isolating each window and requring apps to request permission for screen recording. Thus, we recommend using desktop environments/window managers that works with Wayland. As of now, the list of desktop environments/window managers that support Wayland includes [GNOME](https://www.gnome.org), [KDE](https://kde.org), and [Sway](https://swaywm.org).

##### Proprietary firmware/microcode updates
On libre or DIY distributions, the proprietary microcode update often does not come installed by default. We **highly recommend** that you install the microcode updates, as your CPU is already running the proprietary microcode anyways. Your choices boil down to using an outdated microcode with known security vulnerabilities or an updated one with the fixes for those vulnerabilities, and there is no reason to choose the former.

If you are using Fedora or openSUSE, you do not have to worry about installing the microcode updates, as they are already installed by default.

## Privacy tweaks

##### Mac address randomization

If you are using Network Manager (the default on Fedora, openSUSE, etc), follow [this guide](https://fedoramagazine.org/randomize-mac-address-nm/) on how to enable randomized mac addresses. We recommend changing the setting to `random` as opposed to `stable` like in the article.

If you are using systemd-networkd, Wicked or another network managing solution, refer to the projects' own documentations on how to set this up.

##### Other identifiers

Consider following section [10.1](https://madaidans-insecurities.github.io/guides/linux-hardening.html#hostnames), [10.2](https://madaidans-insecurities.github.io/guides/linux-hardening.html#timezones-locales-keymaps), and [10.3](https://madaidans-insecurities.github.io/guides/linux-hardening.html#machine-id) on Madaidan's [hardening guide](https://madaians-insecurities.github.io/guides/linux-hardening.html#identifiers).

##### System counting

Fedora has fairly interesting [mechanism](https://fedoraproject.org/wiki/Changes/DNF_Better_Counting) which does not involve using unique ids to count its users. According to man pages, it appears to be off by default for DNF based systems right now. However, if you are uncomfortable with this, we recommend adding `countme=false` to `/etc/dnf/dnf.conf` just in case it is enabld in the future. On rpm-ostree based systems, follow [this guide](https://fedoramagazine.org/getting-better-at-counting-rpm-ostree-based-systems/) to disable system counting.

openSUSE uses a unique ID system to track the number of installations by default. Consider following [this guide](https://en.opensuse.org/openSUSE:Statistics) to opt out.

## Application confinement

##### Sandboxing
On Linux, app sandboxing and access control are extremely lacking compared to macOS and ChromeOS. User applications installed via traditional package managers typically have no confinement whatsoever. We will discuss a few common sandboxing methods below:

###### **1. Flatpak**
[Flatpak](https://flatpak.org/) first and foremost is a universal package manager for Linux. It's primary function so to be a package format which can be used in most Linux distributions. However, it does come with the benefit of giving the user some form of permission control.

It should be noted that Flatpak's sandbox is quite weak laid out in [this article](https://madaidans-insecurities.github.io/linux.html#flatpak).

The problem with Flatpak's laxed high level permissions could be mitigated by using an application called [Flatseal](https://flathub.org/apps/details/com.github.tchx84.Flatseal). Consider revoking the access to the network socket (internet access), the pulse audio socket (for both audio in and out), `device=all` (access to all devices including the camera), `org.freedesktop.secrets` dbus (access to secrets stored on your keychain) for applications which do not need it. If an application works natively with Wayland (and not running through the XWayland compatibility layer), consider revoking their access to he X11 socket as well. Broad filesystem permissions such as `filesystem=home` and `filesystem=host` should be revoked and replaced with just the directories the app should be allowed to access. Some sample overrides can be founded [here](https://github.com/tommytran732/Flatpak-Overrides).

However, problems like hard-coded access to some kernel interfaces like `/sys` and `/proc` and a weak seccomp filter still remain and cannot be solved by user.

###### **2. Firejail**

Firejail is another common sandboxing technique. It is, however, a giant SUID binary and has a large attack surface. In short, Firejail makes the system safer from processes that are confined by it, but less safe from processes running outside of it. In general, the usage of Firejail is not recommended. More information on this can be found in Madaidan's [article](https://madaidans-insecurities.github.io/linux.html#firejail).

##### gVisor
Most container based solutions are not the ideal approach for app sandboxing, as they typically share the same kernel as the host for performance reasons. Vulnerabilities in the host's kernel could leak to container breakouts and sandbox bypasses. 

If you are using Docker, it is highly recommended that you use the [gVisor](https://gvisor.dev) runtime which implements a pseudo kernel for each application container and limit their direct access to the host's kernel.

##### Mandatory Access Control
Mandatory access control systems on Linux Desktop are largely ineffective policies/profiles, however, it is still worth it to keep them enabled.

On Fedora, SELinux comes preconfigured with targetted policies and will confine system daemons out of the box. We recommend that you never turn off SELinux or put it into permissive mode on Fedora.

On openSUSE, the user has a choice of AppArmor or SELinux during the installation process. We recommend sticking to the default for each variant (AppArmor for Tumbleweed and SELinux for MicroOS). openSUSE's SELinux policies are derived from those from Fedora.

Arch and Arch-based operating systems often do not come with a mandatory access control system out of the box. We highly recommend that you follow the [Arch Wiki](https://wiki.archlinux.org/title/AppArmor) to set up AppArmor.

##### Making your own policies/profiles
For advanced users, you can make your own AppArmor profiles, SELinux policies, Bubblewrap profiles, Seccomp blacklist to have better confinement of applications. This is quite a tedious and complicated task so we won't go into detail of how to do it here, but we do have a few projects that you could use as reference.

 * Whonix's [AppArmor Everything](https://github.com/Whonix/apparmor-profile-everything)
 * Krathalan's [AppArmor Profiles](https://github.com/krathalan/apparmor-profiles)
 * noatsecure's [SELinux templates](https://github.com/noatsecure/hardhat-selinux-templates)

## Additional Hardening

##### Firewalls
You should have an inbound Firewall to block connections to your computer at all times. Considering Red Hat's [documentation](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/configuring_and_managing_networking/using-and-configuring-firewalld_configuring-and-managing-networking) on how to setup Firewalld or Ubuntu's [documentation](https://help.ubuntu.com/community/UFW) on how to setup UFW.

Fedora comes with Firewalld by default, however, their rules are very permissive by default. Consider closing port 1000-65535 with both TCP and UDP after the operating system installation. You should also remove the whitelist for `smb-client` and `mdns` services if you do not use them.

For unconfined applications, solutions like [OpenSnitch](https://github.com/evilsocket/opensnitch) and [Portmaster](https://safing.io/portmaster/) may help.

Keep in mind that you are still assuming that none of your apps are malicious, because these Firewalls are based on IPTables/Nftables and a malicious app can simply add its own IPTables/Nftables rule higher up in the chain to bypass it.

If you are using Flatpak packages, you can revoke their network socket access using Flatseal and prevent them from accessing your network. This permission is not bypassable.

If you are using non-classic Snap packages on a system with proper snap confinement support (with both AppArmor and CGroupsv1 present), you can use the Snap Store to revoke network permission as well. This is also not bypassable.

##### Kernel hardening
Consider following section [2.2](https://madaidans-insecurities.github.io/guides/linux-hardening.html#sysctl), [2.3](https://madaidans-insecurities.github.io/guides/linux-hardening.html#boot-parameters) and [2.5](https://madaidans-insecurities.github.io/guides/linux-hardening.html#kernel-attack-surface-reduction) on Madaidan's [hardening guide](https://madaians-insecurities.github.io/guides/linux-hardening.html#identifiers) for sysctl and boot parameters hardening and kernel attack surface reduction.

Note that setting `kernel.unprivileged_userns_clone=0` will stop Flatpak, Podman, Docker, LXC containers from working. Do not set this flag if you are using those technologies.

##### Disabling SMT
SMT has been the cause of numerous hardware vulnerabilities, and subsequent patches for those vulnerabilities often come with performance penalties that negate most of the performance gain given by SMT. If you followed the "kernel hardening" section above, some kernel parameters already disables SMT. However, if you are not following it, or if the option is available to you, we recommend that you disable it in your firmware as well.

##### Linux-Hardened
Certain distributions like Arch Linux comes with linux-hardended, a kernel package with hardening patches and more security concious defaults.

Linux-Hardened comes with `kernel.unprivileged_userns_clone=0` by default. If you are using Flatpak, Podman, Docker, LXC containers or other technologies that relies on unpriviledged user namespaces, consider setting `kernel.unprivileged_userns_clone=1`.

##### GRSecurity
GRSecurity is a set of kernel patches that substantially increase security in the Linux kernel. Unfortunately, it went closed in 2017. If you have access to the latest GRSecurity patches, it is highly recommended that you use them.

##### Hardened memory allocator
The [hardened memory allocator](https://github.com/GrapheneOS/hardened_malloc) from [GrapheneOS](https://grapheneos.org) can be used on Linux distributions. It is available by default on Whonix and is available as an [AUR package](https://wiki.archlinux.org/title/Security#Hardened_malloc) on Arch based distributions. If you are using the AUR package, consider setting up `LD_PRELOAD` as described in the [Arch Wiki](https://wiki.archlinux.org/title/Security#Hardened_malloc).

##### Umask
If you are not using openSUSE, consider changing the default umask for both regular users and root to 077.

Changing umask to 077 tends to break snapper on openSUSE and is not recommended.

##### Mountpoint hardening
Consider adding `nodev`, `noexec`, `nosuid` to mountpoints which do not need them. Typically, these could be applied to `/boot`, `/boot/efi`, `/home`, `/root`, `/var`.

If you use [Toolbox](https://docs.fedoraproject.org/en-US/fedora-silverblue/toolbox/), `/var/log/journal` must not have any of those options.

If you are on Arch Linux, do not apply `noexec` to `/var/tmp`.

##### PAM
Consider following section [14](https://madaidans-insecurities.github.io/guides/linux-hardening.html#pam) on [Madaidan's hardening guide](https://madaidans-insecurities.github.io/guides/linux-hardening.html#pam).

On systems where pam_faillock is not available, consider using [pam_tally2](https://access.redhat.com/solutions/37687) instead.

##### USBGuard
Consider following the [Arch Wiki](https://wiki.archlinux.org/title/USBGuard) to set up USBGuard.

##### Secure Boot
Consider following section [21](https://madaidans-insecurities.github.io/guides/linux-hardening.html#physical-security) on Madaidan's [hardening guide](https://madaians-insecurities.github.io/guides/linux-hardening.html#identifiers).

By default, UEFI secure boot on Linux distributions is rather in effective. Besides the problems mentioned in Madaidan's guide as only the chainloader (shim), the boot loader (GRUB), and the kernel are verified. The initramfs is often left unverified, unencrypted, and open up the window for an [evil maid](https://en.wikipedia.org/wiki/Evil_maid_attack) attack.

This problem could be reduced by either [combinding the kernel, initramfs, and microcode](https://wiki.archlinux.org/title/Unified_Extensible_Firmware_Interface/Secure_Boot) into a signed EFI stub or by encrypting the `/boot` partition. If you are using openSUSE, your `/boot` partition should be encrypted by default should you enable drive encrytion.

A guide for converting a normal /boot partition into an encrypted one on Fedora Workstation (not Silverblue!) can be founded [here](https://mutschler.eu/linux/install-guides/fedora-btrfs-33/).

After setting up Secure Boot, set a password on your firmware to prevent an adversary from just opening it and disabling Secure Boot.

Note that these recommendations can only make you a bit more resistant against evil maid attacks, but they cannot compete with proper verified boot like on Android, ChromeOS, or macOS as there is no root filesystem verification to prevent persistent tampering by malware.

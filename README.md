# ultimate-overlay
Gentoo-Overlay for Ultimate Program Analysis Tools 

## Adding the overlay to Gentoo
Gentoo allows the user to add unofficial repositories from where Portage may install packages. Those unofficial repositories are called [Overlays](https://wiki.gentoo.org/wiki/Overlay).

There are two possibilities to add a new Overlay to the system, with [Layman](https://wiki.gentoo.org/wiki/Layman) or as a Local Overlay. Both ways work, but we recommend the Layman way.

### Layman

You will first have to install Layman if it is not already installed. Layman is an overlay manager that allows Portage to pull in packages from various different Overlays.

You can install Layman by issuing the following command:
```
emerge --ask app-portage/layman
```

Afterwards, you can add the Ultimate Overlay with
```
layman -o https://raw.github.com/ultimate-pa/ultimate-overlay/master/repositories.xml -f -a ultimate
```

### Local Overlay

Alternatively, you can add a [local Overlay](https://wiki.gentoo.org/wolo/Overlay/Local_overlay) which allows you to circumvent the need to use Layman.

You need, however, a Portage version of at least `2.2.14` to use local Overlays.

If not already existing, create the directory `/etc/portage/repos.conf/`.

Then, add a file `/etc/portage/repos.conf/ultimate-overlay.conf` with the following contents:

```
[ultimate]
location = /usr/local/ultimate-overlay
sync-type = git
sync-uri = https://github.com/ultimate-pa/ultimate-overlay.git
priority=9999
```

### Syncing

You now may run `emerge --sync` and should be able to see and emerge all packages provided by the Ultimate Overlay.

## Installation

After adding the Ultimate Overlay, you should be able to install Ultimate, by running the command
```
emerge --ask sci-mathematics/ultimate
```

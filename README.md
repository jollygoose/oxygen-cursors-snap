Snap of the Oxygen cursor themes (from both the oxygen-cursor-theme and oxygen-cursor-theme-extra packages) originally created for KDE 4.



---

## Attributions  

All credit goes to the original cursor developers of the KDE project and the package maintainers at Kubuntu.  

## Building the snap locally

Requirements
* snapcraft (```snap install snapcraft```)
* multipass (```snap install multipass```)

```sh
git clone https://github.com/jollygoose/oxygen-cursors-snap
cd oxygen-cursors-snap

snapcraft

# where CURRENT is the latest version of flat-remix-gtk
# and --dangerous since this local snap hasn't been verified
snap install oxygen-cursors-snap_CURRENT_all.snap --dangerous
```

## Applying the theme

In order to work, the snap package needs to have a '[plug](https://ubuntu.com/blog/a-guide-to-snap-permissions-and-interfaces)' 
available for 'icon-themes'.

To apply the theme to a single application, perform the following:

    sudo snap connect [snap-you-want-to-theme]:icon-themes oxygen-cursors:icon-themes

To apply to all applications run the following command. Thanks to @flexiondotorg for the handy loop.

    for plug in $(snap connections | grep gtk-common-themes:icon-themes | awk '{print $2}'); do sudo snap connect ${plug} oxygen-cursors:icon-themes; done

*NOTE*: Some apps like the Ubuntu Snap Store may require logging out, and back in to load the changes.
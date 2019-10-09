# Aerial theme for SDDM

SDDM theme with Apple TV Aerial videos

Videos are played randomly and diferent playlists are used based on time of day (only day and night diferenciation, night between 5pm - 5am) its possible to tweak to have more time diferentiation, the one used is provided with the videos.


### Dependencies

It is necessary to have the Phonon GStreamer backend for qt5, GStreamer ffmpeg Plugin and GStreamer Plugins Good
- For Arch linux : `pacman -S gst-libav phonon-qt5-gstreamer gst-plugins-good qt5-quickcontrols qt5-graphicaleffects qt5-multimedia`
- For Gentoo : these settings allowed me to make the theme work

    * `media-libs/gst-plugins-good`
    * `USE="alsa gsteamer qml widgets" dev-qt/qtmultimedia`
    * `USE="gstreamer" media-libs/phonon`

Havent tryed for other distros...

### Installation

Simply clone the repository and copy it to `/usr/share/sddm/themes/` like this:
```
git clone git@github.com:3ximus/aerial-sddm-theme.git
mv aerial-sddm-theme /usr/share/sddm/themes
```
*Note that super user priviledges are needed to move files into that directory.*

The theme can be tested by running `sddm-greeter --test-mode --theme <path-to-this-repository>`

### Other notes

This theme streams the HD videos so a good internet connection is necessary.
If there is no active connection or the video can't be played the background will fallback to the image background.jpg

If you wish to play local videos files just use the following command to generate the playlist-file (playlist_day.m3u or playlist_night.m3u) from a directory containing the videos:

`find <path-to-your-directory> -maxdepth 1 -type f > <playlist-file>`

If you would like to use the same videos but offline, simply download them using your shell, e.g. :

```
while read -r link; do
    wget "$link"
done < playlist_file
```

### Changing settings in `theme.conf.user`

You can change a few settings in this file
- `displayFont` - Font name
- `background` - Fallback background image
- `backgroundPlaylistDay` and `backgroundPlaylistNight` - Path of .m3u playlist file to play at day and night
- `showLoginButton` - If true shows the login button
- `showClearPasswordButton` - If true shows the clear password button
- `showTopBar` - if set to false will hide the wm/keyboard top bar
- `relativePositionX` and `relativePositionY` - Set the position of the login text box and clock


Default config

```
[General]
displayFont="Droid Sans Mono for Powerline"

background=assets/fallback.jpg
backgroundPlaylistDay=playlists/day.m3u
backgroundPlaylistNight=playlists/night.m3u

showLoginButton=false
showClearPasswordButton=false
showTopBar=true

relativePositionX=0.5
relativePositionY=0.75
```


## License

Theme is licensed under GPL.

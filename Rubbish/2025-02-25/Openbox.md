## [[Linux]] [[Arch]] [[compress and extract]] [[Openbox]]

install XFCE DE

sudo pacman -S --needed xorg-xrandr

openbox 
obconf lxappearance-obconf 
menumaker 
tint2
ttf-dejavu ttf-liberation 
xterm xfce4-terminal 

=====================
obmenu
lxappearance
jgmenu
rofi
rofi theme selector
Polybar - panel like tint2
=====================
openbox, then a display manager

lxappearance
lxappearance-obconf 
obmenu-generator (params: -u -p -c -i)-
nitrogent (for background)
Picom (compositor)
Plank (ctrl + right click -> preference)
tint2  (panel for task manager)

Any themes or icon packs


===================
openbox autostart

/usr/lib/mate-polkit/polkit-mate-authentication-agent-1 &
xrandr -s 1920x1080 &
tint2 &
picom &
plank &
nitrogen --restore &
volumeicon &
alacritty -e fish
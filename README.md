# my arch hyprland journey

*Arch Linux + Hyprland as absolute beginner*

# ARCH LINUX
dual boot win11 & arch
![arch-i-use-arch-btw](https://github.com/user-attachments/assets/07acf7b1-9322-46cd-b3a0-d51dd0859532)
## arch install
followed this [Youtube guide](https://youtu.be/1J_Z_pzzbMo?si=h1Wee8-VfmtQVQAS). to install arch linux
##helpful things in tty
<pre>
setfont -d         #if the scale is too small
sudo loadkeys fr   #to change keyboard layout from en to fr in my case
</pre>
## fix mirrorlist
i fixed mirrorlist (outdated or broken)
<pre> sudo pacman -Sy reflector </pre>
<pre>sudo reflector --country France,Germany,Netherlands --latest 10 --protocol https --sort rate --save /etc/pacman.d/mirrorlist
</pre>
replace those countries by your actual country or countries near to your place 
<pre>sudo pacman -Syy</pre>
and then i was able to install hyprland and kitty,
# HYPRLAND
![hyprland-logo](https://github.com/user-attachments/assets/b5398999-a178-49e7-b2eb-0b17f8b0cb88) 
 ## hyprland env
 although i was able to install hyrland and kitty after fixing mirrorlist, hyprland opened broken, kitty doesnt open , fonts not showing, i fixed this by installing
 xdg-desktop-portal xdg-desktop-portal-hyprland 
<pre>pacman -S hyprland kitty firefox xdg-desktop-portal xdg-desktop-portal-hyprland 
</pre>

## Volume keybindings 
1 - i installed wireplumber pavucontrol playerctl pamixer
<pre>yay -S wireplumber pavucontrol playerctl pamixer </pre>

2 - Run wev with <pre> -S wev </pre>) and press your volume keys to see if they register
if they are not, we need to run <pre> yay -S evtest </pre> and search for "extra"" or "volume" to check they in the kernel,
3 - once done checking go for next step ..

4 - added this to **~/.config/hypr/hyprland.conf** 

<pre># Volume controls
bind = , XF86AudioRaiseVolume, exec, wpctl set-volume @DEFAULT_AUDIO_SINK@ 5%+
bind = , XF86AudioLowerVolume, exec, wpctl set-volume @DEFAULT_AUDIO_SINK@ 5%-
bind = , XF86AudioMute, exec, wpctl set-mute @DEFAULT_AUDIO_SINK@ toggle</pre>

<pre>bind = , XF86AudioRaiseVolume, exec, pactl set-sink-volume @DEFAULT_SINK@ +5%
bind = , XF86AudioLowerVolume, exec, pactl set-sink-volume @DEFAULT_SINK@ -5%
bind = , XF86AudioMute, exec, pactl set-sink-mute @DEFAULT_SINK@ toggle</pre>

<pre>bind = , XF86AudioRaiseVolume, exec, pamixer -i 5
bind = , XF86AudioLowerVolume, exec, pamixer -d 5
bind = , XF86AudioMute, exec, pamixer -t</pre>

5 - make sure these are installed <pre> yay -S pipewire pipewire-pulse wireplumber </pre>

6 - last thing Re-enable : pipewire pipewire-pulse  wireplumber

<pre>systemctl --user enable --now pipewire pipewire-pulse wireplumber
</pre>

<pre>systemctl --user disable --now pipewire pipewire-pulse wireplumber
</pre>

<pre>systemctl --user status pipewire pipewire-pulse wireplumber
</pre>

!you have to reboot after this!












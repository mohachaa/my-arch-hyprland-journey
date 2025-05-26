# my arch hyprland journey

*Arch Linux + Hyprland as absolute beginner*

# ARCH LINUX
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
 although i was able to install hyrland and kitty after fixing mirrorlist, hyprland opened broken, kitty doesnt open , fonts not showing, i fixed this by installing
 xdg-desktop-portal xdg-desktop-portal-hyprland 
<pre>pacman -S hyprland kitty firefox xdg-desktop-portal xdg-desktop-portal-hyprland 
</pre>
















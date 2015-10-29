### Archlinux Conky Configure ###

#### Conky Setting ##

* .public_ip 获取ip脚本
* .public_location 获取ip地理位置信息
* .conkyrc conky程序配置文件

#### 配置信息[archilinux 社区复制过来的稍微修改使用] ####
<pre>

######################
# - Conky settings - #
######################
background yes  # 嵌入到桌面中
update_interval 2  # 2s更新
total_run_times 0
net_avg_samples 1
cpu_avg_samples 2

imlib_cache_size 0
double_buffer yes
no_buffers yes
format_human_readable

#####################
# - Text settings - #
#####################
use_xft yes
xftfont Droid Sans:size=8
override_utf8_locale yes
text_buffer_size 2048

#############################
# - Window specifications - #
#############################
own_window_class Conky
own_window yes  # 桌面显示
own_window_type override # 当按win + D 也不消失, 一直在桌面
own_window_argb_value 150
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
#own_window_argb_visual yes
own_window_transparent yes

alignment top_right  # 位置 top_left则显示在左边
gap_y 6 # 距离屏幕纵方向
gap_x 10 # 距离屏幕横方向
border_inner_margin 8

minimum_size 180 500
maximum_width 180
maximum_height 560

default_bar_size 92 6

#########################
# - Graphics settings - #
#########################
draw_shades yes
default_shade_color 000000
default_color FFFFFF

TEXT  # 显示部分
${font Droid Sans:style=Bold:size=8}SYSTEM $stippled_hr${font}
##############
# - SYSTEM - #
##############
${voffset 6}${font OpenLogos:size=19}B${font}${goto 40}${voffset -15}Kernel:  ${alignr}${kernel}
${goto 40}Uptime: ${alignr}${uptime}
# |--UPDATES
${goto 40}Updates: ${alignr}${font Droid Sans:style=Bold:size=8}${execi 10800 pacman -Qu | wc -l}${font} Packages
# |--CPU
${voffset 6}${font Droid Sans:style=Bold:size=8}CPU${font}${offset -20}${voffset 10}${cpubar cpu0 4,18}
${voffset -23}${goto 40}Core 1: ${font Droid Sans:style=Bold:size=8}${cpu cpu1}%${font} ${alignr}${cpubar cpu1 7,70 EEEEEE}
${voffset 1}${goto 40}Core 2: ${font Droid Sans:style=Bold:size=8}${cpu cpu2}%${font} ${alignr}${cpubar cpu2 7,70 EEEEEE}
${voffset 1}${goto 40}Core 3: ${font Droid Sans:style=Bold:size=8}${cpu cpu3}%${font} ${alignr}${cpubar cpu3 7,70 EEEEEE}
${voffset 1}${goto 40}Core 4: ${font Droid Sans:style=Bold:size=8}${cpu cpu4}%${font} ${alignr}${cpubar cpu4 7,70 EEEEEE}
# |--MEM
${voffset 6}${font Droid Sans:style=Bold:size=8}RAM${font}${goto 40}RAM: ${font Droid Sans:style=Bold:size=8}$memperc%${font}
${voffset 6}${offset 1}${voffset -8}${membar 4,18}${voffset 4}${goto 40}${voffset -2}Free: ${font Droid Sans:style=Bold:size=8}${memeasyfree}${font} ${goto 110}Used: ${font Droid Sans:style=Bold:size=8}${mem}${font}
# |--SWAP
${voffset 5}${font Droid Sans:style=Bold:size=8}SWP${font}${goto 40}Swap: ${font Droid Sans:style=Bold:size=8}${swapperc}%${font}
${voffset 4}${offset 1}${voffset -7}${swapbar 4,18}${voffset 4}${goto 40}Free: ${font Droid Sans:style=Bold:size=8}$swapmax${font} ${goto 110}Used: ${font Droid Sans:style=Bold:size=8}$swap${font}
# |--PROC
${voffset 4}${font Droid Sans:style=Bold:size=8}TOP${font}${voffset 0}${goto 126}CPU${alignr}RAM
${voffset -1}${goto 40}${top name 1}${font Droid Sans:style=Bold:size=8} ${goto 120}${top cpu 1}${alignr }${top mem 1}${font}
${voffset -1}${goto 40}${top name 2}${font Droid Sans:style=Bold:size=8} ${goto 120}${top cpu 2}${alignr }${top mem 2}${font}
${voffset -1}${goto 40}${top name 3}${font Droid Sans:style=Bold:size=8} ${goto 120}${top cpu 3}${alignr }${top mem 3}${font}
${voffset -1}${goto 40}${top name 4}${font Droid Sans:style=Bold:size=8} ${goto 120}${top cpu 4}${alignr }${top mem 4}${font}
${voffset -1}${goto 40}${top name 5}${font Droid Sans:style=Bold:size=8} ${goto 120}${top cpu 5}${alignr }${top mem 5}${font}
${voffset -1}${goto 40}${top name 6}${font Droid Sans:style=Bold:size=8} ${goto 120}${top cpu 6}${alignr }${top mem 6}${font}
${voffset -1}${goto 40}${top name 7}${font Droid Sans:style=Bold:size=8} ${goto 120}${top cpu 7}${alignr }${top mem 7}${font}
${voffset -1}${goto 40}${top name 8}${font Droid Sans:style=Bold:size=8} ${goto 120}${top cpu 8}${alignr }${top mem 8}${font}
${voffset -1}${goto 40}${top name 9}${font Droid Sans:style=Bold:size=8} ${goto 120}${top cpu 9}${alignr }${top mem 9}${font}
${voffset -1}${goto 40}${top name 10}${font Droid Sans:style=Bold:size=8} ${goto 120}${top cpu 10}${alignr }${top mem 10}${font}
#############
# - CLOCK - #
#############
${voffset 6}${font Droid Sans:style=Bold:size=8}DATE $stippled_hr${font}
${font Droid Sans:size=20}${alignc}${time %H:%M}${font}
${alignc}${time %d %B %Y}
###############
# - NETWORK - #
###############
${voffset 4}${font Droid Sans:style=Bold:size=8}NETWORK $stippled_hr${font}
${voffset 4}${goto 20}Upload: ${font Droid Sans:style=Bold:size=8}${upspeed enp1s0}${font} ${alignr}${upspeedgraph enp1s0 8,50 EEEEEE}
${goto 20}Overall: ${font Droid Sans:style=Bold:size=8}${totalup eth0}${font}
${voffset 4}${goto 20}Download: ${font Droid Sans:style=Bold:size=8}${downspeed enp1s0}${font} ${alignr}${downspeedgraph enp1s0 8,50 EEEEEE}
${goto 20}Overall: ${font Droid Sans:style=Bold:size=8}${totaldown enp1s0}${font}
${voffset 4}${goto 20}Local IP: ${alignr}${font Droid Sans:style=Bold:size=8}${addr enp1s0}${font}
${goto 20}Public IP: ${alignr}${font Droid Sans:style=Bold:size=8}${execi 10800 ~/.public_ip}${font}  # 获取ip
${goto 20}IP Location: ${alignr}${font Droid Sans:style=Bold:size=8}${execi 10800 ~/.public_location}${font} # 获取地理位置信息
##########
# - HD - #
##########
${voffset 4}${font Droid Sans:style=Bold:size=8}HD $stippled_hr${font}
# |--HD default
  ${voffset 4}${goto 20}Root: ${font Droid Sans:style=Bold:size=8}${fs_used_perc /}%${font}${goto 100}${alignr}${fs_bar 6,68 /}
  ${offset 7}Free: ${font Droid Sans:style=Bold:size=8}${fs_free /}${font} ${alignr 1}Used: ${font Droid Sans:style=Bold:size=8}${fs_used /}${font}
  ${voffset 4}${goto 20}Home: ${font Droid Sans:style=Bold:size=8}${fs_used_perc /home}%${font}${goto 100}${alignr}${fs_bar 6,68 /home}
  ${offset 7}Free: ${font Droid Sans:style=Bold:size=8}${fs_free /home}${font} ${alignr 1}Used: ${font Droid Sans:style=Bold:size=8}${fs_used /home}${font}
# |--HDTEMP1
  ${voffset 7}${goto 20}${voffset -4}Temperature: ${font Droid Sans:style=Bold:size=8}${execi 120 echo 'luowen' | sudo -S hddtemp /dev/sda -n --unit=C}°C${font}${alignr}/dev/sda  # 获取硬盘温度


</pre>

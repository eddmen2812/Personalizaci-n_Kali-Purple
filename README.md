# Guia para tener una interfaz más a gusto
![](/img/kali.png)

### Todo esto fue posible gracias a Macelo Vázquez, Ve y siguelo. **[¡S4vitar!](https://www.linkedin.com/in/s4vitar/)**  y entra a su academia **[¡Hack4u!](https://hack4u.io/)** 

## Pasos a Seguir
### Ingresar a la terminal y poner en modo **root**
	sudo su
	apt update
	apt install build-essential git vim libxcb-util0-dev libxcb-ewmh-dev libxcb-randr0-dev libxcb-icccm4-dev libxcb-keysyms1-dev libxcb-xinerama0-dev libasound2-dev libxcb-xtest0-dev libxcb-shape0-dev 
	exit
	git clone https://github.com/baskerville/bspwm.git
	git clone https://github.com/baskerville/sxhkd.git
	cd bspwm
	make
	sudo make install
	cd sxhkd
	make
	sudo make install
	sudo apt install libxinerama1 libxinerama-dev
	mkdir ~/.config/{bspwm,sxhkd}
	cd bspwm/examples
	cp bspwmrc ~/.config/bspwm
	cp sxhkd ~/.config/sxhkd
	cat ~/.config/bspwm/bspwmrc
	sudo apt install kitty --> visualiza imagenes, algo similar a termminator
	cd ~/.config/sxhkd
	nano sxhkdrc --> ponemos la ruta de la kitty
		# terminal emulator
		super + Return
		/usr/bin/kitty --> abrira la kitty con windows+enter
		crtl+w
		focus the node in the given direction --> enter
			# focus the node in the given direction
			super + {_,shift + }{Left,Down,Up,Right}
	        bspc node -{f,s} {west,south,north,east}
		ctrl+w
		preselect the direction
			# preselect the direction
			super + ctrl + alt + {Left,Down,Up,Right}
	        bspc node -p {west,south,north,east}
			# cancel the preselection for the focused node
			super + ctrl + alt + space
			--> comentar
			# expand a window by moving one of its side outward
			#super + alt + {h,j,k,l}
			#   bspc node -z {left -20 0,bottom 0 20,top 0 -20,right 20 0}
			#  contract a window by moving one of its side inward
			#super + alt + shift + {h,j,k,l}
			#       bspc node -z {right -20 0,top 0 20,bottom 0 -20,left 20 0}
			# move a floating window
			super + shift + {Left,Down,Up,Right}
	        bspc node -v {-20 0,0 20,0 -20,20 0}
	        # custom Resize
		    alt + super + {Left,Down,Up,Right}
			/home/deed/.config/bspwm/scripts/bspwm_resize {west,south,north,east}
	ctrl+x
	mkdir /home/deed/.config/bspwm/scripts/
	touch /home/deed/.config/bspwm/scripts/bspwm_resize
	chmod +x alt+. --> da permisos de ejecución al archivo anterior
	nano alt+. --> https://hack4u.io/wp-content/uploads/2022/09/bspwm_resize.txt --> permite alterar el tama;o de las ventanas
		#!/usr/bin/env dash
		if bspc query -N -n focused.floating > /dev/null; then
		step=20
		else
		step=100
		fi
		case "$1" in
		west) dir=right; falldir=left; x="-$step"; y=0;;
		east) dir=right; falldir=left; x="$step"; y=0;;
		north) dir=top; falldir=bottom; x=0; y="-$step";;
		south) dir=top; falldir=bottom; x=0; y="$step";;
		esac
		bspc node -z "$dir" "$x" "$y" || bspc node -z "$falldir" "$x" "$y"
	┌──(deed㉿psdeed)-[~/.config/sxhkd]
	└─$ sudo su   
	compaudit
	ls -l /usr/local/share/zsh/site-functions/_bspc
	chown root:root /usr/local/share/zsh/site-functions/_bspc
	exit
	sudo su
	apt install cmake cmake-data pkg-config python3-sphinx libcairo2-dev libxcb1-dev libxcb-util0-dev libxcb-randr0-dev libxcb-composite0-dev python3-xcbgen xcb-proto libxcb-image0-dev libxcb-ewmh-dev libxcb-icccm4 libxcb-xkb-dev libxcb-xrm-dev libxcb-cursor-dev libasound2-dev libpulse-dev libjsoncpp-dev libmpdclient-dev libuv1-dev libnl-genl-3-dev
	exit
	cd Downloads
	git clone --recursive https://github.com/polybar/polybar
	cd polybar
	mkdir build
	cd build
	cmake ..
	make -j$(nproc)
	sudo make install --> ya que no se encuentra aun instlado la polibar
	which polybar
	sudo su
	apt install meson libxext-dev libxcb1-dev libxcb-damage0-dev libxcb-xfixes0-dev libxcb-shape0-dev libxcb-render-util0-dev libxcb-composite0-dev libxcb-image0-dev libxcb-present-dev libxcb-xinerama0-dev libpixman-1-dev libdbus-1-dev libconfig-dev libgl1-mesa-dev libpcre2-dev libevdev-dev uthash-dev libev-dev libx11-xcb-dev libxcb-glx0-dev libpcre3 libpcre3-dev libev-dev
	apt install libpcre3 libpcre3-dev libev-dev
	exit
	cd Download
	git clone https://github.com/ibhagwan/picom.git
	cd picom
	git submodule update --init --recursive
	meson --buildtype=release . build
	ninja -C build
	sudo ninja -C build install
	sudo apt install rofi
	rofi -show drun --> despliega la ventana para elegir un tema
	esc
	nano ~/.config/sxhkd/sxhkdrc
		# program launcher
		super + d
        /usr/bin/rofi -show drun
        # close and kill
        super + {_,shift + }q
        bspc node -{c,k}
	sudo apt install bspwm
	kill -9 -1
		windows+enter --> abre la kitty
		ctrl+shit+t --> abre un nuevo  espacio de trabajo
		ctrl+shif+z --> te mueve a la siguiente ventana de trabajo
		ctrl+win+alt+rigth+left+up+down
		ctrl+win+1+2+3+4  --> abre espacios para un espacio de trabajo (preselectores)
		win+d --> despliega un menu para buscar programas 
		ctrl+shift+enter --> abre una nueva terminal horizontal o vertical
		ctrl+shift+r --> abre el resize
		ctrl+shift+Rigth|Left --> se mueve entre espacios de trabajo
		crtl+shift+alt+t --> cambia el nombre del espacio de trabajo (terminal)
		win+alt+rigth+up+down+left
		win+s --> pone un ventana flotante
		win+alt+rigth+left+up+down --> redirecciona la ventana
		win+clic-rigth --> otra forma de redireccionar la ventana
		win+t --> reacopla la ventana de trabajo al estado inicial
		win+shit+2+3+4... --> mueve los espacios de trabajo 
		win+shit+f --> abre firefox
		win+shit+b --> abre brave
		win+shit+r --> actualiza las configuraciones anteriores
		win+enter --> abre una neuva terminal en el mismo espacio de trabajo
		win+q --> cierra la ventana
		win+shift+q --> reinicia el equipo
	nano ~/.config/sxhkd/sxhkdrc
		# close and kill
        super + {_,shift + }q
        bspc node -{c,k}
        # firefox
        super +shift + f
        /usr/bin/firefox
        # brave
        super +shift + f
        /usr/bin/brave-browser
    win+esc --> realizarlo para que guarde los cambios
    nmcli connection show --> visualiza todas las wired connection
    sudo ifconfig eth0 up
    sudo nmcli connection up uuid bdcdaebc-46d4-4c7e-ae8d-58f96ae50cb6 --> activa una especifica wired connection 
	exit 
    nano ~/.config/bspwm/bspwmrc
    vmware-user-suid-wrapper & --> para cundionar la clipoar
    nano ~/.config/sxhkd/sxhkdrc
    # quit/restart bspwm
	super + shift + {q,r}
	bspc {quit,wm -r}
	win+esc --> aplica despues de guardar cambios de un nano
	win+shit+r --> reinicioa cambios del bspwm previamente configurados
    https://www.nerdfonts.com/font-downloads --> pagina de fuentes
    hack nerd font --> se descarga esa fuente
    cd /usr/local/share/fonts
    sudo su
    mv /home/deed/Downloads/Hack.zip .
    unzip Hack.zip
    rm -rf Hack.zip
    exit
    cd ~/.config/kitty
    nano kitty.conf --> https://hack4u.io/wp-content/uploads/2022/09/kitty.conf_.txt
	    enable_audio_bell no
		include color.ini
		font_family HackNerdFont
		font_size 13
		disable_ligatures never
		url_color #61afef
		url_style curly
		map ctrl+left neighboring_window left
		map ctrl+right neighboring_window right
		map ctrl+up neighboring_window up
		map ctrl+down neighboring_window down
		map f1 copy_to_buffer a
		map f2 paste_from_buffer a
		map f3 copy_to_buffer b
		map f4 paste_from_buffer b
		cursor_shape beam
		cursor_beam_thickness 1.8
		mouse_hide_wait 3.0
		detect_urls yes
		repaint_delay 10
		input_delay 3
		sync_to_monitor yes
		map ctrl+shift+z toggle_layout stack
		tab_bar_style powerline
		inactive_tab_background #e06c75
		active_tab_background #98c379
		inactive_tab_foreground #000000
		tab_bar_margin_color black
		map ctrl+shift+enter new_window_with_cwd
		map ctrl+shift+t new_tab_with_cwd
		background_opacity 0.95
		shell zsh
	win+shit+r --> actualiza las configuraciones anteriores
	nano color.ini -->https://hack4u.io/wp-content/uploads/2022/09/color.ini_.txt
		cursor_shape          Underline
		cursor_underline_thickness 1
		window_padding_width  20
		# Special
		foreground #a9b1d6
		background #1a1b26
		# Black
		color0 #414868
		color8 #414868
		# Red
		color1 #f7768e
		color9 #f7768e
		# Green
		color2  #73daca
		color10 #73daca
		# Yellow
		color3  #e0af68
		color11 #e0af68
		# Blue
		color4  #7aa2f7
		color12 #7aa2f7
		# Magenta
		color5  #bb9af7
		color13 #bb9af7
		# Cyan
		color6  #7dcfff
		color14 #7dcfff
		# White
		color7  #c0caf5
		color15 #c0caf5
		# Cursor
		cursor #c0caf5
		cursor_text_color #1a1b26
		# Selection highlight
		selection_foreground #7aa2f7
		selection_background #28344a   
	win+shit+r --> actualiza las configuraciones anteriores
	win+q --> cierra la ventana
	win+d --> abre una terminal
	sudo apt install zsh-autosuggestions zsh-syntax-highlighting -zsh-autocomplete-
	kitty --version
	kitty -1 --start-as minimized
	sudo su
	kitty
	cd /root/.config/kitty
	cp /home/deed/.config/kitty/* .
	exit
	sudo apt install feh --> configurar el fondo de pantalla
	feh --bg-fill /home/deed/Pictures/img_fonts/
	nano /home/deed/.config/bspwm/bspwmrc
		/usr/bin/feh --bg-fill /home/deed/Pictures/img_fonts/img_hack.jpeg 
	sudo apt install imagemagick --> para abrir o visualizar imagenes
	kitty +kitten icat /home/deed/Pictures/img_fonts/img_hack.jpeg
	sudo apt install scrub --> borra archivos para no aplicar forense, es decir irrecuperable
	scrub -p dod archivo.png
	scrub -zun 10 -v archivo.png
	cd ~/.confg/kitty
	cat /kitty.conf
	mkdir ~/.config/polybar
	cd ~/Donwloads
	git clone https://github.com/VaughnValle/blue-sky.git
	cd /blue-sky/polybar
	cp -r * ~/.config/polybar 
	echo '~/.config/polybar/./launch.sh' >> ~/.config/bspwm/bspwmrc
	cd ~/Donwloads/blue-sky/polybar/fonts
	sudo cp * /usr/share/fonts/truetype
	fc-cache -v
	win+shit+r --> actualiza las configuraciones
	win+shit+q
	mkdir ~/.config/picom
	nano ~/.config/picom/picom.conf --> https://hack4u.io/wp-content/uploads/2022/09/picom.conf_.txt
	win+esc
	win+shit+r
	nano /home/deed/.config/bspwm/bspwmrc
		picom & --> y los tres anteriores ponerlo en segfundo plano tambien con &
	win+shit+r
	nano ~/.config/kitty/kitty.conf
		opacidad defualt 0.95 a 0.85
	nano ~/.config/bspwm/bspwmrc
		bspc config border_width 0
	win+shit+r
	git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/powerlevel10k 
	echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc
	zsh
	y
	y
	y
	y
	2
	1
	2
	n
	1
	3
	4
	1
	2
	2
	2
	y
	1
	y
	cd ~
	nano .p10k.zsh --> configuración del modo de visualización de la terminal
		comentar todo lo que esta para el lado derecho	desde status hasta per_directory_history
		vcs       # git status
		context
		command_execution_time
		status
		abrir y cerrar la terminal para guardar cambios
	sudo apt install neofetch
	sudo su
	cd ~
	git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/powerlevel10k 
	echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc
	cd /root
	ln -s -f /home/deed/.zshrc .zshrc
	cd ~
	zsh
		configuramos con los mismo pasos anteriores 
	p10k configure --> reconfigura de nuevo los pasos de zsh sisque no gusta de la terminal configurada previamente
	https://www.nerdfonts.com/cheat-sheet
	fire
	nano .p10k.zsh --> configuramos lo mismo del paso anterior agregando algo nuevo y para ver cambios, abrimos una nueva ventana
		ctrl+w 
		CONTEXT_ROOT_TEMPLATE
		# Custom prefix.
		'%248Fwith ' --> lo que se debe borrar
		 typeset -g POWERLEVEL9K_CONTEXT_PREFIX=''
		  # Context format when running with privileges: bold user@hostname.
		  '%B%n@%m' --> lo que se debe cambiar
		  typeset -g POWERLEVEL9K_CONTEXT_ROOT_TEMPLATE='%B%n@%m'
		# Custom icon
		typeset -g POWERLEVEL9K_OS_ICON_CONTENT_EXPANSION='' --> Cambiar el icono que va en ' ' y poner el de kali
	nano .zshrc
			# enable command-not-found if installed
			if [ -f /etc/zsh_command_not_found ]; then
		    . /etc/zsh_command_not_found
			fi
			source /home/deed/powerlevel10k/powerlevel10k.zsh-theme
			# History configurations
			HISTFILE=~/.zsh_history
			HISTSIZE=10000
			SAVEHIST=10000
				setopt histignorealldups sharehistory --> opcional, ponerlo y borrar el resto
				borrar
					setopt hist_expire_dups_first # delete duplicates first when HISTFILE size exceeds HISTSIZE
					setopt hist_ignore_dups       # ignore duplicated commands history list
					setopt hist_ignore_space      # ignore commands that start with space
					setopt hist_verify            # show command with history expansion to user before running it
					#setopt share_history         # share command history data
				echo '' > ~/.zsh_history --> comprobamos el borrado del hisotrial, pero es opcional
	exit
	cd ~
	nano .p10k.zsh --> tambien aplica a root
	ctrl+w
	ANCHOR_BOLD
		  # Display anchor directory segments in bold.
		  typeset -g POWERLEVEL9K_DIR_ANCHOR_BOLD=false
	sudo su
	configuramos para root el .p10k.zsh
	https://github.com/sharkdp/bat/releases/tag/v0.24.0
	releases
	bat_0.24.0_amd64.deb     2.35 MB --> descargamos esa versión
	https://github.com/lsd-rs/lsd/releases/tag/v1.0.0
	releases
	lsd_1.0.0_amd64.deb      1.16 MB --: descargamos esa versión
	cd Downloads
	dpkg -i bat_0.24.0_amd64.deb
	dpkg -i lsd_1.0.0_amd64.deb 
	https://github.com/junegunn/fzf --> isntalar la fzf que realiza busquedas más sofisticado
	git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
	~/.fzf/install
		y
		y
		y
	exit
	cd --> tambien instalamos el fzf en usario normal, cono los mismos pasos anteriores, cerrar y abrir una nueva terminal para aplicar cambios
	cat ctrl+t --> ejemplo; dijitar la palabra a buscar y se verá como realiza una busqueda 
	wh ctrl+r --> ejemplo; letras iniciales para ejecutar whoami y nos reflejará un historial de comandos similares
	https://pastebin.com/QGvVx3wG --> crear alias para cat y ls
	copiamos todo y pegamos en .zshrc debajo de la linea source /home/deed/powerlevel10k/powerlevel10k.zsh-theme
	cd
	nano .zshrc
		# Custom Aliases
		# -----------------------------------------------
		# bat
		alias cat='bat'
		alias catn='bat --style=plain'
		alias catnp='bat --style=plain --paging=never'
		 # ls
		alias ll='lsd -lh --group-dirs=first'
		alias la='lsd -a --group-dirs=first'
		alias l='lsd --group-dirs=first'
		alias lla='lsd -lha --group-dirs=first'
		alias ls='lsd --group-dirs=first'
	https://pastes.io/xsqk9oi1hz -->para cambiar los colores
	copiamos y pegamos en .zshrc debajo de la linea de alias
		export LS_COLORS="rs=0:di=34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.dz=01;31:*.gz=31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.zst=01;31:*.tzst=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.wim=01;31:*.swm=01;31:*.dwm=01;31:*.esd=01;31:*.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.webp=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:"
	nano .zshrc --> ponerle después de la línea 6
		# Fix the Java Problem
		export _JAVA_AWT_WM_NONREPARENTING=1
	nano ~/.config/bspwm/bspwmrc --> ponerlo después de los que estan en segundo plano
		wmname LG3D &
	burpsuite
	cd ~/.config/polybar
	nano launch.sh
		#polybar secondary -c ~/.config/polybar/current.ini & --> es la fecha y hora pero lo descomentamos
		#polybar top -c ~/.config/polybar/current.ini & --> es la sonido
	nano current.ini
		[bar/secondary]
		offset-x = 89.7% --> para la fecha
		[bar/log]
		width = 2.7%
		foreground = ${color.white}
		background = ${color.bg}
		[module/my-text-label]
		content = %{T7} --> ir a buscar un icono para remplazar el icono superior izq (https://www.nerdfonts.com/cheat-sheet) y buscamos un skull-kali-bug; el que más os guste
		ctrl+w
			font-6
		font-7 = "Hack Nerd Font Mono:size=32;8"
	nano launch.sh
		polybar ethernet_bar -c ~/.config/polybar/current.ini &
	nano current.ini
		[bar/log] --> copiamos todo el log y lo renombramos | ir tambien a buscar un icono para remplazar el segundo icono superior izq (https://www.nerdfonts.com/cheat-sheet) y buscamos un ethernet el que más os guste
		[bar/ethernet_bar]
		inherit = bar/main
		width = 10%
		height = 40 
		offset-x = 4%
		offset-y = 15
		bottom = false
		font-7="Hack Nerd Font Mono:size=22;5" --> juega con el tamaño del segundo icono e ip superior izq
		foreground = ${color.white}
		background = ${color.bg}
		padding = 0
		modules-center = ethernet_status
		wm-restack = bspwm
		;override-redirect = true
		[bar/micomponente] --> creamos para enviar el settarget
		inherit = bar/main
		width = 16%
		height = 40
		offset-x = 73.4%
		offset-y = 15
		background = ${color.bg}
		foreground = ${color.white}
		bottom = false
		padding = 1
		module-margin-left = 0
		module-margin-right = 0
		modules-center = target_to_hack
		wm-restack = bspwm
	ctrl+w
	https://pastebin.com/FABzmBP9 --> pastebin para el settarget
	module/sep --> creamos un nuevo modúlo para incorpar la ip de mata
		[module/ethernet_status]
		type = custom/script
		interval = 2
		exec = ~/.config/bin/ethernet_status.sh --> el script no esta creado, hay que crearlo para que pueda leer la ip de la mata
		[module/target_to_hack] --> creamos el modulo para enviar el target
		type = custom/script
		interval = 2
		exec = ~/.config/bin/target_to_hack.sh
		mkdir ~/.config/bin
		touch ~/.config/bin/ethernet_status.sh
		chmod +x ~/.config/bin/ethernet_status.sh
		nano ~/.config/bin/ethernet_status.sh --> https://pastebin.com/HcKxU3tD copiarlo y modificar la interfaz enns33 por eth0, dependiendo de el nombre de la interfza de cada S.O e igual el icono
			#!/bin/sh
			echo "%{F#2495e7}󰈀 %{F#ffffff}$(/usr/sbin/ifconfig eth0 | grep "inet " | awk '{print $2}')%{u-}"
		touch ~/.config/bin/target_to_hack.sh
		chmod 755 ~/.config/bin/target_to_hack.sh
		nano ~/.config/bin/target_to_hack.sh
			#!/bin/bash
 			ip_address=$(cat /home/deed/.config/bin/target | awk '{print $1}')
			machine_name=$(cat /home/deed/.config/bin/target | awk '{print $2}')
			 if [ $ip_address ] && [ $machine_name ]; then
		    echo "%{F#e51d0b}Icono ${F#ffffff}$ip_address%{u-} - $machine_name"
			else
		    echo "${F#e51d0b}ICONO %{u-}%{F#ffffff} No target"
			fi
	nano ~/.config/polybar/launch.sh
		#polybar secondary -c ~/.config/polybar/current.ini &
		polybar ethernet_bar -c ~/.config/polybar/current.ini &
		polybar hackthebox_bar -c ~/.config/polybar/current.ini & --> aumentamos esta linea
		polybar micomponente -c ~/.config/polybar/current.ini & --> aumentamos esta linea en el #right bar
	touch ~/.condig/bin/target
	chmod 755 ~/.condig/bin/target
	nvim ~/.zshrc --> agregamos para poder enviar el settarget
		function settarget(){
	    ip_address=$1
	    machine_name=$2
	    echo "$ip_address $machine_name" > /home/tuUsuario/.config/bin/target
	    }
	nano ~/.config/polybar/current.ini
		[bar/ethernet_bar] --> hacemos una copia y la llamamos
		[bar/hackthebox_bar]
		inherit = bar/main
		width = 10%
		height = 40
		offset-x = 14.3%
		offset-y = 15
		bottom = false
		font-7 = "Hack Nerd Font Mono:size=22;5"
		foreground = ${color.white}
		background = ${color.bg}
		padding = 0
		modules-center = hackthebox_status
		wm-restack = bspwm
		;override-redirect = true
		[module/ethernet_status] --> copiamos y lo llamamos
		[module/hackthebox_status]
		type = custom/script
		interval = 2
		exec = ~/.config/bin/hackthebox_status.sh
	touch ~/.config/bin/hackthebox_status.sh
	chmod +x ~/.config/bin/hackthebox_status.sh
	https://pastebin.com/sUk5hB4Q --> script para la vpn de hackthebox
	https://www.nerdfonts.com/cheat-sheet --> buscamos un icono llamado cube para remplazar en la palabra icono del script de pastebin
	nano ~/.config/bin/hackthebox_status.sh
		#!/bin/sh
	    IFACE=$(/usr/sbin/ifconfig | grep tun0 | awk '{print $1}' | tr -d ':')
	    if [ "$IFACE" = "tun0" ]; then
	    echo "%{F#1bbf3e}ICONO %{F#ffffff}$(/usr/sbin/ifconfig tun0 | grep "inet " | awk '{print $2}')%{u-}"
	    else
	    echo "%{F#1bbf3e}ICONO %{u-} Disconnected"
	    fi
	ctrl+w
	bar/primary --> modificamos el boton del lado der superior
		[bar/primary]
		background = ${color.bg}
		ctrl+shift+r --> actualiza los cambios una vez guardados con ctrl+s
	sudo su
	https://github.com/ohmyzsh/ohmyzsh/blob/master/plugins/sudo/sudo.plugin.zsh --> usamos solo el plugin necesario para configurar el sudo y anteponerlo para cualquier comando dijitado con esc+esc
	raw --> para visualizar el script completo
	cd /usr/share
	mkdir zsh-sudo-plugin
	cd zsh-sudo-plugin
	wget https://github.com/ohmyzsh/ohmyzsh/blob/master/plugins/sudo/sudo.plugin.zsh
	chmod +x sudo.plugin.zsh
	cd ..
	chown deed:deed zsh-sudo-plugin/
	cd zsh-sudo-pligin
	/usr/share/zsh-sudo-plugin/sudo.plugin.zsh --> copiamos para agregarlo al .zshrc modo roor
	nano /home/deed/.zshrc
		# enable auto-suggestions based on the history --> creamos una condicional después del contenido de esta linea
		if [ -f /usr/share/zsh-sudo-plugin/sudo.plugin.zsh ]; then
		source /usr/share/zsh-sudo-plugin/sudo.plugin.zsh
		fi
	win+shift+r
	ctrl+shift+enter --: abre una nueva ventana de trabajo y probamos 
	whoami
	esc+esc --> presionamos dos veces esc para que se anteponga el sudo
	cd /home/deed/.config/polybar
	nano workspace.ini
	ctrl+w
	label-active
		label-active = "x "
		bel-active-foreground = ${color.red}
		label-occupied-foreground = ${color.yellow}
	https://pastebin.com/H87J3nMj --> copiamos el script que es para el autocompletado con tab si se llegase a dijitalizar mal el comando
	cd
	nano .zshrc
	ctrl+w
	completion
	# enable completion features --> pegamos antes de esta linea y después lo borramos
			# enable completion features --> lo que se debe borrar
			autoload -Uz compinit
			compinit -d ~/.cache/zcompdump
			zstyle ':completion:*:*:*:*:*' menu select
			zstyle ':completion:*' auto-description 'specify: %d'
			zstyle ':completion:*' completer _expand _complete
			zstyle ':completion:*' format 'Completing %d'
			zstyle ':completion:*' group-name ''
			zstyle ':completion:*' list-colors ''
			zstyle ':completion:*' list-prompt %SAt %p: Hit TAB for more, or the character to insert%s
			zstyle ':completion:*' matcher-list 'm:{a-zA-Z}={A-Za-z}'
			zstyle ':completion:*' rehash true
			zstyle ':completion:*' select-prompt %SScrolling active: current selection at %p%s
			zstyle ':completion:*' use-compctl false
			zstyle ':completion:*' verbose true
			zstyle ':completion:*:kill:*' command 'ps -u $USER -o pid,%cpu,tty,cputime,cmd'
		# Use modern completion system --> nuevo codigo para el autompletado
		autoload -Uz compinit
		compinit
		zstyle ':completion:*' auto-description 'specify: %d'
		zstyle ':completion:*' completer _expand _complete _correct _approximate
		zstyle ':completion:*' format 'Completing %d'
		zstyle ':completion:*' group-name ''
		zstyle ':completion:*' menu select=2
		eval "$(dircolors -b)"
		zstyle ':completion:*:default' list-colors ${(s.:.)LS_COLORS}
		zstyle ':completion:*' list-colors ''
		zstyle ':completion:*' list-prompt %SAt %p: Hit TAB for more, or the character to insert%s
		zstyle ':completion:*' matcher-list '' 'm:{a-z}={A-Z}' 'm:{a-zA-Z}={A-Za-z}' 'r:|[._-]=* r:|=* l:|=*'
		zstyle ':completion:*' menu select=long
		zstyle ':completion:*' select-prompt %SScrolling active: current selection at %p%s
		zstyle ':completion:*' use-compctl false
		zstyle ':completion:*' verbose true
		zstyle ':completion:*:*:kill:*:processes' list-colors '=(#b) #([0-9]#)*=0=01;31'
		zstyle ':completion:*:kill:*' command 'ps -u $USER -o pid,%cpu,tty,cputime,cmd'
	sudo su
	apt install npm
	apt update -y
	apt upgrade -y
	exit
	cd
	cd .config
	mkdir nvim
	git clone https://github.com/NvChad/NvChad ~/.config/nvim --depth 1 --> clona y agregar al directorio creado anterior nvim
	https://github.com/neovim/neovim/releases/tag/stable --> descargamos el nvim-linux64.tar.gx que es el remplazo de vim
	nvim-linux64.tar.gz
	sudo su
	cd /opt
	mv /home/deed/Downloads/nvim-linux64.tar.gz .
	7z l nvim-linux64.tar.gz
	mkdir nvim
	mv nvim-linux64.tar.gz nvim
	cd !$
	ls
	tar -xf nvim-linux64.tar.gz
	rm nvim-linux64.tar.gz
	cd nvim-linux64
	ls
	cd bin
	su deed
	./nvim
	N
	:q! --> para salir
	nano /home/deed/.zshrc
	ctrl+w
	Custom Aliases
	# Custom Aliases --> el alias nuevo va después del contenido de #custom y antes de la linea que dice export
		# nvim --> nuevo alias
		alias nvim='/opt/nvim/nvim-linux64/bin/nvim'
	nvim /etc/hosts
		:NvimTreeToggle --> se despliega un mejor editor de texto
	sudo su
	cd
	git clone https://github.com/NvChad/NvChad ~/.config/nvim
	nvim
	nvim tst.py --> abrimos un nuevo archivo como prueba y no guardamos
	exit
	cd ~/.config/nvim/lua/plugins
	nvim init.lua
	/cmp --> filtramos y borramos desde la linea --load luasnips hasta donde termine su linea de contenido
	sudo su --> lo mismo del borrado se aplica para root
	exit
	cd
	nano /home/deed/.zshrc
	ctrl+w
	nvim
		borramos el aleas anterior y ponemos un path
		export PATH=/opt/nvim/nvim-linux64/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/local/games:/usr/games:/home/deed/.fzf/bin
	echo $PATH --> solo es para poder copiar el path actual y ponerlo arriba
	mkdir /home/deed/.config/rofi/ --> tener en cuenta que todo el contenido de la carpeta debe estar con 755 y deed:deed (chown -R deed:deed rofi)
	nvim config.rasi
		//@theme "/home/deed/.config/rofi/themes/nord.rasi"
		//@theme "/home/deed/.config/rofi/themes/nord.rasi"
		//@theme "/usr/share/rofi/themes/solarized_alternate.rasi"
		//@theme "/home/deed/.config/rofi/themes/nord.rasi"
		//@theme "/home/deed/.config/rofi/themes/nord.rasi"
		//@theme "/home/deed/.config/rofi/themes/nord.rasi"
		//@theme "/home/deed/.config/rofi/themes/nord.rasi"
		//@theme "/home/deed/.config/rofi/themes/omedark.rasi"
		@theme "/home/deed/.config/rofi/themes/nord.rasi"
	mkdir themes
	cd !$
	cp /home/deed/Downloads/blue-sky/nord.rasi . 
	nvim nord.rasi
		show-icons: false;
		font: "Hack Nerd Font Mono 10";
		* {
		  background-color: #2E3440;
		  bg-alt: #3B4252;
		  fg: #ECEFF4;
		  text-color: #ffffff;
		  window {
		  width: 30%;
		  transparency: "real";
		  background-color: #2E3440E6;
		}
	rofi-theme-selector
	nord
	alt+a
	sudo apt install flameshot --> para capturas de pantalla
	nvim /home/deed/.config/bspwm/bspwmrc
		flameshot & --> ponerlo con el resto de los segundo plano y configurar un atajo de teclado en sxhkdrc
	nvim /home/deed/.config/sxhkd/sxhkdrc
		flameshot
		super + shift + s --> va al final de la linea, al igual quiera uno ingresar
		/usr/bin/flameshot gui
		:wq
	win+shit+q
	win+shift+s o flameshot gui
	sudo apt install i3lock -y
	https://github.com/meskarune/i3lock-fancy --> buscamos en un broswer
	cd 
	cd Donwloads
	git clone https://github.com/meskarune/i3lock-fancy.git
	cd i3lock-fancy
	sudo make install
	nvim /home/deed/.config/sxhkd/sxhkdrc
		# i3lock-fancy
		super + shift + x
		  /usr/bin/i3lock-fancy -t "PONER TU PASSWORd\!\!\!" -f /usr/local/share/fonts/HackNerdFontMono-Regular.ttf
	win+shift+x
	sudo apt install ranger --> para andar entre direccotorios
	
### Esos son los pasos a seguir. si gustas saber más, Ve y sigue a: **[¡S4vitar!](https://www.linkedin.com/in/s4vitar/)**  y entra a su academia **[¡Hack4u!](https://hack4u.io/)** 






















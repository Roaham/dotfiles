### Guía de Instalación y Dependencias para Dotfiles

Este documento detalla todas las aplicaciones, paquetes, fuentes y configuraciones necesarias para que tus scripts personalizados funcionen a la perfección.

#### 1\. Dependencias de Aplicaciones y Paquetes

Para que todos los scripts se ejecuten sin errores, necesitas instalar una serie de paquetes desde los repositorios oficiales de Arch y desde el Arch User Repository (AUR).

##### **Paso 1: Instalar un Asistente de AUR**

Si aún no tienes un asistente de AUR como yay o paru, es el primer paso. Te permitirá instalar paquetes mantenidos por la comunidad fácilmente.

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   bash# Instalar yay (ejemplo)  sudo pacman -S --needed git base-devel  git clone https://aur.archlinux.org/yay.git  cd yay  makepkg -si   `

##### **Paso 2: Instalar Paquetes de Repositorios Oficiales**

Estos paquetes son la base de tu entorno y se pueden instalar directamente con pacman.

*   **hyprland**: Tu compositor de Wayland.
    
*   **hyprlock**: El bloqueador de pantalla.
    
*   **eww**: ElKowars Wacky Widgets, el motor de tus widgets.
    
*   **networkmanager**: Para gestionar la red a través de nmcli.
    
*   **pipewire-pulse**: Proporciona pactl para el control de volumen.
    
*   **pamixer**: Una alternativa para controlar el volumen de PulseAudio.
    
*   **playerctl**: Para controlar reproductores de música (Spotify, etc.).
    
*   **jq**: Un procesador de JSON fundamental para muchos scripts.
    
*   **socat**: Necesario para que los scripts escuchen eventos de Hyprland.
    
*   **wget**: Usado por el script de música para descargar carátulas.
    
*   **btop**: Monitor de sistema que aparece en tu menú.
    
*   **neovim**: Tu editor de texto.
    
*   **obs-studio**: Para grabación y streaming.
    
*   **steam**: Plataforma de videojuegos.
    
*   **gawk**: El procesador de texto awk, usado en [get\_kb.sh](code-assist-path:c:\Users\Roa\Desktop\Roaham\dotfiles\.config\eww\scripts\get_kb.sh).
    

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   bash# Comando para instalar todo desde los repositorios oficiales  sudo pacman -S hyprland hyprlock eww networkmanager pipewire-pulse pamixer playerctl jq socat wget btop neovim obs-studio steam gawk   `

##### **Paso 3: Instalar Paquetes del AUR**

Estos son paquetes específicos de tu configuración que se encuentran en el AUR.

*   **spotify-launcher**: Un lanzador para la versión de escritorio de Spotify.
    
*   **discord**: Aplicación de chat.
    
*   **minecraft-launcher**: El lanzador oficial de Minecraft.
    
*   **zen-browser**: Un navegador web (según tu menú).
    
*   **dracula-icons-git**: El tema de iconos Dracula que usas en el menú.
    

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   bash# Comando para instalar todo desde el AUR usando yay  yay -S spotify-launcher discord minecraft-launcher zen-browser dracula-icons-git   `

#### 2\. Dependencias de Fuentes e Iconos

La apariencia de tu barra y widgets depende críticamente de tener las fuentes correctas.

*   **Nerd Fonts**: La mayoría de los iconos (, , , 直, 󰕾, etc.) provienen de una "Nerd Font". Necesitas instalar al menos una y configurarla en tus widgets de eww. Algunas opciones populares son:
    
    *   ttf-firacode-nerd
        
    *   ttf-jetbrains-mono-nerd
        
    *   ttf-hack-nerd
        

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   bash# Ejemplo de instalación de una Nerd Font  sudo pacman -S ttf-firacode-nerd   `

*   **Tema de Iconos Dracula**: Ya fue instalado en el paso anterior (dracula-icons-git), pero es crucial para que los iconos de Discord y Minecraft se muestren en el menú.
    

#### 3\. Guía de Configuración y Pasos Finales

Una vez instaladas las dependencias, sigue estos pasos:

1.  bashchmod +x ~/.config/eww/scripts/\*.shchmod +x ~/.config/hypr/scripts/text\_animation/\*.sh
    
2.  **Verificar Ruta de la Batería**: Varios scripts ([batest.sh](code-assist-path:c:\Users\Roa\Desktop\Roaham\dotfiles\.config\eww\scripts\batest.sh), [batico.sh](code-assist-path:c:\Users\Roa\Desktop\Roaham\dotfiles\.config\eww\scripts\batico.sh), [battery.sh](code-assist-path:c:\Users\Roa\Desktop\Roaham\dotfiles\.config\hypr\scripts\battery.sh)) leen información de /sys/class/power\_supply/BAT0/. En algunos portátiles, la batería podría llamarse BAT1 u otro nombre.
    
    *   **Comprobación**: Ejecuta ls /sys/class/power\_supply/ para ver el nombre correcto.
        
    *   **Acción**: Si es diferente, deberás editar esos tres scripts y reemplazar BAT0 por el nombre correcto.
        
3.  **Verificar ID de Usuario para Hyprland**: Los scripts [workspace.sh](code-assist-path:c:\Users\Roa\Desktop\Roaham\dotfiles\.config\eww\scripts\workspace.sh) y [get\_kb.sh](code-assist-path:c:\Users\Roa\Desktop\Roaham\dotfiles\.config\eww\scripts\get_kb.sh) asumen que tu ID de usuario es 1000 para encontrar el socket de Hyprland (/run/user/1000/hypr/...).
    
    *   **Comprobación**: Ejecuta id -u para ver tu ID de usuario.
        
    *   **Acción**: Si es diferente de 1000, reemplaza el número en las rutas de esos dos scripts.
        
4.  bashmkdir -p ~/.config/hypr/scripts/text\_animation/
    

#### 4\. Resumen de Dependencias por Archivo

ScriptDependencias ClaveNotas[menu.sh](code-assist-path:c:\Users\Roa\Desktop\Roaham\dotfiles\.config\eww\scripts\menu.sh)zen, btop, discord, minecraft-launcher, nvim, obs, spotify-launcher, steam, dracula-icons-gitDefine las aplicaciones del menú principal.[batest.sh](code-assist-path:c:\Users\Roa\Desktop\Roaham\dotfiles\.config\eww\scripts\batest.sh) / [batico.sh](code-assist-path:c:\Users\Roa\Desktop\Roaham\dotfiles\.config\eww\scripts\batico.sh)(ninguna)Depende de la ruta /sys/class/power\_supply/BAT0.[lock.sh](code-assist-path:c:\Users\Roa\Desktop\Roaham\dotfiles\.config\eww\scripts\lock.sh)hyprctl, hyprlockLanza el bloqueador de pantalla.[workspace.sh](code-assist-path:c:\Users\Roa\Desktop\Roaham\dotfiles\.config\eww\scripts\workspace.sh)hyprctl, jq, socat, Nerd FontsGestiona y muestra los espacios de trabajo.[getnet.sh](code-assist-path:c:\Users\Roa\Desktop\Roaham\dotfiles\.config\eww\scripts\getnet.sh)nmcli, jqObtiene la lista de redes Wi-Fi disponibles.[getvol.sh](code-assist-path:c:\Users\Roa\Desktop\Roaham\dotfiles\.config\eww\scripts\getvol.sh)pamixer, pactl, eww, Nerd FontsControla y muestra el estado del volumen.[music.sh](code-assist-path:c:\Users\Roa\Desktop\Roaham\dotfiles\.config\eww\scripts\music.sh) / [pmusic.sh](code-assist-path:c:\Users\Roa\Desktop\Roaham\dotfiles\.config\eww\scripts\pmusic.sh)playerctl, jq, wgetObtiene metadatos y carátulas de la música en reproducción.[get\_kb.sh](code-assist-path:c:\Users\Roa\Desktop\Roaham\dotfiles\.config\eww\scripts\get_kb.sh)socat, awkEscucha los cambios de distribución de teclado en Hyprland.[current-wifi.sh](code-assist-path:c:\Users\Roa\Desktop\Roaham\dotfiles\.config\eww\scripts\current-wifi.sh)nmcli, Nerd FontsMuestra la red Wi-Fi actual y su intensidad.(Otros)ewwLa mayoría de los scripts \*ctl.sh y \*-delay.sh controlan eww.

Con esta guía, deberías poder replicar tu entorno en una nueva instalación de Arch Linux + Hyprland sin problemas.

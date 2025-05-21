# Retro-infoboard

**Retro-infoboard** is a terminal-based, aesthetically pleasing information dashboard that combines several open-source tools into a cohesive, retro-inspired interface. 
Designed for minimalists, tinkerers, and terminal lovers, it integrates real-time news, audio visualization, and system insights—all within a single tmux session.

![Dashboard Demo](demo.gif)

## ✨ Features

- 📡 **Newsboat** – Lightweight RSS reader for terminal-based news aggregation
- 🔊 **CAVA** – Real-time audio spectrum visualizer
- 🌌 **Astroterm** – Terminal-based astronomy and space info tool
- 🖼️ **cool-retro-term** – Optional retro CRT-style terminal emulator
- 🧩 All components orchestrated within a single `tmux` window layout

## 🛠 Requirements

- [tmux](https://github.com/tmux/tmux)
- [tmuxp](https://github.com/tmux-python/tmuxp)
- [newsboat](https://newsboat.org/)
- [cava](https://github.com/karlstav/cava)
- [astroterm](https://github.com/Astroplant/astroterm)
- [cool-retro-term](https://github.com/Swordfish90/cool-retro-term) *(optional)*

## 🚀 Installation

1. Insert this into your tmuxp config (.tmuxp/0.yaml). Change start_directory and optionally: lat/lon for astroterm.

    ```
    session_name: '0'
    windows:
    - focus: 'true'
      layout: 6056,151x35,0,0{113x35,0,0,0,37x35,114,0[37x16,114,0,3,37x18,114,17,4]}
      options: {}
      panes:
      - shell_command:
            - newsboat
        focus: true
      - cava
      - astroterm -u --latitude 47.66788822723712 --longitude 10.310719344176878 -c
      start_directory: /home/atemur
      window_name: python3
    ```

2. Edit your Newsboat config (.newsboat/config).
    ```
    auto-reload yes
    reload-time 2
    max-items 50
    ```
   
3. Insert your RSS feeds into .newsboat/urls. E.g.:
    ```
    https://monero.observer/feed-stories-mini.xml
    https://cointelegraph.com/rss
    ```

4. Create an alias for loading the tmuxp session (.bashrc).
    ```
    alias retroinfo="tmuxp load .tmuxp/0.yaml -f .tmux.config"
    ```
   
5. Optional: add mouse support for tmux (.tmux.config).
    ```
    set -g mouse on
    ```
   
## ▶️ Usage
just type 'retroinfo' in your terminal.
# ☀️Samsung SolarCell Remote Card for Home Assistant

A sleek, modern, and highly functional custom remote card for Home Assistant that mimics the minimalist Samsung SolarCell Remote (TM2180E/TM2360E). This project provides a UI for controlling your Samsung TV with dedicated support for streaming services.

## ✨ Features
* Dual-Layout Design: Separate configurations for Mobile and Desktop to ensure perfect ergonomics.
* App Integration: Quick-launch buttons for Netflix, YouTube, Prime Video, Disney+, and Spotify.
* Smart Visibility: Optimized to work with Home Assistant's native visibility conditions.
* Pure YAML: No complex JS installations; just copy, paste, and configure.

## 📸 Preview
| Mobile View | Desktop View |
| :---: | :---: |
| <img width="200" alt="grafik" src="https://github.com/user-attachments/assets/4d60f9d6-c88c-46d5-aaba-6254383db428" /> | <img width="250" alt="grafik" src="https://github.com/user-attachments/assets/6f325d96-4d7a-4da2-ae4c-494251b8f773" /> |

## 🛠 Step 1: Backend Configuration

To ensure the streaming service buttons function correctly, you need to add logic to your configuration.yaml. This allows Home Assistant to identify the correct sources on your Samsung Tizen OS.

Add the following to your Home Assistant configuration:

    shell_command:
		 launch_netflix: "curl -X POST http://[YOURTVIP]:8001/api/v2/applications/3201907018807"
		 launch_youtube: "curl -X POST http://[YOURTVIP]:8001/api/v2/applications/9Ur5IzDKqV.TizenYouTube"
		 launch_prime: "curl -X POST http://[YOURTVIP]:8001/api/v2/applications/3201910019365"
		 launch_spotify: "curl -X POST http://[YOURTVIP]:8001/api/v2/applications/3201606009684"
		 launch_disney: "curl -X POST http://[YOURTVIP]:8001/api/v2/applications/MCmYXNxgcu.DisneyPlus"

$\color{red}{\text{IMPORTANT: Make sure to restart your HA after this change!}}$

$\color{red}{\text{DISCLAIMER:}}$ The application IDs above might depend on the region you are in. These are for Switzerland and work for me.
You can find yours in going to Activity in HA, and add the [TVName] TV channel name, att a timeline whene you used all the applications you need. Ther you find something like this:

    [YourTV] TV channel name changed to MCmYXNxgcu.DisneyPlus
		
## 📱 Step 2: Frontend Installation
This repository contains two YAML files:
1. mobile-remote.yaml: Designed for narrow screens and one-handed use.
2. desktop-remote.yaml: A wider layout for tablets and desktop browsers.

Implementation:
1. Open your Dashboard.
2. Enter Edit Mode and click Add Card.
3. Choose the Manual card at the bottom of the list.
4. Copy the contents of mobile-remote.yaml from this repo and paste it into the editor.
5. Change the entity_id: media_player.[YourTVName] to your own.
6. Repeat the process for desktop-remote.yaml.
		
This is the code for a custom card in Home Assistant that imitates a Samsung SolarCell Remote controll device. This card can be added to any dashboard. 


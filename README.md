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

<img width="618" alt="grafik" src="https://github.com/user-attachments/assets/7f7012c6-5b1b-4597-a363-bee5f128a407" />

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

## 👁️ Step 3: Setting Visibility

To keep your dashboard clean, use the Visibility settings in the card editor:
* For the Mobile Card: Go to the Visibility tab and set it to show only when the screen factor is Mobile.
* For the Desktop Card: Set the condition to hide on mobile or show only when the screen factor is Desktop.

This ensures that Home Assistant automatically serves the correct remote version based on the device you are holding.

## 🧩 Prerequisites

For this card to render correctly, ensure you have the following installed via [HACS](https://hacs.xyz/docs/use/):
* [button-card](https://github.com/custom-cards/button-card)
* [stack-in-card](https://github.com/custom-cards/stack-in-card) (or use native vertical/horizontal stacks)

## 🤝 Contributing

If you have optimized the YAML further or added new icons for other regions, feel free to open a Pull Request!
1. Fork the Project
2. Create your Feature Branch (git checkout -b feature/NewLayout)
3. Commit your Changes (git commit -m 'Add new feature')
4. Push to the Branch (git push origin feature/NewLayout)
5. Open a Pull Request

Don't forget to ⭐️ this repository if you find it useful!

<div id="top"></div>

<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]



<!-- PROJECT LOGO -->
<br />
<div align="center">
<h3 align="center">things.dev esp8266 firmware</h3>

  <p align="center">
    esp8266 firmware for the things.dev platform
    <br />
    <a href="https://github.com/masonflint44/things-dev-esp8266-firmware"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/masonflint44/things-dev-esp8266-firmware">View Repo</a>
    ·
    <a href="https://github.com/masonflint44/things-dev-esp8266-firmware/issues">Report Bug</a>
    ·
    <a href="https://github.com/masonflint44/things-dev-esp8266-firmware/issues">Request Feature</a>
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#features">Features</a></li>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#dev-container">Dev container</a></li>
        <li><a href="#build-firmware">Build firmware</a></li>
        <li><a href="#flash-firmware">Flash firmware</a></li>
      </ul>
    </li>
    <li>
        <a href="#usage">Usage</a>
        <ul>
            <li><a href="#upload-code-to-device">Upload code to device</a></li>
            <li><a href="#execute-code-on-device">Execute code on device</a></li>
        </ul>
    </li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
<div id="about-the-project"></div>

## About The Project
This is an application written for the NodeMCU framework. It serves as the controller software for an esp8266 node on the things.dev platform.

<div id="features"></div>

### Features
- negotiates and manages Wi-Fi connection
- securely exchanges Wi-Fi credentials
- configure via Android interface
- exchanges data over MQTT

<div id="built-with"></div>

### Built With
- [NodeMCU](https://nodemcu.readthedocs.io/en/release/)
- [Esptool](https://github.com/espressif/esptool)
- [Nodemcu-tool](https://github.com/AndiDittrich/NodeMCU-Tool)

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- GETTING STARTED -->
<div id="getting-started"></div>

## Getting Started
The repo contains a .devcontainer directory that defines a container to be used as the development environment. See [link](https://code.visualstudio.com/docs/remote/containers) for more info about dev containers.

1. Clone the repo
    ```sh
    git clone https://github.com/masonflint44/things-dev-esp8266-firmware.git
    ```
1. Install the `ms-vscode-remote.remote-containers` extension for vscode
1. Open the repo directory with vscode
1. Select "Reopen in Container"

<div id="dev-container"></div>

### Dev container
- Based on debian-slim image
- Python - required for esptool
- Curl - used to install Node.js and npm
- Node.js - required for nodemcu-tool
- PyPi - package management - used to install esptool
- Npm - package management - used to install nodemcu-tool
- Git - source control
- [NodeMCU framework](https://github.com/nodemcu/nodemcu-firmware) - used to build firmware
- [Esptool](https://github.com/espressif/esptool) - used to flash firmware
- [Nodemcu-tool](https://github.com/AndiDittrich/NodeMCU-Tool) - used to upload code to device

<div id="build-firmware"></div>

### Build firmware - [docs](https://nodemcu.readthedocs.io/en/release/build/)
1. Start dev container
1. `cd ~/nodemcu-firmware`
1. Edit `app/include/user_modules.h` to add or remove modules
1. Run `make`
1. Get build output from `bin` directory

<div id="flash-firmware"></div>

### Flash firmware - [docs](https://nodemcu.readthedocs.io/en/release/flash/)
1. Start dev container
1. Navigate to build output directory `cd ~/nodemcu-firmware/bin`. See instructions to build firmware if directory empty.
1. Execute the following:
    ```
    esptool.py --port COM3 write_flash -fm dio 0x00000 0x00000.bin
    esptool.py --port COM3 write_flash -fm dio 0x10000 0x10000.bin
    ````

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- USAGE EXAMPLES -->
<div id="usage"></div>

## Usage

<div id="upload-code-to-device"></div>

### Upload code to device - [docs](https://github.com/andidittrich/NodeMCU-Tool)
1. Start dev container
1. Create initial File System (only required first time)
    - Execute: `nodemcu-tool mkfs`
1. Execute `nodemcu-tool upload <filename>`
1. Make sure device has required dependencies uploaded:
    ```
    ./lua_modules/http/httpserver.lua
    ./lua_modules/fifo/fifosock.lua
    ./lua_modules/fifo/fifo.lua
    ```

<div id="execute-code-on-device"></div>

### Execute code on device
1. Run Arduino IDE
1. Press `Ctrl+Shift+M` to open Serial Monitor
1. Ensure baud rate is set to at least 115200
1. Press RST button on device to restart - output should appear in Serial Monitor

NOTE: It is possible to execute functions on the device by providing input to Serial Monitor. Documentation needs added for this.

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- ROADMAP -->
<div id="roadmap"></div>

## Roadmap

<!-- - [ ] Feature 1
- [ ] Feature 2
- [ ] Feature 3
    - [ ] Nested Feature -->

See the [open issues](https://github.com/masonflint44/things-dev-esp8266-firmware/issues) for a full list of proposed features (and known issues).

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- CONTRIBUTING -->
<div id="contributing"></div>

## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- LICENSE -->
<div id="license"></div>

## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- CONTACT -->
<div id="contact"></div>

## Contact

Mason Flint - mason.flint@things.dev.com

Project Link: [https://github.com/masonflint44/things-dev-esp8266-firmware](https://github.com/masonflint44/things-dev-esp8266-firmware)

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/masonflint44/things-dev-esp8266-firmware.svg?style=for-the-badge
[contributors-url]: https://github.com/masonflint44/things-dev-esp8266-firmware/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/masonflint44/things-dev-esp8266-firmware.svg?style=for-the-badge
[forks-url]: https://github.com/masonflint44/things-dev-esp8266-firmware/network/members
[stars-shield]: https://img.shields.io/github/stars/masonflint44/things-dev-esp8266-firmware.svg?style=for-the-badge
[stars-url]: https://github.com/masonflint44/things-dev-esp8266-firmware/stargazers
[issues-shield]: https://img.shields.io/github/issues/masonflint44/things-dev-esp8266-firmware.svg?style=for-the-badge
[issues-url]: https://github.com/masonflint44/things-dev-esp8266-firmware/issues
[license-shield]: https://img.shields.io/github/license/masonflint44/things-dev-esp8266-firmware.svg?style=for-the-badge
[license-url]: https://github.com/masonflint44/things-dev-esp8266-firmware/blob/master/LICENSE.txt

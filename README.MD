<img src="assets/logo.png" alt="logo">

---
# <div align="center">KC Checker</div>

<div align="center">Experience the speed of a blazingly fast proxy checker</div>
<div align="center">where checking is done with style </div>

<br>

<div align="center">
<img src="https://img.shields.io/github/downloads/Kuucheen/KC-Checker/total.svg" alt="downloads">
<img src="https://img.shields.io/github/license/Kuucheen/KC-Checker.svg" alt="license">
<img src="https://img.shields.io/github/issues/Kuucheen/KC-Checker.svg" alt="issues">
<br>
<!--<a href="https://discord.gg/7FWAGXzhkC">
  <img src="https://img.shields.io/discord/1196551495571738665?logo=discord&colorB=7289DA" alt="discord">
</a>-->
</div>

<br>

<p align="center">
<img src="assets/preview.gif" alt="preview">
</p>

<br>

# Features

- Multi-Threaded
- Keyword website check
- Verify whether the proxy can access a specific website
- Sleek and intuitive UI for a beautiful user experience
- Highly customizable settings to tailor the tool to your needs

<br>

# Requirements

> [!IMPORTANT]
> Your terminal needs to support true color, and using different fonts in your terminal may cause display errors.

These are tested terminals on different operating systems:

| System | Tested | Notes |
|--|--|--|
| Windows 11| <div align="center">✅</div> | Works fine |
| Windows 10 | <div align="center">✅</div> | Works without true color
| Linux (ubuntu) | <div align="center">✅</div> | Works fine
| Mac OS | <div align="center">❌</div> | Should work fine

# Getting started

Download [latest release](https://github.com/Kuucheen/KC-Checker/releases/) & unzip the file

**Windows**<br>
Double click on KC-Checker.exe

**Linux**<br>
Open terminal and enter

`chmod +x KC-Checker`

Now run it with

`./KC-Checker`

## Or build it yourself

1. **Install Prerequisites:**
   - [Go](https://go.dev/doc/install)
   - [Git](https://git-scm.com/downloads)

2. **Clone the Project:**
   Open your terminal and run:
   `git clone https://github.com/Kuucheen/KC-Checker.git`

3. **(OPTIONAL) Set Up GeoLite2 Database:**
   If you want to determine the country and type (ISP, Datacenter, or Residential) of the proxies, you'll need to download the [GeoLite2 Country and GeoLite2 ASN Database](https://dev.maxmind.com/geoip/geolite2-free-geolocation-data) from MaxMind.

   - After downloading, replace the existing databases in the `helper` directory.
   - Ensure they have the same names: `GeoLite2-ASN.mmdb` and `GeoLite2-Country.mmdb`.<br><br>

   > **Note**: These databases are not included in the repository due to their licensing restrictions. However, they are bundled in the [prebuilt version](https://github.com/Kuucheen/KC-Checker/releases/).


<br>**Build**
<details>
  <summary>Using provided scripts</summary>

### Windows

Double click on `start.bat`

### Linux

Open terminal in the directory and make the script executeable

`chmod +x start.sh`

Run it with

`./start.sh`

Now you have an executable. You can run it like described in **Getting Started**
</details>
<details>
  <summary>Using terminal</summary>

Navigate to the directory

    cd KC-Checker

Install dependencies

    go get .

Build with

    go build .

Now you have an executable. You can run it like described in **Getting Started**
</details>

# How to Use

**Navigation**: Use the arrow keys on your keyboard to navigate through the program's interface. Here’s a quick guide to the controls:

| Key               | Description          |
| :---------------- | :------------------- |
| <kbd>↑ Up</kbd>   | Move up              |
| <kbd>↓ Down</kbd> | Move down            |
| <kbd>← Left</kbd> | Move left            |
| <kbd>→ Right</kbd>| Move right           |
| <kbd>↵ Enter</kbd>| Select/Confirm       |

**Saving Proxies**: When you save the proxies at the end of a checking progress, they will always be stored in the `output` folder.

# Customize Settings

> [!NOTE]
> For most users, the default settings will probably be sufficient.

<details>
    <summary>Details for settings.json</summary>

1. **threads**: <br>
   Maximum number of threads<br>

2. **retries**: <br>
   Number of retries for a request<br>

3. **timeout**: <br>
   Timeout duration for requests in ms<br>

4. **privacy_mode**: <br>
   If set to true, the proxies will be blured with "*" while checking

5. **copyToClipboard**: <br>
   If set to true, all proxies checked will be copied to clipboard when saving them to a file

6. **autoSelect**: <br>
   When setting one or more protocols are set to true, it will automatically start checking with the selected protocols.

7. **autoSave**: <br>
   **timeBetweenSafes**: Seconds between the autoSave<br>
   **ip:port**: If set to true it will automatically save the proxies with these format every timeBetweenSafes seconds<br>
   **protocol://ip:port**: Same here<br>
   **ip:port;time**: Same here<br>
   **custom**: You can set a custom autoSave format here. If its not empty it will save it with this format. At the end of a checking process theres an option for "CUSTOM", where you can build your own output. You can put the output you built there in here.<br>

8. **timeBetweenRefresh**: <br>
   This is how often the screen updates in ms. If you experience high CPU usage, it is recommended to set it higher.

9. **iplookup**: <br>
   A website that returns the <a href="https://de.wikipedia.org/wiki/Internet_Protocol">ip</a>. This is needed to know if the proxies are Transparent. The website will only be used once when starting the checker.

10. **judges_threads**: <br>
   Maximum threads for selecting the judge

11. **judges_timeout**: <br>
   Timeout duration of judges in ms

12. **judges**: <br>
   **url**: This is the url the proxy will connect to while checking <br>
   **regex**: The proxy will only be valid if the regex is found. When "default" is used it will check the <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers">headers</a>. Headers are needed to determine the anonymity level of the proxies. <br>
    If there are multiple judges the checker will use the fastest one

13. **blacklisted**:<br>
   Websites that contain blacklisted ips. These ips won't be checked

14. **bancheck**: <br>
    If a website URL is provided, the program verifies whether the proxy can successfully access the site. Proxies that have been checked against the website will be organized and stored in the `banchecked` directory.

15. **keywords**: <br>
    The program inspects the content of the website (in the bancheck option) accessed through the proxy to determine if it contains the specified keywords or phrases. If the proxy successfully reaches the site and the desired keywords are found it will safe them in the `banchecked` directory. If the keywords are not found they will not be safed in the `banchecked` directory (even when the proxy was able to reach the site).

16. **transport**: <br>
    These are the settings used for making a request. Only touch this option if you know what you are doing.

</details>

You can blacklist custom proxies by adding them in `blacklisted.txt`

## License

The code for this project is licensed under the [MIT License](LICENSE).

The GeoLite2 databases used by this project are provided by MaxMind and are licensed under the [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).

## <p align="center">Other

<div align="center">
<strong>this tool is made for educational purposes only</strong>
<br>
<br>
If you need help with anything join our <a href="https://discord.gg/7FWAGXzhkC">discord server</a>
<br>
<br>
Help me keep my projects open source by <a href="https://ko-fi.com/kuucheen">sponsoring</a> me
</div>

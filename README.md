# software-for-CYB-3.5-screen-
Wardriving
Upload it to the 3.5-inch CYD
These steps are for the ESP32-3248S035R, the resistive-touch model. Check the label on the back of the board first. The capacitive S035C needs a different touch setup.
1. Install Arduino IDE and the esp32 board package by Espressif.
2. In Arduino IDE’s Library Manager, install TFT_eSPI, XPT2046_Touchscreen, and TinyGPSPlus.
3. Configure TFT_eSPI for the 3.5-inch display. Use ST7796_DRIVER, panel dimensions 320×480, and the pin settings in the [setup guide](C:/Users/brian/Documents/Codex/2026-09-28/bu/outputs/CYD_35_Wardrive/README.md). This display setup is important; the 2.8-inch CYD configuration won’t work for this board.
4. Open [CYD_35_Wardrive.ino](C:/Users/brian/Documents/Codex/2026-09-28/bu/outputs/CYD_35_Wardrive/CYD_35_Wardrive.ino). In Arduino IDE, select ESP32 Dev Module, choose the board’s port, then click Upload. Connect the CYD by USB; if upload fails to start, hold its BOOT button while it begins connecting.
Prepare WDGWars upload
1. Get your API key from your WDGWars profile. The service documents its CSV upload at wdgwars.pl using the /api/upload-csv endpoint and an X-API-Key header. WDGWars upload instructions
2. On a FAT-formatted microSD card, put the key in a plain-text file named wdg_key.txt in the card’s root. The file should contain just your 64-character key.
3. Download the ISRG Root X1 certificate and save it on the card’s root as isrgrootx1.pem.
4. In the sketch, fill in WIFI_SSID and WIFI_PASSWORD for a Wi-Fi network with internet access. Upload the sketch again after editing.
5. Insert the card and restart the CYD. Open SURVEY, run SCAN, then tap UPLOAD. Uploading sends the logged WiGLE-format survey file to WDGWars.
The app can scan without GPS; GPS coordinates are included only if you connect and enable a compatible receiver. Upload is user-triggered. Since this build targets the S035R, tell me if your board says S035C and I can adapt the touch support.

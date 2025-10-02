# A Windows PowerShell WSJT-X Log Viewer with QRZ.COM integration

**NOTE:** When you go to the directory in this repository where the wsjtxlogviewer.exe resides, it will tell you it can't show the file because it is too large (That makes no sense, but anyway...) just download the RAW file. That will download the wsjtxlogviewer.exe. The file really isn't large but that's a thing with Github 

Command-line 'Terminal User Interface' utility to view WSJT-X ADIF logs, look up callsigns via **QRZ.COM**, and upload QSOs to your **QRZ Logbook**. No GUI, just a fast and simple way to access your WSJT-X .adi file(s) without the need for a separate logbook.
<pre>
------------------------------------------------------------------------------------------------------------------------
  CALL         DATE       TIME     BAND   MODE     FREQ       GRID
  ------------ ---------- -------- ------ -------- ---------- --------
  W0RLD        2025-09-30 08:09:30 40m    FT8      7.075092   EM79
> N7DNF        2025-09-30 07:55:00 40m    FT8      7.075099   DN55
  K7CAR        2025-09-30 07:45:15 40m    FT8      7.075099   DM37
  N3AZ         2025-09-30 07:39:15 40m    FT8      7.075300   EL09
  VE3YRG       2025-09-28 03:05:30 40m    FT8      7.075301   EN92
  W3EWL/QRP    2025-09-28 02:58:30 40m    FT8      7.075301
  N8JSN        2025-09-15 13:43:15 40m    FT8      7.074983   EN72
  AE1N         2025-09-15 13:38:30 40m    FT8      7.075199   FN42
  W4LJT        2025-09-15 13:37:30 40m    FT8      7.075199   EM73
  W6GRE        2025-09-15 13:33:00 40m    FT8      7.075199   EN31
  K4XD         2025-09-15 13:32:00 40m    FT8      7.075199   FM06
  W4UTZ        2025-09-15 13:31:00 40m    FT8      7.075199   EM95
  K4JH         2025-09-15 13:22:45 40m    FT8      7.075199
  K3MVT        2025-09-15 13:14:00 40m    FT8      7.075101   EN91
  WY7GUS       2025-09-09 03:34:08 40m    MFSK     7.049099   DN44
  KC8ZKS       2025-09-09 03:32:16 40m    MFSK     7.049099
  J88BTI       2025-09-03 08:00:00 40m    FT8      7.075168   FK93
  DL4DW        2025-09-02 03:55:45 40m    FT8      7.075168   JO40
  N3FMC        2025-09-01 03:18:16 40m    MFSK     7.049093   FN20
  N5VAN        2025-08-24 07:32:15 40m    FT8      7.075736   DN91
  KQ4KME       2025-08-24 07:22:30 40m    FT8      7.075007   EM70
  N9SES        2025-08-24 07:17:30 40m    FT8      7.075007   EN61
------------------------------------------------------------------------------------------------------------------------
QRZ Result:
CALL: N7DNF
Name: Daniel C Knop
QTH: Billings, MT, United States
Status: Lookup OK
------------------------------------------------------------------------------------------------------------------------
F1 Help  F2 Lookup  F3 Upload  F4 REPLACE=OFF  F5 Reload  F6 Band  F7 Mode  F8 Date  F9 Clear  F10 Quit
</pre>
## Features
- Pure ASCII, No GUI
- QRZ.COM lookup (name, QTH, grid)
- QRZ Logbook upload (INSERT, or optional REPLACE)
- Works on Windows PowerShell

## Requirements
- A QRZ API number (Will function without one, but Call lookup is disabled)
- An Internet connection to use QRZ.COM call lookup and .adi uploading

## How to install, configure and use (Windows)  
### Install:
  Download the precompiled **wsjtxlogviewer.exe** executable and the **wsjtxlogviewer.cfg** to your to your PC. Note that wsjtxlogviewer.exe will automatically find your wsjtx_log.adi file if it is located in the same directory, usally, C:\Users\yourusername\AppData\Local\WSJT-X. If you place the executable into any other location you'll need to start wsjtxlogviewer.exe with command-line arguments as follows -

### Configuration:
  A simple .cfg file is used to identify your QRZ.COM account information and API number. Be sure to download the wsjtxlogviewer.cfg file from this repository and place it in the same location on your PC as the executable file. Open the .cfg file and edit it in a text editor like Notepad or Notepad++. If you do not have a QRZ.COM account, wsjtxlogviewer will still work but it will not be able to look up call information.

Be sure not to change the order of these configuration lines in wsjtxlogviewer.cfg . Replace YOURCALL with your QRZ.COM callsign and save the file.

  QRZ_XML_USERNAME=YOURCALL</br>
  QRZ_XML_PASSWORD=YOURPASSWORD</br>
  QRZ_XML_AGENT=WSJTXLogViewer/1.0 (YOURCALL)</br>

  QRZ_LOGBOOK_KEY=0000-0000-0000-0000</br>
  QRZ_LOG_AGENT=WSJTXLogViewer/1.0 (YOURCALL)</br>

  STATION_CALL=YOURCALL

### Usage:
  wsjtxlogviewer (Without arguments will use the WSJTX_log.adi and wsjtxlogviewer.cfg file in the directory where you put the wsjtxlogviewe.exe program. To make it easy, just put the wsjtxlogviewer.cfg and wsjtxlogviewer.exe files in the c:\users\yourusername\AppData\local\WSJT-X directory where wsjtx_log.adi is.

  or
  
  wsjtxlogviewer -adif c:\users\yourusername\AppData\Local\WSJT-X\wsjtx_log.adi -cfg c:\wherever-you-keep-it\wsjtxlogviewer.cfg </br> (if you add -v to the the end of the command-line for verbose debug info)

### Commands:
| Key | Label       | Description                                                                                                                                          |
| --: | ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
|  F1 | Help        | Display the key commands.                                                                                                                            |
|  F2 | Lookup      | Find QRZ info on the call where the arrow is located.                                                                                                |
|  F3 | Upload      | Upload the `.adi` file to QRZ.com.                                                                                                                   |
|  F4 | REPLACE=OFF | Toggle upload mode. If **OFF**, matching QSO data on QRZ is **not replaced**. If **ON**, it **is replaced** with the data in the active `.adi` file. |
|  F5 | Reload      | Reload the `.adi` file. The display is automatically updated when a QSO is entered into the `.adi` file by WSJT-X.                                   |
|  F6 | Band        | Step through the filter to display QSOs by **BAND**.                                                                                                 |
|  F7 | Mode        | Step through the filter to display QSOs by **MODE**.                                                                                                 |
|  F8 | Date        | Step through the filter to display QSOs by **DATE**.                                                                                                 |
|  F9 | Clear       | Clear all filters and display the log with the last QSO entered at the top.                                                                          |
| F10 | Quit        | Quit the program.                                                                                                                                    |



  



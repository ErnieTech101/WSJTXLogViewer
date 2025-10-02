# WSJT-X Log Viewer with QRZ.COM integration

Command-line 'Terminal User Interface' utility to view WSJT-X ADIF logs, look up callsigns via **QRZ XML**, and upload QSOs to your **QRZ Logbook**. No GUI, just a fast and simple way to access your WSJT-X .adi file(s) without the need for a separate logbook.

## Features
- Sticky header + keybar (pure ASCII; no GUI)
- QRZ XML lookup (name, QTH, grid, DXCC)
- QRZ Logbook upload (INSERT, optional REPLACE)
- Works great on Windows/macOS/Linux terminals

## Requirements
- A QRZ API number (Will function without one, but Call lookup is disabled)
- An Internet connection to use QRZ.COM call lookup and .adi uploading

## How to install and use (Windows)  
Download the precompiled wsjtxlogviewer.exe executable and wsjtxlogviewer.cfg to your PC. Note that wsjtxlogviewer.exe will automatically find your wsjtx_log.adi file if it is located in the same directory, usally, C:\Users\yourusername\AppData\Local\WSJT-X. If you place the executable into any other location you'll need to start wsjtxlogviewer.exe with command-line arguments as follows

Usage:
  wsjtxlogviewer -adif c:\users\yourusername\AppData\Local\WSJT-X\wsjtx_log.adi -cfg c:\wherever-you-keep-it\wsjtxlogviewer.cfg -v

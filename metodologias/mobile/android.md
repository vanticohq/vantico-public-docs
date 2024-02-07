# Android

* debug mode on
* backup mode on
* use of insecure network protocols; Ex: communications via http, ftp or smtp
* leak of private informations; Ex: hardcoded private keys, leak tokens on log (logcat || slog)
* Leak private files to others apps; Ex: via insecure data storage, log, services, cache, memory access
* path traversal || local file include
* Cross-App Scripting:
* HTML Injection or JavaScript Injection (javascript://) in WebViews
* file:// && tel://
* Injection via QR Code Reader
* Unproteced Apps Parts
* exported activities / services
* intent redirection
* implicit broadcasts (sending/receiving)
* specific uri schema exposed, like: Spotify:// or WhatsApp://
* Incorrect URL Verification
* incorrect parsing of url can lead to a "open redirect”
* Unprotected Data on Server
* Data exposure

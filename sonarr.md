# Sonarr: My setup
## Downloading
1. Download a torrent client (**Recommended**: [qBittorrent](https://www.qbittorrent.org/download.php))
2. Download [Sonarr](https://sonarr.tv/)
---

**Note**:
Gnome shell has an error, so before running it, do ```TERM=xterm```

---

## Initial setup
### qBittorrent
1. Goto ```Tools>Preferences>WebUI```
2. Enable Web User Interface
3. Remember the port number
### Sonarr
1. Goto **Settings** and enable **Advanced Setting**
2. Then do the following
### Sonarr - Media Management
1. Rename Episodes - true
2. Make it to your style
3. Under folders, enable empty series folders
4. Under file management, Ignore deleted files
### Sonarr - Indexers
1. For anime, use nyaa.
2. Remove the additional parameters option and also thw website is nyaa.si
3. For tv series, use [usenet crawler](https://www.usenet-crawler.com).
4. Create an account and goto profile and get api key
5. come back to sonarr and goto ```add>newznab>presets>Usenet Crawler```
6. paste the api key
### Sonarr - Download client
1. add qbittorrent and add the port too.

That's it.
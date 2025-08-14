### Why use Jellyfin ?

Jellyfin allows me to have the media I love in one place, accessible at all times and on all my devices. While it does not allow me to discover new movies or shows or music, it is a service on which I can play anything an still be sure to enjoy it forever as I physically own the media.

Moreover, hearing about how little some artists are being paid by massive streaming services, I believe that buying a physical copy is a way to better support the artists and productions that create the media I love, but also creates a deeper emotional link between these works of art and me.

### Procedure

#### Codecs and Containers

1. **Video**
   - **Codec:** HEVC/H.265 for its excellent compression quality and wide compatibility (compared to AVC/H.264).  
   - **Container:** MKV for its support of subtitles, chapters, and multiple audio tracks, plus compatibility with many devices. Files can be remuxed when MKV isn’t supported.

2. **Audio**
   - **Codec:** AAC for its great compatibility and better compression compared to MP3. The difference from FLAC is negligible for most listening while taking about half the space.

---

#### Software for Extracting Media

1. **DVDs and Blu-ray Discs**
   - Rip with **MakeMKV** (bypasses copy protection).  
   - Transcode to the desired codec/container in **HandBrake**.  
   - Rename files for accurate metadata scraping in Jellyfin.

2. **CDs**
   - Rip using **Windows Media Player**.  
   - Rename files for metadata scraping.  
   - Use FLAC for lossless audio with compression.  
   - Get time-synced lyrics from **LRCGET**.

3. **File Transfer**
   - Transfer files to the server using **FileZilla Client**.

**Links to software:**  
- [HandBrake](https://handbrake.fr)  
- [MakeMKV](https://makemkv.com/download)  
- [MakeMKV Beta Key](https://forum.makemkv.com/forum/viewtopic.php?t=1053)

---

### Configuration

#### Transcoding
- Hardware acceleration enabled via **Video4Linux2 (V4L2)**.  
- Hardware decoding enabled for H.264; hardware encoding enabled for HEVC.  
- In practice, transcoding is rarely needed since all files are in AVC or HEVC, both supported by all client devices.  
- All other settings left at defaults.

#### Trickplay
- Uses hardware decoding.  
- All other settings left at defaults.

#### Profile Settings

**Playback:**  
Enable “Préférer le conteneur de média fMP4-HLS.”  
This improves playback of HEVC and AV1 files and allows browser playback by converting the container from MKV to HLS.

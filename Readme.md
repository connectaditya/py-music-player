
Description

It provides a player object which represents the player. It needs a generator player.queue which yields Song objects which provide a way to read file data and seek in the file. See the source code for further detailed reference.

It has the following functionality:

    open source (simplified BSD license, see License.txt)
    very simple interface
    support of most important sound formats (MP3, Flac, Ogg Vorbis, WMA, AAC / ALAC m4a, …)
    Plays audio data via the player object. Uses FFmpeg for decoding and PortAudio for playing.
    Of course, the decoding and playback is done in seperate threads. You can read about that here.
    Supports any sample rate via player.outSamplerate. The preferred sound device is set via player.preferredSoundDevice. Get a list of all sound devices via getSoundDevices().
    Can modify the volume via player.volume and also song.gain (see source code for details).
    Prevents clipping via a smooth limiting functions which still leaves most sounds unaffected and keeps the dynamic range (see smoothClip).
    ReplayGain (for audio volume normalization) (see pyCalcReplayGain). This is as far as I know the only other implementation of ReplayGain despite the original from mp3gain (gain_analysis.c).
    AcoustId audio fingerprint (see pyCalcAcoustIdFingerprint). This one is also used by MusicBrainz. It uses the Chromaprint lib for implementation.
    Provides a simple way to access the song metadata.
    Provides a way to calculate a visual thumbnail for a song which shows the amplitude and the spectral centroid of the frequencies per time (see pyCalcBitmapThumbnail). Inspired by this project.
    Gapless playback

Usages

The main usage is probably in the MusicPlayer project - a full featured high-quality music player.
Installation

To get the source working, you need these requirements:

    boost >=1.55.0
    ffmpeg >= 2.0 (including libswresample)
    portaudio >=v19
    chromaprint

Debian/Ubuntu

apt-get install python-dev libsnappy-dev libtool yasm libchromaprint-dev portaudio19-dev libboost-dev

FFmpeg in Debian/Ubuntu is too old (lacks libswresample), so either do:

add-apt-repository ppa:jon-severinsson/ffmpeg
apt-get update
apt-get install libavformat-dev libswresample-dev

or install it from source.
MacOSX

brew install boost
brew install portaudio
brew install ffmpeg
brew install chromaprint


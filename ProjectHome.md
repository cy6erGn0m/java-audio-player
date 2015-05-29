## What is it \ Was ist das ##
Library that provides a simple way to play audio files. Just set location and call play() to listen. Location also can be internet location (http hosted). In this case player will play and download in the same time and pauses if download speed is low.
Player also provides wrapper for JavaFX.

## What does it support ##
Player currently supports only mp3 files.

Provided features is: playback, pause, stop, seek. API provies way to listen events about playback events such as "stalled notification", end of media notification, current play position and buffered length in microseconds.

## External usages ##

Player uses javazoom mp3 decoder and Java Sound to play audio.

## Documentation ##
JavaAudioPlayer project has sample how to use player with Swing (except seek functionality).
fx repository contains wrapper and simple usage sample for JavaFX.

## Goals ##
Player performs operations asynchronous, so, it will never block your JavaFX UI.

Now player looks stable. **CPU consumption** 1-2%. There is no more memory leaks found. **Memory consumption** ~10-15M. Passes manual tests on Windows and Linux. Testcases will be published later.

Also note that it is not a Player application. This is just the Java Audio Player **Library**.
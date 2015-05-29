## Preparation ##

Please read [LibraryRequirements](LibraryRequirements.md) before use. Download all required jars and put to your project.

## Start and Stop ##

To use player, just create Player instance like this

```
// ....
import cy6erGn0m.player.fx.Player;
// ....

def player : Player = Player {
};
```

Then, you should provide way to set location of file which should be played. For example, you may use this way:

```
var currentTrackUrl : String;

def player : Player = Player {
    location: bind currentTrackUrl
};
```

To start playback just call method play() like this:

```
// .....
import maryb.player.PlayerState;
//.....
def playButton : Button = Button {
    text: "Play"
    disable: bind player.state == PlayerState.PLAYING
    action : function() {
        player.play();
    }
};
```

To stop - call method stop()

## Volume control ##

Lets bind slider control to player volume. You may done it like this:

```
def volumeControl : Slider = Slider {
    min: 0
    max: 1.0
    value: bind player.volume with reverse
};
```

Another way, you may define variable `currentVolume` bound to slider value and bind player to it like this:

```
def currentVolume : Number = bind volumeControl.value;
def player : Player = Player {
    // ......
    volume: bind currentVolume
};
def volumeControl : Slider = Slider {
    min: 0
    max: 1.0
    value: 0.7
};
```

## Seek and advanced control ##

Then, lets track playback position. The one of the ways here:
```
def currentPlayPercent : Number = bind player.currentPosition / player.totalPosition;

def seekBarView : ProgressBar = ProgressBar {
    progress: bind currentPlayPercent
};
```

If you want to detect moment when playback reaches end of media, use function `endOfMedia`. Here is a sample that plays one media in infinite loop:

```
def player : Player = Player {
    // ....
    endOfMedia : function() {
        player.play();
    }
};
```

If you need know, how many seconds was already buffered (for network playback), you may use variable `bufferedPosition` like this:
```
def tx : Text = Text {
    content: bind "{player.bufferedPosition} of {player.totalPosition} buffered"
};
```

To show some effect when playback stalled because buffering you may check player `state`.
```
def buffering : ProgressBar = ProgressBar {
    progress: -1
    visible: bind player.state == PlayerState.PAUSED_BUFFERING
};
```
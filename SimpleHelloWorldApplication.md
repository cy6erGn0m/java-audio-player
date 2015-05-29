# Introduction #
Here is a simple Hello World Application Source

```
import maryb.player.Player;

public class Main {

    public static void main( String[] args ) {
        Player p = new Player();
        p.setCurrentVolume( 0.7f );
        p.setSourceLocation( "/set/path/to/any/mp3/file/here" );
        p.play();
    }

}
```

Do not forget to include required jars (see LibraryRequirements) to classpath at compile time and runtime.

Here a simple JavaFX Application source:

```
// ....
import cy6erGn0m.player.fx.Player;
// ....
var tb : TextBox;
var src : String = bind tb.rawText;

def player : Player = Player{
    location: bind src
};

Stage {
    title: "Application title"
    width: 280
    height: 180
    scene: Scene {
        content: [
            tb = TextBox {
                width: 150
            }
            Button {
                translateY: 50
                action: function() {
                    player.play();
                }
                text: "Play"
            }
            Button {
                translateY: 50
                translateX: 70
                text: "Stop"

                action: function() {
                    player.stop();
                }

            }
            Text {
                font : Font {
                    size : 16
                }
                x: 10
                y: 90
                content: bind "Player state: {player.state}"
            }
            Slider {
                translateY: 50
                translateX: 150
                width: 100
                value: bind player.volume with inverse
                min: 0
                max: 1.
            }

        ]
    }
};

```
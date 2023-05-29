# Simple signals


Simple signals approach. By using this approach game scenes don't need to be connected to communicate between each other. We will add autoload script with signals and functions that emits signals to eliminate chances for a typo.


1. Create `events.gd` file.
2. Add file to Autoload as `Events` so it will be available everywhere.
3. In `events.gd` add signals like:

```gdscript
extends Node2D

# Player signals

signal player_died()

func emit_player_died():
    emit_signal("player_died")

```

4. Then, in scripts that needs to know what player died add:

```gdscript
func _ready():
    Events.connect("player_died", on_player_died)

func on_player_died():
    # Do something...

```

5. In player script you can emit the signal:

```gdscript
func die():
    # do some stuff related to dying.
    Events.emit_player_died()
```


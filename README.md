# Ultimate Magic Cube
Unlocking the full potential of [Mi/Aqara Magic Cube](https://www.aqara.com/us/cube.html) with Home Assistant & Node-RED.  

## How it works:
- **Everything is fully customizable.**
- I don't think it's possible to do without Node-RED.
- Unlike normal usage, you'll need to do an activation gesture first (you don't have to worry about triggering commands by accident when moving the cube around).
- Each activation gesture enables a set of commands. 
- The cube will be deactivated after X seconds of inactivity (default is 10s). Or you do a slide gesture to deactivate it immediately. All states are reset.
- Info of the current action/last action are stored in `$flow.cube` (this info will be deteled when the cube is deactivated).

```json
{
  "activated_mode": "shake",
  "current_action": {
    "gesture": "flip90",
    "detailed_gesture": "flip_1_2",
    "last_side": 1,
    "current_side": 2
  },
  "last_action": {
    "gesture": "rotate_right",
    "detailed_gesture": "rotate_right",
    "last_side": 1,
    "current_side": 1
  }
}
```

## How to add/remove activation gestures:  
1. Edit `$flow.CUBE_ACTIVATION_GESTURES` value in `Setup Gestures` nodes. Supported gestures are available in the `Context Data` window.
2. Add/remove these gestures in the `Check activated gesture`.

## Supported gestures:
- `WAKE_UP`: Cube wakes up from sleep. Trigger by the cube itself.
- `SLIDE`: Slide. Reserved for deactivating the cube, but you can change/remote if you want.
- `SHAKE`: Shake.
- `FREE_FALL`: Fall.
- `DOUBLE_TAP`: Doble Tap.
- `FLIP`: Flip 90/180 degrees. Use this when you don't care about the sides.
- `FLIP_90`: Flip 90 degrees.
- `FLIP_180`: Flip 180 degrees.
- `ROTATE_LEFT`: Turn counter clockwise.
- `ROTATE_RIGHT`: Turn clockwise.
  
Replace X, Y with the side's number (1-6) if you want to be more specific.
- `DOUBLE_TAP_X`: Double Tap on side #X.
- `SLIDE_X`: Slide the cube when side #X is up.
- `FLIP_X_Y`: Flip the cube from side #X to side #Y.

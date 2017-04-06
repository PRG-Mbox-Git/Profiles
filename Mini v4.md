# Mbox Mini v4.1 Mapping
As of March 6, 2017

### Notes:
* Mbox uses default values of 127 and 32767 for some parameters, rather than 128 and 32768.  Using incorrect default values will have a severe negative impact on operation!
* Mbox v4 eliminates the prior idea of single, pan wide, pan dual, and dual independent output setup.  For v4 you add the number of layers desired and then add outputs as desired.  Outputs may be separate or panoramic in some combination with other layers.  Each output can have its own Output Master fixture. Two or more outputs can be linked together as panoramic outputs if desired.
* Mbox Mini v4 does not have controllable Lighting fixtures.  It has a fixed lighting setup, similar to v3.x.  
* Mbox Mini v4 can have up to one (1) effect per layer). The number of effects must be the same for every patched layer.
* Each layer in Mbox v4 has optional Effect, Layer Volume, and Layer DMX Timecode sub-fixtures.  These fixture types are automatically included as part of the standard  quick patch. Each layer receives its own copy of each sub-fixture. Every layer receives the same quantity of each sub-fixture type.  When using the advanced patch these sub-fixtures are optional.
* The Output Master fixture includes Base functionality, plus optional Effect (1), Shutter, and Keystone sub-fixtures.
* A standard/base configuration includes Lighting (5 Pro Lights), Global Master, four Layer controls (each with 1 effect, volume, and timecode), and one Output Master (with all sub-fixtures).
* All 16-bit values are in big-endian format. For example, the value 23 would be presented as 0 in the first channel and 23 in the second channel.

> ## Sections
> * [**Summary - Standard Configuration (Quick Patch)**](#summary---standard-configuration-quick-patch)
> * [**Summary - Custom Configuration (Custom Patch)**](#summary---custom-configuration-custom-patch)
> * [**Fixture Descriptions**](#fixture-descriptions)
>   * [Pro Light](#pro-light)
>   * [Global Master](#global-master)
>   * [Output Master Base](#output-master-base)
>   * [Output Master Effect](#output-master-effect)
>   * [Output Master Camera](#output-master-camera)
>   * [Output Master Geometry](#output-master-geometry)
>   * [Output Master Keystone](#output-master-keystone)
>   * [Output Master Shutter](#output-master-shutter)
>   * [Layer Base](#layer-base)
>   * [Layer FX](#layer-fx)
>   * [Layer Volume](#layer-volume)
>   * [Layer DMX Timecode](#layer-dmx-timecode)
>   * [Pixel Mapping Group Control](#pixel-mapping-group-control)
> * [**Channel Definitions**](#channel-definitions)
>   * [Global Master Control Channel](#global-master-control-channel)
>   * [Shutter Shapes](#shutter-shapes)
>   * [Keystone Blend Curves](#keystone-blend-curves)
>   * [Video and Utility Inputs](#video-and-utility-inputs)
>   * [Play Modes](#play-modes)
>   * [Play Speed](#play-speed)
>   * [Sync Stream](#sync-stream)
>   * [Frame Blending Control](#frame-blending-control)
>   * [Combined Effects](#combined-effects)
>   * [Transitions](#transitions)
>   * [Object Transitions](#object-transitions)
>   * [Layer Mix Modes](#layer-mix-modes)
>   * [Blend Modes](#blend-modes)
>   * [Draw Modes](#draw-modes)
>   * [Pixel Mapping Group Control Modes](#pixel-mapping-group-control-modes)

## Summary - Standard Configuration (Quick Patch)

### Masters
*Universe Offset +0*

| Start  | Size  | Type  |
|---|---|---|
| 1 | 5 | Global Master |
| 6 | 6 | Output Master 1 |
| 12 | 6 | Output 1 FX |
| 18 | 16 | Output 1 Keystone |
| 34 | 12 | Output 1 Shutter |
| | **45**  | **TOTAL DMX CHANNELS** |

>**Notes:**
>* Additional Outputs may be added and use 40 channels each if all sub-fixtures are included.
Warning: The maximum number of Output Masters, six (6), will fit on the first universe, but if more than four Output Masters are used, the sixth playback layer must be moved to a second universe!

### Layers 1-6
*Universe Offset +0 (unless more than four Output Masters are used)*

| Start  | Size  | Type  |
---|---|---
| 1 | 52 | Layer 1 |
| 53 | 52 | Layer 2 |
| 105 | 52 | Layer 3 |
| 157 | 52 | Layer 4 |
| 209 | 52 | Layer 5 |
| 261 | 52 | Layer 6 |
| | **312**  | **TOTAL DMX CHANNELS** |

## Summary - Custom Configuration (Custom Patch)

### Masters
*Universe Offset +0*

| Start  | Size  | Type  | Required/Optional |
---|---|---|---
| 1 | 5 | Global Master | **Required** |
| 6 | 6 | Output Master 1 | **Required** |
| 12 | 6 | Output 1 FX | Optional |
| 18 | 16 | Output 1 Keystone | Optional |
| 34 | 12 | Output 1 Shutter | Optional |
| | **45**  | **TOTAL DMX CHANNELS** |

>**Note:**
* Additional Output Masters may be added.  Each Output Master may have different options enabled - effect, keystone, shutter.

### Layers 1-6
*Universe Offset +0 (unless more than four Output Masters are used)*

*Types listed as Required must be patched for the layer to work.  Optional types can be enabled/disabled for every layer, but not on a per-layer basis.*

| Start  | Size  | Type  | Required/Optional |
---|---|---|---
| **1** | 41 | Layer 1 Base | **Required** |
| +42 | 6 | Layer 1 FX 1 | Optional |
| +48 | 1 | Layer 1 Volume | Optional |
| +49 | 4 | Layer 1 Timecode | Optional |
| **53** | 41 | Layer 2 Base | **Required** |
| +42 | 6 | Layer 2 FX 1 | Optional |
| +48 | 1 | Layer 2 Volume | Optional |
| +49 | 4 | Layer 2 Timecode | Optional |
| **105** | 41 | Layer 3 Base | **Required** |
| +42 | 6 | Layer 3 FX 1 | Optional |
| +48 | 1 | Layer 3 Volume | Optional |
| +49 | 4 | Layer 3 Timecode | Optional |
| **157** | 41 | Layer 4 Base | **Required** |
| +42 | 6 | Layer 4 FX 1 | Optional |
| +48 | 1 | Layer 4 Volume | Optional |
| +49 | 4 | Layer 4 Timecode | Optional |
| **209** | 41 | Layer 4 Base | **Required** |
| +42 | 6 | Layer 4 FX 1 | Optional |
| +48 | 1 | Layer 4 Volume | Optional |
| +49 | 4 | Layer 4 Timecode | Optional |
| **261** | 41 | Layer 4 Base | **Required** |
| +42 | 6 | Layer 4 FX 1 | Optional |
| +48 | 1 | Layer 4 Volume | Optional |
| +49 | 4 | Layer 4 Timecode | Optional |
| | **312**  | **TOTAL DMX CHANNELS** |

# Fixture Descriptions

### Global Master
*(Required, 1 allowed)*

| Channel | Size | Function | Default | Snap | Notes |
---|---|---|---|---|---
| 1 | 1 | Global Intensity | 255 | N | Overall dimming (in IO Module if applicable) |
| 2 | 1 | Control | 0 | **Y** |  see [#Global-Master-Control-Channel](#global-master-control-channel)  |
| 3 | 1 | Control Selector | 0 | **Y** | Modifier for Control macros |
| 4 | 1 | Pixel Mapping Output Level | 255 | N | Master level for pixel-mapped outputs  |
| 5 | 1 | Global Volume | 255 | N | Master level for all audio |
| | **5**  | **TOTAL DMX CHANNELS** | | | |

### Output Master Base
*Required, quantity variable*

| Channel | Size | Function | Default | Snap | Notes |
---|---|---|---|---|---
| 1 | 1 | Master Intensity | 255 | N | Software dimming of output |
| 2 | 1 | Red | 127 | N | Subtractive 0-126, Additive 128 - 255 |
| 3 | 1 | Green | 127 | N | Subtractive 0-126, Additive 128 - 255 |
| 4 | 1 | Blue | 127 | N | Subtractive 0-126, Additive 128 - 255 |
| 5 | 1 | Brightness | 127 | N | |
| 6 | 1 | Contrast | 127 | N | |
| | *6*  | **TOTAL DMX CHANNELS** | | | |

### Output Master Effect
*Optional, 1 per Output Master*

| Channel | Size | Function | Default | Snap | Notes |
---|---|---|---|---|---
| 1 | 1 | Master Effect 1 | 0 | **Y** | see [Combined Effects](#combined-effects) |
| 2 | 1 | Master Effect Modifier 1a | 0 | N | |
| 3 | 1 | Master Effect Modifier 1b | 0 | N | |
| 4 | 1 | Master Effect Modifier 1d | 0 | N | |
| 5 | 1 | Master Effect Modifier 1d | 0 | N | |
| 6 | 1 | Master Effect Modifier 1e | 0 | N | |
| | **6**  | **TOTAL DMX CHANNELS** | | | |

### Output Master Keystone
*(Optional, 1 per Output Master)*

| Channel | Size | Function | Default | Snap | Notes |
---|---|---|---|---|---
| 1 | 2 | Corner 1 - X  | 32767 | N | |
| 3 | 2 | Corner 1 - Y  | 32767 | N | |
| 5 | 2 | Corner 2 - X  | 32767 | N | |
| 7 | 2 | Corner 2 - Y  | 32767 | N | |
| 9 | 2 | Corner 3 - X  | 32767 | N | |
| 11 | 2 | Corner 3 - Y  | 32767 | N | |
| 13 | 2 | Corner 4 - X  | 32767 | N | |
| 15 | 2 | Corner 4 - Y  | 32767 | N | |
| | **16**  | **TOTAL DMX CHANNELS** | | | |

### Output Master Shutter
*Optional, 1 per Output Master*
>**Note:**
>* The shutters in Mini are locked into the "ML" shape mode that Designer and Studio can use.

| Channel | Size | Function | Default | Snap | Notes |
---|---|---|---|---|---
| 1 | 1 | Red | 0 | N | |
| 2 | 1 | Green | 0 | N | |
| 3 | 1 | Blue | 0 | N | |
| 4 | 1 | Shutter Edge  | 0 | N | Blurs shutter edge  |
| 5 | 1 | Shutter 1a  | 0 | N | |
| 6 | 1 | Shutter 1b  | 0 | N | |
| 7| 1 | Shutter 2a  | 0 | N | |
| 8 | 1 | Shutter 2b  | 0 | N | |
| 9 | 1 | Shutter 3a  | 0 | N | |
| 10 | 1 | Shutter 3b  | 0 | N | |
| 11 | 1 | Shutter 4a  | 0 | N | |
| 12 | 1 | Shutter 4b  | 0 | N | |
| | **12**  | **TOTAL DMX CHANNELS** | | | |

### Layer Base
*Required, Up to 6 per server*


| Channel | Size | Function | Default | Snap | Notes |
---|---|---|---|---|---
| 1 | 1 | Opacity  | 0 | N | Controls layer's transparency |
| 2 | 1 | Red | 127 | N | Subtractive 0-126, Additive 128 - 255 |
| 3 | 1 | Green | 127 | N | Subtractive 0-126, Additive 128 - 255 |
| 4 | 1 | Blue | 127 | N | Subtractive 0-126, Additive 128 - 255 |
| 5 | 1 | Brightness | 127 | N | |
| 6 | 1 | Contrast | 127 | N | |
| 7 | 1 | Texture Folder  | 0 | **Y** | Folder 255; see [Video and Utility Inputs](video-and-utility-inputs) |
| 8 | 1 | Texture File  | 0 | **Y** | |
| 9 | 1 | Play Mode  | 0 | **Y** | see [Play Modes](#play-modes) |
| 10 | 1 | Play Speed  | 127  | N | see [Play Speed](#play-speed) |
| 11 | 2 | In Frame  | 0 | N | |
| 13 | 2 | Out Frame  | 65535  | N | |
| 15 | 1 | Sync Stream | 0 | **Y** | see [Sync Stream](#sync-stream) |
| 16 | 1 | Sync Offset | 127  | *N* | One point in value equals one frame, positive or negative |
| 17 | 1 | Frame Blending | 255 | N | see [Frame Blending Control](#frame-blending-control) |
| 18 | 1 | Texture XFade Type  | 0 | **Y** | see [Transitions](#transitions) |
| 19 | 1 | Texture XFade Timing  | 0 | **Y** | |
| 20 | 1 | Object File  | 0 | **Y** |  |
| 21 | 2 | X Position  | 32767  | N | |
| 23 | 2 | Y Position  | 32767  | N | |
| 25 | 2 | Scale  | 32767  | N | Overall scale X, Y, & Z |
| 27 | 2 | X Scale  | 32767  | N | |
| 29 | 2 | Y Scale  | 32767  | N | |
| 31  | 2 | Z Rotation  | 32767  | N | |
| 33 | 2 | X Rotation  | 32767  | N | |
| 35 | 2 | Y Rotation  | 32767  | N | |
| 37 | 1 | Mix Select | 0 | **Y** | Selects which Mix the layer is assigned to |
| 38 | 1 | Mix Center/Scale | 0 | **Y** | see [Layer Mix Modes](#layer-mix-modes) |
| 39 | 1 | Layer Blend Mode/Draw Mode  | 0 | **Y** | see [Blend Modes](#blend-modes) |
| 40 | 1 | Layer Draw Mode  | 0 | **Y** | see [Draw Modes](#draw-modes) |
| 41 | 1 | Image Remap | 0 | **Y** | Selects which Image Remapping configuration the layer uses |
| | **41**  | **TOTAL DMX CHANNELS** | | | |

### Layer FX
*(Optional,  1 per Layer)*

| Channel | Size | Function | Default | Snap | Notes |
---|---|---|---|---|---
| 1 | 1 | Layer Effect 1 | 0 | **Y** | see [Combined Effects](#combined-effects) |
| 2 | 1 | Layer Effect Modifier a | 0 | N | |
| 3 | 1 | Layer Effect Modifier b | 0 | N | |
| 4 | 1 | Layer Effect Modifier c | 0 | N | |
| 5 | 1 | Layer Effect Modifier d | 0 | N | |
| 6 | 1 | Layer Effect Modifier e | 0 | N | |
| | **6**  | **TOTAL DMX CHANNELS** | | | |

### Layer Volume
*(Optional, 1 per Layer)*

| Channel | Size | Function | Default | Snap | Notes |
---|---|---|---|---|---
| 1 | 1 | Layer Volume Control | 255 | N | |
| | **1**  | **TOTAL DMX CHANNELS** | | | |

### Layer DMX Timecode
*(Optional, 1 per Layer)*

| Channel | Size | Function | Default | Snap | Notes |
---|---|---|---|---|---
| 1  | 1 | Hours | 0 | N | 0-23 > Setting value beyond its normal range will invalidate all TC DMX controls for the layer |
| 2 | 1 | Minutes  | 0 | N | 0-59 > Setting value beyond its normal range will invalidate all TC DMX controls for the layer |
| 3 | 1 | Seconds  | 0 | N | 0-59 > Setting value beyond its normal range will invalidate all TC DMX controls for the layer |
| 4 | 1 | Frames  | 0 | N | 0-29 > Setting value beyond its normal range will invalidate all TC DMX controls for the layer |
| | **4**  | **TOTAL DMX CHANNELS** | | | |

## Pixel Mapping Group Control

*Optional, for controlling pixel mapping groups - add one per Pixel Mapping Group, 2000 max)*

| Channel | Size | Function | Default | Snap | Notes |
---|---|---|---|---|---
| 1 | 1 | Control Mode | 0 | **Y** | see [Pixel Mapping Group Control Modes](#pixel-mapping-group-control-modes) |
| 2 | 1 | Intensity/Crossfade | 255 | N | Used as Intensity or Crossfade depending on the selected control mode |
| 3 | 1 | Red/Cyan | 255/0 | N | Used as Red with RGB control modes, and as Cyan with CMY control modes |
| 4 | 1 | Green/Magenta | 255/0 | N | Used as Green with RGB control modes, and as Magenta with CMY control modes |
| 5 | 1 | Blue/Yellow | 255/0 | N | Used as Blue with RGB control modes, and as Yellow with CMY control modes |
| | **5**  | **TOTAL DMX CHANNELS** | | | |

## Channel Definitions

### Global Master Control Channel

|Value|Command| Notes |Macro Trigger Action|Master Control Selector|
---|---|---|---|---
| 10-19  | Output Stats HUD | Shows output size, refresh, rendering stats | n/a | n/a |
| 20-29  | Performance HUD | Shows overall performance, playback, rendering, etc. | n/a | n/a |
| 30-39  | Version HUD | Shows software revision, share name, user defined name | n/a | n/a |
| 40-49  | Lights/Master/Shutter/Keystone HUD - Output 1 Control Input Universe A| | n/a | n/a |
| 50-54  | Texture HUD - Layers 1-6, Output 1 Control Input Universe A| | n/a | n/a |
| 60-64  | Effects HUD - Layers 1-6, Output 1 Control Input Universe A| | n/a | n/a |
| 70-71  | Raw Control Input HUD Universe A| | n/a | n/a |
| 72-73  | Raw Control Input HUD Universe B| | n/a | n/a |
| 74-75  | Raw Control Input HUD Universe C| | n/a | n/a |
| 80-89  | Show Pix-map Context View | 80 = All contexts, 81-89 = context 1-9  | n/a | n/a |
| 110-111  | Show Timecode HUD (Center) | | n/a | n/a |
| 112-113  | Show Timecode HUD (Top Right) | | n/a | n/a |
| 114-115  | Show Timecode HUD (Top Left) | | n/a | n/a |
| 116-117  | Show Timecode HUD (Bottom Right) | | n/a | n/a |
| 118-119  | Show Timecode HUD (Bottom Left) | | n/a | n/a |
| 201  | Run Script | Runs indexed shell script or AppleScript from /Mbox /plugins/scripts | Value then 0 | 0-255 for script # |
| 202  | Change Pixel Mapping File | Switches indexed PixMap config from /Mbox/PixelMapping/ | Value then 0 | 0-255 for config # |
| 220  | Cancel Keyboard HUD | | Value then 0 | n/a |
| 221  | Show Object Mesh | Shows white transparent mesh on objects | n/a | 0 = all, 1-24 = by layer # |
| 222  | Show Edge-blend Guides | Shows guidelines for blend areas | n/a | n/a |
| 224  | Show Single Mix | Shows outline of one mix at a time | n/a | Mix # |  
| 225  | Show All Mixes | Shows outlines of all mixes at the same time | n/a | n/a |
| 226  | Show Output Mixes Only | Shows outlines of all +Output+mixes at the same time | n/a | n/a |
| 227  | Show Keystone Mesh | Shows white transparent mesh on keystone objects | n/a | 0 = all, 1-32 = by output # |
| 230  | File Sharing On | | Value then 0 | n/a |
| 231  | File Sharing Off | | Value then 0 | n/a |
| 232  | Remote Management On | | Value then 0 | n/a |
| 233  | Remote Management Off | | Value then 0 | n/a |
| 234  | Backup Mode On | Backup mode disables Layer Sync and PixMap output | Value then 0 | n/a |
| 235  | Backup Mode Off | Re-enable Layer Sync/PixMap output | Value then 0 | n/a |
| 240  | Rescan Media Library | | Hold 3-sec then 0 | n/a |
| 244  | Pixel Mapping Output Enable | Turn ON pixel mapping engine and output | Value then 0 | n/a |
| 245  | Pixel Mapping Output Disable | Turn OFF pixel mapping engine and output | Value then 0 | n/a |
| 246  | Pixel Mapping Masking Off | Masked fixtures use normal Mbox output | Value then 0 | n/a |
| 247  | Pixel Mapping Masking On | Forces masked fixtures' output to 0 | Value then 0 | n/a |
| 250  | Quit Mbox Application | | Hold 3-sec then 0 | n/a |
| 251  | Shutdown Computer | | Hold 3-sec then 0 | n/a |
| 252  | Restart Computer | | Hold 3-sec then 0 | n/a |
| 253  | Restart Mbox Application | | Hold 3-sec then 0 | n/a |
| 254  | Restart Daemon Application | | Hold 3-sec then 0 | n/a |

### Video and Utility Inputs
*Texture Folder 255 is reserved for special uses such as selecting video/syphon inputs or copying layers:*

| Texture Value | Input |
---|---
| 0  | Patch Info Display |
| 1 | Copy Layer 1 FX+ |
| 2 | Copy Layer 2 FX+ |
| 3 | Copy Layer 3 FX+ |
| 4 | Copy Layer 4 FX+ |
| 5 | Copy Layer 5 FX+ |
| 6 | Copy Layer 6 FX+ |
| 31 | Copy Layer 1 raw |
| 32 | Copy Layer 2 raw |
| 33 | Copy Layer 3 raw |
| 34 | Copy Layer 4 raw |
| 35 | Copy Layer 5 raw |
| 36 | Copy Layer 6 raw |
| 201 | Syphon Input 1 |
| 202 | Syphon Input 2 |
| 231 | CG Color Black |
| 232 | CG Color White |
| 233 | CG Color Red |
| 234 | CG Color Green |
| 235 | CG Color Blue |
| 236 | CG Color Cyan |
| 237 | CG Color Magenta |
| 238 | CG Color Yellow |
| 241  | Video Input 1 |
| 242  | Video Input 2 |
| 254 | CG Color Bars |
| 255 | Null Image |

### Play Modes

|Value| Play Mode |
---|---
| 0  | Forward Loop |
| 1  | Forward Loop, Pause when Layer Opacity = 0 |
| 2  | Forward Loop, Pause and Reset to In-Point when Layer Opacity = 0 |
| 10  | Reverse Loop |
| 11  | Reverse Loop, Pause when Layer Opacity = 0 |
| 12  | Reverse Loop, Pause and Reset to In-Point when Layer Opacity = 0 |
| 20  | Forward Once |
| 21  | Forward Once, Pause when Layer Opacity = 0 |
| 22  | Forward Once, Pause and Reset to In-Point when Layer Opacity = 0 |
| 30  | Reverse Once |
| 31  | Reverse Once, Pause when Layer Opacity = 0 |
| 32  | Reverse Once, Pause and Reset to In-Point when Layer Opacity = 0 |
| 40  | Forward Bounce |
| 50  | Reverse Bounce |
| 60  | Random |
| 70  | Forward Once - Restart on In Frame Change |
| 80  | Scrub - In Frame |
| 90  | Scrub - Out Frame |
| 100  | Forward Loop - Crossfade on Out Frame |
| 110  | Reverse Loop - Crossfade on In Frame |
| 120  | Forward Loop - Restart on In Frame Change |
| 130  | Timecode sync - strict lock |
| 135  | Timecode sync - sync then freewheel |
| 136  | Timecode sync - jam sync |
| 140  | Layer Slave |
| 150  | Layer Master - Forward Loop |
| 160  | Layer Master - Forward Once |
| 180  | Kiosk Mode - play once through folder |
| 181  | Kiosk Mode - play once through folder, loop last file |
| 182  | Kiosk Mode - play once through folder, fade out last file |
| 185  | Kiosk Mode - play through folder then loop |
| 190  | Kiosk Mode - timecode |
| 240  | Play out Mode - last 5 seconds |
| 241  | Play out Mode - last 10 seconds |
| 242  | Play out Mode - last 15 seconds |
| 243  | Play out Mode - last 20 seconds |
| 244  | Play out Mode - last 30 seconds |
| 255  | Restart Movie from In Point |

### Play Speed

|Value| Play speed |
---|---
| 0  | Paused |
| 1-126  | Increasing speeds from paused to normal |
| 127  | Normal Speed - movie fps |
| 128  | Compensated speed - match output refresh rate (with +/- ~5% deviation) |
| 129-255  | Increasing speeds from normal to 4x normal |

### Sync Stream

|Value| Mode | Notes |
---|---|---
| 0 | Layer to Layer Stream (default) | |
| 1-96 | Stream number | Can only output 8 streams |

### Frame Blending Control

0 = no frame blending (more accurately, blend time = 0)
1 - 255 = variable frame blend time, as a proportion of the frame time. This is a square-law control, and 50 blend time is achieved at DMX 210, 25 blend time at DMX 165

## Combined Effects
>**Notes:**
>* The Combined Effects for Mbox Studio v4.0's Layer fixtures include all effects listed below.
>* The Output Master fixture is only able to use Effects 1 - 200
> * Due to GitHub formatting scroll right for Mod.5


|Value | Effect | Description | Mod.1 | Mod.2 | Mod.3 |  Mod.4 |  Mod.5 |
---|---|---|---|---|---|---|---
| 0 | NONE | no effect  | | | | | |
| 1 | Hue | hue adjustment | hue angle | | | | |
| 2 | Hue and Saturation | combines hue and saturation effect | hue angle (127=def.) | saturation (127=def.) | | |  |
| 3 | Gamma | gamma adjustment | gamma | | | | |
| 4 | Exposure | exposure adjustment | exposure | | | | |
| 5 | Monochrome | convert colors to grayscale | amount | red | green | blue | alpha |
| 6 | Sepia Tone | convert colors to sepia tone image | amount | | | | |
| 7 | Invert | color invert  | | | | | |
| 8 | Hilight & Shadow | adjusts tonal mapping | radius | highlight amount | shadow amount | | |
| 9 | Vibrance | adjusts saturation | amount | | | | |
| 10 | Solarize | solarize effect | intensity  | | | | |
| 11 | X-Ray | inverted grayscale | intensity  | | | | |
| 12 | Color Switch | RGB->RBG/BGR/BRG/GBR/GRB | intensity | mode | | | |
| 13 | Color Shift | dynamic color shift (sine function) | mixer | range | speed | | |
| 14 | Posterize | reduce color space | amount | | | | |
| 15 | Bloom | soften edges, add glow | intensity | radius | | | |
| 16 | Gloom | dulls highlights | intensity | radius | | | |
| 17 | Sharpen | increases image detail by sharpening | sharpness | | | | |
| 18 | Unsharp Mask | increases image detail by sharpening | intensity | radius | | | |
| 19 | Median | reduce noise with median calculation | | | | | |
| 20 | Black Threshold | renders black areas as true black | intensity | threshold | | | |
| 21-31 | Reserved | n/a | | | | | |
| 32 | Blur - Quick | simple/quick image blur | mixer | amount | | | |
| 33 | Blur - QuickX | quick blur on x axis | mixer | amount | | | |
| 34 | Blur - QuickY | quick blur on y axis | mixer | amount | | | |
| 35 | Blur - Box | box-shaped convolution | radius | | | | |
| 36 | Blur - Gaussian | more sophisticated/slow blur | radius | | | | |
| 37 | Blur - Zoom | blurs from center of image | size | x position | y position | | |
| 38 | Blur - Motion | blurs along a variable axis | radius | angle | | | |
| 39-43 | Reserved | n/a | | | | | |
| 44 | Key - Black | dark areas transparent | intensity | threshold | | | |
| 45 | Key - White | white areas transparent | intensity | threshold | | | |
| 46 | Key - Red | red areas transparent | intensity | threshold | | | |
| 47 | Key - Green | green areas transparent | intensity | threshold | | | |
| 48 | Key - Blue | blue areas transparent | intensity | threshold | | | |
| 49 | Key - Invert White | everything but white areas transparent | intensity | threshold | | | |
| 50 | Key - Invert Red | everything but red areas transparent | intensity | threshold | | | |
| 51 | Key - Invert Green | everything but green areas transparent | intensity | threshold | | | |
| 52 | Key - Invert Blue | everything but blue areas transparent | intensity | threshold | | | |
| 53 | Key - RGB | specific RGB color transparent | intensity | threshold | red | green | blue |
| 54 | Key - HSV | specific HSV color transparent | intensity | threshold | hue | saturation | value |
| 55 | Key - XY | specific XY location color transparent | intensity | threshold | x position | y position | |
| 56 | Key - Luma | renders bright areas transparent | intensity | threshold | | | |
| 57 | Key - Luma Inverse | renders dark areas transparent | intensity | threshold | | | |
| 58-63 | Reserved | n/a | | | | | |
| 64 | Crop - Circular | circular image crop with edge blur | mixer | size | edge | | |
| 65 | Crop - Rectangular | rectangular image crop with edge blur | mixer | size | edge | | |
| 66 | Crop - Circular XY | circ image crop with edge blur & X/Y position ctrl | mixer | size | edge | x position (127=def.) | x position (127=def.) |
| 67 | Crop - Rectangular XY | rect image crop with edge blur & X/Y position ctrl | mixer | size | edge | x position (127=def.) | x position (127=def.) |
| 68 | Crop - Oval XY | oval image crop with edge blur & X/Y position ctrl | size | edge | x position (127=def.) | y position (127=def.) | aspect |
| 69 | Crop - Horizontal | horizontal 90° shutters | mixer | width | center (127=def.) | | |
| 70 | Crop - Vertical | vertical 90° shutters | mixer | height | center (127=def.) | | |
| 71 | Crop - Orth Shutter | horizontal & vertical 90° shutters | mixer | H insertion | V insertion | | |
| 72 | Crop - Slitscan Horizontal | horizontal 90° shutters | mixer | width | center (127=def.) | | |
| 73 | Crop - Slitscan Vertical | vertical 90° shutters | mixer | height | center (127=def.) | | |
| 74 | Crop - Slitscan Horizontal Swing | horizontal shutters with motion | mixer | width | scanrate | swing | |
| 75 | Crop - Slitscan Vertical Swing | vertical shutters with motion | mixer | height | scanrate | swing | |
| 76 | Crop - Slitscan Horizontal Random Swing | horizontal shutters with random motion | mixer | width | scanrate | swing | |
| 77 | Crop - Slitscan Vertical Random Swing | vertical shutters with random motion | mixer | height | scanrate | swing | |
| 78-80 | Reserved | n/a | | | | | |
| 81 | Layer Edge Blend Right | per-layer edge blend on right side | amount | edge softness | | | |
| 82 | Layer Edge Blend Left | per-layer edge blend on left side | amount | edge softness | | | |
| 83 | Layer Edge Blend Top | per-layer edge blend on top side | amount | edge softness | | | |
| 84 | Layer Edge Blend Bottom | per-layer edge blend on bottom side | amount | edge softness | | | |
| 85 | Layer Edge Blend L/R | per-layer edge blend on left and right sides | left amount | left edge softness | right amount | right edge softness | |
| 86 | Layer Edge Blend T/B | per-layer edge blend on top and bottom sides | top amount | top edge softness | bottom amount | bottom edge softness | |
| 87-89 | Reserved | n/a | | | | | |
| 90 | Mask from File | creates mask using external file w/ alpha | mixer | file # | flip mode 0-7 | | |
| 91 | Matte from Layer | creates alpha matte using selected layer | mixer | 1 - 24 = layer w/o FX, 101 - 124 = layer w/ FX | mode<sup>1</sup> | | |
| 92 | UV Map from Layer | uses red/green to generate texture coordinates for uv mapping image | mode<sup>2</sup> | layer | distort amount (mode 0) | | |
| 93-95 | Reserved | n/a | | | | | |
| 96 | Distortion - Bump | bump distortion | radius | scale | x position | y position | |
| 97 | Distortion - Linear Bump | linear bump distortion | radius | angle | scale | x position | y position |
| 98 | Distortion - Hole | hole distortion | radius | x position | y position | | |
| 99 | Distortion - Pinch | pinch distortion | radius | scale | x position | y position | |
| 100 | Distortion - Torus | torus distortion  | width | radius | x position | y position | |
| 101 | Distortion - Twirl | twirl distortion | radius | angle | x position | y position | |
| 102 | Distortion - Vortex | vortex distortion | radius | angle | x position | y position | |
| 103 | Distortion - Lozenge | lozenge distortion | radius | refraction | point 1 | point 2 | |
| 104 | Distortion - Circular Wrap | wraps image into tube shape | radius | angle | x position | y position | |
| 105 | Distortion - Circular Splash | clamps image from center outwards | size | x position | y position | | |
| 106 | Distortion - Glass | ? | layer | scale | x position | y position | |
| 107 | Distortion - Displacement | ? | layer | scale | | | |
| 108-112 | Reserved | n/a | | | | | |
| 113 | Smear - Horizontal | spread single column over horizontal space | mixer | column | | | |
| 114 | Smear - Vertical | spread single row over vertical space | mixer | row | | | |
| 115-117 | Reserved | n/a | | | | | |
| 118 | Pixellate - Square | pixellates image, square | scale | x position | y position | | |
| 119 | Pixellate - Hexagonal | pixellates image, hexagonal | scale | x position | y position | | |
| 120 | Crystallize | break up into crystal pattern | radius | x position | y position | | |
| 121 | Pointillize | break image into points | radius | x position | y position | | |
| 122-126 | Reserved | n/a | | | | | |
| 127 | Tile - 1 | image tiling | mixer | divisions | | | |
| 128 | Tile - 2 | image tiling | mixer | horizontal divisions | horizontal spacing | vertical divisions | vertical spacing|
| 129 | Tile - Glide Reflected | rectangular Tile Effect | angle | width | x position | y position | |
| 130 | Tile - 4-fold Rotated | four-sided Tile Effect | angle | acute angle | width | x position | y position |
| 131 | Tile - 4-fold Reflected | four-sided Tile Effect | angle | acute angle | width | x position | y position |
| 132 | Tile - 4-fold Translated | four-sided Tile Effect | angle | width | x position | y position | |
| 133 | Tile - 6-fold Rotated | six-sided Tile Effects | angle | width | x position | y position | |
| 134 | Tile - 6-fold Reflected | six-sided Tile Effect | angle | width | x position | y position | |
| 135 | Tile - 8-fold Reflected | eight-sided Tile Effect | angle | width | x position | y position | |
| 136 | Tile - 12-fold Reflected | twelve-sided Tile Effect | angle | width | x position | y position | |
| 137 | Tile - Parallelogram | ? | angle | acute angle | width | x position | y position |
| 138 | Tile - Triangle | ? | angle | width | x position | y position | |
| 139-143 | Reserved | n/a | | | | | |
| 144 | Screen - Line | line patterned halftone screen | width | angle | sharpness | | |
| 145 | Screen - Circular | circular shaped halftone screen | width | sharpness |  x position | y position | |
| 146 | Screen - Dot | dot patterned halftone screen | width | angle | sharpness | | |
| 147 | Screen - Hatched | hatch patterned halftone screen | width | angle | sharpness | | |
| 148 | Screen - CMYK Halftone | color, halftoned rendition | width | angle | sharpness | GCR | UCR |
| 149-152 | Reserved | n/a | | | | | |
| 153 | Decay | Creates decay trails | mixer | amount | | | |
| 154 | Black&White | convert image to transparent/color | mixer | threshold | red | green | blue |
| 155 | Mirrors | various mirror modes | mixer | mode | | | |
| 156 | Horizontal Bars | break image into bars | mixer | number | width | | |
| 157 | Vertical Bars | break image into bars | mixer | number | width | | |
| 158 | Double Vision | offset image and overlay | mixer | x offset | y offset | | |
| 159 | Rippling | simple ripple effect | mixer | size | granularity | | |
| 160 | Flicker | dynamic flickering effect |mixer |  size | speed | | |
| 161 | Shake 2D | dynamic shaking effect | mixer | size | speed | | |
| 162 | Wobble | dynamic wobbling effect | mixer | size | speed | | |
| 163 | Edge Work | B&W conversion | radius  | | | | |
| 164 | Edge Detect | edge detection with color | intensity | | | | |
| 165 | Kaleidoscope | geometric distortion | angle | divisions | | | |
| 166 | LED Wall | break up into dots | mixer | dot amount | dot size | | |
| 167 | Op Tile | glass block tile effect | scale | width | angle | x position | y position |
| 168 | Luma Lines | uses color and luma averaging to create line effect | mixer | width | rows | gap | |
| 169 | Luma Blocks | uses color and luma averaging to create block effect  | mixer | width | rows | gap | |
| 170 | Lattice - Positive | divides image into rectangles | mixer | divisions | size | | |
| 171 | Lattice - Negative | reverse of pos lattice | mixer | divisions | size | | |
| 172 | Duotone - Simple | two-color duotone effect | mixer | mode | threshold | | |
| 173 | Duotone - Hue&Saturation | duotone effect using H+S selection | threshold | hue 1 | saturation 1 | hue 2 | saturation 2 |
| 174 | Channel Shift | separates RGB channels | mixer | horizontal offset | vertical offset | | |
| 175 | ASCII Art | classic ASCII art effect | mixer | scale | saturation | | |
| 176 | MetaImage | uses plugin image<sup>3</sup> to replace sampled areas in source image | mixer | file | scale | saturation | |
| 177 | Drop Shadow 1 | drop shadow effect  | intensity | softness | x offset | y offset | |
| 178 | Drop Shadow 2 | drop shadow effect | intensity | offset | | | |
| 179 | Roll - Down | vertical roll | mixer | speed | pause | | |
| 180 | Roll - Up | vertical roll up | mixer | speed | pause | | |
| 181 | Roll - Right | horizontal roll | mixer | speed | pause | | |
| 182 | Roll - Left | horizontal roll left | mixer | speed | pause | | |
| 183 | Freeze | freezes image | amount: 0 = off, 1 - 254 increasing, 255 = frozen | | | | |
| 184 | Droste | ? | strands | period | rotation | zoom | |
| 185 | Comic Effect | posterizing/halftone effect | | | | | |
| 186 | Cartoon | cartoon effect | mixer | line width | color reduction | | |
| 187 | Shaded Material | luma in input image creates relief map | layer # | scale | | | |
| 188 | Histogram | ? | height | high limit | low limit | | |
| 189 | Roll - XY | horizontal and vertical roll | mixer | x amount | y amount | | |
| 190-220 | Reserved | n/a | | | | | |
| 221 | LRBT Shutter | mask sides of layer | left | right | bottom | top | |
| 222 | Move Center | shift rotational center of image | X (127=def.) | Y (127=def.) | | | |
| 223 | Shake 3D | X/Y shake effect | X | Y | | | |
| 224 | Strobe | strobe effect | off time | on time | | | |
| 225 | Object Tile | tiling effect | number | spacing | | | |
| 226 | Texture Scale/Rotation | adjusts scale & rotation of texture on gobos | scale | rotation | | | |
| 227 | Texture X/Y Position | adjusts X/Y position of texture on gobos | X | Y | | | |
| 228 | X/Y Pos & Scale Damping | damps movement of parameters in 1/30 sec increments | X/Y Position amount | Scale amount | | | |
| 229 | Z Rot & Scale Damping | damps movement of parameters in 1/30 sec increments | Z Rotation amount | Scale amount | | | |
| 230 | Texture Flip | Flips texture drawing on objects | Mode 0>31=X, 32>63=nil, 64>95=XY, 96>127=Y, 128>159=XZ, 160>191=Z, 192>223=XYZ, 224>255=YZ | | | | |
| 231 | Spin | Spins objects | Z Spin: 0=Home, 1-126=Spin Rev, 127=Stop, 128-255=SpinFwd | X Spin: same as Z | Y Spin: same as Z | | |

>**Notes:**
> 1) Mode info for Effect 91 = Matte From Layer
>
> | Value | Description |
> ---|---
> | 0 | Luma |
> | 1 | Luma Invert |
> | 2 | Red |
> | 3 | Red Invert |
> | 4 | Green |
> | 5 | Green Invert |
> | 6 | Blue |
> | 7 | Blue Invert |
> | 8 | Alpha |
> | 9 | Alpha Invert |
>
> 2) Mode info for Effect 92 = UV Map From Layer
>
> | Value | Description |
> ---|---
> | 0 | UV Distortion |
> | 1 | 8/16 bit RG No Flip |
> | 2 | 8/16 bit RG H Flip |
> | 3 | 8/16 bit RG V Flip |
> | 4 | 8/16 bit RG HV Flip |
> | 5 | 12 bit RG No Flip |
> | 6 | 12 bit RG H Flip |
> | 7 | 12 bit RG V Flip |
> | 8 | 12 bit RG HV Flip |
> | 9 | 16 bit RG+BA No Flip |
> | 10 | 16 bit RG+BA H Flip |
> | 11 | 16 bit RG+BA V Flip |
> | 12 | 16 bit RG+BA HV Flip |
>
> 3) Plugin image (PNG or JPG) for the 176 MetaImage effect must be located in /Mbox/plugins/images/masks and must have an 8-bit index number.  File should > be 900x75 pixels, with twelve 75x75 square areas in dark to light progression left to right.


### Transitions

|Value| Transition |  Description |
---|---|---
| 0 | Dissolve  | dissolve (EX1) |
| 1  | Dissolve2  | dissolve |
| 2  | Wipe Right  | slightly blended left to right wipe |
 | 3  | Wipe Left  | slightly blended right to left wipe |
| 4  | Wipe Down  | slightly blended top to bottom wipe |
| 5  | Wipe Up  | slightly blended bottom to top wipe |
| 6  | Wipe Diagonal  | slightly blended diagonal wipe |
| 7  | Wash Right  | more blended left to right |
 | 8  | Wash Left  | more blended right to left |
| 9  | Wash Down  | more blended top to bottom |
| 10  | Wash Up  | more blended bottom to top |
| 11  | Wash Diagonal  | more blended diagonal |
| 12  | White Right  | blended white stripe left to right |
| 13  | White Left  | blended white stripe right to left |
| 14  | White Down  | blended white stripe top to bottom |
| 15  | White Up  | blended white stripe bottom to top |
| 16  | White Diagonal  | blended white stripe diagonal |
| 17  | Through Black  | fade to black and back in |
| 18  | Through White  | fade to white and back in |
| 19  | Through Red  | fade to red and back in |
| 20  | Bright First  | transition by brightness of new image |
| 21  | Dark First  | transition by darkness of new image |
| 22  | Dots  | fade with small dots |
| 23  | Big Dots  | fade with big dots |
| 24  | Burst  | white star burst transition |
| 25  | Flash  | white flash transition |
| 26  | Slow Dissolve | dissolve that comes in more slowly |
| 27  | Slower Dissolve | dissolve that comes in even more slowly |
| 28  | Rotate Left  | simple 3d rotate effect |
| 29  | Rotate Right  | simple 3d rotate effect |
| 30  | Rotate Down  | simple 3d rotate effect |
| 31  | Rotate Up  | simple 3d rotate effect |
| 32  | Rotate Center Vertical  | simple 3d rotate effect |
| 33  | Rotate Center Horizontal  | simple 3d rotate effect |
| 34  | Zoom Out  | zoom out and back in |
| 35  | Zoom In  | zoom in and back out |
| 36  | Horizontal Bars | 10 horizontal bars, hard edge |
| 37  | Horizontal Bars + Blend | 10 horizontal bars, blended edge |
| 38  | Vertical Bars | 20 vertical bars, hard edge |
| 39  | Vertical Bars + Blend | 20 vertical bars, blended edge |
| 40  | Circle Center | circle out from center |
| 41  | Circle Center + Blend | circle out from center, blended edge |
| 42  | Concentric Circles | circles out from center, blended edges |
| 43  | Push Right | new image pushes in left to right |
| 44  | Push Left | new image pushes in right to left |
| 45  | Push Down | new image pushes in top to bottom |
| 46  | Push Up | new image pushes in bottom to top |
| 47  | Split Right | old image splits and slides to the right |
| 48  | Split L/R Center | old image splits and slides left and right from the center |
| 49  | Split Down | old image splits and slides down |
| 50  | Split Up | old image splits and slides up |
| 51  | Split U/D Center | old image splits and slides up/down from the center |
| 52  | Split XY | old image splits slides out from center |
| 53  | Bar Swipe Right | old image slides to right in strips |
| 54  | Bar Swipe Left | old image slides to left in strips |
| 55  | Bar Swipe Up | old image slides upward in strips |
| 56  | Bar Swipe Down | old image slides downward in strips |
| 57  | Page Curl 1 | page corner curls from bottom-right to top-left |
| 58  | Page Curl 2 | page corner curls from top-right to bottom-left |
| 101-110  | Custom Hard-edge wipe 1-10 | hard-edge wipe using custom grayscale file |
| 111-120  | Custom Soft-edge wipe 1-10 | soft-edge wipe using custom grayscale file |
| 255  | Object Dissolve | fade out on current object, fade in on new object |

### Layer Mix Modes

This parameter defines how a layer's content will be cropped, centered, rotated, and/or scaled when assigned to a mix.

|Value | Mode (Name) | Fit H/V/H&V | Center Y/N | Cropping Y/N | Rotation Y/N | Description |
---|---|---|---|---|---|---
| 0 | Crop Only | N | N | Y | N | crops to mix boundary, no fit, no scale, no rotation  |
| 1 | Center, No crop | N | Y | N | N | content center is placed in center of Mix, no scale-to-fit, no rotation, NO CROP to mix boundary |
| 2 | Center, Crop | N | Y | Y | N | content center is placed in center of Mix, no scale-to-fit, no rotation, crops to mix boundary |
| 3 | Center, Horizontal Fit, No crop | H | Y | N | N | content center is placed in center of Mix, scale-to-fit mix horizontally, no rotation, NO CROP to mix boundary |
| 4 | Center, Horizontal Fit, Crop | H | Y | Y | N | content center is placed in center of Mix, scale-to-fit mix horizontally, no rotation, crops to mix boundary |
| 5 | Center, Vertical Fit, No crop | V | Y | N | N | content center is placed in center of Mix, scale-to-fit mix vertically, no rotation, NO CROP to mix boundary |
| 6 | Center, Vertical Fit, Crop | V | Y | Y | N | content center is placed in center of Mix, scale-to-fit mix vertically, no rotation, crops to mix boundary |
| 7 | Center, Horizontal & Vertical Fit, No crop | HV | Y | N | N | content center is placed in center of Mix, scale-to-fit mix horizontally & vertically, no rotation, NO CROP to mix boundary |
| 8 | Center, Horizontal & Vertical Fit, Crop | HV | Y | Y | N | content center is placed in center of Mix, scale-to-fit mix horizontally & vertically, no rotation, crops to mix boundary |
| 9 | Center, Best Fit, No Crop | B | Y | N | N | content center is placed in center of Mix, scale-to-fit mix horizontally or vertically, no rotation, NO CROP to mix boundary |
| 10 | Center, Best Fit, Crop | B | Y | Y | N | content center is placed in center of Mix, scale-to-fit mix horizontally or vertically, no rotation, crops to mix boundary |
| 11 | Center, Rotate, No crop | N | Y | N | Y | content center is placed in center of Mix, no scale-to-fit, rotated to match mix rotation, NO CROP to mix boundary |
| 12 | Center, Rotate, Crop | N | Y | Y | Y | content center is placed in center of Mix, no scale-to-fit, rotated to match mix rotation, crops to mix boundary |
| 13 | Center, Horizontal Fit, Rotate, No crop | H | Y | N | Y | content center is placed in center of Mix, scale-to-fit mix horizontally, rotated to match mix rotation, NO CROP to mix boundary |
| 14 | Center, Horizontal Fit, Rotate, Crop | H | Y | Y | Y | content center is placed in center of Mix, scale-to-fit mix horizontally, rotated to match mix rotation, crops to mix boundary |
| 15 | Center, Vertical Fit, Rotate, No crop | V | Y | N | Y | content center is placed in center of Mix, scale-to-fit mix vertically, rotated to match mix rotation, NO CROP to mix boundary |
| 16 | Center, Vertical Fit, Rotate, Crop | V | Y | Y | Y | content center is placed in center of Mix, scale-to-fit mix vertically, rotated to match mix rotation, crops to mix boundary |
| 17 | Center, Horizontal & Vertical Fit, Rotate, No crop | HV | Y | N | Y | content center is placed in center of Mix, scale-to-fit mix horizontally & vertically, rotated to match mix rotation, NO CROP to mix boundary |
| 18 | Center, Horizontal & Vertical Fit, Rotate, Crop | HV | Y | Y | Y | content center is placed in center of Mix, scale-to-fit mix horizontally & vertically, rotated to match mix rotation, crops to mix boundary |
| 19 | Center, Best Fit, Rotate | B | Y | N | Y | content center is placed in center of Mix, scale-to-fit mix horizontally or vertically, rotated to match mix rotation, NO CROP to mix boundary |
| 20 | Center, Best Fit, Rotate, Crop | B | Y | Y | Y | content center is placed in center of Mix, scale-to-fit mix horizontally or vertically, rotated to match mix rotation, crops to mix boundary |
| 21 | Horizontal Fit, No crop | H | N | N | N | content is not centered in Mix, scale-to-fit mix horizontally, no rotation, NO CROP to mix boundary |
| 22 | Horizontal Fit, Crop | H | N | Y | N | content is not centered in Mix, scale-to-fit mix horizontally, no rotation, crops to mix boundary |
| 23 | Vertical Fit, No crop | V | N | N | N | content is not centered in Mix, scale-to-fit mix vertically, no rotation, NO CROP to mix boundary |
| 24 | Vertical Fit, Crop | V | N | Y | N | content is not centered in Mix, scale-to-fit mix vertically, no rotation, crops to mix boundary |
| 25 | Horizontal & Vertical Fit, No crop | HV | N | N | N | content is not centered in Mix, scale-to-fit mix horizontally & vertically, no rotation, NO CROP to mix boundary |
| 26 | Horizontal & Vertical Fit, Crop | HV | N | Y | N | content is not centered in Mix, scale-to-fit mix horizontally & vertically, no rotation, crops to mix boundary |
| 27 | Best Fit, No Crop | B | N | N | N | content is not centered in Mix, scale-to-fit mix horizontally or vertically, no rotation, NO CROP to mix boundary |
| 28 | Best Fit, Crop | B | N | Y | N | content is not centered in Mix, scale-to-fit mix horizontally or vertically, no rotation, crops to mix boundary |
| 31 | Horizontal Fit, Rotate, No crop | H | N | N | Y | content is not centered in Mix, scale-to-fit mix horizontally, rotated to match mix rotation, NO CROP to mix boundary |
| 32 | Horizontal Fit, Rotate, Crop | H | N | Y | Y | content is not centered in Mix, scale-to-fit mix horizontally, rotated to match mix rotation, crops to mix boundary |
| 33 | Vertical Fit, Rotate, No crop | V | N | N | Y | content is not centered in Mix, scale-to-fit mix vertically, rotated to match mix rotation, NO CROP to mix boundary |
| 34 | Vertical Fit, Rotate, Crop | V | N | Y | Y | content is not centered in Mix, scale-to-fit mix vertically, rotated to match mix rotation, crops to mix boundary |
| 35 | Horizontal & Vertical Fit, Rotate, No crop | HV | N | N | Y | content is not centered in Mix, scale-to-fit mix horizontally & vertically, rotated to match mix rotation, NO CROP to mix boundary |
| 36 | Horizontal & Vertical Fit, Rotate, Crop | HV | N | Y | Y | content is not centered in Mix, scale-to-fit mix horizontally & vertically, rotated to match mix rotation, crops to mix boundary |
| 37 | Best Fit, Rotate, No Crop | B | N | N | Y | content is not centered in Mix, scale-to-fit mix horizontally or vertically, rotated to match mix rotation, NO CROP to mix boundary |
| 38 | Best Fit, Rotate, Crop | B | N | Y | Y | content is not centered in Mix, scale-to-fit mix horizontally or vertically, rotated to match mix rotation, crops to mix boundary |

### Blend Modes

|Value | Blend Mode | Description |
---|---|---
| 0 | Standard | no blending  |
| 1 | Additive | layer’s colors are added to underlying colors (blacks appear transparent) |
| 2 | Screen | similar to Additive, with less of underlying color (blacks appear transparent) |
| 3 | Multiply | multiplies layer’s color with underlying color (blacks appear opaque) |
| 4 | Subtractive | layer’s colors are subtracted from underlying colors (blacks appear transparent) |
| 5 | Exclusion | underlying colors are inverted where layer color is lighter; layer’s colors are then added to underlying colors (blacks appear transparent) |
| 6 | Invert Subtractive | underlying colors are subtracted from layer’s colors (blacks appear opaque) |
| 7 | Invert Additive | layer’s colors are inverted and are added to inverse of underlying colors (blacks appear transparent) |

## Draw Modes

|Value | Draw Mode | Description |
---|---|---
| 0 | No Draw Mode | no effect |
| 1 | Light/Trim | automatic ambient lighting of object/trims edge of backgrounds |
| 2 | Cut | cuts holes in stencil mask |
| 3 | Cut + Light | as above w/ lighting |
| 4 | Cut & Draw | as mode 2 but texture is drawn on object too |
| 5 | Cut & Draw + Light | as above w/ lighting |
| 6 | Draw thru Stencil | this layer's texture is drawn where holes have been cut in stencil |
| 7 | Draw thru Stencil + Light | as above w/ lighting |
| 8 | Draw onto Stencil | this layer's texture is drawn where stencil is not cut |
| 9 | Draw onto Stencil + Light | as above w/ lighting |
| 14 | Opacity fades to Black | opacity on layer fades to black rather than transparent |

## Pixel Mapping Group Control Modes

The modes listed below are used with the Pixel Mapping Group Control fixture.  The mode selected affects how the other controls and/or merge input data will affect the Mbox output.  The use of HTP modes with CMY color inversion (modes 107 & 108) is not recommended.

|Value | Control Mode | Description |
---|---|---
| 0 | Off | no effect  |
| 1 | IRGB Master | RGB controls act as inhibitive submasters for Mbox’s RGB data on all fixtures in the group and Intensity control masters the final output |
| 2 | IRGB Replace | RGB controls generate a color that replaces Mbox’s RGB data for all fixtures in the group and the Intensity control masters the final output |
| 3 | IRGB Master, Merge Replace | merge data replaces Mbox’s output and is then mastered by the group IRGB controls |
| 4 | IRGB Master, Merge Multiply | RGB controls act as inhibitive submasters for incoming merge data.  Mbox data is then multiplied by the result of the first operation and the Intensity control masters the final output |
| 5 | RGB Master, Merge XFade | RGB controls act as inhibitive submasters for Mbox’s RGB data on all fixtures in the group, and the intensity control is used to crossfade between that result and the merge data |
| 6 | RGB Replace, XFade | RGB controls generate a color that replaces Mbox’s RGB data for all fixtures in the group, and the intensity control is used to crossfade between that result and the Mbox data |
| 7 | IRGB Master, Merge HTP | merge data and Mbox data are merged using HTP, the result is then mastered by the group IRGB controls |
| 8 | RGB Replace, HTP | RGB controls generate a color that is HTP merged with Mbox’s data and the result is mastered by the group intensity control |
| 101 | ICMY Master | RGB controls act as inhibitive submasters for Mbox’s RGB data (using CMY inversion) on all fixtures in the group and Intensity control masters the final output |
| 102 | ICMY Replace | RGB controls generate a color (using CMY inversion) that replaces Mbox’s RGB data for all fixtures in the group and the Intensity control masters the final output |
| 103 | ICMY Master, Merge Replace | merge data replaces Mbox’s output and is then mastered by the group IRGB controls (using CMY inversion) |
| 104 | ICMY Master, Merge Multiply | RGB controls (using CMY inversion) act as inhibitive submasters for incoming merge data.  Mbox data is then multiplied by the result of the first operation and the Intensity control masters the final output |
| 105 | CMY Master, Merge XFade | RGB controls (using CMY inversion)act as inhibitive submasters for Mbox’s RGB data on all fixtures in the group, and the intensity control is used to crossfade between that result and the merge data |
| 106 | CMY Replace, XFade | RGB controls (using CMY inversion) generate a color that replaces Mbox’s RGB data for all fixtures in the group, and the intensity control is used to crossfade between that result and the Mbox data |
| 107 | ICMY Master, Merge HTP | merge data and Mbox data are merged using HTP, the result is then mastered by the group IRGB controls (using CMY inversion) |
| 108 | CMY Replace, HTP | RGB controls (using CMY inversion) generate a color that is HTP merged with Mbox’s data and the result is mastered by the group intensity control |
| 255 | Group Force OFF | all output for the group is suppressed, i.e. sent to 0 |

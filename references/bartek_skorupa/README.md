Manual
=======

Blender Stereoscopy addon by Bartek Skorupa.
Addon developed for Blender 2.64.

Setup
======

Select your camera, Alt-Shift-T -> Create Stereo Setup.

The camera that you selected becomes the left camera (' L' suffix will appear in its name if not added earlier)
The second camera will be your right camera.

After the script has done its magic - the right camera is selected.

In its object buttons you'll find custom properties to set the proper stereo base:

"Depth Bracket" - here you specify what depth bracket (FPP - NPP) you want to get. It's measured in pixels
"FP influence" - It's by default set to 1 and it means that distance to far point will be taken into account. If you set it to 0 - far point will be assumed at infinity.
"FP/NP Minimum" - it's by default set to 2. This means that Far Point must be at least 2x as far as the near point. It's to prevent too big stereo base on really shallow scenes.


USAGE
=====
Grab the near plane and position it at the nearest point in scene, position Far Plane at the furthest object and you're done. Right camera position will be set accordingly and dynamically which is crucial.

There is a driver that drives camera shift of right camera, It's been set such that the shift will position the depth bracket so the near plane will be exactly on the screen.
Then in post production you simply have different starting point. If you don't shift right image more or less, you'll simply have all behind the screen.

If you don't want this behavior - simply remove driver from "shift x" property from right camera's data.


All is set such that left camera is our "pivot". Everything is parented to it. I have purposely done it this way. I don't like the idea of "Center Camera" plus left and right that are parented to it.
It looks nice, but gives problems.
If you want to change the base - you'll have to re-render both left and right cameras, as positions of both of them change.

In this setup if you want to change something - you don't touch the left camera, but only the right one, so you'll have to re-render only right eye.
It's helpful especially when you want to use multiple rigs.

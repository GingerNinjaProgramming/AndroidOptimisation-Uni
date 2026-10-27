# AndroidOptimisation-Uni

## Editor/Emulator 

![](https://file.garden/aSY-yx_ZmANpQe1l/Year2Tasks/image_2026-10-21_054332119.png)

In the editor/Emulator when testing the project I noticed no major drops in frame rate during the playtime of the game and then after checking the profiler the graph also reflects this idea with no major inconsistency or anything that would cause any major worry for how it may function on a less performant device like an android phone. The only part to make note of is some spikes in time for the rendering call littered around the 1m 30second runtime test mainly being found at the start and end of the project where the scene is loaded and unloaded which should to be expected however not enough to affect the performance of the game in major way still remaining at a mostly consistent 60~ frames per second . 

## Physical Hardware

![](https://file.garden/aSY-yx_ZmANpQe1l/Year2Tasks/WhatsApp%20Image%202026-10-22%20at%2019.26.56.jpeg)

After testing it in on physical hardware I can confirm that despite some doubts I may of had it functioned perfectly on the physical android device as I had hoped. One major observation I did make when actually playing the game is how important a good control scheme along with appropriate scaling of difficultly is to making sure the game is fun to play. As I had been doing most of my testing up to this point on a pc I was playing by the rules of pc for the controls and by that metric my game is extremely easy. However with a touch control scheme on a phone it was a lot more difficult and things like precise movement were a lot more tedious. For future games this is something that should be kept in mind along with ensuring the game runs well 
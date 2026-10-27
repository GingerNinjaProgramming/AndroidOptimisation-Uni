# iOS Optimization

![](https://file.garden/aSY-yx_ZmANpQe1l/Year2Tasks/image_2026-10-27_152757366.png)
![](https://file.garden/aSY-yx_ZmANpQe1l/Year2Tasks/image_2026-10-27_152657160.png)

## Summary
In this week I have added a save loading system, score system, a new level and a select screen for levels. Along with ensuring all four of these changes still work on android and along with this week also could theoretically work on IOS, even though due to hardware/sdk limitations I can't directly test this fact.

## Score System

![](https://file.garden/aSY-yx_ZmANpQe1l/Year2Tasks/Screenshot%202026-10-27%20145618.png)
![](https://file.garden/aSY-yx_ZmANpQe1l/Year2Tasks/Screenshot%202026-10-27%20145623.png)

I have now added a basic scoring system to the game as my new mechanic. This is linked into a widget which keeps a visual tracker of what the players score is. The score is gained by walking over diamond collectables dotted around the levels. This is also works with my new save system as to ensure that your score remains throughout different play sessions.

## New Level 

![](https://file.garden/aSY-yx_ZmANpQe1l/Year2Tasks/Screenshot%202026-10-27%20145902.png)
![](https://file.garden/aSY-yx_ZmANpQe1l/Year2Tasks/Screenshot%202026-10-27%20145911.png)
![](https://file.garden/aSY-yx_ZmANpQe1l/Year2Tasks/Screenshot%202026-10-27%20145924.png)

I have also created a new level which has the player running with increased speed straight forward trying to dodge arrows which bring the player back to the start on contact. For this purpose a dispenser blueprint was made, who's purpose was to fire arrows towards the player straight down the lane seen in the images with some variation. 

## Level Select Screen

![](https://file.garden/aSY-yx_ZmANpQe1l/Year2Tasks/Screenshot%202026-10-27%20150735.png)
![](https://file.garden/aSY-yx_ZmANpQe1l/Year2Tasks/Screenshot%202026-10-27%20150743.png)
![](https://file.garden/aSY-yx_ZmANpQe1l/Year2Tasks/Screenshot%202026-10-27%20150807.png)
![](https://file.garden/aSY-yx_ZmANpQe1l/Year2Tasks/Screenshot%202026-10-27%20150726.png)
![](https://file.garden/aSY-yx_ZmANpQe1l/Year2Tasks/image_2026-10-27_151106598.png)

I also made a level select screen which comes up when you load the game after you load a save but before you enter any level. This widget is made to be dynamically sized to allow for a functionally infinite amount of levels using a combination of a uniform grid box inside of a scroll box. Along with this each level select is a individual widget button that can send to the level corresponding to its number. This is done by naming the levels with the naming convention of "LVL_LEVELNUMBER" which means by taking the number on the level button and doing a bit of formatting we can open the level by number this way. Additionally to ensure that not all the levels are available at the start using the same number system on the widget we define a max level number allowed variable which is used to hide/reveal levels to the player as the game goes on. This all is stored on the games save and the number is incremented when the player touches the level goal as, if built normally, thats when a level should end.

## Save System

![](https://file.garden/aSY-yx_ZmANpQe1l/Year2Tasks/Screenshot%202026-10-27%20151620.png)
![](https://file.garden/aSY-yx_ZmANpQe1l/Year2Tasks/Screenshot%202026-10-27%20151604.png)
![](https://file.garden/aSY-yx_ZmANpQe1l/Year2Tasks/Screenshot%202026-10-27%20151610.png)
![](https://file.garden/aSY-yx_ZmANpQe1l/Year2Tasks/Screenshot%202026-10-27%20151550.png)
![](https://file.garden/aSY-yx_ZmANpQe1l/Year2Tasks/Screenshot%202026-10-27%20151638.png)

My save system has multiple different features. These include:

* Loading/Saving Score/DateTime of Save/Player Location/Levels permitted 
* A save menu widget to manage for multiple saves
* Inbuilt starter level before level select to ensure a save is loaded

This is done by using the unreal inbuilt save system along with making my own save game object which has its values set by a save game structure I made to make adding and changing things to save easier. To make the widget for saving and loading a similar system to level select is utilized by ensuring that my save slots are named "save(LEVELNUMBER)" sequentially and using this to be able to get the number of the save slot and turn that into whatever actual save that refers to in memory. The inbuilt starter menu utilizes the same WB_SaveMenu the only real difference is in the circumstance no save exists it forgoes this and just gives a start button before creating the first blank save and moves onto the level select as normal. Additionally to keep saves in storage during runtime a GameInstance is used which holds a Map of all the saves in memory grabbed on Init (which runs before anything else when game starts) with the Key being the save number and the value being the save itself. Many of the functions used to interact/grab the save data use this as the input as it means I don't have to perpetually be running a costly get all saves every time I need the saves just needing a reference the game instance which exists perpetually during runtime anyway. Another core feature to make logic more clean is that instead of having to grab all objects that need save data on begin play a interface named "BPI_SaveObject" which runs a LoadSave function on all objects once the save is opened passing the save game object as a reference allowing all objects that need the information the grab the info as they need it.




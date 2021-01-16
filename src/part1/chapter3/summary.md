# Summary

Rooms are an integral part of any game in AGS.  In this chapter we talked about the main elements of rooms:

* **Rooms** The Room editor in AGS is actually one of the more complex editors, but it's important to understand how to use it.  Rooms are where the game action happens.  Rooms in AGS aren't necessarily "rooms" in the traditional sense, in that they might not have four walls, a floor, and a ceiling.  A room can be an outdoor area just as well as a traditional room inside.
* **Backgrounds** The room's image is called the background.  A background that is larger than the game's native resolution will automatically scroll when the character moves around the room.  Also, a background can have up to 5 animated frames and AGS will cycle through them all, creating an animated background.
* **Walkable Areas** The areas of the screen where the character is allowed to walk are called Walkable Areas.
* **Walk-behinds** Walk-behinds give the room a 3-D effect by allowing the character to appear to walk behind areas of the room's background.  This is useful, for example, if you have a tree, a table, a wall, or any other object that is part of the room background that characters should be able to walk behind.
* **Regions** A player might decide to interact with the room's background.  Using regions, you can distinguish between different parts of the background and have each part of the room react differently to player interactions.
* **Room Edges** Walking off the edge of the screen can trigger events to happen, like changing to another room, for example.  The Room Edges define where the player must walk to for those events to occur.
* **Lighting** AGS gives you the illusion of lighting by setting the light level of regions in each room.  When a character is within a region, its brightness is affected by the light level of that region.  You can cause a character to ignore light levels by setting the `IgnoreLighting` attribute of the character to `True` within the script, or by setting `UseRoomAreaLighting` to False in the Character editor.
* **Scaling** Things in your game can grow and shrink with distance by using scaling.  This is a feature of walkable areas.
* **Transitions** When your characters leave and enter rooms, it's nice to give the player feedback of this happening by, instead of triggering a new room as soon as the player crosses the room's edge, have the character continue to walk off the edge of the screen before triggering the new room.

# Asteroids
Thank you for downloading the Asteroids Mod!
This file is a guide on how to add new asteroid fields, biomes, or even encounters to your own mod! The Asteroids framework is meant to be easily customizable and fully generated from the xml_config file, much like the main game.

First of all, you need to make sure that your mod will load after Asteroids, so you mod recognizes Asteroids's functions. To do this, simple add <loadAfter>Asteroids</loadAfter> between the <version> and <init> tags of your mod.

Next of all, you need to tell an area to load an asteroid field config. To do this, simply add <action>generateAsteroidArea(this);</action> inside the <init> tag of the area. Then, define asteroid_field="config_name" in the area's XML. For examples, see the main mod.xml. If you want the area to regenrate when the player leaves, add <onLeave><invokeLater><action>leaveAsteroidArea(getArea(this.orbit.id));</action></invokeLater></onLeave> inside the area tag.

If you have followed the instructions so far, you now have an area ready to load an asteroid config! Next up, you must define the config.
An asteroid field config is made up of some number of biomes. Each of these biomes are made up of asteroids, ores, exotics, and what happens onLoad (when the player enters).

To define a new asteroid field config do the following:
<asteroid_field id="config_name">
  <biome id="combo" p="3" />
  <biome id="science" p="2" />
  <biome id="magic" p="2"/>
</asteroid_field>

This field will generate with three possible biomes. Combo will generate 3/7 of the time, where the other two will generate 2/7. For examples, see xml_config.xml.

To define a new biome, do the following:
<biome id="example_biome" spacing="5">
    <ore id="gold" percent="0.03" />
    <ore id="iron" percent="0.03" />
    <asteroid id="medium" p="1" />
    <asteroid id="small" p="2" />
    <onLoad>
      <enemy id="asteroid_miner_drone" count="4" random="2" />
    </onLoad>
</biome>

This area will have medium and small asteroids, and gold and iron at a percent of 0.03 of the total tiles will be each ore. On load, between 2 and 6 asteroid drones will be spawned. Spacing determines how far apart the asteroids are.
To add this biome to your field config, add <biome id="example_biome" p="1"/>

To add ores or enemies from your mod, simply replace the ids (iron, gold, asteroid_miner_drone) with the appropriate ore or enemy.
<onLoad> supports the following: enemy, function, and setFlag. For examples of these, look at xml_config.xml.
Enemies, by default, spawn only in air tiles. If you want them to spawn inside asteroid tiles, add tile="true" to their tag in the onLoad.
Biomes can also spawn exotics, which are special, rarely appearing treasures. For examples, see xml_config.xml
Important note: The <enemy> tag in the main biome/asteroid tag means those enemies will be placed IN tiles, while <enemy> tags in the <onLoad> will be placed in EMPTY tiles.

To add a new asteroid, you must define its id, size, size variance, and tile, like so:
<asteroid id="huge" size="23" size_var="3" tile="asteroid"/>
Asteroids also support shape, and can have <ore> tags inside them.

That's all! I hope this was a helpful guide. If you have more questions, feel free to leave comments on Steam or Mod.io, or join the Aground Modding Discord at https://discord.gg/ZDyYpTE.

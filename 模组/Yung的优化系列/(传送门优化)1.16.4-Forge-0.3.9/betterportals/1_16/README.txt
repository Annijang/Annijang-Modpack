######################################################
# rifts.json和monoliths.json的查阅指南 #
######################################################
注意：如果修改了rifts.json和monoliths.json文件里的内容，是需要重启游戏才能生效，在每个json文件中都有一个'variants'，该属性是设置维度液体和撤离信标的相关属性。

在rifts.json文件中的以下内容是设置维度裂缝的相关属性：
 - blockSelector：一个方块选择器，描述包含维度液体的裂缝是由哪些方块组成的。
       关于方块选择器的更多内容请查看本文件的底部。
 - fluidColor：设置维度液体的颜色，需要注意的是这些颜色都是基于紫色的，无法完全地自定义液体颜色。
   - red：从00到FF的任何十六进制字符串。
   - green：从00到FF的任何十六进制字符串。
   - blue：从00到FF的任何十六进制字符串。
   - alpha：从00到FF的任何十六进制字符串。
 - minY：设置维度裂缝最低的生成高度。
 - maxY：设置维度裂缝最高的生成高度。
 - playerTeleportedMinY：设置玩家传送到目标维度时的最低高度。
 - playerTeleportedMaxY：设置玩家传送到目标维度时的最高高度。
 - spawnDimension：设置维度裂缝的生成维度，每个维度的ID都是不一样的！
 - targetDimension: 设置维度裂缝的传送维度，每个维度的ID都是不一样的！
 - spawnChance：设置维度裂缝能够生成在该维度的概率。
 - spawnPlatformBlock: 有的时候玩家在传送时会在脚下生成一个3x3的平台以便站立。
       该值是设置这个生成平台是由什么方块组成的。

在monoliths.json文件中的以下内容是设置撤离信标的相关属性：
 - stairSelector：一个方块选择器，设置撤离信标旁边的楼梯和楼梯方向。
 - cornerSelector：一个方块选择器，设置撤离信标旁边角落的方块。
 - insideSelector：一个方块选择器，设置撤离信标内部方块。
 - fenceSelector：一个方块选择器，设置撤离信标旁边外围角落平面的栅栏。
 - powerBlock：设置能够提供给撤离信标能量的方块。
 - decorationBlock：设置撤离信标外围角落的方块。
 - beamStopBlocks：设置不能通过撤离信标传送到其他维度的方块列表。
 - unpoweredBeamColor：设置在撤离信标范围内未传送时的光束颜色。
   - red：从00到FF的任何十六进制字符串
   - green：从00到FF的任何十六进制字符串
   - blue：从00到FF的任何十六进制字符串
   - alpha：从00到FF的任何十六进制字符串
 - poweredBeamColor：设置在撤离信标范围内传送时的光束颜色。
   - red：从00到FF的任何十六进制字符串
   - green：从00到FF的任何十六进制字符串
   - blue：从00到FF的任何十六进制字符串
   - alpha：从00到FF的任何十六进制字符串
 - minY：设置撤离信标最低的生成高度。
 - maxY：设置撤离信标最高的生成高度。
 - playerTeleportedMinY：设置玩家传送到目标维度时的最低高度。
 - playerTeleportedMaxY：设置玩家传送到目标维度时的最高高度。
 - spawnDimension：设置撤离信标的生成维度，每个维度的ID都是不一样的！
 - targetDimension：设置撤离信标的传送维度，每个维度的ID都是不一样的！
 - spawnChance：设置撤离信标能够生成在该维度的概率。

描述方块和方块被选中的概率。
 - entries: 一个对象，每个对象都对应一个值，该值就是方块被选中的概率。
      所有的概率总和不能超过1.0！
 - defaultBlock: 如果没有选中“entries”里的对象则会使用该默认方块来作为补充。
      例如：“entries”对象里的所有概率总和加起来只有0.6（60%），那么就会有0.4（40%）的概率会选择“defaultItem”里的物品来作为补充。

下面是一个例子：
"entries": {
  "minecraft:cobblestone": 0.25,
  "minecraft:air": 0.2,
  "minecraft:stonebrick[variant=stonebrick]": 0.1
},
"defaultBlock": "minecraft:planks[variant=oak]"

默认方块是“minecraft:planks[variant=oak]”（橡木木板），在选择指定方块作为矿物位置时有25%的概率选择圆石、20%的概率选择空气、10%的概率选择为石砖，那么选择默认方块（橡木木板）的概率是：100%-25%-20%-10%=45%，也就是说如果未选中圆石、空气、石砖时，有45%的概率会默认选择橡木木板来作为备用的补充方块。

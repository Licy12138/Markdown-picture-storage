## 导入事项

这是一个见简单的模型导入到服务器ItemsAdder插件内的教程，仅供参考。

## 如何导入？

请先将你的`BBmodel`模型转化成`Json模型`和一个`PNG格式材质`，材质必须是**单个材质**而不是多个多面材质

使用文本文档或者是Visual Studio将你的Json模型文件路径改成如下：

```json
{
	"credit": "Made with Blockbench",
	"texture_size": [32, 32],
	"textures": {
		"1": "<你的材质名称>"
    }
}
```

然后新建一个`yml`文件

# 如果你是物品/武器模型，需要做技能的：
# 示例文件

```yml
info:
  namespace: fire #命名空间，不要带有任何大写字母，特殊符号，纯英文
items:
  fire: #你的物品命名空间
    display_name: Fire Reed Staff #在游戏内的名字，允许使用中文
    resource:
      material: CARROT_ON_A_STICK #如果需要给该模型写入技能，填入CARROT_ON_A_STICK，否则填DIAMOND_SWORD，用Mythic扩展写技能:<
      generate: false             #是否生成3D模型，如果你是2D贴图填true，如果你是3D模型填false
      model_path: test:firereedstaff #模型路径，默认是你文件夹下的
```

# 如果你是物品模型，需要做成家具，自定义方块的：
# 示例文件

```yml
info:
  namespace: test #命名空间
items:
  plants: #同上
    display_name: plants #在游戏内的名字
    resource:
      material: PAPER #填入物品，不要填方块名称
      generate: false #是否生成3D模型，如果是Json模型填false
      model_path: plants #模型路径
    behaviours:
      furniture: #家具
        light_level: 13 #放置光照亮度
        solid: true 
        placeable_on: #可放置在哪些方块上，挂墙壁上，天花板上
          floor: true
          ceiling: false
          walls: false
        hitbox: #碰撞箱，基于盔甲架
          length: 1
          width: 1
          height: 1
        sound:  #放置，破坏声音
          place:
            name: BLOCK_GLASS_PLACE
            volume: 1
            pitch: 0.9
          break:
            name: BLOCK_GLASS_BREAK
            volume: 1
            pitch: 0.9
```

**这样一个模型就算导入成功了**

## 如何实装到服务器里？

参考文档：[ItemsAdder Wiki](https://itemsadder.devs.beer/)

1.在`ItemsAdder\contents`新建一个文件夹，命名为你的物品 例如：`youritems`

2.在新建的文件夹`youritems`中，新建`configs`，`resourcepack`两个文件夹

3.在`configs`文件夹丢入上面的`yml`配置文件，名字必须是英文

4.在`resourcepack`文件夹中，新建`youritems`文件夹，`youritems`中再新建`models`,`textures`两个文件夹

5.在`models`放置你的Json模型，名字要和配置文件的`model_path: <你的模型名称> #模型路径`一致

6.在`textures`放置你的贴图文件，名字要和Json模型中的`"textures": {"1": "<你的材质名称>"}`一致

~~7.在服务器后台输入`iareload`,`iazip`指令，生成材质文件并发送到我的(Alist网盘上)[https://alist.meowlicy.cn]上，重新生成直链并复制到服务器配置文件上awa~~


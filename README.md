# svg-babydoodle
宝宝来画画的svg步骤尝试

## 目的
1. 可以根据想要的节奏绘制线条和填充 然后播放声音和中文字幕
2. 优点是文件很小 很容易保存, 缺点是需要编程和
## TODO
- [ ] 能否有个什么机制可以在中间step中控制classlist 这样可以让某个需要填充的的图形在中间显示出来
- [ ] 能否单独控制某一个步骤 [prototype.next](https://github.com/maxwellito/vivus/issues/85)
- [x] 能否整体reverse  option.reverseStack:true
- [ ] 如何multi 能不能更方便的叠加 - 可以多个实例
- [ ] 如何跟audio整合


## 文件说明

* original/lines.svg sketch.app 制作出来的
* animated/lines_animated.svg 是 经过 https://maxwellito.github.io/vivus-instant/ 转换的svg-animate文件



## 绘制顺序
vivus 绘制顺序就是按照图层顺序从back的图层front的到依次绘制, 如果你选择了{types:"oneByOne"}的话


## 如何让填充颜色最后出现 
[参考这里](https://github.com/maxwellito/vivus/blob/master/hacks.md)
简单讲原理就是先给整个`svg`的opacity设为0, 并设置好transition时间, 然后在vivus结束之后的回调里将获取`svg`对象的classlist,
把opacity变成1,填充颜色就出现了. 因为对于 `svg` opacity不影响 path的绘制

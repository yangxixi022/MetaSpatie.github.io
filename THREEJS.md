## 1、目录结构
#### css -->> css 资源文件
#### home -->> threeJs 案例资源文件
#### index.html -->> 访问链接

## 2、学习笔记
#### 第一章 创建三维场景 总结

- 最好的学习方法就是不断寻找例子，研究这些例子。
- 每种材质对光源的反应都不一样。
- 通过修改物体的`position` 和 `rotation` 可以实现动画效果。
- three-r93.js 一直不断在更新，需要去关注更新的信息，才能与新的使用方式同步。

#### 第二章 构建 three.js 的基本组件 总结

- 场景是ThreeJs库的最主要的容器，我们可以将想要渲染的对象添加到场景中去。
- 场景并没有很多特殊的选项和属性，最主要的功能就是允许我们添加对象、移除对象，以及处理场景中的 children 属性。
- 我们可以通过配置 **Fog** 对象为场景添加雾化的效果。
- 几何体和网格关系密切，几何体定义对象的外观，赋予材质后我们可以用它来创建网格。
- threeJs 提供了很多的标准几何体，我们也可以自己去创建。
- 可以通过编程去控制 **mesh** 的 **position**、**rotation**、和**scale**属性。
- 通过 **translate** 属性，可以相对当前的位置移动网格。

#### 第三章 各种光源 总结

- 学会配置光源，颜色和阴影不是严谨的科学，需要不断去试验，使用dat.GUI去调试处最优的效果。
- 环境光光源 `AmbientLight` 的颜色，可以附加到场景中的每一种颜色上，它没有位置的概念，通过使用环境光来柔化那些硬生生的光源和阴影。
- 点光源 `PointLight` 可以生成阴影，查看`LightShadow`，朝向所有方向的发光体，例如夜空中的照明弹。
- 聚光灯光源 `SpotLight` 类似手电筒，发射出一种锥形光源，可以生成阴影。
- 聚光灯光源和平行光光源一样，都有一个 `debug`微调开关，可以用来微调相机和阴影的配置。
- 平行光光源 `DirectionalLight` 与太阳光类似，因为很远，所以光线都是互相平行的，光线离指定的目标越远，则光强衰减的越多。
- 半球光光源 `HemisphereLight` 模拟更加自然的室外效果，可以阿静天空的光照和来自地面的反射计算在内。
- 矩形面光源 `RectAreaLight` 矩形面光源不支持，阴影，需要条件库文件 `RectAreaLightUniformsLib`才能实现镜面反射效果，并且只有标准材质和物理材质得到支持。
- 炫光效果 `lensflare` 需要加载材质，并且要引入，`lensflare.js`库文件。

#### 第四章 材质 总结

- 各种材质有很多共同的属性。
- 并不是所有材质都会场景中的光源做出反应，若想计算材质对光源的影响，可以使用`MeshPhongMaterial`和`MeshLambertMaterial`。
- 如果要创建一种透明的材质，仅仅设置透明（`transparent`）是不够的，还需要设置透明度（`opacity`）。
- 材质的大部分属性在运行时都可以修改，但是有一些属性并不可以修改，若是修改需要将 `needUpdate`这只为`true`。
- 可以为一个几何体赋予多种材质，但是要记住，这么做会复制几何体，从而创建出多个网格。
- `THREE.Line` 不可以使用普通材质来覆盖，因此只能使用`THREE.LineBasicMaterial`和`THREE.LineDashedMaterial`。
- `THREE.Points`的默认材质是 `PointsMaterial`，也就是后面的粒子。
- 如果想要一个光亮的物体可以使用 `MeshPhongMaterial`,如果想要一个暗淡的物体可以使用`MeshLambertMaterial`。
- 灵活使用 `dat.GUI`来测试各种材质的属性。

#### 第五章 学习使用几何体 总结

- 创建二维几何体是，不需要考虑 z 轴，如果想要拥有一个水平的二维平面，则必须将此网格绕x轴旋转 -0.5 * Math.PI。
- 如果要旋转一个二维图形，或者开放的三维图形，圆柱或者柱子，最好将材质的`side`设置为，`THREE.DoubleSide`，否则将看不到几何体的背面。
- 使用这些几何体，以及里面的一下参数，文档都有很好的说明，所以不需要再一一的演示，使用时不明白的地方，直接查看文档即可。

#### 第六章 高级几何体以及二元操作 总结

无

#### 第七章 粒子和粒子系统 总结

- 本章解释了什么是粒子、粒子系统，精灵的概念，需要慢慢消化。
- 通过 `THREE.Sprite`可以创建一个粒子。
- 通过 `THREE.Points`可以创建大量的粒子，并且共享一个材质，使用`THREE.Points`可以把几何体中的顶点都被渲染成粒子。
- 让粒子动起来，只需要改变粒子的位置。
- 通过 `map`属性，可以使用图片或者`HTML5`的`canvas`画布来格式化粒子。
- 可以使用 `THREE.Sprite`来创建一个文字标签。
- 可以把记载进的几何体的顶点变成粒子来显示，粒子效果，可以使用`CPU`或者`GPU`来渲染，可以维护唯一、颜色、尺寸。

#### 第八章 创建和加载高级几何体 总结

- three.js r92 以及以上版本 删除了 Blender json 格式导出器，并且，现在使用 Blender 导出 json 格式的文件 会出错
- three.js 官方推荐使用 glTF 格式的模型，而且可以通过 Blender 导出 glTf 格式的模型
- 学习 glTf 格式的数据结构，学习模型的加载
- 组合对象的时候，每个对象依然可以进行单独的操作，对父对象进行操作的时候可以影响到子对象
- 将对象合并到一起，就失去了对单个模型的控制，如果要渲染成千上万的几何体，而性能成为瓶颈的时候，可以将对象将对象进行组合来就进行操作
- 使用 three.js 提供的各种加载器的时候，可以在回调函数中输出加载过程，以及错误的回到函数的信息输出
- `THREE.JSONLoader` 和 `THREE.ObjectLoader` 加载`json`文件的时候，出现的问题，`THREE.JSONLoader`d的回调函数中出现的是 一个几何结构`Geometry`
- 而`THREE.ObjectLoader`的回调函数中出现的是 一个`scene`对象

#### 第九章 创建动画和移动相机

- three.js 提供了很多相机控件，尽管他们的功能类似，不过也有各自使用的地方，如果找不到一个适用的控件，可以自己研究一下代码自己开发一个。
- 让模型动起来主要有两种方法，使用变形目标或者骨骼动画。
- 加载模型时最好先将模型的输出到控制台，查看一下模型的数据结构，然后再进行相应的处理，否则容易出错。




<!-- https://developers.weixin.qq.com/miniprogram/dev/api/canvas/get-image-data.html -->

wx.canvasGetImageData(OBJECT)
=============================

> 基础库 1.9.0 开始支持，低版本需做[兼容处理](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)

返回一个数组，用来描述 canvas 区域隐含的像素数据

**OBJECT参数说明：**

  参数       |  类型       |  必填 |  说明                                                                                                         | 最低版本
-------------|-------------|-------|---------------------------------------------------------------------------------------------------------------|---------
  canvasId   |  String     |  是   |画布标识，传入 [`<canvas />`](https://developers.weixin.qq.com/miniprogram/dev/component/canvas.html) 的 canvas-id|         
  x          |  Number     |  是   |  将要被提取的图像数据矩形区域的左上角 x 坐标                                                                  |         
  y          |  Number     |  是   |  将要被提取的图像数据矩形区域的左上角 y 坐标                                                                  |         
  width      |  Number     |  是   |  将要被提取的图像数据矩形区域的宽度                                                                           |         
  height     |  Number     |  是   |  将要被提取的图像数据矩形区域的高度                                                                           |         
  success    |  Function   |  否   |  接口调用成功的回调函数                                                                                       |         
  fail       |  Function   |  否   |  接口调用失败的回调函数                                                                                       |         
  complete   |  Function   |  否   |  接口调用结束的回调函数（调用成功、失败都会执行）                                                             |         

**success回调返回参数：**

  参数     |  类型                |  说明                           
-----------|----------------------|---------------------------------
  errMsg   |  String              |                                 
  width    |  Number              |  图像数据矩形的宽度             
  height   |  Number              |  图像数据矩形的高度             
  data     |  Uint8ClampedArray   |图像像素点数据，一维数组，每四项表示一个像素点的rgba

**示例代码：**

    wx.canvasGetImageData({
      canvasId: 'myCanvas',
      x: 0,
      y: 0,
      width: 100,
      height: 100,
      success(res) {
        console.log(res.width) // 100
        console.log(res.height) // 100
        console.log(res.data instanceof Uint8ClampedArray) // true
        console.log(res.data.length) // 100 * 100 * 4
      }
    })

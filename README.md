# Waterfall

<pre>
{
    itemSelector:'.post-home',     //子元素id/class, 可留空
    columnCount:4,                 // 列数,  纯数字, 可留空
    columnWidth:300,               // 列宽度, 纯数字, 可留空
    isResizable:false,             // 自适应浏览器宽度, 默认false
    isAnimated:false,              // 元素动画, 默认false
    Duration:500,                  // 动画时间
    Easing:'swing',                // 动画效果, 配合 jQuery Easing Plugin 使用
    endFn:function(){},            // 回调函数
}
</pre>


# 插件配置

<pre>
var opt = {	//用户自定义配置
   cellWidth: 190,			//单元格宽度
   cellMargin: 10,			//单元格边距
   showFade: true,			//渐显效果
   showFadeSpeed: 600,			//渐显效果速度
   insertToShort: true,			//往短的列插入，不设置等待图片时会有误差
   waitImage:true			//等待图片加载完再插入，因网络问题会造成卡
 
};
</pre>

Documentation: [En](http://wlog.cn/waterfall/index.html) [中文](http://wlog.cn/waterfall/index-zh.html)

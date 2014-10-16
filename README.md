# Waterfall

<pre>
$(function(){
    /*!
    * Ublue jQuery Waterfall
    * Create 2012.02.21
    * Update 2012.10.18 ( 1.由于内容是absolute属性，导致元素偏离了文档，嵌入网页时无法撑开父级区域 2. 性能和代码结构优化 3.已知BUG修复)
    * Copyright (c) 2011, 梦幻神化
    * http://www.bluesdream.com
    */
    function waterfall(){
        var wfArea = $("#waterfall"); //显示区域名称
        var wfList = $(".picList"); //内容区域名称
        var wfWidth = wfList.outerWidth(true); //获取内容区域实际宽度（含Margin值）
        var wfArr = new Array(); //创建数组，用来记录内容区域高度
        var maxCol = Math.floor( $(window).width() / wfWidth ); //窗口的宽度除以内容区域宽度，并且向下取整（得出每行能放多少列）
        for(var i = 0; i < wfList.length; i++) { //根据内容区域数量进行循环
            colHeight = wfList.eq(i).outerHeight(true); //获取每个内容区域的高度
            if( i < maxCol ){ //如果i小于maxCol，那就说明是在一行里面（例如每行有4列，那就是4个为一组）
                wfArr[i] = colHeight; //把每组内容区域的高度，放入到数组中
                wfList.eq(i).css("top",0); //第一行Li的默认Top值为0
                wfList.eq(i).css("left",i * wfWidth); //每个列的Left值就是当前列数*内容区域宽度
            }else{
                minHeight = Math.min.apply(null,wfArr); //比较数值中的值，取得最小值（也就是每行中，最小高度）
                minCol = getArrayKey(wfArr, minHeight); //最小的值对应的指针
                wfArr[minCol] += colHeight; //加上新高度后更新高度值
                wfList.eq(i).css("top",minHeight); //先得到高度最小的Li，然后把接下来的li放到它的下面
                wfList.eq(i).css("left",minCol * wfWidth); //第i个列的左坐标就是i*列的宽度
            }
            wfList.eq(i).attr('id',"post_"+i);
        };
        function getArrayKey(s, v) { //使用for in运算返回数组中某一值的对应项数(比如算出最小的高度值是数组里面的第几个)
            for( k in s ) {
                if( s[k] == v)  {
                    return k;
                }
            }
        };
        var fwLastLayerT = parseInt(wfList.last().css("top")); //最后一个元素的Top值
        var fwLastLayerH = wfList.last().outerHeight(true); //最后一个元素的高度
        var wfAreaH = fwLastLayerT + fwLastLayerH + "px"; //显示区域的高度为 最后一个元素的Top值+自身高度
        wfArea.css({ "width":wfWidth * maxCol,"height":wfAreaH }); //设置显示区域宽度和高度
     }
    window.onload = function() { waterfall(); } //当页面加载完毕，执行函数
    $(window).resize(function(){ //当窗口改变时，执行函数
        waterfall();
    });
});
</pre>


Documentation: [En](http://wlog.cn/waterfall/index.html) [中文](http://wlog.cn/waterfall/index-zh.html)

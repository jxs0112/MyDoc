#影响用户体验的WebView两三事

虽然目前android和iphone是最主流的智能手机平台（WP平台哭去吧，FirefoxOS是啥？），并且自带的浏览器内核都是WebKit，但是对于做H5的同学来说还会受系统自身的影响某些CSS和Javascript进行兼容性制作；
    
##有的有、有的没

###去除android上a标签产生的边框
        a,button,input{-webkit-tap-highlight-color:rgba(255,0,0,0);}
        
        @media all and (-webkit-transform-3d){/* Android4.0下不识别该-webkit-transform-3d，使用它可做Android4.0下版本兼容 */
        
        }
###让人又爱又恨的iScroll

iScroll的诞生，主要是因为早期的webkit内核浏览器没有一种原生支持固定高度的容器。
到目前为止，iScroll最大的问题就是慢，在千元以下Android设备上表现尤为突出。
使用局部滚动来替代iScroll滚动是最好的一种方式，但很可惜，现在只有iOS5、6支持局部滚动，并且支持程度并不好，而Android压根就不打算支持。
这样，我们就不得不抛弃iScroll，除非UE在设计交互原型时，将固定高度容器和局部区域滚动的需求完全砍掉。
分析结束，问题来了，现在到底使用iScroll呢？还是不使用？使用的话，大部分Android设备在滚动时会很卡，如不使用，部分功能又实现不了。其实，这个问题也不必太纠结。

* 首先,对于header、footer需要固定位置的页面，可以直接使用position:fixed实现。部分不支持fixed定位的浏览器问题也不大，这部分设备一般都是Android2.x的系统，配置也较低，相对交互而言，速度显然更加重要；
* 对于需要依赖固定高度实现切换动画效果的交互，应尽量保证滚动条在页面顶部时处理。必要时做出一些牺牲，舍弃部分影响用户使用流畅的交互；
* 尽量使用浏览器原生支持代替iScroll；
* 如果必须使用iScroll才能实现的功能，一定要控制在最小范围，不要在常用场景应用iScroll；
 

虽然iScroll在iOS下表现得非常出色，但是都应当尽量使用浏览器原生支持特性来实现功能，这样才能最大化保证交互操作的流畅性。


#影响用户体验的WebView两三事

虽然目前android和iphone是最主流的智能手机平台（WP平台哭去吧，FirefoxOS是啥？），并且自带的浏览器内核都是WebKit，但是对于做H5的同学来说还会受系统自身的影响某些CSS和Javascript进行兼容性制作；
    
##去除android上a标签产生的边框
        @media all and (-webkit-transform-3d){/* Android4.0下不识别该-webkit-transform-3d，使用它可做Android4.0下版本兼容 */
        .css{...}
        }

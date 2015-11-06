#SVG TEXT
<svg width="200" height="100" viewBox="0 0 20 10">
    <text>SVG TEXT</text>
</svg>

    <svg width="200" height="100" viewBox="0 0 20 10">
        <text>SVG TEXT</text>
    </svg>


##viewBox&preserveAspectRatio
viewBox可理解为实际显示的大小，preserveAspectRatio则是与之配合的属性。例如：preserveAspectRatio="xMidYMid meet"

    <svg width="400" height="200" viewBox="0 0 200 200" preserveAspectRatio="xMidYMid meet" style="border:1px solid #cd0000;">
        <text>SVG TEXT</text>
    </svg>

[理解SVG的viewport,viewBox,preserveAspectRatio](http://www.zhangxinxu.com/wordpress/2014/08/svg-viewport-viewbox-preserveaspectratio/)    
    
##与分辨率无关
    
    
##易于css和js配合
    <svg width="400" height="200" viewBox="0 0 200 200" style="border:1px solid #cd0000;">
        <text class="text">SVG TEXT</text>
    </svg>
    <style>text:hover{fill:#f00}<style>
    
    
##可被选取
意味着可以复制~

##并不会自动换行

    <svg width="200" height="100" viewBox="0 0 20 10">
        <text>SVG TEXT SVG TEXT SVG TEXT SVG TEXT SVG TEXT SVG TEXT SVG TEXT SVG TEXT SVG TEXT SVG TEXT SVG TEXT SVG TEXT SVG TEXT </text>
    </svg>

##<tspan>
<tspan> ≈ html <span>
x y 绝对定位
dx dy 相对定位

##textLength&lengthAdjust 

##RESPONSIVE 
[fitter-happier-text](http://jxnblk.com/fitter-happier-text/)

##textPath

    <svg viewBox="0 50 500 150">
        <path id="arc" stroke="red" d="M82.372,165.969 c44.126-35.084,60.236-50.782,150.325-50.782s131.802,28.198,158.194,62.77" />
        <text fill="#5D509D" width="500">
          <textPath alignment-baseline="middle" xlink:href="#arc" font-size="44"  dy="100">
            Are You Afraid
          </textPath>
        </text>
    </svg>

##<defs>
定义可复用的SVG模块，例如渐变，动画，滤镜

##Gradient 渐变
线性，径向渐变

    <linearGradient id="fire" x1="0" y1="0" x2="100%" y2="100%">
        <stop stop-color="hotpink" offset="0%"/>
        <stop stop-color="goldenrod" offset="100%"/>
      </linearGradient>
      <radialGradient id="ring-of-fire" cx="50%" cy="50%" r="40"
          gradientUnits="userSpaceOnUse">
          <stop stop-color="hotpink" offset="0%"/>
          <stop stop-color="goldenrod" offset="100%"/>
        </radialGradient>

gradientUnits 坐标系的选择 

##图片，图案，裁切
<image>
需要定义高宽
preserveAspectRatio 实现填充位置
patternUnits 填充方式

    <svg viewBox="0 0 200 100" width="600px">
        <!-- default value is 'meet', not 'slice' -->
        <image preserveAspectRatio="xMidYMid slice"
          xlink:href="img/moon.jpg" width="200" height="100" />
      </svg>
      
可填充GIF实现绚丽的效果      
      
<pattern> 可将任何的SVG原件转化为pattern
    
    <svg viewBox="0 0 200 60">
        <defs>
          <pattern id="moon" width="200" height="60"
            patternUnits="userSpaceOnUse">
            <image xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="img/moon.jpg" width="200" height="60" preserveAspectRatio="xMidYMid slice"></image>
          </pattern>
        </defs>
        <text fill="url(#moon)" y="1em">moon</text>
      </svg>

<clipPath>
    
    <svg viewBox="0 0 200 60">
        <defs>
          <clipPath id="mars-text">
            <text y="1em">mars</text>
          </clipPath>
        </defs>
        <image clip-path="url(#mars-text)" xlink:href="img/mars2.jpeg"
        width="200" height="60" preserveAspectRatio="xMidYMax slice"/>
      </svg>
      
##<mask>遮罩
类似<clipPath>，但功能更强大
和PS类似，黑白灰实现透明度
    
    <svg viewBox="0 0 200 25">
                    <rect fill="#000" fill-opacity=".75" mask="url(#ham-text)"
                    x="0" y="0" width="200" height="50" />
                    <mask id="ham-text">
                      <rect fill="#fff" x="0" y="0" width="200" height="50"></rect>
                      <text y="20" fill="#000" text-anchor="middle" x="50%" font-size="20">
                         Buy 2 hams $20
                      </text>
                    </mask>
                  </svg>
                  
##<animate>
基本上可对任何属性实现动画
    <svg viewBox="0 0 800 100">
        <line stroke="goldenrod" stroke-width="10"
          x1="0" y1="50" x2="0" y2="50">
          <animate attributeName="x2"
          from="0" to="800"
          dur="2s" repeatCount="indefinite"/>
        </line>
    </svg>

<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>

# Rotating Calipers - 旋转卡壳

#### 定义

$$ (1) $$ 凸$$ n $$边形直径

凸$$ n $$边形上相距最远的任意两点（不只是顶点，也可以是边上任意一点）间距离

//用旋转卡壳方法求一凸多边形的直径

//旋转卡壳算法的核心思路是用一对卡壳(平行线)卡住凸多边形然后旋转一圈
//被卡壳正好卡住的两个顶点称为对踵点
//
//1)用旋转卡壳求凸多边形直径
//凸多边形直径: 
//凸多边形上相距最远的任意两点间的距离
//注意这两点不一定是凸多边形的顶点 也可以是凸多边形的边上任意一点
//
//初始时选取凸多边形上y坐标最大和最小的两个点 这两点是初始的一对对踵点
//构造两条水平平行线穿过这两个点 计算出两平行线间距离 并维护这个最大距离
//重复以下步骤: 
//按照固定一个方向同时旋转这两条线 总是保持两条线相互平行
//直到其中一条线与凸多边形上的一条边重合
//这时产生一个新的对踵点 计算两平行线间距离并于前一状态时的距离比较
//若当前的距离更大则更新最大距离
//直到两平行线再次回到凸多边形上y坐标最大和最小的两点 算法结束
//两平行线的最大距离即为凸多边形直径
//
//在旋转中 当两条平行线都不与凸多边形上的边完全重合时
//两条平行线分别与凸多边形上一个顶点相切
//
//在旋转过程中 每次平行线停留的位置总是其中一条平行线与凸多边形上一条边完全重合
//这时另一条平行线与凸多边形的位置关系可能有三种情况
//i)另一条平行线与凸多边形的一个顶点相切
//在这种情况下 两平行线间距离是多边形的一个顶点到另一条边所在直线的距离
//ii)另一条平行线与凸多边形的一条边也完全重合 即凸多边形上这两条边是相互平行的
//在这种情况下 两平行线间距离是多边形的两条平行的边所在直线的距离
//
//但在求凸多边形直径时 只需要判断其中一条平行线与凸多边形的边重合即可
//本文实现旋转卡壳求凸多边形直径
//在后一节凸包中读者可以看到其实凸多边形是一个凸包
//
//2)用旋转卡壳求凸多边形宽度
//凸多边形宽度: 
//凸多边形上相距最近的任意两点间的距离 即凸多边形直径的相反意思
//这里的两点也是凸多边形上的任意两点 不只是顶点
//
//使用旋转卡壳的方法基本一样 仍然是将一对平行线按照一定方向沿着凸多边形外围旋转一圈
//每当两条平行线中的一条与凸多边形的边重合时 就停下来
//然后计算并更新两平行线间的最小距离 直到重新回到起始的两顶点 算法结束
//
//3)用旋转卡壳求其他问题
//旋转卡壳方法还可以应用于其他很多几何问题 甚至三维或多维空间中的几何问题: 
//i)距离计算
//凸多边形的直径
//凸多边形的宽度
//两凸多边形之间的最小距离
//两凸多边形之间的最大距离
//ii)外接矩形
//凸多边形的最小面积外接矩形
//凸多边形的最小周长外接矩形
//iii)三角剖分
//洋葱三角剖分
//螺旋三角剖分
//四边形剖分
//iv)凸多边形属性
//合并两凸多边形
//两凸多边形的公切线
//两凸多边形的相交
//两凸多边形的临界切线
//两凸多边形的矢量和
//v)最薄截面
//最薄横截带


--------

#### CSDN旋转卡壳

* https://blog.csdn.net/hanchengxi/article/details/8639476

#### CSDN旋转卡壳-ACMaker

* https://blog.csdn.net/ACMaker/article/details/3561147
* https://blog.csdn.net/ACMaker/article/details/3561150
* https://blog.csdn.net/ACMaker/article/details/3561145
* https://blog.csdn.net/acmaker/article/details/3188177
* https://blog.csdn.net/ACMaker/article/details/3561131
* https://blog.csdn.net/ACMaker/article/details/3561127
* https://blog.csdn.net/ACMaker/article/details/3561141

--------

#### 源码

[RotatingCalipers.h](https://github.com/linrongbin16/Way-to-Algorithm/blob/master/src/AnalyticGeometry/ConvexHull/RotatingCalipers.h)

[RotatingCalipers.cpp](https://github.com/linrongbin16/Way-to-Algorithm/blob/master/src/AnalyticGeometry/ConvexHull/RotatingCalipers.cpp)

#### 测试

[RotatingCalipersTest.cpp](https://github.com/linrongbin16/Way-to-Algorithm/blob/master/src/AnalyticGeometry/ConvexHull/RotatingCalipersTest.cpp)

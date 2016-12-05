# android-ride-route-plan
骑行路径规划示例
## 前述 ##
- [高德官网申请Key](http://lbs.amap.com/dev/#/).
- 阅读
  [地图SDK参考手册](http://a.amap.com/lbs/static/unzip/Android_Map_Doc/index.html). 
- 工程基于高德3D地图实现

## 使用方法##
###1:配置搭建AndroidSDK工程###
- [Android Studio工程搭建方法](http://lbs.amap.com/api/android-sdk/guide/creat-project/android-studio-creat-project/#add-jars).
- [通过maven库引入SDK方法](http://lbsbbs.amap.com/forum.php?mod=viewthread&tid=18786).

## 扫一扫安装##

 ![Screenshot](https://github.com/amap-demo/android-ride-route-plan/blob/master/resource/download.png)

## 示例效果##

 - overlay效果展示
 
 ![Screenshot](https://github.com/amap-demo/android-ride-route-plan/blob/master/resource/Screenshot_overlay.png)

 - 列表效果展示
 
 ![Screenshot](https://github.com/amap-demo/android-ride-route-plan/blob/master/resource/Screenshot_list.png)
 
 ## 核心类/接口 ##
| 类    | 接口  | 说明   | 版本  |
| -----|:-----:|:-----:|:-----:|
|RouteSearch|calculateRideRouteAsyn()|根据指定的参数计算骑行路径、异步方法|V3.5.0|
|RouteSearch|onRideRouteSearched()|骑行路径规划结果回调方法|V3.5.0|
 
  ## 核心难点 ##
  - 构造骑行路径规划类
  
  ```java
        mRouteSearch = new RouteSearch(this);
        mRouteSearch.setRouteSearchListener(this);
  ```
  
  -发起骑行路径规划异步请求
   
  ```java
         RideRouteQuery query = new RideRouteQuery(fromAndTo, mode);
         mRouteSearch.calculateRideRouteAsyn(query);// 异步路径规划骑行模式查询
  ```
  
  - 将骑行路径规划结果用overlay在地图展现
  
  ```java
       RideRouteOverlay rideRouteOverlay = new RideRouteOverlay(
                this, aMap, ridePath,
                mRideRouteResult.getStartPos(),
                mRideRouteResult.getTargetPos());
        rideRouteOverlay.removeFromMap();
        rideRouteOverlay.addToMap();
        rideRouteOverlay.zoomToSpan();
  ```

<template>
  <div class='baidumap' id="allmap">
  </div>
  
</template>
<script>
import BMap from 'BMap'
// import BMapSymbolSHAPEPOINT from 'BMap_Symbol_SHAPE_POINT'

export default {
  name:'HelloWorld',
  data(){
    return{

    }
  },
  methods: {
        baiduMap () {
                    var map = new BMap.Map("allmap");
                    var point = new BMap.Point(107.31612162513613,30.43983123446668);//当前坐标经纬可改
                    map.centerAndZoom(point,19);//显示级数越大越细
                    map.addOverlay(new BMap.Marker(point));//定点坐标红点覆盖
                    map.enableScrollWheelZoom(true);
                    	var geolocation = new BMap.Geolocation();
                      geolocation.getCurrentPosition(function(r){
                        if(this.getStatus() == BMAP_STATUS_SUCCESS){
                          var mk = new BMap.Marker(r.point);
                          map.addOverlay(mk);
                          map.panTo(r.point);
                          alert('您的位置：'+r.point.lng +'+'+r.point.lat);
                           
                        }
                        else {
                          alert('failed'+this.getStatus());
                        }        
                      },{enableHighAccuracy: true})
      
  
     },
      bd09_to_gcj02(bd_lon, bd_lat) {
        debugger;
        var x_PI = 3.14159265358979324 * 3000.0 / 180.0
        var PI = 3.1415926535897932384626
        var a = 6378245.0
        var ee = 0.00669342162296594323
        var bd_lon = +bd_lon
        var bd_lat = +bd_lat
        var x = bd_lon - 0.5065
        var y = bd_lat + 0.06
        var z = Math.sqrt(x * x + y * y) - 0.00002 * Math.sin(y * x_PI)
        var theta = Math.atan2(y, x) - 0.000003 * Math.cos(x * x_PI)
        var gg_lng = z * Math.cos(theta)
        var gg_lat = z * Math.sin(theta)
        console.log(gg_lng);
        console.log(gg_lat);
        return [gg_lng, gg_lat]
    }

    //成功
  },
  mounted () {
     this.baiduMap();
     this.bd09_to_gcj02(120.21937542,30.25924446);
    
  }

}

</script>

<style scoped>
  .baidumap{
    width: 100%;height: 500px;
    margin: 0; padding: 0;
  }
</style>
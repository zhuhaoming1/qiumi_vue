<template>
  <div id="app">
    <div class="hd-wrap">
      <div class="idx-hd">
        <span class="back"><img src="../src/img/bc.png" alt=""></span>
        <h1>每日心水专区</h1>
        <span class="service">在线客服</span>
      </div>
      <div class="idx-nav">
       <!--  <ul>
         <li class="router-link-active" @click="change($event)"><router-link to="/first">每日心水</router-link></li>
         <li @click="change($event)"><router-link to="/jingcai">竞彩专区</router-link></li>
         <li @click="change($event)"><router-link to="/experts">专家</router-link></li>
         <li @click="change($event)"><router-link to="/guanzhu">关注</router-link></li>
         <li @click="change($event)"><router-link to="/buy">已购买</router-link></li>
       </ul> -->
         <ul @click='setSelected()'>
           <li v-for="(item,index) in arr" :class="item.path==selected?'router-link-active':''">
              <router-link :to="{path:item.path}" >{{item.name}}</router-link>
            </li>
         </ul>
      </div>
      </div>
    <router-view class="view"></router-view>
  </div>
</template>

<script>
    import first from './component/first.vue'

    export default {
      name: 'app',
      data () {
        return {
          selected:'/first',
          arr: [
            {name:'每日心水',path:'/first'},
            {name:'竞彩专区',path:'/jingcai'},
            {name:'专家',path:'/experts'},
            {name:'已购买',path:'/buy'}
          ]
        }      
      },
      methods: {
         change(e){
          var pele = e.srcElement.parentElement.parentNode.children;
          for(let i = 0; i<pele.length; i++){
            pele[i].className = "";            
          }
            e.srcElement.parentElement.className = 'router-link-active';
         },
         setSelected(){
            let hash=window.location.href;
            //this.selected=this.arr;//可在设置默认
            for(let i=0,len=this.arr.length;i<len;i++){
                let data=this.arr[i];
                if(hash.indexOf(data.path)!=-1){
                    this.selected=data.path;
                }
            }
         }　　　　
      }
    }
</script>



<template>
  <div class="wrapper">

    <div class="listcon" v-for="(item,index) in data">
      <div class="txtbox">
        <dl :author_id="item.id">
          <dt onclick="goauthor(380)">
            <img :src="item.authorPic">
          </dt>
          <dd class="h38" onclick="goarticle(item.id)">
            <span class="name">{{item.authorName}}</span>
            <span class="tm">今天 11:13</span>
          </dd>
        </dl>
        <span class="txt" onclick="goarticle(297895)">
          <i v-if='item.chargeable' class="vip">VIP</i><i v-for="(i,index) in item.portal_list">{{i.name}}</i>{{item.digest}}
        </span>
      </div>
      <div v-if="item.matches.length>0" v-for="(items,index) in item.matches" class="titbox" onclick="gomatch(115711)">
        <span>{{items.cup_name}}</span><span>{{items.home_team}} vs {{items.away_team}}</span><span>今天 10:30</span>
      </div>
    </div>

  </div>
</template>

<script type="text/javascript">
    export default {
      data () {
        return {data:""}
      },
      mounted: function() {
        var _self = this;
        this.$http.get('data/list.json?time=' + Math.random(),{          
            params: {
             
            }
        }).then(function(data) {
          console.log(data.data.result.artileList.Articles)
            _self.data = data.data.result.artileList.Articles;
        }, function(data) {

          console.log(data)

        })
      },
      format: function() {
        return '345';
      }
    }
</script>


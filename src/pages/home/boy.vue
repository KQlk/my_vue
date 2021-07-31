<template>
  <div>
    <tab-module :item="item"></tab-module>
  </div>
</template>

<script>
//页签组件
  import  tabModule from '@/components/tab-module'
  export default {
    name: "boy",
    components: {
      tabModule
    },
    data: function (){
      return {
        item:[]
      }
    },
    create(){
      this.initItems();
    },
    methods:{
      //初始化主页
      initItems(){
        this.getRecentPaintRequests('/index',{type:2,page:1,limit:10}).then(resp => {
          if(resp.code && resp.code == 200){
            this.items = resp.data;
          }
        })
      }
    }
  }
</script>

<style scoped>

</style>
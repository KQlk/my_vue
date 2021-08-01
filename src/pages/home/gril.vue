<template>
  <div>
    <tab-module :item="items"></tab-module>
  </div>
</template>

<script>
  //页签组件
  import tabModule from '@/components/tab-module'
  export default {
    name: "gril",
    components: {
      tabModule
    },
    data: function () {
      return {
        items:[]
      }
    },
    created(){
      this.initItems();
    },
    methods:{
      //初始化主页
      initItems(){
        this.getRequest('/index',{type:3,page:1,limit:10}).then(resp => {
          if (resp.code && resp.code == 200){
            this.items = resp.data();
          }
        })
      }
    }
}
</script>
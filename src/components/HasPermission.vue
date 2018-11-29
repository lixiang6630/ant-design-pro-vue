<template>
  <div v-show="visible">
    <slot></slot>
  </div>
</template>

<script>
export default {

  name: 'HasPermission',
  props: {
    hasPermission: String
  },
  data(){
    return{
      visible:false,
      roles:null
    }
  },created(){
    let that = this
    let roles =this.$store.getters.roles;
    // console.log(roles.permissions)
    let permission =roles.permissionList.join("/");
    if(permission.indexOf(that.hasPermission) !== -1){
      that.visible = true;
    }
    // for(var i=0;i< roles.permissionList.length;i++){
    //   if(roles.permissionList[i] === that.hasPermission){
    //     that.visible = true;
    //     break
    //   }
    // }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>

<template>
  <div>
    <h1 @click="changeAction">3333333333</h1>
    <div>
      <transition name="bounce">
        <p v-show="isshow">动画效果在这里</p>
      </transition>
    </div>
    <numlist nunm="789564"></numlist>
    <div class="borderimg">

    </div>

  </div>
</template>
<style lang="less">
  .borderimg{
    width: 200px;
    height:500px;
    border:1px solid;
    margin:20px;
    border-image: -webkit-linear-gradient( blue 10%, #ccc 50%) 30 31;
  }
</style>
<script>
  import numlist from './moveNum.vue'
    export default {
      components:{
        numlist
      },
        data(){
            return {
              isshow:true,
              numb:5432167
            }
        },
      computed:{
        umlength(){
            return this.numb.length
        }
      },
      beforeRouteEnter (to, from, next) {
        /* if(this.$store.state.scrolltop!=0){
         document.body.scrollTop = this.$store.state.scrolltop
         }*/
        next(vm=>{
          vm.$store.commit('changetit','hello3');
          vm.$store.commit('changeshowBar',false);
          if(vm.$store.state.scrolltop!=0){
            document.body.scrollTop = vm.$store.state.scrolltop
          }
        })
      },
      methods:{
        changeAction(){
            this.isshow = !this.isshow;
            var promise1 = new Promise(function(resolve){
                setTimeout(()=>{
                  resolve('first')
                },1000)
            });
            var promise2 = new Promise(function(resolve){
              setTimeout(()=>{
                resolve('second')
              },3000)
            });
          var promise3 = new Promise(function(resolve){
            setTimeout(()=>{
              resolve('three')
            },2000)
          });
          Promise.all([promise1,promise2,promise3]).then(function(resovearr){
            console.log(resovearr);
//            var map1 = resovearr.map()
          })
        }
      }
    }
</script>

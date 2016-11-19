#Vuejs知识总结

##Component组成
```Vue
<template>
	 <!--Vue2.0 只能存在一个根元素，所以通常做法是template下放入一个div做包裹-->
    <div>

    </div>
</template>

<script>
export default {
  /* 
    类型:'string'
    限制:只有作为组件选项时起作用。
    主要作用或影响：
    1.当有 vue-devtools, 未命名组件将显示成 <AnonymousComponent>, 这很没有语义。通过提供 name 选项，可以获得更有语义信息的组件树。
  */
  name: 'hello',
  /*
    类型:'string'
    主要作用或影响：
    1.用于接收来自父组件的数据如类型检测、对象允许配置高级选项,自定义校验和设置默认值。
  */
  props:{
      // 只检测类型
      height:Number,
      // 检测类型 + 其他验证
      age: {
        //检测类型
        type: Number,
        //设定默认值
        default: 0,
        //设置必须
        required: true,
        //添加自定义验证
        validator: function (value) {
            return value >= 0
        }
    }
  }
  /*  
      类型： Object | Function
      限制: 组件的定义只接受 function。
      主要作用或影响：
      1.
  */
  // 在ES6对象中函数可以省略function关键字
  data(){
      return {
        dataString:'text',  
        dataNumber:2,
        dataBool:false,
        dataObject:{
            Object1:'1',
            Object2:2,
        },
        dataArray:[10,20,30],
      }
  },
  /*
     类型： [key: string]: Function 
     限制：无
     主要作用或影响：
     1.声明组件中事件方法
  */
  methods:{
      plus:function(){
          //this 自动绑定为vue实例
          this.dataNumber++
      }
  },
  /*
    类型：[key: string]: string | Function | Object
    限制：无
    主要作用或影响：
    1.一个对象，键是需要观察的表达式，值是对应回调函数。值也可以是方法名，或者包含选项的对象。Vue 实例将会在实例化时调用 $watch()，遍历 watch 对象的每一个属性。
  */
  watch:{
    dataString: function (val, oldVal) {
      console.log('new: %s, old: %s', val, oldVal)
    },
    dataNumber:'plus',
  },
  /*
    类型：[key: string]: Function | { get: Function, set: Function }
    限制：无
    主要作用或影响：
    1.当组件内属性需要太多逻辑时，为保证模板的简单及逻辑清晰，我们应当使用计算属性
  */
  computed:{
    // 仅读取，值只须为函数
    aDouble: function () {
      return this.dataNumber * 2
    },
    // 读取和设置
    aPlus: {
      get: function () {
        return this.dataNumber + 1
      },
      set: function (v) {
        this.dataNumber = v - 1
      }
    }
  },
  /*
    类型：Function
    主要作用或影响：
    1.是例已经创建完成之后调用。在这一步，实例已完成以下的配置:数据观测(data observer),属性和方法的运算，watch/event事件回调。然而，挂载阶段还没开始，$el属性目前不可见
  */
  created:{
    console.log('component created!')
  },
  /*
    类型：Object
    限制：官方建议对于自定义签名遵循[W3C规则](https://www.w3.org/TR/custom-elements/#concepts)
    主要作用或影响：
    1.引用其他功能组件
  */
  components:{
    "nv-header": require('../components/header.vue'),
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<!-- -->
<style lang="less" scoped>
</style>
```
#Vue-router
前端路由控制
##在Component组件中的应用
```Vue
<script>
  /* 
    类型:'function'
    限制:
    主要作用或影响：
    1.当有 vue-devtools, 未命名组件将显示成 <AnonymousComponent>, 这很没有语义。通过提供 name 选项，可以获得更有语义信息的组件树。
  */
  beforeRouteEnter(to,from,next){
    console.log('beforeRouteEnter'),
    getPost(to.params.id, (err, post) => 
      if (err) {
        // display some global error message
        next(false)
      } else {
        next(vm => {
          vm.post = post
        })
      }
    })
  }
</script>
```
# transmit
Vue不同组件之间的通信方式 🙉
添加: 父往子中传递参数还可以用到 provide/inject方法
其中在父元素中
export default {
  provide: {
    Num: 100,
    ID: 1000
  },
}
在子元素中
inject: ["Num", "ID"]
子元素中可以取到父元素中的Num，ID 
console.log(this.Num, this.ID);

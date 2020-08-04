<template>
  <div class="largetest">
    Testing
    <!-- <img src="../assets/step1bgi.jpg" /> -->
  </div>
</template>

<script>
import Shepherd from "shepherd.js";
export default {
  name: "ShepherdExample",
  data() {
    return {
      img: require("../assets/step1bgi.jpg")
    };
  },
  mounted() {
    //Vue.nextTick用于延迟执行一段代码，它接受2个参数（回调函数和执行回调函数的上下文环境），如果没有提供回调函数，那么将返回promise对象。
    this.$nextTick(() => {
      const tour = new Shepherd.Tour({ //新建一个引导层事件
        defaultStepOptions: {//一些全局的配置
          cancelIcon: {//是否为每个引导框添加关闭按钮(可以单独添加也可以全局添加)
            enabled: false
          },
          classes: "class-1 class-2",//默认的样式
          scrollTo: { behavior: "smooth", block: "center" }//引导框切换的方式，平滑切换，居中位置显示
        },
        useModalOverlay: true//是否显示背景的遮罩层
      });
      //添加引导步骤，可添加多个
      tour.addStep({
        //title:"", 可选属性，引导框的标题
        text: `<div class="tipstep1"></div>`,//引导框的文本内容，可以使用HTML代码
        attachTo: {//引导框依附的div,可以用类名或ID确定
          element: ".test",//要依附的div的名称
          on: "right"//引导框显示在div的哪个位置
        },
        cancelIcon: {//单独的引导框关闭按钮，显示位置为title右边
          enabled: true,
          label: "1111"
        },

        buttons: [//引导框的按钮，可添加多个，靠右依次排列
          {
            action() {//按钮的功能函数
              return this.next();
            },
            text: "下一步"
          }
        ],
        id: "creating"//引导框的唯一识别ID，用来在外部控制该引导框，比如移除某个引导框的时候使用
      });
      tour.addStep({
        text: `<div class="tipstep2"></div>`,
        attachTo: {
          element: ".test1",
          on: "left"
        },
        cancelIcon: {
          enabled: true,
          label: "1111"
        },
        buttons: [
          {
            action() {
              return this.back();
            },
            classes: "shepherd-button-secondary", //按钮的样式
            text: "上一步"
          },
          {
            action() {
              return this.next();
            },
            text: "完成"
          }
        ],
        id: "creating2"
      });
      tour.start();//开始运行引导流程
    });
  }
};
</script>
<style lang="less" >
.shepherd-element /deep/.shepherd-content {
  border-radius: 5px;
  outline: none;
  padding: 0;
  border-radius: 5px;
  background: rgba(80, 80, 80, 0);
}
.shepherd-header /deep/.shepherd-cancel-icon {
  background: transparent;
  border: none;
  /* color: hsla(0,0%,50.2%,.75); */
  color: rgb(80, 80, 80, 0.75);
  font-size: 2em;
  cursor: pointer;
  font-weight: 400;
  margin: 0;
  padding: 0;
  transition: color 0.5s ease;
  span:hover {
    color: black;
    transition: color 0.5s ease;
  }
}
.shepherd-content /deep/ .shepherd-text {
  color: rgba(0, 0, 0, 0.75);
  font-size: 2rem;
  overflow: auto;
  line-height: 1.3em;
  max-height: 100vh;
  padding: 0px;
}
.shepherd-content /deep/.shepherd-footer {
  background-color: rgba(0, 0, 0, 0);
  border-bottom-left-radius: 5px;
  border-bottom-right-radius: 5px;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: end;
  -ms-flex-pack: end;
  justify-content: flex-end;
  padding: 0.75rem 0.75rem;
}
.tipstep1 {
  width: 950px;
  height: 500px;
  background-image: url(../assets/step3bgi.png);
}
.tipstep2 {
  width: 950px;
  height: 500px;
  background-image: url(../assets/step2bgi.jpg);
}

// .shepherd-element{
//   // background: none!important;;
//   // border-radius: none!important;
//   // box-shadow: none!important;
//   // /* max-width: 400px; */
//   // border: none!important;
//   opacity: 0;
//   outline: none;
//   transition: opacity 0.3s, visibility 0.3s;
//   visibility: hidden;
//   width: 100%;
//   z-index: 9999;
// }
</style>

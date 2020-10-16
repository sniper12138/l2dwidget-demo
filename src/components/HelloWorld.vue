<template>
  <div class="hello">
    <div class="text">
      <h1>{{ msg }}</h1>
      <p>
        For a guide and recipes on how to configure / customize this project,<br />
        check out the
        <a href="https://cli.vuejs.org" target="_blank" rel="noopener"
          >vue-cli documentation</a
        >.
      </p>
      <h3>Installed CLI Plugins</h3>
      <ul>
        <li>
          <a
            href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-babel"
            target="_blank"
            rel="noopener"
            >babel</a
          >
        </li>
      </ul>
      <h3>Essential Links</h3>
      <ul>
        <li>
          <a href="https://vuejs.org" target="_blank" rel="noopener"
            >Core Docs</a
          >
        </li>
        <li>
          <a href="https://forum.vuejs.org" target="_blank" rel="noopener"
            >Forum</a
          >
        </li>
        <li>
          <a href="https://chat.vuejs.org" target="_blank" rel="noopener"
            >Community Chat</a
          >
        </li>
        <li>
          <a href="https://twitter.com/vuejs" target="_blank" rel="noopener"
            >Twitter</a
          >
        </li>
        <li>
          <a href="https://news.vuejs.org" target="_blank" rel="noopener"
            >News</a
          >
        </li>
      </ul>
      <h3>Ecosystem</h3>
      <ul>
        <li>
          <a href="https://router.vuejs.org" target="_blank" rel="noopener"
            >vue-router</a
          >
        </li>
        <li>
          <a href="https://vuex.vuejs.org" target="_blank" rel="noopener"
            >vuex</a
          >
        </li>
        <li>
          <a
            href="https://github.com/vuejs/vue-devtools#vue-devtools"
            target="_blank"
            rel="noopener"
            >vue-devtools</a
          >
        </li>
        <li>
          <a href="https://vue-loader.vuejs.org" target="_blank" rel="noopener"
            >vue-loader</a
          >
        </li>
        <li>
          <a
            href="https://github.com/vuejs/awesome-vue"
            target="_blank"
            rel="noopener"
            >awesome-vue</a
          >
        </li>
      </ul>
    </div>
    <button class="reset" @click="initModel">换个人物</button>
  </div>
</template>

<script>
import { L2Dwidget } from "live2d-widget";
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      L2Ddatas: [
        "shizuku",
        "tororo",
        "unitychan",
        "wanko",
        "z16",
        "miku",
        "ni-j",
        "nico",
        "nipsilon",
        "nito",
        "haruto",
        "chitose",
        "hibiki",
        "hijiki",
        "izumi",
        "koharu",
      ],
      modelUrl: "",
      opt: {
        model: {
          jsonPath: "",
        },
        display: {
          position: "right", //定位
          width: 400, //宽度
          height: 1400, //高度
          hOffset: document.body.clientWidth / 2 - 200, //左右
          vOffset: document.body.clientHeight / 2 - 700, //上下
        },
        mobile: {
          show: false,
        },
        log: false,
        react: {
          // 设置透明度
          opacityDefault: 1,
          opacityOnHover: 0.5,
        },
      },
    };
  },
  mounted() {
    this.initModel()
  },
  methods: {
    random(min, max) {
      if (max == null) {
        max = min;
        min = 0;
      }
      return min + Math.floor(Math.random() * (max - min + 1));
    },
    initModel() {
      let model = this.L2Ddatas[this.random(0, this.L2Ddatas.length - 1)];
      let modelUrl = `https://cdn.jsdelivr.net/gh/wangsrGit119/wangsr-image-bucket/L2Dwidget/live2d-widget-model-${model}/assets/${model}.model.json`;
      this.opt.model.jsonPath = modelUrl;
      L2Dwidget.init(this.opt);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
.hello {
  .text {
    pointer-events: none;
    -webkit-user-select: none;
    -moz-user-select: none;
    user-select: none;
    -webkit-filter: blur(10px);
    filter: blur(10px);
  }
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.reset {
  display: inline-block;
  margin-bottom: 0;
  font-weight: 400;
  text-align: center;
  vertical-align: middle;
  -ms-touch-action: manipulation;
  touch-action: manipulation;
  cursor: pointer;
  background-image: none;
  border: 1px solid transparent;
  white-space: nowrap;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  height: 32px;
  padding: 0 15px;
  font-size: 14px;
  border-radius: 4px;
  transition: color 0.2s linear, background-color 0.2s linear,
    border 0.2s linear, box-shadow 0.2s linear;
  color: #fff;
  background-color: #2d8cf0;
  border-color: #2d8cf0;
  outline: none;
  line-height: 1.5;
  right: 100px;
  bottom: 100px;
  position: absolute;
  &:hover {
    background-color: #57a3f3;
    border-color: #57a3f3;
  }
}
</style>

<template>
  <div class="app">
    <vue-approval-progress :data-list="dataList"></vue-approval-progress>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      dataList: [
        [
          {
            title: "发起人",
            icon: "vapfont vap-top_icon4",
            headportrait: [
              "https://v3.cn.vuejs.org/logos.png",
              "https://v3.cn.vuejs.org/logos.png",
            ],
            iconLabel: "发",
            handlerInfo: [
              {
                name: "xxx",
                post: "UI设计师",
                approvalType: "",
              },
            ],
            desc:
              "转正时间到，申请转正，望领导批准！转正时间到，申请转正，望领导批准！转正时间到，申请转正，望领导批准！",
          },
        ],
        [
          {
            title: "或签",
            headportrait: ["https://v3.cn.vuejs.org/logos.png"],
            handlerInfo: [
              {
                name: "xxx",
                post: "部门主管",
                time: "2021-03-15  20:42:00",
                approvalType: "同意",
              },
            ],
            desc:
              "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxaaaaaaaaaaaaaaaaaaabbbbbbbbbbbbbbbbbbbbbbbccccccccccccccccccccdddddddddddddddddd",
          },
          {
            title: "",
            handlerInfo: [
              {
                name: "xxx",
                post: "商务主管",
                time: "2021-03-15  20:42:00",
                approvalType: "拒绝",
                approvalTypeColor: "red",
                timeColor: "red",
                stepList: "red",
              },
            ],
            desc: "该员工任职UI设计师，态度认真，故本人同意转正。",
          },
        ],
        [
          {
            title: "会签",
            headportrait: ["https://v3.cn.vuejs.org/logos.png"],
            handlerInfo: [
              {
                name: "xxx",
                post: "财务主管",
                time: "2021-03-15  20:42:00",
                approvalType: "同意",
              },
            ],
            desc: "",
          },
          {
            title: "",
            handlerInfo: [
              {
                name: "xxx",
                post: "行政主管",
                time: "2021-03-15  20:42:00",
                approvalType: "拒绝",
                approvalTypeColor: "red",
                timeColor: "red",
                stepList: "red",
              },
            ],
            desc: "该员工任职UI设计师，态度认真，故本人同意转正。",
            mark: "第2次审批",
            markColor:"red"
          },
        ],
        [
          {
            title: "抄送",
            handlerInfo: [
              {
                name: "xxx",
                post: "总裁",
                time: "2021-03-15  20:42:00",
                approvalType: "",
                icon: "vapfont vap-gou",
              },
              {
                name: "xxx",
                post: "副总裁",
                time: "2021-03-15  20:42:00",
                approvalType: "抄送",
                icon: "vapfont vap-gou",
              },
            ],
            desc: "",
          },
        ],
      ],
    };
  },
};
</script>

<style lang="scss">
.app {
}
</style>
